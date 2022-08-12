---
layout: post
title: "[AWS] Amazon DynamoDB 이해"
subtitle: AWS
date: '2022-06-06 6:30:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-06-[AWS]_Amazon_DynamoDB_이해/logo.png
---

NoSQL 데이터베이스 **Amazon DynamoDB**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>
 
## 1. Amazon DynamoDB 개요

  Amazon DynamoDB 는 완전관리형 NoSQL 데이터베이스이다.

<hr/>

## 2. Amazon DynamoDB 특징

  * 테이블 생성이 단순하고 신속하기 때문에, **설계부터 운용까지 걸리는 시간이 적다**.

  * DynamoDB는 저장되는 데이터의 용량이 증가하면 **자동으로 스토리지를 늘리고 클러스터를 확장하여 데이터를 분산시킨다**.
  따라서 **어떠한 수준의 요청 트래픽도 일관적인 속도로 처리**할 수 있으며, 하드웨어 프로비저닝, 설정 및 구성, 복제, 소프트웨어 패치 또는 클러스터 크기 조정에 대해 걱정할 필요가 없다.

  * 읽기/쓰기 처리량(Read/Write Throughput)을 **직접 지정**할 수 있고, 다운타임 또는 성능 저하 없이 **테이블의 처리 능력을 확장 또는 축소할 수 있다**.
    - 처리량은 한 번에 2배씩 늘릴 수 있으며(횟수 제한 없음), 낮출때는 한 번에 최저치까지 낮출 수 있다(하루 4번 제한).
    - 처리량 지정은 **반영되는데에 시간이 꽤 소요**되기 때문에, 초기에 넉넉히 설정해야 한다.
    - 이렇게 설정된 처리량은 위 특징에 따라 지정된 속도로 **일관되게 유지**된다.

  * AWS Management Console을 사용하여 리소스 사용률 및 성능 지표를 **모니터링**할 수 있다.

  * DynamoDB는 리전별로 생성이 가능하고, 데이터를 여러 가용영역에 복제하여 저장하기 때문에 일부 장애가 발생하더라도 문제없이 사용이 가능하다.<br>
  덕분에 **고가용성과 데이터 내구성을 제공**하고, 사용자가 따로 데이터를 백업할 필요가 없다.<br>

  * 유휴 시 **암호화**를 제공하여 중요한 데이터 보호와 관련된 운영 부담 및 복잡성을 제거한다.

  * NoSQL이지만 **보조 인덱스**를 사용하여 빠른 조회 속도를 제공한다.

  * DynamoDB의 모든 데이터는 **SSD**에 저장된다.

  * DynamoDB는 **온디맨드 백업** 기능을 제공한다.<br>
  따라서 테이블의 전체 백업을 생성하여 규제 준수 요건에 맞도록 장기간 유지하고 보관할 수 있다.<br>
  또한 백업을 통해 **특정 시점으로 복구**도 가능하다.(최근 35일 중으로 제한)

  * **데이터 유지 시간(TTL)**이 만료된 항목을 테이블에서 자동 삭제할 수 있으므로 스토리지 사용량과 더 이상 관련 없는 데이터를 저장하는 비용을 줄일 수 있다.

  * **키 값 데이터 모델**을 사용한다.

<hr/>

## 3. Amazon DynamoDB 사용 목적

  * 대규모 RDBMS 기반 데이터베이스는 서버 한 대에 대용량의 데이터베이스를 저장하기가 어려우므로 샤딩(Shading)을 통해 데이터베이스를 분산 저장시키는데, DynamoDB는 자동으로 처리해주므로 비용과 시간을 아낄 수 있다.

  * 읽기와 쓰기가 매우 빈번하고 처리 속도가 빨라야하며(밀리초 단위, **DAX**의 경우 마이크로초 단위), 작은 용량의 데이터가 많을 때 적합하다.
    - 예 : 모바일 게임, SNS, 채팅 앱 등

  * 일반적인 RDBMS(Oracle, MySQL 등)가 아닌 Amazon에서 개발한 **NoSQL 데이터베이스**로서 관계형 스키마를 가지지 않는다.<br>
    때문에 **조인(Join)과 같은 복잡한 쿼리가 필요한 환경에는 부적합**하다.<br>
    하지만 스키마가 고정되지 않은 비정형 데이터를 저장하는데에는 적합하다.

<hr/>

