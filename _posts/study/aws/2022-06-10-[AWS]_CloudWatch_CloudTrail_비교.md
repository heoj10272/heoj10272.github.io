---
layout: post
title: "[AWS] CloudWatch와 Cloudtrail 비교"
subtitle: AWS
date: '2022-06-10 18:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-10-[AWS]_CloudWatch_CloudTrail_비교/logo.png
---

AWS의 **Amazon CloudWatch, AWS CloudTrail**을 이해하고 비교해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## 1-1. Amazon CloudWatch 개요

아래는 AWS의 **Amazon CloudWatch**에 대한 설명이다.

> **Amazon CloudWatch**는 DevOps 엔지니어, 개발자, SRE(사이트 안정성 엔지니어) 및 IT 관리자를 위해 구축된 **모니터링 및 관찰 기능 서비스**입니다.<br>
> **CloudWatch**는 애플리케이션을 모니터링하고, 시스템 전반의 성능 변경 사항에 대응하며, 리소스 사용률을 최적화하고, 운영 상태에 대한 통합된 보기를 확보하는 데 필요한 데이터와 실행 가능한 통찰력을 제공합니다.

<br>
<hr/>
<hr/>

## 1-2. Amazon CloudWatch 주요 기능

* AWS에서 제공하는 AWS 서비스 전반에 대한 모니터링 서비스 : **퍼포먼스 체크**

* 크게 3가지 기능
  + **로그**
  + **이벤트**
    - 이벤트 기능은 **EventBridge** 서비스로 따로 빠졌으나, CloudWatch에도 아직 남아있음
  + **경보**

* 기타 로그를 위한 **대시보드** 등의 기능 제공

<br>
<hr/>
<hr/>

## 1-2-1. CloudWatch 로그

* **AWS 내외의 로그를 모아 보관하고 사용자에게 전달**

* **주요 서비스들에 대한 모니터링** (로그, 메트릭 등) 제공
  + EC2, AutoScaling Groups, ELB, Route53
  + CloudFront, EBS, Storage Gateway 등등

* **주요 서비스의 출력 결과 기록** (Lambda 등)

* 사용자가 **직접 로그 그룹을 만들어 외부로부터 로그를 적재 가능**
  + 주로 온프레미스의 로그를 저장 및 사용

* 로그를 쿼리 형식으로 분석 가능한 **Insight** 활용 가능

<br>
<hr/>

## 1-2-2. CloudWatch 이벤트

* 일정 주기 혹은 AWS의 **여러 이벤트를 감지해 다른 AWS 서비스(SNS, Lambda 등)를 호출하는 규칙**
  + **EventBridge** 규칙과 동일

* **일정 주기로 이벤트 생성 가능**
  + 예 : 매시 정각마다 하루에 쌓인 로그를 분석

* AWS의 **여러 이벤트를 잡아 생성**

![CloudWatch_eventbus](/assets/img/study_AWS/2022-06-10-[AWS]_CloudWatch_CloudTrail_비교/CloudWatch_eventbus.png)

위 그림은 **CloudWatch**가 **이벤트 버스(Event Bus)**로부터 **이벤트를 잡아 규칙을 생성**하여 **다른 서비스들을 호출**하는 과정을 나타낸다.

<br>
<hr/>

## 1-2-3. CloudWatch 경보

* 로그를 기반으로 지표를 생성해서 **특정 지표의 조건에 따라 경보 발생**
  + 경보는 **다른 서비스(SNS 등)를 통해 호출 가능**
  + 예시 : CPU 사용량이 일정 수준 이상, 호출 Lambda에 에러 발생


<br>
<hr/>
<hr/>

## 2-1. AWS CloudTrail 개요

아래는 AWS의 **AWS CloudTrail**에 대한 설명이다.

> **AWS CloudTrail**은 AWS 계정의 거버넌스, 규정 준수, 운영 감사, 위험 감사를 지원하는 서비스입니다.<br>
> CloudTrail을 사용하면 AWS 인프라에서 계정 활동과 관련된 작업을 기록하고 지속적으로 모니터링하며 보관할 수 있습니다.

<br>
<hr/>
<hr/>

## 2-2. AWS CloudTrail 주요 기능

* AWS의 보안 및 감사를 위한 서비스 : **감시(CCTV)**

* 여러 서비스에 대해 **API 이용 로그 등을 제공**
  + **API 호출의 시간 및 결과, 에러, 사용 인증 정보 등을 기록**
  + AWS CLI, 콘솔 이용, API 호출 등 **모든 이벤트가 대상**
  + **몇몇 Data AP의 경우 수동으로 활성화 필요(S3, Lambda, DynamoDB 등)**
    - 기본으로 활성화되면 너무 많은 로그가 쌓일 가능성이 있음

<br>
<hr/>
<hr/>

## 3. CloudTrail vs CloudWatch

* **CloudTrail** : AWS를 감사(audit) 하기 위한 서비스 : **감시(CCTV)**
  + AWS의 **모든 서비스**가 사용될 떄마다 **사용 로그를 저장**
  + **누가 어디서 언제 사용했는지**가 중점
  + AWS가 언제 어디서 누구에 의해 사용되는가?
  + **단순하게 AWS 사용 로그만 저장**
  + **Lambda**로 트리거 될 수 없음

* **CloudWatch** : AWS를 모니터링 하기 위한 서비스 : **퍼포먼스 체크**
  + AWS의 **서비스 뿐만 아니라 어플리케이션의 로그 및 동작 로그 취합**
  + **내용**에 중점
  + 어플리케이션이 어떻게 동작하였는가? 무슨 버그가 있었는가? 메모리는 얼마나 소모되었는가?
  + **대시보드 및 알람** 등 **모니터링을 위한 서비스 제공**
  + CloudWatch Event - **Lambda**로 트리거 가능

<br>
<hr/>
<hr/>
<br>

* Ref
  - [Youtube](https://youtu.be/h6KDij0TCEw)