---
layout: post
title: "[ORACLE-SQL] ExamTopics 11~20"
subtitle: ORACLE
date: '2022-xx-xx 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-xx-xx-[ORACLE]_ExamTopics_11~20/logo.png
---

1z0-071 Examtopics 11~20번 문제를 풀어보자.<br>
1차 x/x<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 11 ❌
---

Which three are true about scalar subquery expressions? (Choose three.)

A. They can be nested.

B. They cannot be used in the VALUES clause of an INSERT statement.

C. A scalar subquery expression that returns zero rows evaluates to zero.

D. They can be used as default values for columns in a CREATE TABLE statement.

E. A scalar subquery expression that returns zero rows evaluates to NULL.

F. They cannot be used in GROUP BY clauses.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, E, F

해설 :

scalar subquery란 하나의 값, 즉 하나의 행에서 하나의 칼럼 값을 반환하는 표현식이다.

만약 서브쿼리가 0개의 행을 반환할 경우, scalar subquery 표현식의 값은 `NULL`이 된다.<br>
추가로 1개 초과의 행을 반환할 경우, 오라클에서 에러를 출력한다.

칼럼의 default values로는 올 수 없다.<br>
`GROUP BY` 절에는 올 수 없다.


[참고 링크](https://docs.oracle.com/database/121/SQLRF/expressions014.htm#SQLRF52093)

1차 시도 : A, D, E 틀림<br>
</div>
</details>

<br>

## Prob. 12 ⭕❌
---

Examine this query:
![prob12](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_11~20/prob12.png)

Which two methods should you use to prevent prompting for a hire date value when this query is executed? (Choose two.)

A. Use the DEFINE command before executing the query.

B. Replace '&1' with '&&1' in the query.

C. Use the UNDEFINE command before executing the query.

D. Execute the SET VERIFY OFF command before executing the query.

E. Execute the SET VERIFY ON command before executing the query.

F. Store the query in a script and pass the substitution value to the script when executing it.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, F

해설 :

A and F<br>


1차 시도 : B, D<br>
</div>
</details>

<br>

## Prob. 13 ⭕❌
---

You need to allow user ANDREW to:
1. Modify the TITLE and ADDRESS columns of your CUSTOMERS table.
2. GRANT that permission to other users.
Which statement will do this?

A. GRANT UPDATE ON customers.title, customers.address TO andrew;

B. GRANT UPDATE (title, address) ON customers TO andrew;

C. GRANT UPDATE (title, address) ON customers TO andrew WITH GRANT OPTION;

D. GRANT UPDATE ON customers.title, customers.address TO andrew WITH ADMIN OPTION;

E. GRANT UPDATE ON customers.title, customers.address TO andrew WITH GRANT OPTION;

F. GRANT UPDATE (title, address) ON customers TO andrew WITH ADMIN OPTION;

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

## Prob. 14 ⭕❌
---

You own table DEPARTMENTS, referenced by views, indexes, and synonyms.
Examine this command which executes successfully:
DROP TABLE departments PURGE;
Which three statements are true? (Choose three.)

A. It will remove the DEPARTMENTS table from the database.

B. It will drop all indexes on the DEPARTMENTS table.

C. It will remove all views that are based on the DEPARTMENTS table.

D. It will remove all synonyms for the DEPARTMENTS table.

E. Neither can it be rolled back nor can the DEPARTMENTS table be recovered.

F. It will delete all rows from the DEPARTMENTS table, but retain the empty table.

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

## Prob. 15 ⭕❌
---

Which three statements are true about Structured Query Language (SQL)? (Choose three.)

A. It requires that data be contained in hierarchical data storage.

B. It best supports relational databases.

C. It provides independence for logical data structures being manipulated from the underlying physical data storage.

D. It is the only language that can be used for both relational and object-oriented databases.

E. It guarantees atomicity, consistency, isolation, and durability (ACID) features.

F. It is used to define encapsulation and polymorphism for a relational table.

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

## Prob. 16 ⭕❌
---

Which two statements are true about Oracle synonyms? (Choose two.)

A. Any user can create a PUBLIC synonym.

B. A synonym has an object number.

C. All private synonym names must be unique in the database.

D. A synonym can be created on an object in a package.

E. A synonym can have a synonym.

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

## Prob. 17 ⭕❌
---

Which is true about the ROUND, TRUNC and MOD functions?

A. TRUNC(MOD(25,3),-1) is invalid.

B. ROUND(MOD(25,3),-1) is invalid.

C. ROUND(MOD(25,3),-1) and TRUNC(MOD(25,3),-1) are both valid and give the same result.

D. ROUND(MOD(25,3),-1) and TRUNC(MOD(25,3),-1) are both valid but give different results.

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

## Prob. 18 ⭕❌
---

Which two are true about transactions in the Oracle Database? (Choose two.)

A. DML statements always start new transactions.

B. DDL statements automatically commit only data dictionary updates caused by executing the DDL.

C. A session can see uncommitted updates made by the same user in a different session.

D. A DDL statement issued by a session with an uncommitted transaction automatically commits that transaction.

E. An uncommitted transaction is automatically committed when the user exits SQL*Plus.

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

## Prob. 19 ⭕❌
---

Examine the description of the MEMBERS table:
![prob19](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_11~20/prob19.png)

Examine the partial query:
SELECT city, last_name AS lname FROM members ...;
You want to display all cities that contain the string AN. The cities must be returned in ascending order, with the last names further sorted in descending order.
Which two clauses must you add to the query? (Choose two.)

A. ORDER BY 1, 2

B. ORDER BY 1, lname DESC

C. WHERE city IN ('%AN%')

D. WHERE city = '%AN%'

E. WHERE city LIKE '%AN%'

F. ORDER BY last_name DESC, city ASC

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

## Prob. 20 ⭕❌
---

Examine this partial command:
![prob20](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_11~20/prob20.png)

Which two clauses are required for this command to execute successfully? (Choose two.)

A. the access driver TYPE clause

B. the DEFAULT DIRECTORY clause

C. the REJECT LIMIT clause

D. the LOCATION clause

E. the ACCESS PARAMETERS clause

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