## 4. Amazon DynamoDB 데이터 모델

  기본 구성요소로는 **Table**, **Item**, **Attribute**가 있다.

### I. Table

  Table은 **Item들의 모임**이다.<br>
  들어갈 수 있는 Item의 **갯수 제한은 없다**.<br>
  반드시 Table마다 **기본 키**가 지정되어야 한다.<br>
  리전 당 생성할 수 있는 Table 최대 갯수는 **256개**이고, AWS에 요청시 더 늘릴 수 있다.

### II. Item

  Item은 **Attribut들의 모임**이다.<br>
  들어갈 수 있는 Attribute의 **갯수 제한은 없다**.<br>
  아이템의 크기는 **속성 이름과 값을 포함하여 64KB**까지이다.<br>
  **기본 키는 필수로 포함**하고 있어야 하며, **복합 키**와 **기타 속성**을 가질 수 있다.

### III. Attribute

  Attribute는 **Key-Value 방식**이다.<br>
  **Key는 문자열**이어야 한다.<br>
  Attribute가 지원하는 값 데이터 형식은 **스칼라 데이터 형식(Scalar Data types)**, **다중 값 형식(Multi-valued types)**가 있다.
  공통 사항으로 **NULL이나 빈 문자열은 저장이 불가하다**.

  * **스칼라 데이터 형식(Scalar Data types)**
    - 숫자(Number), 문자열(String), 바이너리(Binary)를 사용

  * **다중 값 형식(Multi-valued types)**
    - **스칼라 데이터 형식의 배열 형태**
    - 숫자 세트(Number Set), 문자열 세트(String Set), 바이너리 세트(Binary Set)를 사용
    - 다중 값 형식은 **들어가는 값이 중복될 수 없으며**, **값이 하나라도 들어가 있어야 함**
    - 값은 **정렬되지 않고 정렬 순서도 저장되지 않음**
    - 다중 값 형식은 ****기본 키로 사용할 수 없음**

<hr/>

## 5. Amazon DynamoDB 사용 로직

  DynamoDB에서 검색을 하려면 기본 키로 인덱스를 생성해야 한다.<br>
  기본 키는 테이블 생성시 반드시 지정되어야 하고, 이 기본 키로 생성되는 인덱스를 **테이블 인덱스**라고 한다.

### I. 기본 키

  기본 키 형식은 **Hash 형식 기본 키**, **Hash와 Range 형식 기본 키**가 있다.

  * **Hash 형식 기본 키**
    - **Attribute 1개를 기본 키로 사용**
    - 기본 키의 값은 **스칼라 데이터 형식만 가능**
    - **일치(Equal) 방식의 검색만 지원**
    - 고유한 값을 가져야 함
  
  * **Hash와 Range 형식 기본 키**
    - **Attribute 2개를 기본 키로 사용(복합 키)**
    - **첫 Attribute는 해시 형식 기본 키로 사용**, **두 번째 Attribute는 범위 기본 키로 사용**
    - 범위 기본 키는 **일치(Equal), 부등호, 포함, ~로 시작하는 범위를 지정할 수 있는 검색을 지원**
    - 해시 키나 범위 키가 고유한 값을 가지지 않더라도 복합 키로서 둘의 조합이 유일하면 저장 가능

### II. 보조 인덱스 유형

  DynamoDB는 기본키로 생성하는 테이블 인덱스 이외에 **보조 인덱스(Secondary Index)**를 생성할 수 있다.<br>
  이로 인해 기본 키로 생성한 테이블 인덱스만으로는 부족한 **검색 성능을 높일 수 있다**.<br>
  보조 인덱스는 **Read/Write 용량 유닛을 따로 설정**할 수 있다.<br>

  보조 인덱스는 **로컬 보조 인덱스(Local Secondary Index)**, **글로벌 보조 인덱스(Global Secondary Index)**로 나뉜다.

  * **로컬 보조 인덱스(Local Secondary Index)**
    - **해시 키** : **해시 기본 키(테이블 인덱스와 같음)**
    - **범위 키** : **목적에 따라 다르게 설정**
    - 로컬 보조 인덱스는 **테이블당 5개까지 생성 가능**
    - 테이블에서 **해시 기본 키와 범위 기본 키를 사용하고 있을 때만 생성 가능**

  * **글로벌 보조 인덱스(Global Secondary Index)**
    - **해시 키** : **테이블 인덱스와 다르게 설정**
    - **범위 키** : **테이블 인덱스와 다르게 설정**, **생략 가능**
    - 글로벌 보조 인덱스는 **테이블당 5개까지 생성 가능**

