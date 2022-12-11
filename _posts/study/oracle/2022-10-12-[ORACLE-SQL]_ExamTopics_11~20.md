---
layout: post
title: "[ORACLE-SQL] ExamTopics 11~20"
subtitle: ORACLE
date: '2022-10-12 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-10-12-[ORACLE-SQL]_ExamTopics_11~20/logo.png
---

1z0-071 Examtopics 11~20번 문제를 풀어보자.<br>
1차 4/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 11 ❌⭕
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
2차 시도 : A, E, F 맞음<br>
</div>
</details>

<br>

## Prob. 12 ❌❌
---

Examine this query:<br>
![prob12](/assets/img/study_Oracle/2022-10-12-[ORACLE-SQL]_ExamTopics_11~20/prob12.png)

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
A : `DEFINE` 을 사용해서 치환변수에 들어갈 값을 미리 지정할 수 있다.<br>
F : 정확히는 모르겠지만 스크립트에 쿼리를 저장하여 할 수 있다고 한다...<br>
[F 참고 링크 1 - Passing Parameters through the START Command](https://docs.oracle.com/cd/F49540_01/DOC/server.815/a66736/ch33.htm)<br>
[F 참고 링크 2 - 구루비](http://wiki.gurubee.net/pages/viewpage.action?pageId=20021302)

1차 시도 : B, D 틀림<br>
2차 시도 : B, F 틀림<br>
</div>
</details>

<br>

## Prob. 13 ❌⭕
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
Answer : C

해설 :

C가 맞는 표현이다.

[Examtopics](https://www.examtopics.com/discussions/oracle/view/22162-exam-1z0-071-topic-2-question-69-discussion/)

1차 시도 : E 틀림<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>

## Prob. 14 ❌❌
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
Answer : A, B, E

해설 :

A : 맞음. `PURGE` 를 사용했기 떄문에 테이블이 `recyclebin`에 가지 않고 바로 삭제됨.<br>
B : 맞음. `DROP` 시 `INDEX`, `TRIGGER` 가 함께 삭제된다.<br>
C : 틀렸음. `DROP` 을 해도 `VIEW`, `SYNONYM`, `STORED PROECEDURE`, `FUNCTION`, `PACKAGE` 는 비활성화 되지만 삭제되지는 않는다. 테이블을 RECREATE 할 경우, 재활성화된다.<br>
D : 틀렸음. C의 설명과 동일.<br>
E : 맞음. `PURGE` 를 사용했기 때문에 롤백될수도 없고, 복구될수도 없다.<br>
F : 틀렸음. 행이 삭제될 뿐만 아니라 테이블이 모두 삭제된다.<br>

[Oracle Docs 링크](https://docs.oracle.com/database/121/SQLRF/statements_9003.htm#SQLRF01806)

1차 시도 : B, C, D 틀림<br>
2차 시도 : A, C, D 틀림<br>
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
Answer : B, C, E

해설 :

A. 틀렸음. hierarchical은 relational과는 다른 개념이다. hierarchical 구조는 일대일 관계로 일대다, 다대다 관계는 지원하지 않는 반면, relational 구조는 모두 지원한다.<br>
B. 맞음. SQL은 관계형 데이터베이스를 위한 언어이다.<br>
C. 맞음. 잘 모르겠는데 맞는 말인가보다.<br>
D. 틀렸음. SQL은 관계형 데이터베이스를 위한 언어이다.<br>
E. 맞음. SQL은 ACID를 특징으로 가진다.<br>
F. 틀렸음. 그냥 틀린듯...<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/8463-exam-1z0-071-topic-1-question-290-discussion/)

1차 시도 : B, C, E 맞음<br>
2차 시도 : B, E, F 틀림<br>
</div>
</details>

<br>

## Prob. 16 ❌⭕
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
Answer : B, E

해설 :

A : 틀렸음. `CREATE PUBLIC SYNONYM` 권한이 있어야 한다.<br>
B : 맞음. 시노님은 object number를 가진다. `USER_OBJECTS` 테이블에서 `OBJECT_ID`를 가진다.<br>
C : 틀렸음. 프라이빗 시노님은 해당 스키마에서만 unique하다.<br>
D : 틀렸음. 스키마 오브젝트는 패키지에 있을 수 없다. -> PL/SQL 패키지에 있는 오브젝트에 생성할 수는 있으나, 활성화되지 않는다고 한다.<br>
E : 맞음. 시노님은 시노님을 가질 수 있다.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/8431-exam-1z0-071-topic-1-question-270-discussion/)

1차 시도 : A, D 틀림<br>
1차 시도 : B, E 맞음<br>
</div>
</details>

<br>

## Prob. 17 ⭕⭕
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
Answer : C

해설 :

둘 다 0을 출력한다.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>

## Prob. 18 ⭕⭕
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
Answer : D, E

해설 :

A : 틀렸음. 항상 새로운 트랜재션을 생성하지는 않는다.<br>
B : 틀렸음. DDL문은 항상 커밋을 한다고 알고 있다.<br>
C : 틀렸음. 커밋되지 않은 업데이트는 다른 세션에서 볼 수 없다.<br>
D : 맞음.<br>
E : 맞음.<br>

1차 시도 : D, E<br>
2차 시도 : D, E<br>
</div>
</details>

<br>

## Prob. 19 ⭕⭕
---

Examine the description of the MEMBERS table:<br>
![prob19](/assets/img/study_Oracle/2022-10-12-[ORACLE-SQL]_ExamTopics_11~20/prob19.png)

Examine the partial query:<br>
SELECT city, last_name AS lname FROM members ...;<br>
You want to display all cities that contain the string AN. The cities must be returned in ascending order, with the last names further sorted in descending order.<br>
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
Answer : B, E

해설 :

`%AN%` 는 `LIKE` 절을 통해 사용할 수 있다.

1차 시도 : B, E 맞음<br>
2차 시도 : B, E 맞음<br>
</div>
</details>

<br>

## Prob. 20 ❓❓
---

Examine this partial command:<br>
![prob20](/assets/img/study_Oracle/2022-10-12-[ORACLE-SQL]_ExamTopics_11~20/prob20.png)

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
Answer : B, E

해설 :

external data properties를 포함해야한다.<br>
이 때 properties는 `DEFAULT DIRECTORY`, `LOCATION` 으로 구성된다.

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/9437-exam-1z0-071-topic-1-question-297-discussion/)

1차 시도 : B, 모름<br>
2차 시도 : 모름<br>
</div>
</details>

<br>