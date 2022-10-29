---
layout: post
title: "[ORACLE-SQL] ExamTopics 41~50"
subtitle: ORACLE
date: '2022-10-29 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/logo.png
---

1z0-071 Examtopics 41~50번 문제를 풀어보자.<br>
1차 4/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 41 ❌ 다시보기
---

Examine the description of the EMPLOYEES table:
![prob41](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob41.png)

Which two queries return rows for employees whose manager works in a different department? (Choose two.)

A.
![prob41-a](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob41-a.png)

B.
![prob41-b](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob41-b.png)

C.
![prob41-c](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob41-c.png)

D.
![prob41-d](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob41-d.png)

E.
![prob41-e](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob41-e.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, E

해설 :

`LEFT JOIN`, `RIGHT JOIN` 에 대해서 다시 보자.

1차 시도 : B, C 틀림<br>
</div>
</details>

<br>

## Prob. 42 ❌
---

Which three are true about dropping columns from a table? (Choose three.)

A. A column must be set as unused before it is dropped from a table.

B. A primary key column cannot be dropped.

C. Multiple columns can be dropped simultaneously using the ALTER TABLE command.

D. A column can be removed only if it contains no data.

E. A column that is referenced by another column in any other table cannot be dropped.

F. A column drop is implicitly committed.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, E, F

해설 :

좀 애매한 문제다 ...<br>
C, F는 당연한데, B, E가 좀 애매하다.

A : 틀림. `UNUSED` 로 비활성화 시킨 뒤 `DROP` 을 하면 편하지만, 필수 조건은 아님.<br>
B : 맞음. 하지만 해당 `PK` 를 참조하는 `FK` 가 없을 경우, 삭제 가능.
C : 맞음. 가능함. [DBA-ORACLE 링크](http://www.dba-oracle.com/t_alter_table_drop_column_syntax_example.htm)<br>
D : 틀림. 데이터를 가지고 있어도 `DROP` 가능.<br>
E : 틀림. `CASCADE` 옵션을 사용하면 가능.<br>
F : 맞음. 당연함.

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/8226-exam-1z0-071-topic-1-question-244-discussion/)

1차 시도 : B, C, F 틀림<br>
</div>
</details>

<br>

## Prob. 43 ⭕
---

Which three statements are true about views in an Oracle Database? (Choose three.)

A. A SELECT statement cannot contain a WHERE clause when querying a view containing a WHERE clause in its defining query.

B. Views have no segment.

C. Views have no object number.

D. Views can join tables only if they belong to the same schema.

E. A view can be created that refers to a non-existent table in its defining query.

F. Rows inserted into a table using a view are retained in the table if the view is dropped.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, E, F

해설 :

B : 뷰는 세그먼트를 가지지 않는다.<br>
E : `FORCE` 를 옵션으로 뷰를 생성하면 `INVALID` 상태지만 생성이 가능하다.<br>
F : 당연하다.

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/9426-exam-1z0-071-topic-1-question-231-discussion/)

1차 시도 : B, E, F 맞음<br>
</div>
</details>

<br>

## Prob. 44 ❌
---

You start a session and execute these commands successfully:
![prob44](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob44.png)

Which two are true? (Choose two.)

A. To drop the table in this session, you must first truncate it.

B. Other sessions can view the committed row.

C. You can add a column to the table in this session.

D. You can add a foreign key to the table.

E. When you terminate your session, the row will be deleted.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, E

해설 :

A : 맞음. `insert`가 이루어졌기 떄문에, `truncate`가 우선되어야 한다. 사용중인 임시 테이블에는 `drop`을 할 수 없다.<br>
B : 틀림. 다른 세션에서 전역 임시 테이블을 조회할 수 없음.<br>
C : 틀림. 임시 테이블에는 칼럼을 추가할 수 없음.<br>
D : 틀림. 임시 테이블에는 `FK`를 추가할 수 없음.<br>
E : 맞음. 세션이 종료되면, 모든 행은 삭제됨. 하지만 테이블 스키마는 남는다고 한다.<br>

1차 시도 : D, E 틀림<br>
</div>
</details>

<br>

## Prob. 45 ❓
---

Examine this statement:
![prob45](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob45.png)

Which two statements are true? (Choose two.)

A. The names of employees earning the maximum salary will appear first in an unspecified order.

B. All remaining employee names will appear in descending order.

C. All remaining employee names will appear in an unspecified order.

D. All remaining employee names will appear in ascending order.

E. The names of employees earning the maximum salary will appear first in ascending order.

F. The names of employees earning the maximum salary will appear first in descending order.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D, F

해설 :

잘 모르겠다.
remaining 이라는게 `case`의 대상이 되지 않는 행들을 말하는 것 같은데 ...

1차 시도 : B, E <br>
</div>
</details>

<br>

## Prob. 46 ❓
---

