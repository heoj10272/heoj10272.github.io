---
layout: post
title: "[AWS] Amazon Aurora Serverless 이해"
subtitle: AWS
date: '2022-06-07 5:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-07-[AWS]_Amazon_Aurora_Serverless_이해/logo.png
---

AWS에서 제공하는 **Amazon Aurora Serverless**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

## 1. Amazon Aurora Serverless 개요

아래는 **AWS**에서 소개하는 **Amazon Aurora Serverless**이다.

> **Amazon Aurora Serverless**는 Amazon Aurora의 **온디맨드 Auto Scaling 구성**입니다.<br>
> 애플리케이션 요구 사항을 기반으로 **자동으로 시작 및 종료하고 용량을 확장 또는 축소**합니다.<br>
> Aurora Serverless를 사용하면 데이터베이스 용량을 관리하지 않고도 클라우드에서 데이터베이스를 실행할 수 있습니다.

즉 **Amazon Aurora Serverless**는 **Aurora의 Serverless 버전**으로, **인스턴스를 미리 프로비전하거나 관리할 필요가 없다**.<br>
T2.micro/T2.midium 등의 **인스턴스 타입도 선택할 필요가 없다**.

**Amazon Aurora Serverless**는 **V1**과 **V2**가 존재한다.<br>
해당 포스트에서는 **V1**에 대해서만 기술한다.

<hr/>

## 2. Amazon Aurora Serverless 특징

* **OnDemand**
  + 사용한 만큼만 요금을 지불함
  + 사용한 리소스를 1초 단위로 과금

* **Single AZ**
  + 단 **Multi-AZ Failover**를 지원하기 때문에 장애가 발생할 시 다른 AZ로 복구된다.
    - 기존의 Provisioned(Amazon Aurora)보단 느리다.

* **용량은 10GB~128TB로 자동 스케일링됨**

* **DB Cluster Parameter Group만 지원**
  + **RDS**에는 두 개의 파라미터 그룹이 존재한다.
    - **DB Cluster Parameter Group** : **클러스터 전체**에 적용
    - **DB Instance Parameter Group** : **개별 인스턴스**에 적용

* **ACU(Aurora Capacity Unit)** 단위로 컴퓨팅 조절
  + **1ACU** = 2GB RAM, 그에 상응하는 CPU, 네트워크
  + 사용자가 **최대/최소 ACU 설정 가능**
  + AWS의 **Warm Pool**에서 인스턴스를 준비하고 스케일링에 따라 인스턴스를 할당/회수
  + **최소 0ACU까지 스케일 다운 가능(기존 Amazon Aurora에서는 불가능, 선택사항기능)**
    - **스토리지 비용만 지불**한다는 뜻
    - 단 **0ACU**에서 **1이상의 ACU**로 전환하는데에는 **시간이 소요됨**(25초~40초)
    - **디폴트로 5분**간 사용이 없을시 **자동으로 0ACU 전환**, **최대 24시간**까지 확장 가능
    - **7일간 아무 이용 내역이 없으면 스냅샷으로 저장**, 요청 발생시 자동 복구함

<hr/>
  
## 3. Amazon Aurora Serverless 구조

  ![Architecture](/assets/img/study_AWS/2022-06-07-[AWS]_Amazon_Aurora_Serverless_이해/Architecture.png)

  Aurora Serverless에는 **외부에서 직접 연결할 수 없으며** **퍼블릭 IP도 없다**.<br>
  외부 VPC의 인스턴스에서 VPC Endpoints를 통해 Network Load Balancer를 거쳐 내부 VPC Endpoints를 통해 동작한다.

  **Request Router**, **Instance Layer**, **Storage Layer**로 구성된다.

  * **Request Router**
    + Connection을 유지시킴
    + Instance Layer에서 구성이 계속 바뀌기 때문에, 이에 대응해 연결을 계속 유지시켜줄 필요가 있음
  * **Instance Layer**
    + Request Router를 통해 들어온 요청을 처리해 Storage Layer로 보냄
    + 인스턴스들은 Stateless
      - Warm Instance Pool이나 다른 곳을 왔다갔다 할 수 있기 때문
  * **Storage Layer**
    + Instance Layer로부터의 데이터를 저장

**초기**에 Instance Layer는 비어있다.<br>
요청이 들어오면 Warm Instance Pool로부터 Instance Layer로 인스턴스를 할당받는다.<br>
요청을 Instance Layer의 인스턴스가 처리를 하면, 결과는 Storage Layer에 저장된다.

