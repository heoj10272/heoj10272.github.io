---
layout: post
title: "[ORACLE-SQL] ExamTopics 51~60"
subtitle: ORACLE
date: '2022-10-30 3:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/logo.png
---

1z0-071 Examtopics 51~60번 문제를 풀어보자.<br>
1차 2/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 51 ❌
---

Examine the description of the EMPLOYEES table:
![prob51](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob51.png)

Which two queries will result in an error? (Choose two.)

A.
![prob51-a](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob51-a.png)

B.
![prob51-b](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob51-b.png)

C.
![prob51-c](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob51-c.png)

D.
![prob51-d](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob51-d.png)

E.
![prob51-e](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob51-e.png)

F.
![prob51-f](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob51-f.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, E

해설 :

`WHERE` 절에서는 `Alias` 사용이 불가능하다.
`ORDER BY` 절에서는 `Alias` 도 허용되고, 표현식을 사용해도 된다.

1차 시도 : C, D 틀림<br>
</div>
</details>

<br>

## Prob. 52 ❌
---

You create a table named 123.
Which statement runs successfully?

A. SELECT * FROM TABLE(123);

B. SELECT * FROM "123";

C. SELECT * FROM \'123\';

D. SELECT * FROM '123';

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 :

19c에서는 쌍따옴표로 테이블명 감싸기 불가능.<br>
12c에서는 가능

1차 시도 : A 틀림<br>
</div>
</details>

<br>

## Prob. 53 ❌
---

Which two statements are true regarding indexes? (Choose two.)

A. An update to a table can result in updates to any or all of the table's indexes.

B. An update to a table can result in no updates to any of the table's indexes.

C. A UNIQUE index can be altered to be non-unique.

D. When a table is dropped and is moved to the RECYCLE BIN, all indexes built on that table are permanently dropped.

E. A table belonging to one user cannot have an index that belongs to a different user.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, D

해설 :

A : 틀림. 인덱스와 테이블은 별개이다. 따라서 `UPDATE` 를 하더라도 인덱스에는 영향이 없다.<br>
B : 맞음. A의 설명 참고.<br>
C : 틀림. 인덱스는 바꿀 수 없으며, 삭제 후 재생성 하는 방법 밖에 없다.<br>
D : 맞음. 테이블을 삭제하면 그에 따른 인덱스도 함께 삭제된다.<br>
E : 맞음. 가능하다. 권한은 있어야 하는듯.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/24117-exam-1z0-082-topic-1-question-77-discussion/)

1차 시도 : A, D 틀림<br>
</div>
</details>

<br>

## Prob. 54 ❓
---

Which two are true about queries using set operators (UNION, UNION ALL, INTERSECT and MINUS)? (Choose three.)

A. The name of each column in the first SELECT list must match the name of the corresponding column in each subsequent SELECT list.

B. None of the set operators can be used when selecting CLOB columns.

C. There must be an equal number of columns in each SELECT list.

D. Each SELECT statement in the query can have an ORDER BY clause.

E. The FOR UPDATE clause cannot be specified.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, C, E

해설 :

답이 세 개다. 수정완료.<br>

A : 틀림. 칼럼의 이름은 달라도 되며, 데이터 타입과 갯수만 일치하면 된다.<br>
B : 맞음. Oracle Docs에 따르면, `BLOB`, `CLOB`, `BFILE`, `VARRAY` 데이터 타입과 `NESTED TABLE` 은 사용할 수 없다.<br>
C : 맞음. 갯수와 데이터 타입은 일치해야 한다.<br>
D : 틀림. `ORDER BY` 절은 각 서브쿼리에 사용될 수 없다. <br>
E : 맞음. Oracle Docs에 따르면, `FOR UPDATE` 절은 사용할 수 없다.<br>

