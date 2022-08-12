---
layout: post
title: "[AWS] Amazon EC2 이해"
subtitle: AWS
date: '2022-06-02 4:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-02-[AWS]_Amazon_EC2_이해/logo.png
---

AWS 서비스 중 하나인 **EC2**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## 1. Amazon EC2란?

**Amazon Elastic Compute Cloud(Amazon EC2**)는 Amazon Web Services(AWS) 클라우드에서 가변 가능한 컴퓨팅 용량을 제공한다.<br>
Amazon EC2를 사용하면 더 이상 하드웨어에 선투자할 필요가 없어 더 빠르게 어플리케이션을 개발하고 배포할 수 있다.<br>
Amazon EC2를 사용해 원하는 수의 가상 서버를 구축하고 보안 및 네트워킹을 구성하며 스토리지를 관리할 수 있다.<br>
Amazon EC2에서는 확장 또는 축소를 통해 요구사항이나 popularity spike의 변화에 대처할 수 있으므로 트래픽을 예측할 필요성이 줄어든다.

<br>
<hr/>
<hr/>

## 2. Amazon EC2 사용 용도

* **서버를 구축할 때**
  + 게임 서버, 웹 서버, 어플리케이션 서버

* **어플리케이션을 사용하거나 호스팅할 때**
  + 데이터베이스
  + 머신 러닝
  + 비트코인 채굴
  + 연구용 프로그램

* **기타 다양한 목적**
  + 그래픽 랜더링
  + 게임 등

<br>
<hr/>
<hr/>

## 3. Amazon EC2 특성

* 초 단위 **온디맨드** 가격 모델
  + 온디맨드 모델에서는 가격이 **초 단위**로 결정
  + 서비스 요금을 미리 약정하거나 선입금이 필요 없음

* **빠른 구축 속도와 확장성**
  + 몇 분이면 전 세계에 인스턴스 수백여대를 구축 가능

* **다양한 구성방법 지원**
  + 머신러닝, 웹 서버, 게임 서버, 이미지 처리 등 다양한 용도에 최적화된 서버 구성 가능
  + 온디맨드 외에도 다양한 과금 모델 사용 가능(하단 요금제 항목 참조)

* **여러 AWS 서비스와 연동**
  + 오토 스케일링, Elastic Load Balancer(ELB), CloudWatch

<br>
<hr/>
<hr/>

## 4. Amazon EC2 기능

**Amazon EC2**는 아래의 기능들을 제공한다.

* **인스턴스(Inctance)** 
  + 가상 컴퓨팅 환경
  + 클라우드에서 사용하는 가상 서버로 CPU, 메모리, 그래픽카드 등 연산을 위한 **하드웨어**를 담당

* **Amazon Machine Images(AMI)** 
  + 서버에 필요한 운영체제와 여러 소프트웨어들이 적절히 구성된 상태로 제공되는 **템플릿**으로, 인스턴스를 쉽게 만들 수 있음
  + 우리가 인스턴스를 만든 뒤 그 인스턴스를 토대로 **Image**를 만들어 다른 인스턴스를 생성할 때 템플릿으로 사용하면, **원본 인스턴스와 동일한 일을 하는 인스턴스를 생성할 수 있음**
  + 위 특성을 이용해 백업 등의 용도에 사용됨
  + **Amazon Marketplace**, **Community AMIs**에서 다른 사람들이 배포한 AMI를 받아 사용할 수도 있음

* **Instance types** 
  + 인스턴스를 위한 CPU, 메모리, 스토리지, 네트워킹 용량의 다양한 구성을 제공

* **key pair**
  + key pair를 사용한 인스턴스 로그인 정보 보호
  + **AWS는 퍼블릭 키를 저장**하고 **사용자는 개인 키를 안전한 장소에 보관**하는 방식

* **Instance store volumes** 
  + **임시 데이터를 저장하는 스토리지 볼륨**으로 인스턴스 중단, 최대 절전 모드로 전환 또는 종료 시 삭제됨

