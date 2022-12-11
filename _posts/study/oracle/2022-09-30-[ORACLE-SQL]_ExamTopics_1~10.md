---
layout: post
title: "[ORACLE-SQL] ExamTopics 1~10"
subtitle: ORACLE
date: '2022-09-30 14:00:00 +0900'
category: study
tags: oracle examtopics 1z0-071
image:
  path: /assets/img/study_Oracle/2022-09-22-[ORACLE]_SQL_함수_활용_1/logo.png
---

1z0-071 Examtopics 1~10번 문제를 풀어보자.<br>
1차 4/9<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 1 ⭕⭕
---

Examine the description of the PROMOTIONS table:
![prob1](/assets/img/study_Oracle/2022-09-30-[ORACLE-SQL]_ExamTopics_1~10/prob1.png)

You want to display the unique promotion costs in each promotion category.
Which two queries can be used? (Choose two.)

A. SELECT DISTINCT promo_category \|\| ' has ' \|\| promo_cost AS COSTS FROM promotions ORDER BY 1;

B. SELECT DISTINCT promo_cost \|\| ' in ' \|\| DISTINCT promo_category FROM promotions ORDER BY 1;

C. SELECT DISTINCT promo_category, promo_cost FROM promotions ORDER BY 1;

D. SELECT promo_category DISTINCT promo_cost, FROM promotions ORDER BY 2;

E. SELECT promo_cost, promo_category FROM promotions ORDER BY 1;

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

해설 :

`promo_category`별로 `promo_cost`를 출력하는데, 중복을 제외하고 출력해야하는 문제이다.<br>
B : 중복 제거를 위해서 사용하는 `DISTINCT`는 한 번만 적으면 된다.<br>
D : `DISTINCT`는 `promo_category`앞에 적는게 적절해보인다.<br>
E : 중복 제거가 되지 않는다. <br>

1차 시도 : A, C 맞음<br>
2차 시도 : A, C 맞음<br>
</div>
</details>

<br>

## Prob. 2 ⭕⭕
---

Examine the description of the PRODUCTS table:
![prob2](/assets/img/study_Oracle/2022-09-30-[ORACLE-SQL]_ExamTopics_1~10/prob2.png)

Which three queries use valid expressions? (Choose three.)

A. SELECT product_id, unit_price, S "Discount", unit_price + surcharge - discount FROM products;

B. SELECT product_id, (unit_price * 0.15 / (4.75 + 552.25)) FROM products;

C. SELECT product_id, (expiry_date - delivery_date) * 2 FROM products;

D. SELECT product_id, unit_price \|\| 5 "Discount", unit_price + surcharge - discount FROM products;

E. SELECT product_id, expiry_date * 2 FROM products;

F. SELECT product_id, unit_price, unit_price + surcharge FROM products;

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, C, F

해설 : 

B : `unit_price`는 `NUMBER` 데이터타입이므로, 숫자 연산이 가능하다.<br>
C : `DATE` 타입 끼리의 뺄셈 연산시 결과는 일 수가 나오며, 숫자 연산이 가능하다.<br>
F : `unit_price`는 `NUMBER`형, `surcharge`는 `VARCHAR2`형으로 두 칼럼의 데이터 타입이 다르지만, `surcharge` 칼럼의 이름을 보았을 때 데이터가 숫자임이 예상되고, 이 때 묵시적 형변환에 의해 연산이 가능하다.<br>

A, D : "Discount" 가 무엇을 의미하는지 모르겠다...<br>
E : `DATE` 타입의 곱셈 연산은 불가능하다.


1차 시도 : B, C, F 맞음<br>
2차 시도 : B, C, F 맞음<br>
</div>
</details>

<br>

## Prob. 3 ❌⭕
---

What is true about non-equijoin statement performance? (Choose two.)

A. The BETWEEN condition always performs less well than using the >= and <= conditions.

B. The BETWEEN condition always performs better than using the >= and <= conditions.

C. The Oracle join syntax performs better than the SQL:1999 compliant ANSI join syntax.

D. Table aliases can improve performance.

E. The join syntax used makes no difference to performance.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D는 확실, C와 E 중 하나 // E가 답인듯

해설 : 

