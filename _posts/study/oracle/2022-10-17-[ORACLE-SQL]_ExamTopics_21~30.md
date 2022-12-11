---
layout: post
title: "[ORACLE-SQL] ExamTopics 21~30"
subtitle: ORACLE
date: '2022-10-17 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-10-17-[ORACLE-SQL]_ExamTopics_21~30/logo.png
---

1z0-071 Examtopics 21~30번 문제를 풀어보자.<br>
1차 5/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 21 ❌❌
---

Which two are true about unused columns? (Choose two.)

A. A query can return data from unused columns, but no DML is possible on those columns.

B. Unused columns retain their data until they are dropped.

C. Once a column has been set to unused, a new column with the same name can be added to the table.

D. The DESCRIBE command displays unused columns.

E. A primary key column cannot be set to unused.

F. A foreign key column cannot be set to unused.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, C

해설 :

A : 틀렸음. `UNUSED` 된 칼럼의 데이터는 값을 반환하지 않는다.<br>
B : 맞음. `UNUSED` 는 `DROP` 된 것이 아니기 때문에 값은 유지된다.<br>
C : 맞음. `UNUSED` 칼럼을 신규 칼럼으로 추가할 수 있다.<br>
D : 틀렸음. `UNUSED` 된 칼럼은 `DESCRIBE` 로 볼 수 없으며, `DATA DICTIONARY` 에서 확인할 수 있다.<br>
E : 틀린듯? `PK` 도 `UNUSED` 될 수 있나보다.<br>
F : 틀린듯? `FK` 도 `UNUSED` 될 수 있나보다.<br>