**요청이 많아질수록** Request Router에 연결되는 Instance Layer의 인스턴스가 많아지며, 각 인스턴스의 크기는 수시로 변한다.<br>
수시로 변하는 인스턴스들의 연결을 유지해주는 것이 Request Router의 역할이다.

**요청이 적어지면** 인스턴스를 회수하거나 크기를 줄여 적정한 ACU를 유지한다.

**요청이 아예 없어지면** 마지막 남은 인스턴스도 회수해 0ACU로 전환한다.<br>
Aurora Serverless는 지속적으로 Connection이 없을 때를 찾는다.<br>
이를 **Scaling point**라고 한다.

<hr/>

## 4. Amazon Aurora Serverless 보안과 복구

  * **Multi-AZ Failover**
    + 장애 발생시 **자동으로 다른 AZ에 복구**함

  * **기본적으로 암호화됨**
    + **비활성 불가능**
  
  * **패치/업데이트시 스케일링 포인트를 찾아 업데이트**
    + **스케일링 포인트(Scaling Point)** : 쿼리 처리가 없는 상태
    + 하루 이상 찾지 못하면 **클러스터 이벤트로 알림**
    + 이후 **TimeoutAction 설정**에 따라 **롤백 혹은 강제 업데이트**
  
<hr/>
  
## 5. Amazon Aurora Serverless 제약사항

  * **VPC 밖에서 액세스 불가능**
    + 즉 직접 **밖에서 로그인 불가능**
    + **Public IP 할당 불가능**
    + **Data API** 혹은 **Bastion Host**등의 방법으로 접근
      - Aurora Serverless용 **Data API**를 사용하면 Aurora Serverless DB 클러스터에 대한 **웹 서비스 인터페이스**로 작업할 수 있음
      - Data API에서 DB 클러스터에 **지속적으로 연결하지 않아도 됨**
      - 대신 **AWS SDK와의 통합**과 **보안 HTTP 엔드포인트를 제공**함
      - 연결을 관리하지 않고 **엔드포인트를 사용하여 SQL 문을 실행할 수 있음**

  * **Replica 불가능**
  
  * **클로닝 불가능**

  * **Backtrack 불가능**
  
  * **Multi-Mater 불가능**

  * **포트 3306(MySQL), 5432(PostgreSQL) 고정**
  
  * **Inter Region VPC Peering 불가능**

  * **엔진 버전 고정**
    + MySQL-5.6 or 5.7

<hr/>
  
## 6. Amazon Aurora Serverless 사용 사례

* **자주 사용하지 않는 애플리케이션**
  + 하루 또는 일주일에 고작 몇 분씩 몇 차례만 사용되는 애플리케이션의 경우, Aurora Serverless는 요금을 초 단위로 지불하기 때문에 유리함
  + 예 : 사용자가 적은 블로그 사이트

* **새 애플리케이션**
  + 새 애플리케이션 작성시 인스턴스 크기가 예측되지 않을 때 Aurora Serverless의 자동 확장이 유리함

* **가변성 높은 워크로드**
  + 피크가 하루에 몇 번 안 되거나 1년에 몇 번, 30분~몇 시간에 불과한 사용량이 낮은 애플리케이션의 경우 Aurora Serverless는 피크 또는 평균 용량에 맞추어 프로비저닝 하지 않아도 되기 때문에 유리함
  + 예 : 인사 관리, 예산 작성 및 운영 보고 애플리케이션

* **에측 불가능한 워크로드**
  + 작업의 증가가 갑작스럽고 에측할 수 없는 일일 워크로드의 경우 Aurora Serverless의 자동 확장이 유리함
  + 예 : 비가 내리기 시작하면 활동이 급증하는 트래픽 사이트

* **개발 및 테스트 데이터베이스**
  + 개발자가 작업하는 시간 중에는 데이터베이스를 사용하지만 밤이나 주말에는 사용하지 않으므로 Aurora Serverless의 데이터베이스가 사용되지 않을 때 자동으로 종료되는 기능이 유리함

* **다중 테넌트 애플리케이션**
  + Aurora Serverless v1은 사용자를 대신하여 개별 데이터베이스 용량을 관리해 줌

<hr/>

* Ref
  - [AWS Amazon Aurora Serverless Userguide](https://docs.aws.amazon.com/ko_kr/AmazonRDS/latest/AuroraUserGuide/aurora-serverless.html)
  - [Youtube](https://youtu.be/QnvbtuPk8OE)
