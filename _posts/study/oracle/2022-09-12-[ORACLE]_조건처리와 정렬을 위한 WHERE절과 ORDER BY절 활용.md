---
layout: post
title: "[ORACLE] 조건처리와 정렬을 위한 WHERE절과 ORDER BY절 활용"
subtitle: Oracle
date: '2022-09-12 03:50:00 +0900'
category: study
tags: oracle
image:
  path: /assets/img/study_Oracle/2022-09-12-[ORACLE]_조건처리와 정렬을 위한 WHERE절과 ORDER BY절 활용/logo.png
---

WHERE절과 ORDER BY절에 대해서 알아보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

# WHERE절 이해

---

## WHERE절을 이용한 행 선택
---

* 중요
  + `WHERE` 절에는 `Alias` 를 사용할 수 없다.

- 선택되는 행 제한
    
    ```sql
    -- 부서번호 90에 소속된 사원정보(사번, 이름, 업무, 부서번호)를 출력하시오.
    SELECT  employee_id, last_name, job_id, department_id
      FROM  employees
     WHERE  department_id=90;
    ```
    
    ```sql
    SELECT  last_name, job_id, department_id
      FROM  employees
     WHERE  last_name = 'Whalen';
    
    ```
    
    ```sql
    SELECT  last_name
      FROM  employees
     WHERE  hire_date = '17-FEB-96';
    ```
    
- 문자열 및 날짜 값은 작은따옴표로 묶는다
- 문자 값은 대소문자를 구분하고 날짜 값은 형식을 구분
- 기본 날짜 표시 형식은 `DD-MON-RR`

각 행은 `FROM`→`WHERE`→`SELECT`의 순서로 처리된다.

요구사항에 따른 SQL문을 작성할때는 다음과 같이 하자.

```sql
  SELECT  -- 5. 출력할 칼럼 선정
    FROM  -- 1. 테이블 선정
   WHERE  -- 2. 조건문
GROUP BY  -- 3.
  HAVING  -- 4.
ORDER BY  -- 6.
```

이런식으로 미리 써놓고, 한 줄 한 줄을 요구사항대로 채우는 식으로 연습한다.

실제 실행 순서대로 채우자.

SQL문에서 키워드(`SELECT`, `FROM` …)과 구문은 대소문자 중 아무렇게나 써도 되지만, 규칙을 가지고 써야한다.

키워드는 대문자로, 구문은 소문자로 쓰는게 권장사항이다.

**다만, 저장된 Data(’Whalen’)는 대소문자를 구분한다.**

예를 들어, ‘Whalen’ 대신 ‘whalen’을 쓰면 결과가 제대로 출력되지 않는다.

기본 날짜 표시 형식은 `DD-MON-RR`이다.

날짜/달/년도로 년도는 YY를 사용하지 않고 RR을 사용한다.

다음 SQL문의 결과를 확인해보자

```sql
SELECT sysdate
  FROM dual; -- dual은 더미테이블이다.
```

| SYSDATE |
| --- |
| 21/07/10 |

위 결과 형식은 `RR/MM/DD` 이다.

즉, 위의 `DD-MON-RR` 형식으로 작성된 SQL문을 실행시키면 날짜 형식이 다르기 때문에 결과가 나오지 않을 것이다.

날짜 형식은 환경에 따라 다를 수 있다.

날짜 형식은 다음 문장을 통해 변경할 수 있다.

```sql
ALTER  session 
  SET  nls_date_format='DD-MON-RR' -- nls = national language support
```

이렇게 하면 위의 SQL문을 그대로 사용해도 결과가 출력이 된다.

다음의 오류가 발생할 수 있다.

```sql
ORA-01843: 지정한 월이 부적합합니다.
01843. 00000 - "not a valid month"
```

이 경우 현재 환경이 한글로 되어있기 때문에, FEB를 월로 인식하지 못해서 발생하는 오류이다.

```sql
 WHERE  hire_date = '17-2월-96';
```

위와 같이 2월 등으로 고치면 잘 실행된다.

### 비교 연산자

---

| 연산자 | 의미 |
| --- | --- |
| = | 같음 |
| > | 큼 |
| ≥ | 크거나 같음 |
| < | 작음 |
| ≤ | 작거나 같음 |
| <> | 같지 않음 |
| BETWEEN …AND… | 두 값의 사이(두 값 포함) |
| IN(set) | set에 해당하는 값과 같은 결과들만 출력 |
| LIKE | 패턴에 맞는 값 출력 |
| IS NULL | null 값인 값만 출력 |