[구루비 링크](http://www.gurubee.net/article/48959)

1차 시도 : B, E 틀림<br>
2차 시도 : B, C 틀림<br>
</div>
</details>

<br>

## Prob. 22 ⭕⭕
---

Which two are true about the precedence of operators and conditions? (Choose two.)

A. \|\| has a higher order of precedence than + (addition).

B. + (addition) has a higher order of precedence than * (multiplication).

C. NOT has a higher order of precedence than AND and OR in a condition.

D. AND and OR have the same order of precedence in a condition.

E. Operators are evaluated before conditions.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, E

해설 :

연산자 우선순위는 다음과 같다.<br>
`산술연산자` > `NOT` > `AND` > `OR`

1차 시도 : C, E<br>
2차 시도 : C, E<br>
</div>
</details>

<br>

## Prob. 23 ⭕⭕
---

In your session, the NLS_DATE_FORMAT is DD-MM-YYYY.
There are 86400 seconds in a day.
Examine this result:

DATE -<br>
ㅡㅡㅡㅡㅡㅡ<br>
02-JAN-2020

Which statement returns this?

A. SELECT TO_CHAR(TO_DATE('29-10-2019') + INTERVAL '2' MONTH + INTERVAL '4' DAY - INTERVAL '120' SECOND, 'DD-MON-YYYY') AS "date" FROM DUAL;

B. SELECT TO_CHAR(TO_DATE('29-10-2019') + INTERVAL '3' MONTH + INTERVAL '7' DAY - INTERVAL '360' SECOND, 'DD-MON-YYYY') AS "date" FROM DUAL;

C. SELECT TO_CHAR(TO_DATE('29-10-2019') + INTERVAL '2' MONTH + INTERVAL '5' DAY - INTERVAL '120' SECOND, 'DD-MON-YYYY') AS "date" FROM DUAL;

D. SELECT TO_CHAR(TO_DATE('29-10-2019') + INTERVAL '2' MONTH + INTERVAL '5' DAY - INTERVAL '86410' SECOND, 'DD-MON- YYYY') AS "date" FROM DUAL;

E. SELECT TO_CHAR(TO_DATE('29-10-2019') + INTERVAL '2' MONTH + INTERVAL '6' DAY - INTERVAL '120' SECOND, 'DD-MON-YYYY') AS "date" FROM DUAL;

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 :

`INTERVAL` 을 사용하면 날짜 계산을 편하게 할 수 있다고 한다.<br>
[참고 링크](https://gent.tistory.com/64)

그냥 계산해보니까 C가 답이다...

1차 시도 : C<br>
2차 시도 : C<br>
</div>
</details>

<br>

## Prob. 24 ⭕⭕
---

Examine the data in the INVOICES table:<br>
![prob24](/assets/img/study_Oracle/2022-10-17-[ORACLE-SQL]_ExamTopics_21~30/prob24.png)

Examine the data in the CURRENCIES table:<br>
![prob24-1](/assets/img/study_Oracle/2022-10-17-[ORACLE-SQL]_ExamTopics_21~30/prob24-1.png)

Which query returns the currencies in CURRENCIES that are not present in INVOICES?

A.
![prob24-a](/assets/img/study_Oracle/2022-10-17-[ORACLE-SQL]_ExamTopics_21~30/prob24-a.png)

B.
![prob24-b](/assets/img/study_Oracle/2022-10-17-[ORACLE-SQL]_ExamTopics_21~30/prob24-b.png)

C.
![prob24-c](/assets/img/study_Oracle/2022-10-17-[ORACLE-SQL]_ExamTopics_21~30/prob24-c.png)

D.
![prob24-d](/assets/img/study_Oracle/2022-10-17-[ORACLE-SQL]_ExamTopics_21~30/prob24-d.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 :

그냥 C 같다.
B는 `MINUS`를 하더라도 Currency가 출력될 수 있다.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>

## Prob. 25 ❌⭕
---

The SALES table has columns PROD_ID and QUANTITY_SOLD of data type NUMBER.
Which two queries execute successfully? (Choose two.)

A. SELECT prod_id FROM sales WHERE quantity_sold > 55000 AND COUNT(\*) > 10 GROUP BY COUNT(\*) > 10;

B. SELECT prod_id FROM sales WHERE quantity_sold > 55000 GROUP BY prod_id HAVING COUNT(\*) > 10;

C. SELECT COUNT(prod_id) FROM sales GROUP BY prod_id WHERE quantity_sold > 55000;

D. SELECT prod_id FROM sales WHERE quantity_sold > 55000 AND COUNT(\*) > 10 GROUP BY prod_id HAVING COUNT(\*) > 10;

E. SELECT COUNT(prod_id) FROM sales WHERE quantity_sold > 55000 GROUP BY prod_id;

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, E

해설 :

A : `COUNT(*)`은 `GROUP BY` 절이 아니라 `HAVING` 절에 들어가야 하며, `GROUP BY` 절의 문법도 틀렸다.<br>
B : 맞음<br>
C : `WHERE` 절은 `GROUP BY` 앞에 위치해야 한다.<br>
D : `COUNT(*)`은 `HAVING` 절의 조건으로 들어가야 한다.<br>
E : 맞음<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/11349-exam-1z0-071-topic-1-question-242-discussion/)

1차 시도 : B, C 틀림<br>
1차 시도 : B, E 맞음<br>
</div>
</details>

<br>

## Prob. 26 ⭕❌
---

Which three statements are true about single-row functions? (Choose three.)

A. They return a single result row per table.

B. They can be nested to any level.

C. They can accept only one argument.

D. The argument can be a column name, variable, literal or an expression.

E. They can be used only in the WHERE clause of a SELECT statement.

F. The data type returned can be different from the data type of the argument.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, D, F

해설 :

A : 틀렸음. 단일 행 함수는 테이블당이 아니라 로우당 하나의 결과를 출력한다.<br>
B : 맞음. 반면에 서브쿼리는 255 level까지 `nest` 될 수 있음에 주의.<br>
C : 틀렸음. <br>
D : 맞음.<br>
E : 틀렸음. `WHERE` 절 뿐만 아니라 `SELECT`, `HAVING` 절 등 다양한 절에 올 수 있음.<br>
F : 맞음.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/20182-exam-1z0-071-topic-2-question-46-discussion/)

1차 시도 : B, D, F 맞음<br>
2차 시도 : A, B, D 틀림<br>
</div>
</details>

<br>

## Prob. 27 ❌❌
---

Which two statements are true about *_TABLES views? (Choose two.)

A. USER_TABLES displays all tables owned by the current user.

B. You must have ANY TABLE system privileges, or be granted object privileges on the table, to view a table in USER_TABLES.

C. All users can query DBA_TABLES successfully.

D. You must have ANY TABLE system privileges, or be granted object privileges on the table, to view a table in DBA_TABLES.

E. ALL_TABLES displays all tables owned by the current user.

F. You must have ANY TABLE system privileges, or be granted object privileges on the table, to view a table in ALL_TABLES.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, D

해설 :

A : 맞음.<br>
D : 맞음. `DBA_TABLES` 를 참조하기 위해서 `ANY TABLE` 시스템 권한이 필요한 것이다.<br>

`ALL_TABLES` 는 현재 사용자가 접근 가능한 모든 테이블을 보여준다.<br>
`USER_TABLES` 는 현재 사용자가 소유한 모든 테이블을 보여준다. 이 때 `ALL_TABLES` 에서는 나오는 `ÒWNER` 칼럼이 나오지 않는다.<br>
`DBA_TABLES` 는 데이터베이스에 존재하는 모든 테이블을 보여준다. 구조가 `ALL_TABLES` 의 칼럼들과 동일하다.<br>

1차 시도 : A, B 틀림<br>
2차 시도 : A, F 틀림<br>
</div>
</details>

<br>

## Prob. 28 ❌⭕
---

Which two statements are true about conditional INSERT ALL? (Choose two.)

A. Each row returned by the subquery can be inserted into only a single target table.

B. A single WHEN condition can be used for multiple INTO clauses.

C. Each WHEN condition is tested for each row returned by the subquery.

D. It cannot have an ELSE clause.

E. The total number of rows inserted is always equal to the number of rows returned by the subquery.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, C

해설 :

A : 틀렸음. 여러 테이블에도 삽입할 수 있나보다. 아래 구문 문법 참조.<br>
B : 맞음. <br>
C : 맞음. 각각의 `WHEN` 조건은 서브쿼리의 각 행에 사용된다.<br>
D : 틀렸음. 다음 `INSERT` 구문 문법 참조.<br>
```sql
INSERT [ ALL | FIRST ] 
WHEN condition1 THEN INTO table_1(column_list) VALUES (value_list) 
WHEN condition2 THEN INTO table_2(column_list) VALUES (value_list) 
ELSE INTO table_3(column_list ) VALUES (value_list) Subquery
```
E : `WHEN` 절의 조건에 따라 다를 듯 하다.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/8439-exam-1z0-071-topic-1-question-278-discussion/)

