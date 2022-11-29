---
layout: post
title: "[ORACLE-SQL] ExamTopics 71~80"
subtitle: ORACLE
date: '2022-11-19 16:20:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/logo.png
---

1z0-071 Examtopics 71~80번 문제를 풀어보자.<br>
1차 x/x<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 71 ⭕
---

Examine this statement:<br>
![prob71](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob71.png)

On which two columns of the table will an index be created automatically? (Choose two.)

A. ORDER_ID

B. ORDER_TOTAL

C. ORDER_DATE

D. PRODUCT_ID

E. STATUS

F. SERIAL_NO

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, F

해설 :

`INDEX` 는 기본적으로 하나의 칼럼 당 하나의 인덱스를 생성할 수 있다.<br>
또한 `PK`, `UNIQUE` 가 지정된 칼럼일 경우, 자동으로 인덱스가 생성된다.<br>

1차 시도 : A, F 맞음<br>
</div>
</details>

<br>

## Prob. 72 ❌
---

Examine this partial query:<br>
![prob72](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob72.png)

Examine this output:<br>
![prob72-1](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob72-1.png)

Which GROUP BY clause must be added so the query returns the results shown?

A. GROUP BY ch.channel_type, ROLLUP(t.month, co.country_code);

B. GROUP BY ch.channel_type, t.month, ROLLUP(co.country_code);

C. GROUP BY CUBE(ch.channel_type, t.month, co.country_code);

D. GROUP BY ch.channel_type, t.month, co.country_code;

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 :

`ROLLUP` 함수를 사용하여 칼럼을 감싸면, 인자가 된 칼럼의 각 소계, 합계가 나오게 된다.<br>
그리고 `ROLLUP` 으로 감싸지지 않은 남은 칼럼은 합계가 나오지 않으므로, 해당 문제의 결과를 출력하는 답은 A이다.

1차 시도 : D 틀림<br>
</div>
</details>

<br>

## Prob. 73 ⭕❌
---

Examine the description of the EMPLOYEES table:<br>
![prob73](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob73.png)

Which statement will execute successfully, returning distinct employees with non-null first names?

A. SELECT first_name, DISTINCT last_name FROM employees WHERE first_name <> NULL;

B. SELECT first_name, DISTINCT last_name FROM employees WHERE first_name IS NOT NULL;

C. SELECT DISTINCT * FROM employees WHERE first_name IS NOT NULL;

D. SELECT DISTINCT * FROM employees WHERE first_name <> NULL;

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

## Prob. 74 ⭕❌
---

Examine the description of the BRICKS table:<br>
![prob74](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob74.png)

Examine the description of the BRICKS_STAGE table:<br>
![prob74-1](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob74-1.png)

Which two queries execute successfully? (Choose two.)

A.<br>
![prob74-a](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob74-a.png)

B.<br>
![prob74-b](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob74-b.png)

C.<br>
![prob74-c](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob74-c.png)

D.<br>
![prob74-d](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob74-d.png)

E.<br>
![prob74-e](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob74-e.png)

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

## Prob. 75 ⭕❌
---

Table EMPLOYEES contains columns including EMPLOYEE_ID, JOB_ID and SALARY.
Only the EMPLOYEE_ID column is indexed.<br>
Rows exist for employees 100 and 200.<br>
Examine this statement:<br>
![prob75](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob75.png)

Which two statements are true? (Choose two.)

A. Employees 100 and 200 will have the same SALARY as before the update command.

B. Employee 100 will have JOB_ID set to the same value as the JOB_ID of employee 200.

C. Employee 200 will have JOB_ID set to the same value as the JOB_ID of employee 100.

D. Employees 100 and 200 will have the same JOB_ID as before the update command.

E. Employee 100 will have SALARY set to the same value as the SALARY of employee 200.

F. Employee 200 will have SALARY set to the same value as the SALARY of employee 100.

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

## Prob. 76 ⭕❌
---

Examine these two queries and their output:<br>
SELECT deptno, dname FROM dept;<br>
![prob76](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob76.png)

SELECT emame, job, deptno FROM emp ORDER BY deptno;<br>
![prob76-1](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob76-1.png)

Now examine this query:<br>
![prob76-2](/assets/img/study_Oracle/2022-11-19-[ORACLE-SQL]_ExamTopics_71~80/prob76-2.png)

How many rows will be displayed?

A. 64

B. 6

C. 3

D. 12

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

## Prob. 77 ⭕❌
---

You want to return the current date and time from the user session, with a data type of TIMESTAMP WITH TIME ZONE.

Which function will do this?

A. SYSDATE

B. CURRENT_TIMESTAMP

C. LOCALTIMESTAMP

D. CURRENT_DATE

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

## Prob. 78 ⭕❌
---

You have been tasked to create a table for a banking application.
One of the columns must meet three requirements:

1) Be stored in a format supporting date arithmetic without using conversion functions

2) Store a loan period of up to 10 years

3) Be used for calculating interest for the number of days the loan remains unpaid

Which data type should you use?

A. INTERVAL YEAR TO MONTH

B. TIMESTAMP WITH TIMEZONE

C. INTERVAL DAY TO SECOND

D. TIMESTAMP WITH LOCAL TIMEZONE

E. TIMESTAMP

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

## Prob. 79 ⭕❌
---


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

## Prob. 80 ⭕❌
---


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