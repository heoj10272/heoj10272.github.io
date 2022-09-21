---
layout: post
title: "[ORACLE] 그룹 데이터 처리를 위한 GROUP BY와 HAVING 절 1"
subtitle: Oracle
date: '2022-09-22 01:02:00 +0900'
category: study
tags: oracle
image:
  path: /assets/img/study_Oracle/2022-09-22-[ORACLE]_그룹 데이터 처리를 위한 GROUP BY와 HAVING 절 1/logo.png
---

그룹 데이터 처리를 위한 GROUP BY와 HAVING 절 1

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

# 집계 함수

---

- 그룹 함수
    - AVG - 평균
    - COUNT - 카운트
    - MAX - 최대
    - MIN - 최소
    - STDDEV - 표준편차
    - SUM - 합계
    - VARIANCE - 분산

위 함수들을 “집계 함수” 라고 한다.

“그룹 함수” = “집계 함수” 이다.

집계 함수는 여러개의 데이터로 하나의 결과 데이터를 만들어준다.

## 숫자 처리 함수 AVG(), SUM()

---

```sql
-- AVG, MAX, MIN, SUM 은 숫자를 처리할 수 있다.

SELECT  AVG(salary), MAX(salary), MIN(salary), SUM(salary)
  FROM  employees
 WHERE  job_id, LIKE '%REP%'
```

|  | AVG(SALARY) | MAX(SALARY) | MIN(SALARY) | SUM(SALARY) |
| --- | --- | --- | --- | --- |
| 1 | 8150 | 11000 | 6000 | 32600 |

## 숫자, 문자, 날짜 처리 함수 MAX(), MIN()

---

```sql
-- MAX, MIN 은 숫자 뿐만 아니라 문자, 날짜도 처리할 수 있다.

SELECT  MIN(hire_date), MAX(hire_date)
  FROM  employees;
```

|  | MIN(HIRE_DATE) | MAX(HIRE_DATE) |
| --- | --- | --- |
| 1 | 17-JUN-87 | 29-JAN-00 |

`MAX` 와 `MIN` 은 숫자 뿐만 아니라 문자, 날짜도 처리할 수 있다.

이 때 문자는 “A~Z”, “ㄱ~ㅎ” 으로 구분되어 출력된다.

날짜는 자연스럽게 가장 오래된 날짜가 `MIN` , 가장 최근 날짜가 `MAX` 로 출력된다.

아래 예시를 참고하자.

```sql
SELECT  MIN(last_name), MAX(last_name)
  FROM  employees;
```

|  | MIN(LAST_NAME) | MAX(LAST_NAME) |
| --- | --- | --- |
| 1 | Abel | Zlotkey |

## 테이블의 모든 행 수 COUNT(*)

---

“테이블의 모든 행의 수”를 출력한다.

```sql
-- 부서 id가 50인 사원의 수를 출력

SELECT  COUNT(*)
  FROM  employees
 WHERE  department_id = 50;
```

|  | COUNT(*) |
| --- | --- |
| 1 | 5 |

위와 같이 `*` 을 사용했을 경우 `COUNT` 의 출력 결과는 `NULL` 과 무관하다.

정확하게 말하면 각 행의 칼럼 값에 `NULL` 이 포함되든 말든 상관없이, 행으로 출력되면 집계에 포함된다.

## null이 아닌 값을 가진 행 수 COUNT(expr)

---

```sql
SELECT  COUNT(commission_pct)
  FROM  employees
 WHERE  department_id = 80;
```

|  | COUNT(COMMISSION_PCT) |
| --- | --- |
| 1 | 3 |

위 처럼 칼럼을 지정할 경우 집계에서 `NULL` 이 제외된다.

즉 `COUNT(expr)` 은 결과 행에서 `NULL` 값을 제외한 행 수를 출력한다.

## expr의 null과 중복 값이 아닌 행 수 COUNT(DISTINCT expr)

---

```sql
SELECT  COUNT(DISTINCT department_id)
  FROM  employees;
```