[Oracle Docs](https://docs.oracle.com/database/121/SQLRF/queries004.htm#SQLRF52341)

1차 시도 : B, C 모름<br>
</div>
</details>

<br>

## Prob. 55 ❓
---

BOOK_SEQ is an existing sequence in your schema.
Which two CREATE TABLE commands are valid? (Choose two.)

A.
![prob55-a](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob55-a.png)

B.
![prob55-b](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob55-b.png)

C.
![prob55-c](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob55-c.png)

D.
![prob55-d](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob55-d.png)

E.
![prob55-e](/assets/img/study_Oracle/2022-10-30-[ORACLE-SQL]_ExamTopics_51~60/prob55-e.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, D

해설 :

livesql에서 돌려본 바로는 다음과 같다.
```sql
--A.    
create table bookings (
    bk_id       NUMBER(4)   DEFAULT book_seq.nextval primary key,
    start_date  DATE        DEFAULT SYSDATE,
    end_date    DATE        DEFAULT SYSDATE NOT NULL);
-- table created.

--B.
create table bookings (
    bk_id       NUMBER(4),
    start_date  DATE    DEFAULT SYSDATE,
    end_date    DATE    DEFAULT (end_date >= start_date));
-- ORA-00907: missing right parenthesis

--C.
create table bookings (
    bk_id       NUMBER(4)   NOT NULL DEFAULT book_seq.CURRVAL,
    start_date  DATE        NOT NULL,
    end_date    DATE        DEFAULT SYSDATE);
-- ORA-00907: missing right parenthesis

--D.
create table bookings (
    bk_id       NUMBER(4)   NOT NULL PRIMARY KEY,
    start_date  DATE        NOT NULL,
    end_date    DATE        DEFAULT SYSDATE);
DROP TABLE BOOKINGS;
-- table created.

--E.
create table bookings (
    bk_id       NUMBER(4)   DEFAULT book_seq.CURRVAL,
    start_date  DATE        DEFAULT SYSDATE,
    end_date    DATE        DEFAULT start_date);
-- ORA-00904: "START_DATE": invalid identifier 
```

'missing right parenthesis' 는 우괄호가 없을 때 나오는 오류라는데, 제대로 줬음에도 불구하고 나와서 이유는 잘 모르겠다...<br>
하지만 B, E의 경우는 `start_date` 라는 값이 아예 없기 때문에 실행이 불가능한 것으로 보이고, C의 경우는 `CURRVAL` 을 사용하기 위해서는 해당 세션에서 `NEXTVAL` 의 실행이 선행되어야 하기 때문에 불가능한 것으로 보인다.

1차 시도 : 모름<br>
</div>
</details>

<br>

## Prob. 56 ❌
---

Which three statements are true about multiple row subqueries? (Choose three.)

A. Two or more values are always returned from the subquery.

B. They can contain HAVING clauses.

C. They can contain GROUP BY clauses.

D. They can return multiple columns.

E. They cannot contain a subquery.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, C, D

해설 :

A : 틀림. 다중 행 서브쿼리는 하나 이상의 값을 반환한다.<br>
B : 맞음. `HAVING` 절을 포함할 수 있다. `WHERE` 절이랑 같이 둘 다 포함할 수 있나보다.<br>
C : 맞음. `GROUP BY` 절을 포함할 수 있다.<br>
D : 맞음. 다중 열을 반환할 수 있다.<br>
E : 틀림. 서브쿼리는 서브쿼리를 포함할 수 없나보다.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/9457-exam-1z0-071-topic-1-question-254-discussion/)

1차 시도 : A, B, D 틀림<br>
</div>
</details>

<br>

## Prob. 57 ⭕
---

Which three actions can you perform on an existing table containing data? (Choose three.)

A. Increase the width of a numeric column.

B. Add a new column as the table's first column.

C. Define a default value that is automatically inserted into a column containing nulls.

D. Change a DATE column containing data to a NUMBER data type.

E. Change the default value of a column.

F. Add a new NOT NULL column with a DEFAULT value.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, E, F

해설 :

A. 맞음.<br>
B. 틀렸음. 실습 때 경험했던걸 떠올려보자. 테이블의 칼럼 순서를 바꾸는것은 불가능하다.<br>
C. 틀렸음. 솔직히 무슨 말인지 모르겠다.<br>
D. 틀렸음. 데이터타입을 바꿀 칼럼은 비어있어야 한다.<br>
E. 맞음.<br>
F. 맞음.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/20227-exam-1z0-071-topic-2-question-25-discussion/)

