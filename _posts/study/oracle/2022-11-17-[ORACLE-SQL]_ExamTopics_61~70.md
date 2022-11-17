---
layout: post
title: "[ORACLE-SQL] ExamTopics 61~70"
subtitle: ORACLE
date: '2022-xx-xx 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-xx-xx-[ORACLE-SQL]_ExamTopics_61~70/logo.png
---

1z0-071 Examtopics 61~70번 문제를 풀어보자.<br>
1차 x/x<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 61 ❌
---

Which three statements are true about inner and outer joins? (Choose three.)

A. A full outer join returns matched and unmatched rows.

B. Outer joins can be used when there are multiple join conditions on two tables.

C. A full outer join must use Oracle syntax.

D. Outer joins can only be used between two tables per query.

E. A left or right outer join returns only unmatched rows.

F. An inner join returns matched rows.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B, F

해설 :

A : 맞음.<br>
B : 맞음. <br>
C : 틀렸음. Oracle 문법 말고도 사용할 수 있다.<br>
D : 틀렸음. 여러개의 테이블도 가능하다.<br>
E : 틀렸음. 매치되는 행도 출력한다.<br>
F : 맞음.<br>

1차 시도 : A, D, F 틀림<br>
</div>
</details>

<br>

## Prob. 62 ❌
---

Which statement will execute successfully?

A.<br>
![prob62-a](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob62-a.png)

B.<br>
![prob62-b](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob62-b.png)

C.<br>
![prob62-c](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob62-c.png)

D.<br>
![prob62-d](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob62-d.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 :

`ORDER BY` 뒤에 오는 숫자는 칼럼을 뜻한다.<br>
알고는 있었는데 칼럼명이 숫자일 때 그걸 그대로 쓸 때에도 오류가 나는줄은 몰랐다 ...<br>

1차 시도 : C 틀림<br>
</div>
</details>

<br>

## Prob. 63 ⭕
---

Examine the description of the EMPLOYEES table:
![prob63](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob63.png)

Which two queries return all rows for employees whose salary is greater than the average salary in their department? (Choose two.)

A.
![prob63-a](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob63-a.png)

B.
![prob63-b](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob63-b.png)

C.
![prob63-c](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob63-c.png)

D.
![prob63-d](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob63-d.png)

E.
![prob63-e](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob63-e.png)

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, E

해설 :

A : 틀렸음. `WHERE` 절에는 그룹 함수가 올 수 없다.<br>
B : 맞음.<br>
C : 틀렸음. `WHERE` 절은 단일 행 서브쿼리를 요구하지만, 해당 서브쿼리는 다중 행 서브쿼리이다.<br>
D : 틀렸음. C를 개선하여 다중 행 서브쿼리로 만들었지만, 이번에는 문제 의도와 맞지 않음. 자신의 부서의 평균 급여 뿐만 아니라 다른 부서의 평균 급여보다 높으면 전부 출력됨.<br>
E : 맞음.<br>

1차 시도 : B, E 맞음<br>
</div>
</details>

<br>

## Prob. 64 ⭕❌
---

Which three statements are true about the Oracle join and ANSI join syntax? (Choose three.)

A. The Oracle join syntax supports creation of a Cartesian product of two tables.

B. The Oracle join syntax only supports right outer joins.

C. The SQL:1999 compliant ANSI join syntax supports creation of a Cartesian product of two tables.

D. The Oracle join syntax performs less well than the SQL:1999 compliant ANSI join syntax.

E. The Oracle join syntax supports natural joins.

F. The Oracle join syntax performs better than the SQL:1999 compliant ANSI join syntax.

G. The SQL:1999 compliant ANSI join syntax supports natural joins.

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

## Prob. 65 ⭕❌
---

Which two are true about the NVL, NVL2, and COALESCE functions? (Choose two.)

A. NVL must have expressions of the same data type.

B. NVL can have any number of expressions in the list.

C. NVL2 can have any number of expressions in the list.

D. COALESCE stops evaluating the list of expressions when it finds the first non-null value.

E. The first expression in NVL2 is never return
ed.

F. COALESCE stops evaluating the list of expressions when it finds the first null value.

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

## Prob. 66 ⭕❌
---

Examine this statement:
![prob66](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob66.png)

What is returned upon execution?
A. an error
B. 2 rows
C. 0 rows
D. 1 row

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

## Prob. 67 ⭕❌
---

Examine this statement:
![prob67](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob67.png)

What is returned upon execution?
A. an error
B. 2 rows
C. 0 rows
D. 1 row

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

## Prob. 68 ⭕❌
---

Which two statements execute successfully? (Choose two.)

A.
![prob68-a](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob68-a.png)

B.
![prob68-b](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob68-b.png)

C.
![prob68-c](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob68-c.png)

D.
![prob68-d](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob68-d.png)

E.
![prob68-e](/assets/img/study_Oracle/2022-10-xx-[ORACLE-SQL]_ExamTopics_51~60/prob68-e.png)

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

## Prob. 69 ⭕❌
---

An Oracle Database session has an uncommitted transaction in progress which updated 5000 rows in a table.
In which three situations does the transaction complete thereby committing the updates? (Choose three.)

A. when a CREATE TABLE AS SELECT statement is issued in the same session but fails with a syntax error

B. when a DBA issues a successful SHUTDOWN TRANSACTIONAL statement and the user then issues a COMMIT

C. when the session logs out successfully

D. when a CREATE INDEX statement is executed successfully in the same session

E. when a DBA issues a successful SHUTDOWN IMMEDIATE statement and the user then issues a COMMIT

F. when a COMMIT statement is issued by the same user from another session in the same database instance

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

## Prob. 70 ⭕❌
---

Which two are true about using constraints? (Choose two.)

A. NOT NULL can be specified at the column and at the table level.

B. A table can have only one PRIMARY KEY and one FOREIGN KEY constraint.

C. A FOREIGN KEY column in a child table and the referenced PRIMARY KEY column in the parent table must have the same names.

D. PRIMARY KEY and FOREIGN KEY constraints can be specified at the column and at the table level.

E. A table can have multiple PRIMARY KEY and multiple FOREIGN KEY constraints.

F. A table can have only one PRIMARY KEY but may have multiple FOREIGN KEY constraints.

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