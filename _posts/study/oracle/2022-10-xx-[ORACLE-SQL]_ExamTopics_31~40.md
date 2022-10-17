---
layout: post
title: "[ORACLE-SQL] ExamTopics 31~40"
subtitle: ORACLE
date: '2022-xx-xx 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-xx-xx-[ORACLE-SQL]_ExamTopics_31~40/logo.png
---

1z0-071 Examtopics 31~40번 문제를 풀어보자.<br>
1차 x/x<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 31 ⭕❌
---

Which three statements are true about GLOBAL TEMPORARY TABLES? (Choose three.)

A. GLOBAL TEMPORARY TABLE space allocation occurs at session start.

B. GLOBAL TEMPORARY TABLE rows inserted by a session are available to any other session whose user has been granted select on the table.

C. A TRUNCATE command issued in a session causes all rows in a GLOBAL TEMPORARY TABLE for the issuing session to be deleted.

D. Any GLOBAL TEMPORARY TABLE rows existing at session termination will be deleted.

E. A DELETE command on a GLOBAL TEMPORARY TABLE cannot be rolled back.

F. A GLOBAL TEMPORARY TABLE'S definition is available to multiple sessions.

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

## Prob. 32 ⭕❌
---

Which two statements are true about the SET VERIFY ON command? (Choose two.)

A. It displays values for variables used only in the WHERE clause of a query.

B. It displays values for variables created by the DEFINE command.

C. It can be used only in SQL*Plus.

D. It displays values for variables prefixed with &&.

E. It can be used in SQL Developer and SQL*Plus.

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

## Prob. 33 ⭕❌
---

Examine this list of requirements for a sequence:
1. Name: EMP_SEQ
2. First value returned: 1
3. Duplicates are never permitted.
4. Provide values to be inserted into the EMPLOYEES.EMPLOYEE_ID column.
5. Reduce the chances of gaps in the values.
Which two statements will satisfy these requirements? (Choose two.)

A. CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1 CYCLE;

B. CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1 CACHE;

C. CREATE SEQUENCE emp_seq;

D. CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1 NOCACHE;

E. CREATE SEQUENCE emp_seq NOCACHE;

F. CREATE SEQUENCE emp_seq START WITH 1 CACHE;

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

## Prob. 34 ⭕❌
---

Which three queries execute successfully? (Choose three.)

A. SELECT 1 - SYSDATE - DATE '2019-01-01' FROM DUAL;

B. SELECT SYSDATE - DATE '2019-01-01' - 1 FROM DUAL;

C. SELECT SYSDATE / DATE '2019-01-01' - 1 FROM DUAL;

D. SELECT SYSDATE - 1 - DATE '2019-01-01' FROM DUAL;

E. SELECT (SYSDATE - DATE '2019-01-01') / 1 FROM DUAL;

F. SELECT 1 / SYSDATE - DATE '2019-01-01' FROM DUAL;

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

## Prob. 35 ⭕❌
---

Which two are true about granting object privileges on tables, views, and sequences? (Choose two.)

A. INSERT can be granted only on tables and sequences.

B. DELETE can be granted on tables, views, and sequences.

C. SELECT can be granted on tables, views, and sequences.

D. ALTER can be granted only on tables and sequences.

E. REFERENCES can be granted only on tables.

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

## Prob. 36 ⭕❌
---

Examine the description of the BOOKS table:
![prob36](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob36.png)

The table has 100 rows.
Examine this sequence of statements issued in a new session:
INSERT INTO books VALUES ('ADV112', 'Adventures of Tom Sawyer', NULL, NULL);
SAVEPOINT a;
DELETE FROM books;
ROLLBACK TO SAVEPOINT a;
ROLLBACK;
Which two statements are true? (Choose two.)

A. The second ROLLBACK command replays the delete.

B. The first ROLLBACK command restores the 101 rows that were deleted and commits the inserted row.

C. The first ROLLBACK command restores the 101 rows that were deleted, leaving the inserted row still to be committed.

D. The second ROLLBACK command undoes the insert.

E. The second ROLLBACK command does nothing.

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

## Prob. 37 ⭕❌
---

Which two statements are true about an Oracle database? (Choose two.)

A. A table can have multiple primary keys.

B. A column definition can specify multiple data types.

C. A table can have multiple foreign keys.

D. A VARCHAR2 column without data has a NULL value.

E. A NUMBER column without data has a zero value.

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

## Prob. 38 ⭕❌
---

Examine the data in the EMP table:
![prob38](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob39.png)

You execute this query:
![prob38-1](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_21~30/prob38-1.png)

Why does an error occur?

A. An alias name must not contain space characters.

B. An alias name must always be specified in quotes.

C. An alias name must not be used in an ORDER BY clause.

D. An alias name must not be used in a GROUP BY clause.

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

## Prob. 39 ⭕❌
---

Which two actions can you perform with object privileges? (Choose two.)

A. Create roles.

B. Create FOREIGN KEY constraints that reference tables in other schemas.

C. Delete rows from tables in any schema except SYS.

D. Set default and temporary tablespaces for a user.

E. Execute a procedure or function in another schema.

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

## Prob. 40 ⭕❌
---

No user-defined locks are used in your database.
Which three are true about Transaction Control Language (TCL)? (Choose three.)

A. ROLLBACK without the TO SAVEPOINT clause undoes all the transaction's changes, releases its locks, and erases all its savepoints.

B. ROLLBACK without the TO SAVEPOINT clause undoes all the transaction's changes but does not release its locks.

C. ROLLBACK without the TO SAVEPOINT clause undoes all the transaction's changes but does not erase its savepoints.

D. ROLLBACK TO SAVEPOINT undoes the transaction's changes made since the named savepoint and then ends the transaction.

E. COMMIT ends the transaction and makes all its changes permanent.

F. COMMIT erases all the transaction's savepoints and releases its locks.

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