|  | COUNT(DISTINCTDEPARTMENT_ID) |
| --- | --- |
| 1 | 7 |

먼저 `DISTINCT` 에 의해 “department_id”에서 중복된 값이 제외된다.

이렇게 중복이 제외된 결과 행 수를 출력하게 되는데, 위에서 봤듯이 칼럼을 지정하였기 때문에 `NULL` 값은 제외된다.

## 그룹 함수는 칼럼에 있는 null 값 무시

---

```sql
SELECT  AVG(commission_pct)
  FROM  employees;
```

|  | AVG(COMMISSION_PCT) |
| --- | --- |
| 1 | 0.2125 |

기본적으로 그룹 함수는 칼럼에 있는 `NULL` 값은 무시한다.

즉 “commission_pct” 칼럼에서 `NULL` 값을 제외한 행이 4개 있을 경우, 이 4개의 값에 대해서만 평균을 계산한다.

## NVL을 이용하여 강제로 그룹 함수에 null을 사용가능 값으로

---

```sql
SELECT  AVG(NVL(commission_pct, 0))
  FROM  employees;
```

|  | AVG(NVL(COMMISSION_PCT,0)) |
| --- | --- |
| 1 | 0.0425 |

만약 전체 사원 대상으로 평균값을 내고 싶을 경우, `NULL` 값을 `NVL` 을 사용하여 0으로 치환 함으로서 집계에 포함시킬 수 있다.

## QUIZ 1

---

**전체 사원수와 1998년에 입사한 사원 수를 출력하시오.**

- DECODE 를 사용한 방법
    
    ```sql
    SELECT  '총 사원수 = ' || COUNT(*) total,
            '1998년 입사한 사원수 = ' ||
    				SUM(DECODE(TO_CHAR(hire_date, 'YYYY'), 1998, 1, 0)) "1998"
      FROM  employees;
    ```
    
    먼저 아래 부분부터 보자.
    
    ```sql
    TO_CHAR(hire_date,'YYYY')
    ```
    
    전체 “employees” 테이블에서 “hire_date” 중 년도만 뽑는다.
    
    ```sql
    DECODE(TO_CHAR(hire_date, 'YYYY'), 1998, 1, 0)
    ```
    
    이 연도는 `DECODE` 에 의해 값이 “1998”일 경우 1, 아닐 경우 0으로 출력된다.
    
    즉 1998년에 입사한 사원은 1로, 아닐 경우 0으로 출력되므로 이를 `SUM` 으로 합계를 구하면 1998년에 입사한 사원 수를 뽑을 수 있을 것이다.
    
- CASE 를 사용한 방법
    
    ```sql
    SELECT  '총 사원수 = ' || COUNT(*) total,
            '1998년 입사한 사원수 = ' ||
    				COUNT(CASE WHEN hire_date LIKE '98%' THEN 1 END) "1998"
      FROM  employees;
    ```
    
    `DECODE` 를 사용한 방법과 유사하지만, `CASE` 는 부등호, `LIKE` , `BETWEEN` 과 같은 조건 처리를 할 수 있는 유일한 조건 처리 함수이다.
    
    ‘98%’의 의미는 98로 시작하는 값을 의미한다.
    
    따라서 98년도에 입사한 사원은 1로 출력될 것이고, 이를 `COUNT` 를 통해 집계하면 된다.
    

## QUIZ 2

---

**1994, 1998, 1999년도에 입사한 사원들의 급여 합계를 구하시오.**

- DECODE 를 사용한 방법
    
    ```sql
    SELECT  SUM(DECODE(TO_CHAR(hire_date,'YYYY'), '1994', salary, 0)) "1994",
    		SUM(DECODE(TO_CHAR(hire_date,'YYYY'), '1998', salary, 0)) "1998",
    		SUM(DECODE(TO_CHAR(hire_date,'YYYY'), '1999', salary, 0)) "1999",
      FROM  employees;
    ```
    
    `DECODE` 부분의 의미는 입사일이 199X년일 경우 ‘salary’를 출력하고, 아니면 0을 출력한다는 것이다.
    
    결과 값의 합계를 `SUM` 으로 구하면 된다.
    