`LIKE`는 뒤에 오는 패턴에 맞는 값이 출력된다.

`NULL`은 비교가 되지 않는 값이므로, `=` 대신에 `IS` 를 써야한다.

```sql
-- 사원정보 테이블에서 급여가 3000이하인 사원의 성과 급여를 출력하시오.
SELECT  last_name, salary -- 3.
  FROM  employees -- 1.
 WHERE  salary <= 3000; -- 2.
```

|  | LAST_NAME | SALARY |
| --- | --- | --- |
| 1 | Matos | 2600 |
| 2 | Vargas | 2500 |

```sql
SELECT  last_name, salary
  FROM  employees
 WHERE  salary BETWEEN 2500 AND 3500; -- 2500과 3500도 값에 포함된다.
```

|  | LAST_NAME | SALARY |
| --- | --- | --- |
| 1 | Rajs | 3500 |
| 2 | Davies | 3100 |
| 3 | Matos | 2600 |
| 4 | Vargas | 2500 |

```sql
SELECT  employee_id, last_name, salary, manager_id
  FROM  employees
 WHERE  manager_id IN (100, 101, 201); -- value = (100 or 101 or 201)
```

|  | EMPLOYEE_ID | LAST_NAME | SALARY | MANAGER_ID |
| --- | --- | --- | --- | --- |
| 1 | 201 | Hartstein | 13000 | 100 |
| 2 | 101 | Kochhar | 17000 | 100 |
| 3 | 102 | De Haan | 17000 | 100 |
| 4 | 124 | Mourgos | 5800 | 100 |
| 5 | 149 | Zlotkey | 10500 | 100 |
| 6 | 200 | Whalen | 4400 | 101 |
| 7 | 205 | Higgins | 12000 | 101 |
| 8 | 202 | Fay | 6000 | 201 |

`IN` 은 여러번의 `OR` 을 단축시킬 수 있다.

### 비교 연산자(LIKE)

---

- `LIKE` 연산자를 사용하여 유효한 검색 문자열 값의 대체 문자 검색을 수행
- 검색 조건에는 리터럴 문자나 숫자가 포함될 수 있다.
    - `%`는 0개 이상의 문자 표현
    - `_`은 한 문자 표현
        
        ```sql
        SELECT  first_name
          FROM  employees
         WHERE  first_name LIKE 'S%'; -- 대문자 S로 시작하는 모든 값
        
        -- '%S%' 일 경우, S를 포함한 모든 값이 출력된다. S가 맨 앞이든 뒤이든 상관없다.
        ```
        
        ```sql
        SELECT  last_name
          FROM  employees
         WHERE  last_name LIKE '_o%'; -- 두 번째 글짜가 o로 시작하는 모든 값
        ```
        
        |  | LAST_NAME |
        | --- | --- |
        | 1 | Kochhar |
        | 2 | Lorentz |
        | 3 | Mourgos |
        
        이보다 더 자세한 설정은 **정규표현식**을 통해서 구현할 수 있다.
        
    - `ESCAPE` 식별자를 사용하여 실제 `%` 및 `_` 기호를 검색할 수 있다.
        
        ```sql
        SELECT  employee_id, last_name, job_id
          FROM  employees
         WHERE  job_id LIKE '%SA?_%' ESCAPE '?' -- '&'를 제외한 모든 기호가 대상이 될 수 있다.
        ```
        
        |  | EMPLOYEE_ID | LAST_NAME | JOB_ID |
        | --- | --- | --- | --- |
        | 1 | 149 | Zlotkey | SA_MAN |
        | 2 | 174 | Abel | SA_REP |
        | 3 | 176 | Taylor | SA_REP |
        | 4 | 178 | Grant | SA_REP |
        
        `%` 와 `_` 는 **와일드카드**라고 부른다.
        
        이는 기능이지, 문자가 아니기 때문에 기본적으로 문자로 인식되지 않는다.
        
        `ESCAPE`를 사용해서 문자로 인식하게 할 수 있다.
        
        위 SQL문은 물음표 기호를 `ESCAPE` 문자로 지정하였다.
        
        이렇게 하면 물음표 기호 뒤에 있는 와일드카드의 기능이 배제되고 문자로서 인식된다.
        
        그렇다면 성에 ‘a’와 ‘e’가 둘 다 포함된 값은 어떻게 출력해야할까?
        
        ```sql
        SELECT  last_name || ' ' || first_name
          FROM  employees
         WHERE  last_name LIKE '%a%'
           AND  last_name LIKE '%e%'
        ```
        
        위 처럼 `AND`를 통해 `LIKE`를 두 번 사용하여 구현할 수 있다.
        
        |  | LAST_NAME \|\|’ ’\|\|FIRST_NAME |
        | --- | --- |
        | 1 | Baer Hermann |
        | 2 | Bates Elizabeth |
        | 3 | Colmenares Karen |
        | 4 | Davies Curtis |
        | 5 | De Haan Lex |
        | 6 | Fabiet Daniel |
        | 7 | Fleaur Jean |

