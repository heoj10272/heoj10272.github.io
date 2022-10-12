---
layout: post
title: "[ORACLE] 데이터 조작을 위한 DML과 트랜잭션 이해"
subtitle: Oracle
date: '2022-10-11 01:06:00 +0900'
category: study
tags: oracle
image:
  path: /assets/img/study_Oracle/2022-10-11-[ORACLE]_데이터 조작을 위한 DML과 트랜잭션 이해/logo.png
---

데이터 조작을 위한 DML과 트랜잭션 이해

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

# DML (Transaction) 처리

---

- DML 문은 다음의 상황에 실행된다 :
    - 테이블에 새 행 추가
    - 테이블의 기존 행 수정
    - 테이블에서 기존 행 제거
- 트랜잭션은 논리적 작업 단위를 형성하는 DML 문의 모음으로 구성
    - 주요 특성 : ACID
        - A : Atomicity, 원자성
        - C : Consistency, 일관성
            - 일관성을 유지하는 대표적인 기능이 undo
        - I : Isolation, 고립성
        - D : Durability, 영구성
    - 예
        - ATM 기기
        - 은행 거래
        - 주식 거래
        - 마일리지 적립 작업
    

다음의 쿼리를 실행했다고 생각해보자.

```sql
UPDATE  emp
   SET  sal = sal*1.1
 WHERE  empno = 7788;
```

이 경우 사원 번호가 7788인 사원의 봉급은 10% 인상된다.

원래 봉급이 3000이었다면, 3300으로 업데이트가 된다.

```sql
SELECT  *
  FROM  v$transaction;
```

위 쿼리문을 통해 실행중인 트랜잭션을 확인할 수 있다.

현재 `UPDATE` 만이 실행중이므로, 한 건의 트랜잭션이 출력될 것이다.

또한 이 때 원래 봉급이었던 3000은 `UNDO` 세그먼트에 보관된다.

```sql
SELECT  *
  FROM  v$rollstat;
```

위 쿼리를 실행하면 0번부터 10번까지의 세그먼트 행이 출력되는데, 0번은 시스템것이라 제외하면 된다.

해당 `UNDO` 세그먼트는 1번부터 10번중에서 랜덤으로 배치된다.

`XACTS` , 즉 액티브 트랜잭션 칼럼에서 확인할 수 있다.

아무런 트랜잭션을 실행하지 않았을때는 0일 것이므로 1로 출력된 세그먼트에 `UNDO` 세그먼트가 배치되었음을 알 수 있다.

```sql
rollback;
```

이 때 `rollback` 을 실행하면, 실행중인 트랜잭션은 종료되고 `UNDO` 세그먼트로부터 값을 복구한다.

즉, `v$transaction` 을 조회하면 목록에서 기존의 트랜잭션은 사라지고, `v$rollstat` 에서의 4번 세그먼트에서 `XACTS` 의 값이 0으로 되돌아간다.

## INSERT

---

- INSERT 문을 사용하여 테이블에 새로운 행들을 추가할 수 있다.

```sql
INSERT  INTO table[(column[, column...])]
VALUES  (value [, value...]);
```

만약 칼럼을 생략했을 경우, 대상 테이블의 모든 칼럼이 대상이 된다.

만약 대상 테이블의 일부 칼럼만 적었을 경우, 나머지 칼럼들의 값은 `NULL` 이 된다.

- 이러한 문법을 통해, 한 번에 단 하나의 행만 삽입할 수 있다.

```sql
INSERT  INTO departments(department_id, department_name, manager_id, location_id)
VALUES                  (70, 'Public Relations', 100, 1700);
```

> 1 rows inserted
> 

위 규칙에 따라, 위 쿼리문은 해당 테이블의 모든 칼럼을 써주었지만 생략 가능하다.

다만, `VALUES` 이하로 값을 넣을 때 해당 테이블의 제약조건을 알고 있을 필요가 있다.

`departments` 테이블에서 `department_id` 는 해당 테이블의 `PK` 이다.

이는 즉 중복이 불가능하며 `NULL` 이 될 수 없음을 뜻한다.

즉 이 때 값을 생략하거나, 이미 존재하는 값을 넣으려고 할 경우 제약조건을 위반했기 때문에 오류가 발생하게 된다.

또한 데이터타입과 크기도 반드시 유념해야한다.

정리하자면 다음과 같다.

- INSERT 시 주의해야할 점
    1. 제약조건
    2. Datatype
        1. ‘desc table명’ 을 통해 알아볼 수 있다.
    3. size
    4. Not Null 

- Implicit method : 열 리스트에서 열을 생략

```sql
INSERT  INTO departments (department_id, department_name)
VALUES                   (30, 'Purchasing');
```

암시적 `NULL` 처리를 뜻한다.

`manager_id`, `location_id` 는 `NULL` 을 허용하기 때문에, 해당 값은 칼럼 목록에서 생략 가능하며 자동 `NULL` 처리 된다.