- PIVOT 을 사용한 방법
    
    ```sql
    SELECT  *
      FROM  (SELECT  TO_CHAR(hire_date, 'YYYY') AS HDATE, salary
    		   FROM  employees)
     PIVOT  (SUM(salary) FOR HDATE IN ('1994', '1998', '1999'));
    ```
    
    제일 바깥에 있는 `FROM` 내부의 쿼리를 “서브 쿼리” 라고 한다. (인라인 뷰)
    
    여기에서 `PIVOT` 을 통해 “HDATE” 값이 '1994', '1998', '1999' 인 값만 `SUM` 으로 “salary”를 집계한다.
    

# Group data 처리

---

## GROUP 개념

---

Group data는 `GROUP BY` 를 통해 처리할 수 있다.

```sql
  SELECT  department_id, round(AVG(salary), 2)
    FROM  employees
GROUP BY  department_id
ORDER BY  1;
```

|  | DEPARTMENT_ID | ROUND(AVG(SALARY), 2) |
| --- | --- | --- |
| 1 | 10 | 4400 |
| 2 | 20 | 9500 |
| 3 | 50 | 3500 |
| 4 | (null) | 7000 |

“department_id”를 기준으로 group을 나누었다.

각 “department_id”의 값에 따른 ‘salary’의 평균이 소숫점 두 번째 자리까지 반올림되어 출력되며, `ORDER BY` 에 의해 “department_id” 기준 오름차순 정렬되었다.

즉 정리를 하자면 다음과 같다.

`SELECT` 절에 일반 칼럼(”department_id”)와 그룹 함수(round(AVG(salary), 2)가 있을 경우, 일반 칼럼을 기준으로 그룹 함수의 결과 값이 출력된다.

이 때 일반 칼럼, 즉 그룹 함수에 속하지 않는 `SELECT` 리스트의 모든 열은 무조건 `GROUP BY` 절에 와야한다.

 `GROUP BY` 에는 여러 칼럼이 올 수 있다.

이를 **“다중 칼럼 group by”**라고 한다.

```sql
  SELECT  department_id, job_id, SUM(salary)
    FROM  employees
   WHERE  department_id > 40
GROUP BY  department_id, job_id
ORDER BY  department_id;
```

|  | DEPARTMENT_ID | JOB_ID | SUM(SALARY) |
| --- | --- | --- | --- |
| 1 | 50 | ST_CLERK | 11700 |
| 2 | 50 | ST_MAN | 5800 |
| 3 | 60 | IT_PROG | 19200 |
| 4 | 80 | SA_MAN | 10500 |

앞서 서술했듯 그룹 함수를 제외한 `SELECT` 의 열들은 모두 `GROUP BY` 에 위치해야 한다.

`GROUP BY` 에서 그룹화 되는 방식은 이전의 “다중 칼럼 order by” 에서의 방식과 비슷하다.

## 잘못된 GROUP 함수 사용 예

---

```sql
SELECT  department_id, COUNT(last_name)
  FROM  employees;
```

> ORA-00937: not a single-group group function

각 department_id에 대해 성의 갯수를 세려면 `GROUP BY` 절을 추가해야 한다.

```sql
  SELECT  department_id, job_id, COUNT(last_name)
    FROM  employees
GROUP BY  department_id;
```

> ORA-00979: not a GROUP BY expression

`GROUP BY` 에 job_id를 추가하거나 `SELECT` 리스트에서 job_id 열을 제거.

```sql
  SELECT  department_id, AVG(salary)
    FROM  employees
   WHERE  AVG(salary) > 8000
GROUP BY  department_id;
```

> Error encountered

`WHERE` 절은 그룹을 제한하는데 사용할 수 없다.

자세하게는 `WHERE` 은 그룹 함수를 조건 처리 할 수 없다.

그룹 함수에 조건 처리를 하려면 `HAVING` 을 사용해야 한다.