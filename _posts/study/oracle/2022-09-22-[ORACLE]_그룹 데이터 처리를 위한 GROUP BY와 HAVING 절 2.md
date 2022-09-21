---
layout: post
title: "[ORACLE] 그룹 데이터 처리를 위한 GROUP BY와 HAVING 절 2"
subtitle: Oracle
date: '2022-09-22 01:03:00 +0900'
category: study
tags: oracle
image:
  path: /assets/img/study_Oracle/2022-09-22-[ORACLE]_그룹 데이터 처리를 위한 GROUP BY와 HAVING 절 2/logo.png
---

그룹 데이터 처리를 위한 GROUP BY와 HAVING 절 2

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

# 집계 처리

---

## Group data 결과 제한(Having)

---

```sql
-- 최고 급여가 $10,000가 넘는 각 부서의 최고 급여
  
  SELECT  department_id, MAX(salary)
    FROM  employees
GROUP BY  department_id
  HAVING  MAX(salary) > 10000;
```

|  | DEPARTMENT_ID | MAX(SALARY) |
| --- | --- | --- |
| 1 | 20 | 13000 |
| 2 | 90 | 24000 |
| 3 | 110 | 12000 |
| 4 | 80 | 11000 |

`HAVING` 절을 제외했다면 부서별 최고 급여가 출력되었을 것이다.

하지만 `HAVING` 절에서 최고 급여가 10000을 넘는 값만을 출력하도록 했으므로 위와 같이 출력된다.

## QUIZ 1

---

**업무별 전체 급여 합계 중 $13000 보다 큰 것만 출력하시오.
단, 업무에 REP가 포함된 것은 제외하고, 전체 급여에 대한 내림차순 정렬을 수행하시오.**

```sql
  SELECT  job_id, sum(salary) PAYROLL -- 업무별 급여 합계
    FROM  employees
   WHERE  job_id NOT LIKE '%REP%' -- REP가 포함된 것은 제외
GROUP BY  job_id
  HAVING  SUM(salary) > 13000 -- $13000 보다 큰 것만
ORDER BY  SUM(salary) DESC -- 급여에 대한 내림차순 정렬
```

|  | JOB_ID | PAYROLL |
| --- | --- | --- |
| 1 | AD_VIP | 34000 |
| 2 | AD_PRES | 24000 |
| 3 | IT_PROG | 19200 |

- Group 함수를 중첩하는 경우 반드시 Group by 절을 사용해야 한다.

```sql
  SELECT  MAX(AVG(salary)) -- ,department_id 가 붙게되면 오류 발생
    FROM  employees
GROUP BY  department_id;
```

# 고급(상위) 집계 처리

---

## GROUP BY에 ROLLUP 및 CUBE 연산자 사용

---

- GROUP BY에 ROLLUP 또는 CUBE를 사용하여 상호 참조 열별로 대 집계 행을 생성
- ROLLUP 그룹화는 일반 그룹화 행과 소계 값을 포함한 결과 집합을 생성
- CUBE 그룹화는 ROLLUP에 따른 행과 교차 분석 행이 포함된 결과 집합을 생성

## GROUP BY에 ROLLUP 사용

---

- ROLLUP 연산자 없이 n차원(즉, GROUP BY 절에 있는 n개의 열)에서 소계를 생성하려면 **n+1**개의 SELECT 문을 UNION ALL과 연결해야 한다.
- 이렇게 하면 SELECT 문마다 테이블에 액세스하게 되므로 query가 비효율적으로 실행되므로
- **ROLLUP 연산자는 테이블에 한 번만 액세스하여 해당 결과를 수집**한다.
- 소계 새성에 관련된 열이 많을 경우에는 ROLLUP 연산자가 유용하다.

```sql
-- 각 부서의 급여 합계 계산
  
  SELECT  department_id, job_id, SUM(salary)
    FROM  employees
   WHERE  department_id < 60
GROUP BY  ROLLUP(department_id, job_id);
```

|  | DEPARTMENT_ID | JOB_ID | SUM(SALARY) |
| --- | --- | --- | --- |
| 1 | 10 | AD_ASST | 4400 |
| 2 | 10 | (null) | 4400 |
| 3 | 50 | ST_MAN | 36400 |
| 4 | 50 | (null) | 36400 |
| … |  |  |  |
| 15 | (null) | (null) | 211200 |