- Explicit method : VALUES 절에서 NULL 키워드를 지정

```sql
INSERT  INTO departments
VALUES  (100, 'Finance', NULL, NULL);
```

명시적 `NULL` 처리를 뜻한다.

칼럼을 모두 생략했기 때문에, 모든 칼럼이 대상이 된다.

`manager_id`, `location_id` 에 명시적으로 `NULL` 이 들어가도록 `VALUES` 절에 선언하였다.

### 다른 테이블의 행 복사

---

- INSERT 문을 subquery로 작성:

```sql
INSERT  INTO sales_reps(id, name, salary, commission_pct)
        SELECT  employee_id, last_name, salary, commission_pct
          FROM  employees
         WHERE  job_id LIKE '%REP%'
```

> 4 rows inserted
> 
- VALUES 절을 사용 안함
- INSERT 절의 열 개수를 subquery의 열 개수와 일치
- subquery에서 반환되는 모든 행을 sales_reps 테이블에 삽입
- Datatype, size 명심

## UPDATE

---

- UPDATE 문을 사용하여 테이블의 기존 값을 수정:

```sql
UPDATE  table
   SET  column = value[, column = value, ...]
[WHERE  condition];
```

필요한 경우 두 개 이상의 행을 갱신할 수 있다.

- WHERE 절을 지정하면 특정 행에서 값이 수정:

```sql
UPDATE  employees
   SET  department_id = 50
 WHERE  employee_id = 113;
```

- WHERE 절을 생략하면 테이블의 모든 행에서 값이 수정:

```sql
UPDATE  compy_emp
   SET  department_id = 110;
```

- 열값을 NULL로 갱신하려면 SET column_name=NULL을 지정

### Subquery를 이용한 여러 열 변경

---

- 사원 113의 직무와 급여를 사원 205와 일치하도록 갱신

```sql
UPDATE  employees
   SET  job_id = (SELECT  job_id
                    FROM  employees
                   WHERE  employee_id = 205),
        salary = (SELECT  salary
                    FROM  employees
                   WHERE  employee_id = 205)
 WHERE  employee_id = 113;
```

## DELETE

---

- DELETE 문을 사용하여 테이블에서 기존 행을 제거할 수 있다.

```sql
DELETE [FROM] table
[WHERE] condition]
```

```sql
DELETE  FROM departments
 WHERE  department_name = 'Finanace'

-- 부서명이 Finance인 모든 행 제거
```

### 다른 테이블 기반의 데이터 삭제

---

- DELETE 문에서 subquery를 사용하여 다른 테이블의 값을 기반으로 테이블에서 행을 제거

```sql
DELETE  FROM employees
 WHERE  department_id = (SELECT  department_id
                           FROM  departments
                          WHERE  department_name
                                 LIKE '%Public%');
```

서브쿼리를 사용하는 이유는 현재로선 알 수 없는 정보를 쿼리를 통해서 알아오기 위함이다.

따라서 서브쿼리를 통해서 알아온 정보를 통해 행을 삭제할수도 있다.

# 데이터베이스 트랜잭션의 시작과 종료

---

- 데이터베이스 트랜잭션은 다음 중 하나로 구성 :
    - 데이터를 일관되게 변경하는 여러 DML 문 → 기본적으로 커밋 명시, 자동 커밋 설정 가능
    - 하나의 DDL 문 → 자동 커밋
    - 하나의 DCL(데이터 제어어) 문 → 자동 커밋
- 첫 번째 DML SQL 문이 실행될 때 시작
- 다음 상황 중 하나가 발생하면 종료 :
    - COMMIT 또는 ROLLBACK 문 실행
    - DDL 또는 DCL 문 실행(자동 커밋)
    - 유저가 SQL Developer 또는 SQL*Plus를 종료
    - 시스템 중단 → 자동으로 rollback

# COMMIT과 ROLLBACK 구문

---

- COMMIT and ROLLBACK 구문의 특징
    - 데이터 일관성 보장
    - 변경사항을 영구 적용하기 전에 데이터 변경사항 검토
    - 논리적으로 관련된 작업 그룹화 = Tx(트랜잭션)

세션에서는 `DML` 을 던지는 모든 순간을 하나로 본다.

따라서 세션당 트랜잭션이 하나만 존재할 수 있으며, 이를 논리적 작업 그룹화라고 한다.

AUDS

