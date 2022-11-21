---
layout: post
title: "[ORACLE-SQL] ExamTopics 61~70"
subtitle: ORACLE
date: '2022-11-17 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/logo.png
---

1z0-071 Examtopics 61~70번 문제를 풀어보자.<br>
1차 3/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 61 ❌
---

Which three statements are true about inner and outer joins? (Choose three.)

A. A full outer join returns matched and unmatched rows.

B. Outer joins can be used when there are multiple join conditions on two tables.

C. A full outer join must use Oracle syntax.

D. Outer joins can only be used between two tables per query.

E. A left or right outer join returns only unmatched rows.

F. An inner join returns matched rows.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B, F

해설 :

A : 맞음.<br>
B : 맞음. <br>
C : 틀렸음. Oracle 문법 말고도 사용할 수 있다.<br>
D : 틀렸음. 여러개의 테이블도 가능하다.<br>
E : 틀렸음. 매치되는 행도 출력한다.<br>
F : 맞음.<br>

1차 시도 : A, D, F 틀림<br>
</div>
</details>

<br>

## Prob. 62 ❌
---

Which statement will execute successfully?

A.<br>
![prob62-a](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob62-a.png)

B.<br>
![prob62-b](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob62-b.png)

C.<br>
![prob62-c](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob62-c.png)

