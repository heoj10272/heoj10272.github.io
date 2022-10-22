---
layout: post
title: "[ORACLE-SQL] ExamTopics 31~40"
subtitle: ORACLE
date: '2022-10-18 01:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-10-18-[ORACLE-SQL]_ExamTopics_31~40/logo.png
---

1z0-071 Examtopics 31~40번 문제를 풀어보자.<br>
1차 7/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 31 ❌
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
Answer : C, D, F

해설 :

`GLOBAL TEMPORARY TABLE`, 즉 `전역 임시 테이블`은 `SESSION` 또는 `TX` 레벨의 임시 데이터를 저장하는 용도로 사용된다.<br>
오라클의 실행 계획을 저장하기 위한 `Plan` 테이블이 전역 임시 테이블의 대표적인 사례이다.

`ON COMMIT DELETE ROWS` : `TX` 단위 데이터 유지, `COMMIT` 시 데이터 소실.<br>
`ON COMMIT PRESERVE ROWS` : `SESSION` 단위 데이터 유지, `COMMIT` 해도 데이터 유지, 다른 세션에서 조회 불가.

즉, 테이블 정의는 모든 세션에서 권한 보유시 조회 가능하나 내부 데이터는 세션별로 독립적이기 때문에 다른 세션에서 접근이 불가능하다.

임시 테이블에도 `INDEX`, `VIEW`, `TRIGGER` 생성, `PK` 설정 가능하다.

A : 틀렸음. 첫 `DML` 이 시작될 때 할당되는 듯 하다.
B : 틀렸음. 다른 세션에서는 접근이 불가능함.
C : 맞음. `TRUNCATE` 를 사용하면 테이블의 모든 행을 삭제한다.
D : 맞음. 어떤 옵션이든 `SESSION` 이 종료되면 함께 종료된다.
E : 틀렸음. `ON COMMIT PRESERVE ROWS` 로 설정하면, `DELETE` 를 해도 `ROLLBACK` 가능하다.
F : 맞음. 세션별로 정의가 가능하다. 권한은 있어야하는듯 하다.

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/8895-exam-1z0-071-topic-1-question-298-discussion/)

1차 시도 : B, D, E 틀림<br>
</div>
</details>

<br>

## Prob. 32 ⭕
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
Answer : D, E (+B)

해설 :

`DEFINE` 한 값, `&&` 도 나오고, `SQL Developer` 와 `SQL*Plus` 에서도 사용 가능하다는데 ..<br>
B도 답이라는데 일단 맞다고 해야겠다.

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/20161-exam-1z0-071-topic-2-question-28-discussion/)

1차 시도 : D, E<br>
</div>
</details>

<br>

## Prob. 33 ❓
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
Answer : D, E

해설 :

3번 문항에 의해 중복된 값은 허용되지 않으므로, `CYCLE` 옵션은 배제되어야 할 것 같다.<br>
5번 문항은 값에 차이가 날 경우를 줄이라는 뜻 같은데, 이 경우 캐시를 사용하지 않는 `NOCACHE`를 사용하면 될 것 같다.<br>

[시퀀스 갭에 대한 블로그 설명 링크](https://doughman.tistory.com/m/11)

1차 시도 : 모름<br>
</div>
</details>

<br>

## Prob. 34 ⭕
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
Answer : B, D, E

해설 :

날짜와 날짜, 날짜와 숫자(일 수로 계산됨)은 허용되므로, B, D, E가 답인 것 같다.<br>
E는 아마 일 수가 출력될 것 같다.

1차 시도 : B, D, E 맞음<br>
</div>
</details>

<br>

## Prob. 35 ⭕
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
Answer : C, D

해설 :

![oracle_privs](/assets/img/study_Oracle/2022-10-18-[ORACLE-SQL]_ExamTopics_31~40/oracle_privs.png)

위 표를 참조하자.

[표 출처 링크](https://techgoeasy.com/create-user-system-privileges-object-privileges/)

1차 시도 : C, D 맞음<br>
</div>
</details>

<br>

## Prob. 36 ⭕
---

Examine the description of the BOOKS table:<br>
![prob36](/assets/img/study_Oracle/2022-10-18-[ORACLE-SQL]_ExamTopics_31~40/prob36.png)

The table has 100 rows.<br>
Examine this sequence of statements issued in a new session:<br>
INSERT INTO books VALUES ('ADV112', 'Adventures of Tom Sawyer', NULL, NULL);<br>
SAVEPOINT a;<br>
DELETE FROM books;<br>
ROLLBACK TO SAVEPOINT a;<br>
ROLLBACK;<br>
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
Answer : C, D

해설 :

그냥 C, D

1차 시도 : C, D 맞음<br>
</div>
</details>

<br>

## Prob. 37 ⭕
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
Answer : C, D

해설 :

E : `NUMBER` 칼럼에 데이터가 들어있지 않은 경우, 0이 아닌 `NULL` 값이 위치한다.

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/21762-exam-1z0-071-topic-2-question-64-discussion/)

1차 시도 : C, D 맞음<br>
</div>
</details>

<br>

## Prob. 38 ⭕
---

Examine the data in the EMP table:<br>
![prob38](/assets/img/study_Oracle/2022-10-18-[ORACLE-SQL]_ExamTopics_31~40/prob38.png)

You execute this query:<br>
![prob38-1](/assets/img/study_Oracle/2022-10-18-[ORACLE-SQL]_ExamTopics_31~40/prob38-1.png)

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
Answer : D

해설 :

`GROUP BY` 절에는 앨리어스를 사용할 수 없다.

1차 시도 : D 맞음<br>
</div>
</details>

<br>

## Prob. 39 ❌
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
Answer : B, E

해설 :

A : 틀림. `ROLE` 을 생성하는건 `System Priv` 가 필요하다.<br>
B : 맞음. `REFERENCE` 권한으로 가능.<br>
C : 틀림. `DELETE ANY TABLE` 이라는 시스템 권한으로 가능.<br>
D : 틀림? 아마도 시스템 권한인듯.
E : 맞음.

[Oracle Docs - CREATE ROLE](https://docs.oracle.com/database/121/SQLRF/statements_6014.htm#SQLRF01311)

[Oracle Docs - Privilegs](https://docs.oracle.com/database/121/TTSQL/privileges.htm#TTSQL338)

1차 시도 : A, D 틀림<br>
</div>
</details>

<br>

## Prob. 40 ⭕
---

No user-defined locks are used in your database.<br>
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
Answer : A, E, F

해설 :

트랜잭션이 끝나는 경우는 다음과 같다 :
1. `COMMIT` 을 사용한 경우.
2. `SAVEPOINT` 절을 사용하지 않은 `ROLLBACK` 을 사용했을 경우.
3. `DDL` 을 사용했을 경우.
4. 연결을 종료했을 경우.
5. 비정상적으로 프로세스가 종료되었을 경우. 이 경우 트랜잭션은 롤백된다.

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/20437-exam-1z0-071-topic-2-question-58-discussion/)

1차 시도 : A, E, F 맞음<br>
</div>
</details>

<br>