1차 시도 : A, E, F 맞음<br>
</div>
</details>

<br>

## Prob. 58 ❌
---

Which two statements are true about selecting related rows from two tables based on an Entity Relationship Diagram (ERD)? (Choose two.)

A. Rows from unrelated tables cannot be joined.

B. Relating data from a table with data from the same table is implemented with a self join.

C. Implementing a relationship between two tables might require joining additional tables.

D. Every relationship between the two tables must be implemented in a join condition.

E. An inner join relates rows within the same table.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, D

해설 :

A : 틀렸음. 가능하다.<br>
B : 맞음.<br>
C : 틀렸음. 그냥 두 테이블만 있으면 되는거 아닌가?<br>
D : 맞음. <br>
E : 틀렸음. `INNER JOIN` 이 아닌 `SELF JOIN` 에 대한 설명.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/20271-exam-1z0-071-topic-2-question-32-discussion/)

1차 시도 : B, E 틀림<br>
</div>
</details>

<br>

## Prob. 59 ⭕
---

Which three statements about roles are true? (Choose three.)

A. Roles are assigned to users using the ALTER USER statement.

B. Privileges are assigned to a role using the GRANT statement.

C. A role is a named group of related privileges that can only be assigned to a user.

D. A single user can be assigned multiple roles.

E. Privileges are assigned to a role using the ALTER ROLE statement.

F. Roles are assigned to roles using the ALTER ROLE statement.

G. A single role can be assigned to multiple users.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 :

A : 틀렸음. `GRANT` 를 통해 부여된다.<br>
B : 맞음.<br>
C : 틀렸음. 연관된 권한의 집합이 아닐 수 있고, `USER` 만이 아닌 `ROLL` 에도 부여될 수 있다.<br>
D : 맞음.<br>
E : 틀렸음. `GRANT` 를 사용한다.<br>
F : 틀렸음. `GRANT` 를 사용한다.<br>
G : 맞음.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/25763-exam-1z0-071-topic-2-question-63-discussion/)

1차 시도 : B, D, G 맞음<br>
</div>
</details>

<br>

## Prob. 60 ❌
---

The INVOICE table has a QTY_SOLD column of data type NUMBER and an INVOICE_DATE column of data type DATE.
NLS_DATE_FORMAT is set to DD-MON-RR.
Which two are true about data type conversions involving these columns in query expressions? (Choose two.)

A. invoice_date = '15-march-2019' : uses implicit conversion

B. qty_sold BETWEEN '101' AND '110' : uses implicit conversion

C. invoice_date > '01-02-2019' : uses implicit conversion

D. qty_sold = '0554982' : requires explicit conversion

E. CONCAT (qty_sold, invoice_date) : requires explicit conversion

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B

해설 :

A : 맞음. `dd-month-yyyy`는 묵시적 형변환으로 인정된다.<br>
B : 맞음.<br>
C : 틀렸음. 명시적 형변환이 요구된다. 'ORA-01843: not a valid month'<br>
D : 틀렸음. 암시적 형변환으로 인정된다.<br>
E : 틀렸음. 암시적 형변환으로 인정된다.<br>

[ExamTopics 링크](https://www.examtopics.com/discussions/oracle/view/21058-exam-1z0-071-topic-2-question-39-discussion/)

1차 시도 : B, E 틀림<br>
</div>
</details>

<br>