* **Amazon EBS volumes** 
  + **Amazon Elastic Block Store(Amazon EBS)**를 사용하여 영구 스토리지 볼륨에 데이터를 저장
  + 클라우드에서 사용하는 **가상 하드디스크**

* **Regions and Availability Zones** 
  + 인스턴스와 Amazon EBS volumes와 같은 리소스를 위한 여러 물리적 장소

* **보안 그룹(Security groups)**
  + security group을 사용해 인스턴스에 연결할 수 있는 프로토콜, 포트, 소스 IP 범위를 지정할 수 있게 하는 **가상의 방화벽** 기능

* **Elastic IP address(EIP)** 
  + 동적 클라우드 컴퓨팅을 위한 고정 IPv4 주소

* **Tags** 
  + Amazon EC2 리소스에 사용자가 만들고 할당할 수 있는 **메타데이터**

* **[Virtual Private Clouds(VPC)](https://heoj10272.github.io/study/Amazon-VPC-%EC%9D%B4%ED%95%B4.html)** 
  + AWS 클라우드에서는 논리적으로 격리되어 있지만 사용자가 원할 때 마다 자신의 네트워크에 연결할 수 있는 가상 네트워크

<br>
<hr/>
<hr/>

## 5. Amazon EC2 구입 옵션(요금제)

[인스턴스 구입 옵션](https://heoj10272.github.io/study/Instance-Purchasing-%EC%9D%B4%ED%95%B4.html)에는 온디맨드 인스턴스, 예약 인스턴스, 스팟 인스턴스 등이 있다.

## 6. 최대 절전 모드

[Amazon EBS](https://heoj10272.github.io/study/Amazon_EBS_%EC%9D%B4%ED%95%B4_Snapshot.html)를 지원하는 인스턴스 유형에만 가능하다.<br>
인스턴스의 데이터를 Amazon EBS에 임시 저장하고, 다시 복원할 수 있는 기능이다.<br>

인스턴스를 최대 절전 모드로 전환하면 운영체제에 최대 절전 모드를 수행하도록 알리고, 인스턴스 RAM의 콘텐츠를 Amazon EBS 루트 보륨에 저장한다.<br>
따라서 인스턴스를 재시작하면 EBS 루트 볼륨이 이전 상태로 복원되며 RAM의 컨텐츠가 다시 로드된다.

즉 비용을 최소화 하면서 진행중이던 컨텐츠를 잃지 않고 이어갈 수 있다.

## 7. 배치 그룹 (Placement Group)

일반적인 인스턴스는 기본 하드웨어 전반에 분산되어 상호 관련 오류의 위험성을 줄인다.
하지만 인스턴스 배치 그룹을 사용함으로서 인스턴스를 좀 더 효율적으로 배치하고 활용할 수 있다.

  ![Single_Master](/assets/img/study_AWS/2022-06-02-[AWS]_Amazon_EC2_이해/placement_group.png)

* 클러스터 배치 그룹
  + 단일 가용 영역 내에 있는 인스턴스 논리적 그룹
  + **짧은 네트워크 지연 시간**, **높은 네트워크 처리량**을 요하는 애플리케이션에 권장

* 파티션 배치 그룹
  + 논리적 파티션을 나누고, 각 인스턴스 그룹이 서로 기본 하드웨어를 공유하지 않게 함
  + Hadoop, Cassandra, Kafka 등 **대규모의 분산 및 복제된 워크로드**에 필요

* 분산형 배치 그룹
  + 소규모의 인스턴스 그룹을 다른 기본 하드웨어로 분산하여 상호 관련 오류를 줄임
  + 동일한 리전의 여러 가용 영역에 적용될 수 있고, 그룹당 가용 영역별로 최대 7개의 인스턴스까지 가능
  
<br>
<hr/>
<hr/>
<br>

* Ref
  - [AWS UserGuide](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/concepts.html)
  - [blog](https://wbluke.tistory.com/54)
  - [Youtube](https://youtu.be/rdlHszMujnw)