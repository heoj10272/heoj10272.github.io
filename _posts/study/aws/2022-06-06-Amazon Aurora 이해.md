---
layout: post
title: Amazon Aurora 이해
subtitle: AWS
date: '2022-06-06 8:00:00 +0900'
category: study
tags: aws
image:
  path: /assets/img/study_AWS/Amazon Aurora 이해/logo.png
---

AWS에서 제공하는 **Amazon Aurora**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

## 1. Amazon Aurora 개요

  **Amazon Aurora**는 고성능 상용 데이터베이스의 성능과 가용성에 오픈 소스 데이터베이스의 간편성과 비용 효율성을 결합하여 클라우드를 위해 구축된 **MySQL 및 PostgreSQL 호환 관계형 데이터베이스**이다.

  Amazon Aurora는 **표준 MySQL 데이터베이스보다 최대 5배** 빠르고 **표준 PostgreSQL 데이터베이스보다 3배** 빠르다.<br>
  또한 **1/10의 비용**으로 상용 데이터베이스의 보안, 가용성 및 안전성을 제공한다.<br>
  하드웨어 프로비저닝, 데이터베이스 설정, 패치 및 백업과 같은 시간 소모적인 관리 작업을 자동화하는 **Amazon Relational Database Service(RDS)**에서 Amazon Aurora의 모든 것을 관리한다.

  기존의 RDS와는 다른 아키텍쳐를 가지고 있기 때문에, 클라우드 환경에 최적화된 RDBMS라고 볼 수 있다.

## 2. Amazon Aurora 아키텍쳐

  Aurora의 아키텍쳐는 **Single-Master**와 **Multi-Master**로 나뉜다.

  ### I. Single-Master

  ![Single_Master](/assets/img/study_AWS/Amazon Aurora 이해/Single_Master.png)

  **Single-Master**는 여러 가용 영역에 걸쳐서 **Storage Cluster(=Cluster Volume, 저장 공간)**이 분리되어있으며, 그 위에 **Master 인스턴스(쓰기, 읽기를 담당)**와 **Replica 인스턴스(읽기만 가능)**이 올려져 있는 형태이다.

  **쓰기**의 경우 **Master 인스턴스**만이 사용자로부터 요청을 받아 **Storage Cluster**에 데이터를 저장할 수 있다.<br>
  **읽기**의 경우 **Master 인스턴스**와 **Replica 인스턴스**들이 **Storage CLuster**로부터 값을 받아와 사용자에게 전달한다.

  Replica 인스턴스는 **최대 15개**까지 생성할 수 있다.
  **Async 복제**가 가능하다.
  **하나의 리전**안에 생성이 가능하다.
  한 대의 Master 인스턴스가 다운될 경우 **자동으로 Replica 중 하나가 Master로 승격(Failover)된다**.

  이렇게 읽기/쓰기와 저장을 분리했기 때문에 **인스턴스 생성과 전환을 매우 빠르게 할 수 있다**.<br>
  이 뿐만 아니라 고가용성을 확보하기 위해 스토리지 노드끼리 백업이나 싱크를 맞추는 등 Replication 작업 없이도 **설계단에서  스토리지를 공유하기 때문에 이미 고가용성을 확보한 상태이다**.

  ### II. Multi-Master

  ![Multi_Master](/assets/img/study_AWS/Amazon Aurora 이해/Multi_Master.png)

  **Multi-Master**는 Single Master와 다르게 읽기/쓰기를 담당하는 **Master 인스턴스가 여러개이다**.<br>
  이러한 Master 인스턴스는 **최대 4개**까지 생성할 수 있다.<br>
  이 경우 **고가용성**, **부하 분산**, **샤딩(Sharding)**에서의 유리함이 있다.


  대부분의 경우 **Single-Master**를 사용한다.<br>
  왜냐하면 Multi-Master도 나름의 장점이 있지만, Multi-Master를 사용할 경우 **Aurora의 몇 가지 기능을 사용하지 못하게 되기 때문이다**.

## 3. Amazon Aurora 특징

### I. 용량의 자동 증감

  **RDS**의 경우 **EBS**를 기반으로 했기 때문에 **미리 저장공간을 확보해서 EBS를 생성**해야 했지만, **Aurora**의 경우 **10GB**부터 시작하여 **10GB 단위**로 **최대 128TB**까지 **자동으로 용량이 늘어난다**.<br>
  이는 RDS와 달리 **읽기/쓰기 인스턴스를 스토리지와 분리시켰기 때문에 가능한 것**이다.

### II. 데이터 분산 저장

  **최소 3개 이상의 AZ** X **각 AZ마다 2개의 데이터 복제본 저장** = **최소 6개의 복제본**

  즉 3개 이상의 복제본이 손상되기 전에는 쓰기 능력이 유지된다.
  즉 4개 이상의 복제본이 손상되기 전에는 읽기 능력이 유지된다.
  
  또한 복제본이 손상되더라도 클러스터가 **지속적으로 손실된 부분을 검사 후 복구**한다.
  **Quorum 모델**을 사용하여 읽기/쓰기를 적용한다.