Which two are true about external tables that use the ORACLE_DATAPUMP access driver? (Choose two.)

A. When creating an external table, data can be selected only from a table whose rows are stored in database blocks.

B. Creating an external table creates a directory object.

C. When creating an external table, data can be selected from another external table or from a table whose rows are stored in database blocks.

D. Creating an external table creates a dump file that can be used by an external table in the same or a different database.

E. Creating an external table creates a dump file that can be used only by an external table in the same database.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, D

해설 :

As part of creating an external table with a SQL CREATE TABLE AS SELECT statement, the ORACLE_DATAPUMP access driver can write data to a dump file. The data in the file is written in a binary format that can only be read by the ORACLE_DATAPUMP access driver. Once the dump file is created, it cannot be modified (that is, no data manipulation language (DML) operations can be performed on it). However, the file can be read any number of times and used as the dump file for another external table in the same database or in a different database. <br> (https://docs.oracle.com/database/121/SUTIL/GUID-0B2EC1B2-701D-42ED-874C-47F22F21D847.htm#SUTIL1457)

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/22606-exam-1z0-071-topic-2-question-60-discussion/)

1차 시도 : 모름<br>
</div>
</details>

<br>

## Prob. 47 ⭕
---

Examine the description of the EMPLOYEES table:
![prob47](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob47.png)

Which statement will fail?

A.
![prob47-a](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob47-a.png)

B.
![prob47-b](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob47-b.png)

C.
![prob47-c](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob47-c.png)

D.
![prob47-d](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob47-d.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 :

`WHERE` 절은 그룹을 제한하는데 사용할 수 없다.

1차 시도 : A 맞음<br>
</div>
</details>

<br>

## Prob. 48 ⭕
---

Examine the data in the NEW_EMPLOYEES table:
![prob48](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob48.png)

Examine the data in the EMPLOYEES table:
![prob48-1](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob48-1.png)

You want to:
1. Update existing employee details in the EMPLOYEES table with data from the NEW_EMPLOYEES table.
2. Add new employee details from the NEW_EMPLOYEES table to the EMPLOYEES table.
Which statement will do this?

A.
![prob48-a](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob48-a.png)

B.
![prob48-b](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob48-b.png)

C.
![prob48-c](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob48-c.png)

D.
![prob48-d](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob48-d.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 :

`MERGE INTO` 문에 대한 문제이다.
1. `ON` VS `WHERE`
2. `MATCHED` VS `FOUND`
위 키워드를 구분하는 문제인데, 답은 `ON`, `MATCHED` 이다.

1차 시도 : A 맞음<br>
</div>
</details>

<br>

## Prob. 49 ⭕
---

Examine the description of the EMPLOYEES table:
![prob49](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob49.png)

For each employee in department 90 you want to display:
1. their last name
2. the number of complete weeks they have been employed
The output must be sorted by the number of weeks, starting with the longest serving employee first.
Which statement will accomplish this?

A.
![prob49-a](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob49-a.png)

B.
![prob49-b](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob49-b.png)

C.
![prob49-c](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob49-c.png)

D.
![prob49-d](/assets/img/study_Oracle/2022-10-29-[ORACLE-SQL]_ExamTopics_41~50/prob49-d.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 :

완료한 주차만 세는 것이므로 `TRUNC` 를 사용하는 것이 타당하다.

1차 시도 : B 맞음<br>
</div>
</details>

<br>

## Prob. 50 ❌
---

Examine the description of the PRODUCT_DETAILS table:

Which two statements are true? (Choose two.)

A. EXPIRY_DATE contains the SYSDATE by default if no date is assigned to it.

B. PRODUCT_PRICE can be used in an arithmetic expression even if it has no value stored in it.

C. PRODUCT_NAME cannot contain duplicate values.

D. EXPIRY_DATE cannot be used in arithmetic expressions.

E. PRODUCT_PRICE contains the value zero by default if no value is assigned to it.

F. PRODUCT_ID can be assigned the PRIMARY KEY constraint.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, F

해설 :

A : 틀림. `NULL` 이 들어간다.<br>
B : 맞음. 하지만 값이 들어있지 않는 `NULL` 이 대상이기 때문에, 결과도 `NULL`이 나올 것이다.<br>
C : 틀림. `PK` 거나 `UNIQUE` 칼럼이 아니기 때문에, 중복된 값을 가질 수 있음.<br>
D : 틀림. `DATE` 형의 데이터타입에 산술 연산을 하면, 날짜에 반영됨.<br>
E : 틀림. `DEFAULT` 로 정해둔게 없기 때문에, `NULL` 이 들어감.<br>
F : 맞음. 좀 애매하지만, 보통 ID 칼럼을 `PK` 로 쓰기 때문에 맞을듯.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/8221-exam-1z0-071-topic-1-question-229-discussion/)

1차 시도 : E, F 틀림<br>
</div>
</details>

<br>