1차 시도 : A, C 틀림<br>
1차 시도 : B, C 맞음<br>
</div>
</details>

<br>

## Prob. 29 ❌⭕
---

Which two statements are true about the COUNT function? (Choose two.)

A. COUNT(/*) returns the number of rows in a table including duplicate rows and rows containing NULLs in any column.

B. It can only be used for NUMBER data types.

C. COUNT(DISTINCT inv_amt) returns the number of rows excluding rows containing duplicates and NULLs in the INV_AMT column.

D. COUNT(inv_amt) returns the number of rows in a table including rows with NULL in the INV_AMT column

E. A SELECT statement using the COUNT function with a DISTINCT keyword cannot have a WHERE clause.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

해설 :

아스타리스크(`*`)를 `COUNT`에 사용하면, `NULL`을 포함한 값을 세고, 확실한 표현식을 넣으면, `NULL` 값을 제외한 값을 센다.

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/12707-exam-1z0-071-topic-1-question-258-discussion/)

1차 시도 : A, D 틀림<br>
1차 시도 : A, C 맞음<br>
</div>
</details>

<br>

## Prob. 30 ⭕❌
---

The EMPLOYEES table contains columns EMP_ID of data type NUMBER and HIRE_DATE of data type DATE.<br>
You want to display the date of the first Monday after the completion of six months since hiring.<br>
The NLS_TERRITORY parameter is set to AMERICA in the session and, therefore, Sunday is the first day of the week.<br>
Which query can be used?

A. SELECT emp_id, ADD_MONTHS(hire_date, 6), NEXT_DAY('MONDAY') FROM employees;

B. SELECT emp_id, NEXT_DAY(ADD_MONTHS(hire_date, 6), 1) FROM employees;

C. SELECT emp_id, NEXT_DAY(MONTHS_BETWEEN(hire_date, SYSDATE), 6) FROM employees;

D. SELECT emp_id, NEXT_DAY(ADD_MONTHS(hire_date, 6), 'MONDAY') FROM employees;

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 :

`ADD_MONTHS` 와 `NEXT_DAY` 의 구문 문법을 확인해보자.

[내 블로그 링크](https://heoj10272.github.io/study/ORACLE-_SQL_함수_활용_1.html)

1차 시도 : D 맞음<br>
2차 시도 : B 틀림<br>
</div>
</details>

<br>