`ROLLUP` 에 의해 ‘department_id’, ‘job_id’에 대해 부분 집계 처리가 된다.

`GROUP BY` 절에 있는 2개(n개)의 열에서 3개(n+1)개의 그룹을 출력한다.

2행은 ‘department_id’가 10인 모든 ‘job_id’에 대한 급여 합계이며, 5행은 모든 급여 총계이다.

즉 정리하면 다음과 같다.

1. 1행, 3행은 ‘department_id'와 ‘job_id’로 합계된 그룹.
2. 2행, 4행은 ‘department_id’로만 합계된 그룹
3. 5행은 총계이다.

## GROUP BY에 CUBE 사용

---

- CUBE 연산자를 사용하여 단일 SELECT 문으로 교차 분석 값 생성
- ROLLUP은 가능한 소계 조합의 일부만 생성하지만, CUBE는 GROUP BY 절에 지정된 가능한 모든 그룹화 조합의 소계와 총계를 생성
- GROUP BY 절에 N 열이나 표현식이 있을 경우 2^n개의 가능한 대집계 조합을 생성
- 응용 프로그램이나 프로그래밍 도구를 사용하여 이러한 대집계 값을 차트와 그래프에 제공하여 결과와 관계를 시각적이고 효율적으로 전달할 수 있다.

```sql
  SELECT  department_id, job_id, SUM(salary)
    FROM  employees
   WHERE  department_id < 60
GROUP BY  CUBE(department_id, job_id);
```

|  | DEPARTMENT_ID | JOB_ID | SUM(SALARY) |
| --- | --- | --- | --- |
| 1 | (null) | (null) | 211200 |
| 2 | (null) | HR_REP | 6500 |
| 3 | (null) | MK_MAN | 13000 |
| 4 | 10 | (null) | 4400 |
| 5 | 10 | AD_ASST | 4400 |
| 6 | 20 | (null) | 13000 |
| 7 | 20 | MK_MAN | 13000 |
| … |  |  |  |
| 16 | 30 | (null) | 24900 |

`GROUP BY` 절에 있는 2개(n개)의 열에서 4개(2^n)개의 그룹을 출력한다.

1. 1행 총계
2. 2행, 3행은 ‘job_id’로만 합계된 그룹
3. 5행, 7행은 ‘department_id’와 ‘job_id’로 합계된 그룹
4. 4행, 6행, 16행은 ‘department_id’만으로 합계된 그룹

`ROLLUP` 과 다른 점은 2번이 추가되었다는 점이다.

## GROUPING 함수

---

- CUBE 또는 ROLLUP 연산자와 함께 사용
- 행에서 소계를 형성하는 그룹을 찾는데 사용
- ROLLUP 또는 CUBE로 생성된 NULL 값과 저장된 NULL 값을 구분하는데 사용
- **0**(해당 열을 이용한 group data 고려) 또는 **1**(고려 안함)을 반환

```sql
  SELECT  department_id DEPTID, job_id JOB, SUM(salary),
          GROUPING(department_id) GRP_DEPT, GROUPING(job_id) GRP_JOB
    FROM  employees
   WHERE  department_id < 50
GROUP BY  ROLLUP(department_id, job_id);
```

|  | DEPTID | JOB | SUM(SALARY) | GRP_DEPT | GRP_JOB |
| --- | --- | --- | --- | --- | --- |
| 1 | 10 | AD_ASST | 4400 | 0 | 0 |
| 2 | 10 | (null) | 4400 | 0 | 1 |
| … |  |  |  |  |  |
| 11 | (null) | (null) | 54800 | 1 | 1 |

1행은 두 행을 모두 고려했기 때문에 ‘GRP_DEPT’, ‘GRP_JOB’ 가 모두 0이 출력되었다.

2행은 ‘job_id’를 고려하지 않았기 때문에 ‘GRP_DEPT’만 1이 출력되었다.

11행은 모두 집계하는 행이므로 두 행을 모두 고려하지 않았기에 둘 다 1이 출력되었다.