### Null 연산자

---

- Null 값은 알 수 없는 값이므로 어떤 값과도 같거나 다를 수 없다.

```sql
SELECT  last_name, manager_id
  FROM  employees
 WHERE  manager_id IS NULL ; -- IS 를 사용하여야 한다.
```

|  | LAST_NAME | MANAGER_ID |
| --- | --- | --- |
| 1 | King | (null) |

### 논리 연산자

---

| 연산자 | 의미 |
| --- | --- |
| AND | 양 변의 값이 모두 참인 경우, 결과는 참 |
| OR | 양 변의 값 중 하나라도 참이면 결과는 참 |
| NOT | 부정, 참과 거짓의 반대 값 출력 (예, 지정한 조건이 아닌 경우) |

```sql
SELECT  employee_id, last_name, job_id, salary
  FROM  employees
 WHERE  salary >= 10000
   AND  job_id LIKE '%MAN%';
```

|  | EMPLOYEE_ID | LAST_NAME | JOB_ID | SALARY |
| --- | --- | --- | --- | --- |
| 1 | 201 | Hartstein | MK_MAN | 13000 |
| 2 | 149 | Zlotkey | SA_MAN | 10500 |

1. 급여가 10000 이상
2. job_id에 ‘MAN’이 포함

위 두 개의 조건을 모두 충족하는 값이 출력된다.

```sql
SELECT  employee_id, last_name, job_id, salary
  FROM  employees
 WHERE  salary >= 10000
    OR  job_id LIKE '%MAN%';
```

|  | EMPLOYEE_ID | LAST_NAME | JOB_ID | SALARY |
| --- | --- | --- | --- | --- |
| 1 | 201 | Hartstein | MK_MAN | 13000 |
| 2 | 205 | Higgins | AC_MCR | 12000 |
| 3 | 100 | King | AD_PRES | 24000 |
| 4 | 101 | Kochhar | AD_VIP | 17000 |
| 5 | 102 | De Haan | AD_VIP | 17000 |
| 6 | 124 | Mourgos | ST_MAN | 5800 |
| 7 | 149 | Zlotkey | SA_MAN | 10500 |

1. 급여가 10000 이상
2. job_id에 ‘MAN’이 포함

위 두 개의 조건 중 하나라도 충족하면 값을 출력한다.

### 논리 연산자(NOT)

---

```sql
SELECT  last_name, job_id
  FROM  employees
 WHERE  job_id NOT IN ('IT_PROG', 'ST_CLERK', 'SA_REP');
```

|  | LAST_NAME | JOB_ID |
| --- | --- | --- |
| 1 | De Haan | AD_VIP |
| 2 | Fay | MK_REP |
| 3 | Clietz | AC_ACCOUNT |
| 4 | Hartstein | MK_MAN |
| 5 | Higgins | AC_MCR |
| 6 | King | AD_PRES |
| 7 | Kochhar | AD_VIP |

`IN` 앞에 `NOT` 이 붙으면 ‘~을 제외한’ 이라고 해석된다.

즉, job_id가 'IT_PROG', 'ST_CLERK', 'SA_REP'인 값을 제외한 모든 값이 출력된다.

### 연산 우선 순위

---

```sql
SELECT  last_name, job_id, salary
  FROM  employees
 WHERE  job_id = 'SA_REP' -- 1
    OR  job_id = 'AD_PRES' -- 2
   AND  salary > 15000; -- 3
```

|  | LAST_NAME | JOB_ID | SALARY |
| --- | --- | --- | --- |
| 1 | King | AD_PRES | 24000 |
| 2 | Abel | SA_REP | 11000 |
| 3 | Taylor | SA_REP | 8600 |
| 4 | Crant | SA_REP | 7000 |

연산 우선 순위는 `AND` 가 `OR` 보다 높다.