<hr/>

## 6. Amazon DynamoDB 데이터 읽기

  DynamoDB는 데이터를 읽을 때 **Eventually Consistent Read**, **Strongly Consistent Read**를 사용할 수 있다.

  * **Eventually Consistent Read**
    - 읽기 처리량(Read Throughput)을 최대화하지만 읽은 데이터가 최근 완료된 쓰기 결과를 반영하지 못했을 수 있음
    - 쓰기가 데이터의 모든 복사본에 반영되는 것은 1초내에 이루어지므로, 최신 데이터를 얻으려면 짧은 시간 내에 읽기를 반복해야 함

  * **Strongly Consistent Read**
    - 최근 완료된 쓰기 결과가 모두 반영된 데이터를 가져옴(Eventually Consistent Read의 쓰기 결과가 반영되지 않은 경우가 일어나지 않음)

<hr/>

## 7. 프로비저닝된 처리량(Provisioned Throughput)

  **Provisioned Throughput**은 사용자가 원하는 수치를 지정하면 DynamoDB가 알아서 지정된 수치만큼 처리량을 제공해주는 것을 말한다.<br>
  처리량은 한 번에 2배씩 늘릴 수 있으며(횟수 제한 없음), 낮출때는 한 번에 최저치까지 낮출 수 있다(하루 4번 제한).<br>
  처리량 지정은 **반영되는데에 시간이 꽤 소요**되기 때문에, 초기에 넉넉히 설정해야 한다.
  
  **필요한 읽기 용량 유닛(Read Capacity Units)**과 **필요한 쓰기 용량 유닛(Write Capacity Units)**으로 **필요한 Read/Write Capacity Units을 설정**한다.

  * **필요한 읽기 용량 유닛(Read Capacity Units)**
    - 초당 읽은 아이템 수 X KB 단위 아이템 크기(근사치 반올림) 
    - Eventually Consistent Read를 사용하는 경우 초당 읽은 아이템 용량은 **두 배**가 됨

  * **필요한 쓰기 용량 유닛(Write Capacity Units)**
    - 초당 쓴 아이템 수 X KB 단위 아이템 크기(근사치 반올림)

  > 예를 들어,<br>
  > **512Bytes**(**1KB**로 반올림 됨)을 **초당 200**개 항목을 읽거나 쓰면, **1KB** X **200** = **200** 유닛이 필요<br>
  > **1.6KB**(**2KB**로 반올림 됨)을 **초당 200**개 항목을 읽거나(쓰면), **2KB** X **200** = **400** 유닛 필요<br><br>
  > 읽기에 **Eventually Consistent Read**를 사용할 경우 **500** 읽기 용량 유닛으로 **1KB** 용량의 아이템을 **초당 1000번** 읽을 수 있음<br>
  > 읽기에 **Strongly Consistent Read**를 사용할 경우 **1000** 읽기 용량 유닛으로 **1KB** 용량의 아이템을 **초당 1000번** 읽을 수 있음

  **또한 읽기 용량의 유닛 수는 API 호출 수가 아닌 초당 읽은 아이템 수로 결정된다**.<br>
  즉, **1KB** 용량의 아이템을 **GetItem(아이템을 1개 읽는 메소드)**으로 **500번** 호출하는 것과,<br>
  **BatchGetItem(아이템을 군집하여 읽는 메소드)**을 호출하여 아이템을 **10개**씩 **50번** 호출하는 것은 같다.

<hr/>

## 8. DAX(DynamoDB Accelerator)

  DynamoDB를 위한 가용성이 뛰어난 **완전관리형인 메모리 cache**로서, 초당 요청 수가 몇 백만 개인 경우에도 몇 밀리초에서 몇 **마이크로초**까지 **최대 10배의 성능을 제공**한다.

DAX는 캐시를 사용하는 것임에 명심
{:.note}

<hr/>

* Ref
  - [AWS Amazon DynamoDB Userguide](https://docs.aws.amazon.com/ko_kr/amazondynamodb/latest/developerguide/Introduction.html)
  - [AWS Amazon DAX Userguide](https://docs.aws.amazon.com/ko_kr/amazondynamodb/latest/developerguide/DAX.html)
  - [Tistory](https://interconnection.tistory.com/60)