D.<br>
![prob62-d](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob62-d.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 :

`ORDER BY` 뒤에 오는 숫자는 칼럼을 뜻한다.<br>
알고는 있었는데 칼럼명이 숫자일 때 그걸 그대로 쓸 때에도 오류가 나는줄은 몰랐다 ...<br>

1차 시도 : C 틀림<br>
</div>
</details>

<br>

## Prob. 63 ⭕
---

Examine the description of the EMPLOYEES table:<br>
![prob63](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob63.png)

Which two queries return all rows for employees whose salary is greater than the average salary in their department? (Choose two.)

A.<br>
![prob63-a](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob63-a.png)

B.<br>
![prob63-b](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob63-b.png)

C.<br>
![prob63-c](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob63-c.png)

D.<br>
![prob63-d](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob63-d.png)

E.<br>
![prob63-e](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob63-e.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, E

해설 :

A : 틀렸음. `WHERE` 절에는 그룹 함수가 올 수 없다.<br>
B : 맞음.<br>
C : 틀렸음. `WHERE` 절은 단일 행 서브쿼리를 요구하지만, 해당 서브쿼리는 다중 행 서브쿼리이다.<br>
D : 틀렸음. C를 개선하여 다중 행 서브쿼리로 만들었지만, 이번에는 문제 의도와 맞지 않음. 자신의 부서의 평균 급여 뿐만 아니라 다른 부서의 평균 급여보다 높으면 전부 출력됨.<br>
E : 맞음.<br>

1차 시도 : B, E 맞음<br>
</div>
</details>

<br>

## Prob. 64 ❌
---

Which three statements are true about the Oracle join and ANSI join syntax? (Choose four.)

A. The Oracle join syntax supports creation of a Cartesian product of two tables.

B. The Oracle join syntax only supports right outer joins.

C. The SQL:1999 compliant ANSI join syntax supports creation of a Cartesian product of two tables.

D. The Oracle join syntax performs less well than the SQL:1999 compliant ANSI join syntax.

E. The Oracle join syntax supports natural joins.

F. The Oracle join syntax performs better than the SQL:1999 compliant ANSI join syntax.

G. The SQL:1999 compliant ANSI join syntax supports natural joins.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>

Answer : A, C, E, G

해설 :

원래는 3개를 고르는 문제였으나, 4개로 정정.

A : 맞음.<br>
B : 틀렸음. 오라클에서는 `FROM` 절의 테이블에 `(+)` 를 붙여줌으로써 right, left join을 지정할 수 있음.<br>
C : 맞음.<br>
D : 틀렸음. 성능에 관해서는 무엇이 낫다고 할 수 없음.<br>
E : 맞음.<br>
F : 틀렸음. 성능에 관해서는 무엇이 낫다고 할 수 없음.<br>
G : 맞음.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/9432-exam-1z0-071-topic-1-question-248-discussion/)

1차 시도 : C, E, G 틀렸다 침<br>
</div>
</details>

<br>

## Prob. 65 ❌
---

Which two are true about the NVL, NVL2, and COALESCE functions? (Choose two.)

A. NVL must have expressions of the same data type.

B. NVL can have any number of expressions in the list.

C. NVL2 can have any number of expressions in the list.

D. COALESCE stops evaluating the list of expressions when it finds the first non-null value.

E. The first expression in NVL2 is never return
ed.

F. COALESCE stops evaluating the list of expressions when it finds the first null value.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D, E

해설 :

A : 틀렸음. 두 표현식은 같지 않을 경우, 하나의 데이터 타입으로 형변환되고, 형변환 될 수 없을 경우 에러를 반환함.<br>
B : 틀렸음. 두 개의 표현식을 인수로 가짐.<br>
C : 틀렸음. 세 개의 표현식을 인수로 가짐.<br>
D : 맞음.<br>
E : 맞음.<br>
F : 틀렸음. `NULL` 이 아닌 값을 찾을 때 멈추고 반환함.<br>

1차 시도 : A, D 틀림<br>
</div>
</details>

<br>

## Prob. 66 ❌
---

Examine this statement:<br>
![prob66](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob66.png)

What is returned upon execution?
A. an error
B. 2 rows
C. 0 rows
D. 1 row

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 :

`UNION` 은 '중복된 값을 배제한 합집합'을 출력한다.<br>
즉, 위와 아래의 결과 값은 중복되므로 하나의 행만 출력된다.<br>

1차 시도 : B 틀림<br>
</div>
</details>

<br>

## Prob. 67 ❌
---

Examine this statement:<br>
![prob67](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob67.png)

What is returned upon execution?
A. an error
B. 2 rows
C. 0 rows
D. 1 row

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 :

`INTERSECT` 는 교집합을 의미하는데 차집합이랑 헷갈렸다 ...<br>
바본가 ...<br>

1차 시도 : C 틀림<br>
</div>
</details>

<br>

## Prob. 68 ⭕
---

Which two statements execute successfully? (Choose two.)

A.<br>
![prob68-a](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob68-a.png)

B.<br>
![prob68-b](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob68-b.png)

C.<br>
![prob68-c](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob68-c.png)

D.<br>
![prob68-d](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob68-d.png)

E.<br>
![prob68-e](/assets/img/study_Oracle/2022-11-17-[ORACLE-SQL]_ExamTopics_61~70/prob68-e.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B

해설 :

`TO_DATE` 함수는 `String` 을 `Date` 로 바꾸는 함수이고,<br>
`TO_CHAR` 함수는 `Date` 를 `String` 으로 바꾸는 함수이다.<br>
<br>
C : `TO_CHAR` 의 인수로 `String` 이 들어와서 오류.<br>
D : `TO_CHAR` 의 인수로 `String` 이 들어와서 오류.<br>
E : `TO_CHAR` 의 인수로 `String` 이 들어와서 오류.<br>

1차 시도 : A, B 맞음<br>
</div>
</details>

<br>

## Prob. 69 ❌
---

An Oracle Database session has an uncommitted transaction in progress which updated 5000 rows in a table.
In which three situations does the transaction complete thereby committing the updates? (Choose three.)

A. when a CREATE TABLE AS SELECT statement is issued in the same session but fails with a syntax error

B. when a DBA issues a successful SHUTDOWN TRANSACTIONAL statement and the user then issues a COMMIT

C. when the session logs out successfully

D. when a CREATE INDEX statement is executed successfully in the same session

E. when a DBA issues a successful SHUTDOWN IMMEDIATE statement and the user then issues a COMMIT

F. when a COMMIT statement is issued by the same user from another session in the same database instance

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, C, D

해설 :

A : ~~맞음.~~ 틀렸음. 본래 `DDL` 은 오류가 발생하여도 묵시적으로 `COMMIT`이 실행되나, 문법적으로 틀린 쿼리는 파싱 단계에서 실행이 중지되기 때문에 틀렸다.<br>
다음은 `DDL` 의 프로세스이다.
  1. Parsing of the DDL statement
  2. Commit
  3. Execute the DDL
  4. Commit

B : 맞음. 마지막 트랜잭션이 유저에 의해 커밋되거나, 롤백되고 나서 세션이 종료된다.<br>
C : ~~틀렸음.~~ 맞음. 정상적으로 세션을 종료할 경우, 자동으로 커밋됨.<br>
D : 맞음. `DDL` 실행 시 자동 커밋됨.<br>
E : 틀렸음. 존재하는 모든 트랜잭션은 롤백되고, 유저의 연결은 끊어지기 때문에 `COMMIT` 을 할 수 조차 없다.<br>
F : 틀렸음. 다른 세션에서의 커밋은 의미가 없다.<br>

```sql
SHUTDOWN [NORMAL|IMMEDIATE|TRANSACTIONAL|ABORT]
```
* `NORMAL(DEFAULT)`
  + 이후의 새로운 커넥션들을 모두 거부한다.
  + 데이터베이스가 종료되기 전에, 현재 연결되어있는 모든 유저가 연결을 끊기를 기다린다.
* `IMMEDIATE`
  + 이후의 새로운 커넥션들 뿐만 아니라, 새로운 트랜잭션도 모두 거부한다.
  + 커밋되지 않은 트랜잭션들은 모두 롤백된다.
    - 커밋되지 않은 긴 트랜잭션이 존재할 경우, 해당 셧다운은 빠르게 처리되지 않을 수 있다.
  + 유저들이 스스로 연결을 끊기까지 기다리지 않고 활성화되어 있는 모든 트랜잭션을 묵시적으로 롤백하고 모든 유저들의 연결을 끊는다.
* `TRANSACTIONAL`
  + 이후의 새로운 커넥션들 뿐만 아니라, 새로운 트랜잭션도 모두 거부한다.
  + 모든 트랜잭션들이 완료될 때까지 기다리기 때문에, 시간이 상당히 걸릴 수 있다.
  + 트랜잭션이 모두 완료되면, 연결되어 있던 모든 클라이언트들의 연결이 끊어진다.
* `ABORT`
  + 이후의 새로운 커넥션들 뿐만 아니라, 새로운 트랜잭션도 모두 거부한다.
  + 모든 현재 데이터베이스 클라이언트의 SQL문은 즉시 종료된다.
  + 커밋되지 않은 트랜잭션들이 롤백되지 않고 종료된다.
  + 유저들이 연결을 끊을때까지 기다리지 않고 묵시적으로 모든 유저들의 연결을 끊는다.

강도로 따지면 다음과 같다고 생각할 수 있다.<br>
`ABORT(바로 즉시 종료)` > `IMMEDIATE(롤백은 함)` > `TRANSACTIONAL(트랜잭션 종료까지 기다림` > `NORMAL(유저가 스스로 종료할때까지 기다림)`<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/20174-exam-1z0-071-topic-2-question-38-discussion/)

[SHUTDOWN에 관한 Oracle Docs](https://docs.oracle.com/database/121/ADMIN/start.htm#ADMIN11159)

1차 시도 : A, B, D 틀림<br>
</div>
</details>

<br>

## Prob. 70 ⭕
---

Which two are true about using constraints? (Choose two.)

A. NOT NULL can be specified at the column and at the table level.

B. A table can have only one PRIMARY KEY and one FOREIGN KEY constraint.

C. A FOREIGN KEY column in a child table and the referenced PRIMARY KEY column in the parent table must have the same names.

D. PRIMARY KEY and FOREIGN KEY constraints can be specified at the column and at the table level.

E. A table can have multiple PRIMARY KEY and multiple FOREIGN KEY constraints.

F. A table can have only one PRIMARY KEY but may have multiple FOREIGN KEY constraints.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D, F

해설 :

A : 틀렸음. `NOT NULL` 은 칼럼 레벨에서 적용 가능함.<br>
B : 틀렸음. `PK` 는 하나를 가질 수 있지만, `FK` 갯수 제한이 없음.<br>
C : 틀렸음. 칼럼 명은 달라도 되고 값만 일치하면 됨.<br>
D : 맞음.<br>
E : 틀렸음. `PK` 는 하나만 허용됨.<br>
F : 맞음.<br>

1차 시도 : D, F 맞음<br>
</div>
</details>

<br>