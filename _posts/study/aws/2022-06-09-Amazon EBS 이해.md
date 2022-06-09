---
layout: post
title: Amazon EBS 이해
subtitle: AWS
date: '2022-06-09 17:00:00 +0900'
category: study
tags: aws
image:
  path: /assets/img/study_AWS/Amazon EBS 이해/logo.png
---

AWS의 **Amazon EBS**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## 1. Amazon EBS 개요

아래는 AWS의 EBS에 대한 설명이다.

> **Amazon Elastic Block Store(EBS)**는 AWS 클라우드의 EC2 인스턴스에 사용할 **영구 블록 스토리지 볼륨을 제공**합니다.<br>
> 각 Amazon EBS 볼륨은 가용 영역 내에 **자동으로 복제**되어 구성요소 장애로부터 보호해주고, **고가용성** 및 **내구성**을 제공합니다.<br>
> Amazon EBS 볼륨은 워크로드 실행에 필요한 **지연 시간이 짧고 일관된 성능**을 제공합니다.<br>
> Amazon EBS를 사용하면 단 몇 분 내에 사용량을 많게 또는 적게 **확장**할 수 있으며, 프로비저닝한 부분에 대해서만 저렴한 비용을 지불합니다.

<br>
<hr/>
<hr/>

## 2. Amazon EBS 특징

1. 가상 하드 드라이브

2. EC2 인스턴스가 종료되어도 계속 유지 가능

3. EBS는 인스턴스와 네트워크로 연결되어있음

4. 인스턴스 정지 후 재기동 가능(인스턴스 정지중엔 EBS 스토리지 요금만 부과)

5. 하나의 EBS를 여러 EC2에 장착 가능(EBS Multi Attach)

6. 루트 볼륨으로 사용시 EC2가 종료되면 같이 삭제됨
    + 단 설정을 통해 EBS만 따로 존속 가능

7. EC2와 같은 가용영역에 존재함
    + EC2와 EBS가 서로 다른 가용영역에 있을 경우 연결 불가능

8. 총 5가지 타입을 제공
    + 범용 (General Purpose of GP3) : SSD
    + 프로비저닝된 IOPS(Provisioned IOPS or io2) : SSD
    + 쓰루풋 최적화 (Throughput Optimized HDD or st1)
    + 콜드 HDD (SC1)
    + 마그네틱 (Standard)

![EBS_connect1](/assets/img/study_AWS/Amazon EBS 이해/EBS_connect1.png){: width="60%" height="60%"}{:.centered}

EBS는 EC2 인스턴스와 네트워크로 연결되어 있기 때문에, 네트워크만 바꿔주면 다른 EC2와 연결할 수 있다.

![EBS_connect2](/assets/img/study_AWS/Amazon EBS 이해/EBS_connect2.png){: width="50%" height="50%"}{:.centered}

또한 위 그림처럼 하나의 EC2 인스턴스에 여러 EBS를 연결하는 것도 가능하다.

<br>
<hr/>
<hr/>
<br>

* Ref
  - [AWS Amazon EBS Userguide](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/AmazonEBS.html)
  - [Youtube](https://youtu.be/N8TB_6AbaM4)