57번 문제와 동일한 문제인 모양이다.<br>
링크[https://www.examtopics.com/discussions/oracle/view/24426-exam-1z0-082-topic-1-question-57-discussion/] 참고<br>
D : alias를 사용하면 성능을 향상시킬 수 있다.<br>
E : 성능적으로 별 영향이 없나보다.

A, B : 내부적으로 `BETWEEN`은 `<=, >=`으로 변환되는 모양이다.<br>
C : Discussion에 따르면 성능적으로 별 차이가 없다고 한다.

1차 시도 : C, D 틀림<br>
2차 시도 : D, E 맞음<br>
</div>
</details>

<br>

## Prob. 4 ⭕⭕
---

Which two are true? (Choose two.)

A. ADD_MONTHS adds a number of calendar months to a date.

B. CEIL requires an argument which is a numeric data type.

C. CEIL returns the largest integer less than or equal to a specified number.

D. LAST_DAY returns the date of the last day of the current month only.

E. LAST_DAY returns the date of the last day of the month for the date argument passed to the function.

F. LAST_DAY returns the date of the last day of the previous month only.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, E

해설 : 

B : 숫자형 데이터 뿐만 아니라 숫자로 변환 가능한 데이터도 입력 가능하다.<br>
C : `CEIL`은 인자보다 크거나 같은 정수 중 제일 작은 수를 출력하므로 틀렸다. 본 설명은 `FLOOR`에 해당하는 것으로 보인다.<br>
D : `LAST_DAY` 에 대한 올바른 설명은 E이다.

1차 시도 : A, E 맞음<br>
2차 시도 : A, E 맞음<br>
</div>
</details>

<br>

## Prob. 5 ⭕⭕ 유념
---

Which three statements are true about Oracle synonyms? (Choose three.)

A. A synonym cannot be created for a PL/SQL package.

B. A synonym can be available to all users.

C. A SEQUENCE can have a synonym.

D. Any user can drop a PUBLIC synonym.

E. A synonym created by one user can refer to an object belonging to another user.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, C, E

해설 : 

A : 잘 모르겠는데 가능한 모양이다. <br>
D : `PUBLIC SYNONYM`을 `CREATE`나 `DROP`할 때는 각각의 시스템 권한이 필요하다.

1차 시도 : B, C, E 맞았는데 다시보기<br>
2차 시도 : B, C, E 맞았는데 다시보기<br>

</div>
</details>

<br>

## Prob. 6 ⭕❌
---

Which two are true? (Choose two.)

A. CONCAT joins two character strings together.

B. CONCAT joins two or more character strings together.

C. FLOOR returns the largest positive integer less than or equal to a specified number.

D. INSTR finds the offset within a character string, starting from position 0.

E. INSTR finds the offset within a string of a single character only.

F. FLOOR returns the largest integer less than or equal to a specified number.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, F

해설 : 

B : `CONCAT`은 A의 설명이 알맞다.<br>
C : `FLOOR`은 F의 설명이 알맞다.<br>
D : `INSTR`은 대상 문자열에서 인자로 들어온 글자를 찾고 그 위치를 출력하며, 포지션 1부터 시작한다.<br>
E : `INSTR`은 하나의 글자만이 아니라 문자열도 찾을 수 있다.<br>

1차 시도 : A, F 맞음<br>
2차 시도 : B, F 틀림<br>
</div>
</details>

<br>

## Prob. 7 ❌❌
---

Examine these SQL statements which execute successfully:
![prob7](/assets/img/study_Oracle/2022-09-30-[ORACLE-SQL]_ExamTopics_1~10/prob7.png)

Which two statements are true after execution? (Choose two.)

A. The primary key constraint will be enabled and IMMEDIATE.

B. The foreign key constraint will be enabled and DEFERRED.

C. The primary key constraint will be enabled and DEFERRED.

D. The foreign key constraint will be disabled.

E. The foreign key constraint will be enabled and IMMEDIATE.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, D

해설 : 

3번째 쿼리에서 `CASCADE`로 PK를 `DISABLE` 하면 그에 종속된 FK도 함께 비활성화된다.<br>
4번째 쿼리에서 `ENABLE`로 PK를 재활성화 하더라도 FK는 그대로 비활성화 상태로 유지된다.<br>

명시하지 않을 경우, 기본으로 제약조건은 `NOT DEFERRABLE IMMEDIATE` 이라고 한다. 

1차 시도 : A, E 틀림 <br>
2차 시도 : A, B 틀림 <br>
</div>
</details>

<br>

## Prob. 8 ⭕❌
---

Examine this SQL statement:<br>
![prob8](/assets/img/study_Oracle/2022-09-30-[ORACLE-SQL]_ExamTopics_1~10/prob8.png)

Which two are true? (Choose two.)

A. All existing rows in the ORDERS table are updated.

B. The subquery is executed before the UPDATE statement is executed.

C. The subquery is not a correlated subquery.

D. The subquery is executed for every updated row in the ORDERS table.

E. The UPDATE statement executes successfully even if the subquery selects multiple rows.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D, E

해설 : 

A. 틀렸다. 양 테이블에 매칭되는 행만 업데이트된다.<br>
B. 틀렸다. 서브쿼리는 메인쿼리 안에 포함된 종속적인 관계이기 떄문에 논리적인 실행순서는 항상 메인쿼리에서 읽혀진 데이터에 대해 서브쿼리에서 해당 조건이 만족하는지를 확인하는 방식으로 수행된다. 즉 메인쿼리 -> 서브쿼리 순서.<br>
C. 틀렸다. 서브쿼리가 메인쿼리 칼럼을 참조하고 있으므로 이는 correlated subquery(연관 서브쿼리)이다.<br>
D. 맞다.<br>
E. 맞다.<br>

1차 시도 : D, E 맞음<br>
2차 시도 : B, D 틀림<br>
</div>
</details>

<br>

## Prob. 9 ⭕⭕
---

Which two statements are true about TRUNCATE and DELETE? (Choose two.)

A. DELETE can use a WHERE clause to determine which row(s) should be removed.

B. TRUNCATE can use a WHERE clause to determine which row(s) should be removed.

C. TRUNCATE leaves any indexes on the table in an UNUSABLE state.

D. The result of a TRUNCATE can be undone by issuing a ROLLBACK.

E. The result of a DELETE can be undone by issuing a ROLLBACK.

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, E

해설 : 

`DELETE` 는 `WHERE` 절로 조건을 지정하여 행을 삭제할 수 있지만, `TRUNCATE` 는 해당 테이블의 행들을 모두 삭제하는 키워드이므로 불가능하다.

`DELETE` 는 `ROLLBACK` 으로 복구가 가능하지만, `TRUNCATE` 는 자동 커밋이 되는 명령어이기 때문에 복구가 불가능하다.

추가로, `DELETE` 는 `WHERE` 절을 사용하지 않고 전체 행을 삭제하려 할 때도 내부적으로 한 줄 한 줄을 삭제하기 때문에 처리속도가 느리며, 데이터가 담겨있던 Storage가 Release 되지 않는 반면 `TRUNCATE` 는 테이블의 데이터를 한 번에 제거함과 동시에 테이블이 최초 생성되었을 당시의 Storage만 남기고 나머지는 모두 Release된다.

[참고 링크](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=idjoopal&logNo=221559099309)

1차 시도 : A, E 맞음<br>
2차 시도 : A, E 맞음<br>
</div>
</details>

<br>

## Prob. 10 ❌❌
---

The STORES table has a column START_DATE of data type DATE, containing the date the row was inserted.<br>
You only want to display details of rows where START_DATE is within the last 25 months.<br>
Which WHERE clause can be used?

A. WHERE TO_NUMBER(start_date - SYSDATE) <= 25

B. WHERE MONTHS_BETWEEN(start_date, SYSDATE) <= 25

C. WHERE MONTHS_BETWEEN(SYSDATE, start_date) <= 25

D. WHERE ADD_MONTHS(start_date, 25) <= SYSDATE

---
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

`MONTHS_BETWEEN(date1, date2)`은 인수로 들어가는 날짜 date1, date2의 날짜 차이 일수를 출력한다.<br>
이때 date1이 date2보다 클 경우 양수가 출력되고 date2가 date1보다 클 경우 음수가 출력된다.

1차 시도 : B 틀림<br>
2차 시도 : B 틀림<br>

</div>
</details>

<br>