따라서 위와 같이 조건에 번호를 매겼을 때, 2번과 3번이 처리된 후 1번이 처리된다.

```sql
SELECT  last_name, job_id, salary
  FROM  employees
 WHERE  (job_id = 'SA_REP' -- 1
    OR  job_id = 'AD_PRES') -- 2
   AND  salary > 15000; -- 3
```

|  | LAST_NAME | JOB_ID | SALARY |
| --- | --- | --- | --- |
| 1 | King | AD_PRES | 24000 |

의도적으로 괄호를 씌워 우선 순위를 바꿀 수 있다.

위의 경우 1번과 2번이 처리된 후 3번이 마지막으로 처리된다.

# 치환변수

---

- 치환 변수를 사용하면
    - 단일 앰퍼샌드(&) 및 이중 앰퍼샌드(&&) 치환을 사용하여 값을 임시로 저장
        - 단일 앰퍼샌드(&)는 일회성, 이중 앰퍼샌드(&&)는 세션동안 유지
- 치환 변수를 사용하여 다음을 보완
    - `WHERE` 조건
    - `ORDER BY` 조건
    - 열 표현식
    - 테이블 이름
    - 전체 `SELECT` 문

```sql
SELECT  employee_id, last_name, salary, department_id
  FROM  employees
 WHERE  employee_id = &employee_num;
-- 문자일 경우 '&name' 과 같이 작은따옴표를 붙여야 한다.
```

`&` 가 포함된 값을 변수라고 한다.

위 쿼리를 실행시키면 대체 변수를 입력하라는 창이 뜬다.

`&&` 를 사용했을 경우, 최초 1회만 입력하고 창을 다시 키지 않는 한 물어보지 않는다.

이 때 ‘200’을 입력하면, 위 쿼리는 다음과 같은 의미가 된다.

```sql
SELECT  employee_id, last_name, salary, department_id
  FROM  employees
 WHERE  employee_id = 200;
```

|  | EMPLOYEE_ID | LAST_NAME | SALARY | DEPARTMENT_ID |
| --- | --- | --- | --- | --- |
| 1 | 200 | Whalen | 4840 | 10 |

# ORDER BY절 사용

---

- `ORDER BY` 절을 사용하여 검색된 행을 정렬
    - `ASC`(기본값) : 오름차순
    - `DESC` : 내림차순
    - `SELECT`절 마지막에만 지정 가능
    - `ORDER BY`절은 쿼리의 맨 마지막에 작성한다.
    
    ```sql
      SELECT  last_name, job_id, department_id, hire_date
        FROM  employees
    ORDER BY  hire_date DESC; -- 입사일을 오름차순으로 정렬
    ```
    
    ```sql
      SELECT  employee_id, last_name, salary*12 annsal -- alias
        FROM  employees
    ORDER BY  annsal; -- alias가 허용된다. GROUP BY에서는 허용되지 않음
    ```
    
    ```sql
      SELECT  last_name, job_id, department_id, hire_date
        FROM  employees
    ORDER BY  3; -- SELECT절에 나열된 순서, 즉 department_id 오름차순 정렬
    ```
    
    ```sql
      SELECT  last_name, department_id, salary
        FROM  employees
    ORDER BY  department_id, salary DESC; -- 다중 칼럼 ORDER BY
    -- department_id 뒤에 ASC 생략
    ```
    
    `다중 칼럼 ORDER BY` 는 앞에서부터 순서대로 정렬된다.
    
    즉, 먼저 department_id에 대해서 오름차순 정렬한다.
    
    이후 그 정렬이 깨지지 않는 한에서 salary에 대해 내림차순 정렬한다.
    
    department_id에 대해선 전체 정렬, salary에 대해선 부분 정렬이라고 생각할 수 있다.
    
    - `NULL` 값은 `NULLS FRIST` 나 `NULLS LAST` 키워드를 사용하여 `NULL` 값의 정렬순서를 변경할 수 있다.
    
    ```sql
      SELECT  last_name, job_id, department_id, hire_date
        FROM  employees
    ORDER BY  manager_id DESC NULLS LAST;
    -- ORDER BY  manager_id DESC NULLS FIRST;
    ```
    
    `NULL` 값은 기본적으로 큰 값으로 인식된다.
    
    이를 의도적으로 바꾸어서 출력할 수 있다.
    
    `NULLS FIRST` 로 작성할 경우 `NULL` 값이 제일 위에 출력되게 된다.