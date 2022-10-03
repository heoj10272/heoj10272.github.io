---
layout: post
title: "[ORACLE-SQL] ExamTopics 21~30"
subtitle: ORACLE
date: '2022-xx-xx 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-xx-xx-[ORACLE]_ExamTopics_21~30/logo.png
---

1z0-071 Examtopics 21~30번 문제를 풀어보자.<br>
1차 x/x<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 21 ⭕❌
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
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>

## Prob. 22 ⭕❌
---

Which two are true about the precedence of operators and conditions? (Choose two.)

A. || has a higher order of precedence than + (addition).

B. + (addition) has a higher order of precedence than * (multiplication).

C. NOT has a higher order of precedence than AND and OR in a condition.

D. AND and OR have the same order of precedence in a condition.

E. Operators are evaluated before conditions.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>

## Prob. 23 ⭕❌
---

In your session, the NLS_DATE_FORMAT is DD-MM-YYYY.
There are 86400 seconds in a day.
Examine this result:

DATE -
-----------
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
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>

## Prob. 24 ⭕❌
---

Examine the data in the INVOICES table:
![prob24](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob24.png)

Examine the data in the CURRENCIES table:
![prob24-1](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob24-1.png)

Which query returns the currencies in CURRENCIES that are not present in INVOICES?

A.
![prob24-a](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob24-a.png)

B.
![prob24-b](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob24-b.png)

C.
![prob24-c](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob24-c.png)

D.
![prob24-d](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob24-d.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>

## Prob. 25 ⭕❌
---

The SALES table has columns PROD_ID and QUANTITY_SOLD of data type NUMBER.
Which two queries execute successfully? (Choose two.)

A. SELECT prod_id FROM sales WHERE quantity_sold > 55000 AND COUNT(*) > 10 GROUP BY COUNT(*) > 10;

B. SELECT prod_id FROM sales WHERE quantity_sold > 55000 GROUP BY prod_id HAVING COUNT(*) > 10;

C. SELECT COUNT(prod_id) FROM sales GROUP BY prod_id WHERE quantity_sold > 55000;

D. SELECT prod_id FROM sales WHERE quantity_sold > 55000 AND COUNT(*) > 10 GROUP BY prod_id HAVING COUNT(*) > 10;

E. SELECT COUNT(prod_id) FROM sales WHERE quantity_sold > 55000 GROUP BY prod_id;

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 :



1차 시도 : <br>
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
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>

## Prob. 27 ⭕❌
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
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>

## Prob. 28 ⭕❌
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
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>

## Prob. 29 ⭕❌
---

Which two statements are true about the COUNT function? (Choose two.)

A. COUNT(*) returns the number of rows in a table including duplicate rows and rows containing NULLs in any column.

B. It can only be used for NUMBER data types.

C. COUNT(DISTINCT inv_amt) returns the number of rows excluding rows containing duplicates and NULLs in the INV_AMT column.

D. COUNT(inv_amt) returns the number of rows in a table including rows with NULL in the INV_AMT column

E. A SELECT statement using the COUNT function with a DISTINCT keyword cannot have a WHERE clause.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>

## Prob. 30 ⭕❌
---

The EMPLOYEES table contains columns EMP_ID of data type NUMBER and HIRE_DATE of data type DATE.
You want to display the date of the first Monday after the completion of six months since hiring.
The NLS_TERRITORY parameter is set to AMERICA in the session and, therefore, Sunday is the first day of the week.
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
Answer : 

해설 :



1차 시도 : <br>
</div>
</details>

<br>