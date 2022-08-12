---
layout: post
title: "[AWS] SES, SNS, SQS 비교"
subtitle: AWS
date: '2022-06-15 19:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-15-[AWS]_SES_SNS_SQS_비교/logo.png
---

AWS의 **SES, SNS, SQS**를 이해하고 비교해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## 1-1. Amazon Simple Email Service(SES) 개요

아래는 AWS에서 소개하는 Amazon Simple Email Service(SES) 설명이다. 

> **Amazon Simple Email Service(SES)**는 개발자가 모든 애플리케이션 안에서 이메일을 보낼 수 있는 경제적이고, 유연하며, 확장 가능한 이메일 서비스입니다. Amazon SES를 빠르게 구성하여 트랜잭션, 마케팅 또는 대량 이메일 커뮤니케이션을 포함한 다수의 이메일 사용 선례를 지원할 수 있습니다.

<br>
<hr/>
<hr/>

## 1-2. SES 개념

* Email을 보내거나 받을 수 있는 서비스

* 이메일을 받을 때 여러 방법으로 처리 가능
    + Lambda 호출
    + SNS 호출
    + S3에 저장

* 대량의 이메일을 보내기 위해서는 샌드박스 모드 해제 필요(AWS Support 센터)
    + 스팸 메일 유포 방지를 위함

<br>
<hr/>
<hr/>

## 2-1. Amazon Simple Notification Service(SNS) 개요

아래는 AWS에서 소개하는 Amazon Simple Notification Service(SES) 설명이다. 

> Amazon Simple Notification Service(SNS)는 애플리케이션간(A2A) 및 애플리케이션과 사용자간(A2P) 통신 모두를 위한 완전관리형 메시징 서비스입니다.

<br>
<hr/>
<hr/>

## 2-2. SNS 개념

* Pub/Sub(Publish/Subscribe) 기반의 메시징 서비스
    + 하나의 토픽을 여러 주체가 구독
        - 토픽에 전달된 내용을 구독한 모든 주체가 전달받아 처리

* 다양한 프로토콜로 메시지 전달 가능
    + 이메일
    + HTTP(S)
    + SQS
    + SMS
    + Lambda

* **하나의 메시지를 여러 서비스에서 처리**

아래는 SNS의 간단한 구조도이다.

![sns_archi](/assets/img/study_AWS/2022-06-15-[AWS]_SES_SNS_SQS_비교/sns_archi.png)

아래는 자세한 전달 대상들이다.

![sns_archi2](/assets/img/study_AWS/2022-06-15-[AWS]_SES_SNS_SQS_비교/sns_archi2.png)

<br>
<hr>

### Fan Out Architecture

다음은 SNS를 말할 때 빼놓을 수 없는 `Fan Out Architecture`에 대한 그림이다.

![fan_out](/assets/img/study_AWS/2022-06-15-[AWS]_SES_SNS_SQS_비교/fan_out.png)

1. 먼저 User가 S3에 원본 영상을 업로드한다.
2. 이를 Lambda를 통해(그림에선 생략) SNS로 보낸다.
3. SNS에서 각각의 인코딩 할 수 있는 EC2로 메시지를 보낸다.

즉 S3에 전달된 하나의 내용을 SNS가 여러 인스턴스로 증폭시킬 수 있다.<br>
이를 `Fan Out Architecture`라고 한다.

<br>
<hr/>
<hr/>

## 3-1. Amazon Simple Queue Service(SQS) 개요

아래는 AWS에서 소개하는 Amazon Simple Queue Service(SES) 설명이다. 

> Amazon Simple Queue Service(SQS)는 마이크로서비스, 분산 시스템 및 서버리스 애플리케이션을 쉽게 분리하고 확장할 수 있도록 지원하는 완전관리형 메시지 대기열 서비스입니다.

<br>
<hr/>
<hr/>

## 3-2. SQS 개념

* AWS에서 제공하는 큐 서비스
    + 다른 서비스에서 사용할 수 있도록 메시지를 잠시 저장하는 용도
    + 최대 사이즈 : 256KB, 최대 14일까지 저장 가능

* 주로 AWS 서비스들의 느슨한 연결(decoupling)을 수립하려 사용

* **하나의 메시지를 한 번만 처리**

* AWS에서 제일 오래된 서비스

## 3-3. Amazon Simple Queue Service(SQS)용 Temporary Queue Client

- 클라이언트는 요청-응답과 같은 일반 메시지 유형을 지원하고 애플리케이션 관리형 임시 대기열을 생성할 때 발전 시간과 발전 비용 절약을 지원합니다.

- 클라이언트는 다양한 여러 대기열을 단일 Amazon SQS 대기열에 매핑하여 애플리케이션이 더 적은 API 호출을 실시하여 더 높은 처리량을 얻을 수 있도록 합니다. 임시 대기열이 더 이상 사용되지 않으면 클라이언트가 임시 대기열을 자동으로 정리합니다.

### SQS의 필요성

![sqs_fail](/assets/img/study_AWS/2022-06-15-[AWS]_SES_SNS_SQS_비교/sqs_fail.png)

위는 유저가 S3에 영상을 올리면 EC2에서 인코딩하는 시스템을 나타낸 그림이다.

유저가 S3에 원본 영상을 업로드하면, Lambda를 통해서 EC2로 전달된다.<br>
하지만 만약 그 당시 갑자기 EC2가 떨어지면, 오류가 발생하고 그대로 끝난다.

즉, Fail 처리에 대한 매커니즘이 없다.<br>
Lambda는 tight한 연결이기 때문에, 로직이 Fail이 나면 그대로 끝이 나게 된다.

![sqs_decoupling](/assets/img/study_AWS/2022-06-15-[AWS]_SES_SNS_SQS_비교/sqs_decoupling.png)

따라서 이를 방지하기 위해 중간에 Amazon SQS를 배치한다.

Lambda를 통해서 SQS에 전달될 경우 EC2 클러스터들이 SQS에서 메시지를 빼서 처리하게 된다.

즉, 만약 EC2가 전부 Fail이 나서 메시지를 처리할 수 없게 되더라도 메시지는 SQS에 보관되어 있기 때문에 유실되지 않는다.
이후에 EC2가 복구되면 보관된 메시지를 처리할 수 있다.

SQS는 이런 경우를 방지하기 위한 하나의 서비스에서 다른 서비스로 메시지를 안전하게 전달하기 위한 서비스이다.

추가로 현재 Lambda에서 다른 서비스로의 전달은 SQS를 거치기 때문에, 메시지를 받는 주체인 EC2가 다른 서비스(Lambda, Fargate, ECS 등)로 변경되더라도 Lambda는 바뀔 필요가 없다.<br>
즉, 완전히 독립적인 아키텍쳐를 구성한다.<br>
이를 디커플링(decoupling)이라고 한다.

## 4. SNS와 SQS 비교

![sns_sqs](/assets/img/study_AWS/2022-06-15-[AWS]_SES_SNS_SQS_비교/sns_sqs.png)

SNS와 SQS는 위 표와 같은 차이를 가진다.

SQS는 비동기식 데이터 캡쳐에 사용된다.<br>
SNS는 한 번 메시지를 푸쉬하고 나면 회복력이 없다.