- 데이터 일관성 보장
    - ‘SCOTT’ 유저로 두 개의 세션을 연다.
        - `v$session` 에서 확인 가능
    - 하나의 세션에서, `UPDATE` 를 통해 값을 변경한다.
    - 다른 세션에서 그 값을 조회하면, 변경하기 전 값이 보인다.
    - 다른 세션에서 그 값을 변경하려고 하면 세션이 멈춰버린다.
    
    이를 **‘락 충돌’**이라고 한다.
    
    모든 `DML` 은 락을 보유하는데, 기본적으로 트래잭션을 던지면 락이 성립된다.
    
    이것을 **‘TMTX 락**’이라고 한다.
    
    다음 쿼리를 살펴보자.
    
    ```sql
    SELECT  sid, type
      FROM  v$lock
     WHERE  sid in (73, 79) AND type <> 'AE';
    
    -- 73, 79는 현재 실행되고 있는 세션 id이다.
    ```
    
    |  | SID | TYPE |
    | --- | --- | --- |
    | 1 | 73 | TM |
    | 2 | 79 | TM |
    | 3 | 79 | TX |
    | 4 | 73 | TX |
    
    여기서 각 용어를 먼저 알아보자.
    
    - TM : table level lock
    - TX : row level lock
    
    현재 상황은 두 세션에서 `DML` 을 던졌지만, 73번 세션에서 쿼리를 먼저 던졌고, 79번은 충돌이 나서 대기중인 상황이다.
    
    이 lock은 `enqueue` 라는 곳에서 대기상태에 들어간다.
    
    이 대기상태는 첫 번째 세션에서 `COMMIT` 이나 `ROLLBACK` 을 할 때 까지 지속된다.
    
    다시 위 상황으로 돌아가자.
    
    - 73번 세션(먼저 실행한 세션)에서 `ROLLBACK` 을 한다.
    - 멈춰있던 79번 세션에서 바로 쿼리가 완료된다.
    - 즉, 대기중이었던 쿼리가 첫 번째 세션의 lock이 풀리자마자 잡아서 실행시킨 것이다.
    - 이 때 다시 락을 조회해보자.
    
    |  | SID | TYPE |
    | --- | --- | --- |
    | 1 | 79 | TX |
    | 2 | 79 | TM |
    - 73번 락은 `ROLLBACK` 되어 목록에서 사라지고, 79번 락만이 출력된다.
    
    위 사례가 `ACID` 중 `Consistency` 와 `Isolation` 을 보여준다.
    

# 명시적 트랜잭션 제어

---

그냥 `ROLLBACK` 을 실행시키면, 무조건 트랜잭션의 시작으로 돌아가게 된다.

하지만 중간에 `SAVEPOINT` 를 세우면, 각 `SAVEPOINT` 로 돌아가게 할 수 있다.

## Savepoint를 이용한 rollback

---

- SAVEPOINT 문을 사용하여 현재 트랜잭션에 마커 생성
- ROLLBACK TO SAVEPOINT 문을 사용하여 해당 마커로 롤백 수행

```sql
UPDATE  ...
SAVEPOINT update_done;
-- SAVEPOINT update_done succeeded.

INSERT  ...
ROLLBACK TO update_done;
-- ROLLBACK TO succeeded.
```

`SAVEPOINT` 도 `ROLLBACK` 이나 `COMMIT` 으로 트랜잭션을 끝내면 함께 사라진다.

# 명시적 트랜잭션 처리

---

- 자동 커밋은 다음 상황에서 발생
    - DDL 구문 사용시
    - DCL 구문 사용시
    - Exit 명령 사용시 자동 커밋
    
- SQL Developer 또는 SQL*Plus가 비정상적으로 종료되거나 시스템 failure가 발생된 경우 자동 롤백 발생

두 경우의 차이는 정상적으로 종료되었는지와, 비정상적으로 종료되었는지이다.

정상적으로 종료되는 전자는 자동 커밋, 비정상적으로 종료되는 후자는 자동 롤백이 된다.

# COMMIT or ROLLBACK 전 데이터 상태

---

- 이전의 데이터 상태를 복구할 수 있다
- 현재 유저는 SELECT 문을 사용하여 DML 작업의 결과를 확인할 수 있다
- 다른 유저는 현재 유저가 실행한 DML 문의 결과를 볼 수 없다 - 일관성
- 영향을 받는 행이 잠기므로 다른 유저가 영향을 받는 행의 데이터를 변경할 수 없다

# COMMIT 후 데이터 상태

---

- 데이터 변경사항이 데이터베이스에 저장된다 - 영속성
- 이전의 데이터 상태를 겹쳐쓴다
    - COMMIT이 되더라도 UNDO 데이터는 일정시간동안 남아있다
- 모든 유저가 결과를 확인할 수 있다
- 영향을 받는 행의 Lock이 해제되어 이러한 행을 다른 유저가 조작할 수 있다
- 모든 저장점(savepoint)이 지워진다

# ROLLBACK 후 데이터 상태

---

- ROLLBACK 문을 사용하여 보류 중인 모든 변경 사항을 폐기
    - 데이터 변경 완료
    - 이전 데이터 상태로 되돌림
    - 보유한 Lock 및 자원은 해제됨
    
    ```sql
    DELETE  FROM copy_emp;
    ROLLBACK;
    ```