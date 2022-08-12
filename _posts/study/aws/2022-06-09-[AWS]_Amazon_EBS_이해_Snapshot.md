---
layout: post
title: "[AWS] Amazon EBS 이해, Snapshot"
subtitle: AWS
date: '2022-06-09 17:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-09-[AWS]_Amazon_EBS_이해_Snapshot/logo.png
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

1. **가상 하드 드라이브**

2. **EC2 인스턴스가 종료되어도 계속 유지 가능**
  + 옵션으로 `종료 시 삭제`를 활성화하면, 인스턴스 종료시 함께 EBS를 삭제할 수 있다.

3. **EBS는 인스턴스와 네트워크로 연결되어있음**

4. **인스턴스 정지 후 재기동 가능(인스턴스 정지중엔 EBS 스토리지 요금만 부과)**

5. **하나의 EBS를 여러 EC2에 장착 가능(EBS Multi Attach)**

![EBS_Multi_Attach](/assets/img/study_AWS/2022-06-09-[AWS]_Amazon_EBS_이해_Snapshot/multi_attach.png){: width="60%" height="60%"}{:.centered}

하나의 EBS를 여러 EC2에서 접속하는것이 가능하다.<br>
최대 16개의 클라이언트를 지원한다? <- 확실하지 않음.<br>
[그림 출처](https://towardsdatascience.com/stop-duplicating-deep-learning-training-datasets-with-amazon-ebs-multi-attach-d9f61fdc1de4)

6. **루트 볼륨으로 사용시 EC2가 종료되면 같이 삭제됨**
    + 단 설정을 통해 EBS만 따로 존속 가능

7. **EC2와 같은 가용영역에 존재함**
    + EC2와 EBS가 **서로 다른 가용영역에 있을 경우 연결 불가능**

![EBS_connect1](/assets/img/study_AWS/2022-06-09-[AWS]_Amazon_EBS_이해_Snapshot/EBS_connect1.png){: width="60%" height="60%"}{:.centered}

**EBS는 EC2 인스턴스와 네트워크로 연결되어 있기 때문에**, **네트워크만 바꿔주면 다른 EC2와 연결할 수 있다**.

![EBS_connect2](/assets/img/study_AWS/2022-06-09-[AWS]_Amazon_EBS_이해_Snapshot/EBS_connect2.png){: width="50%" height="50%"}{:.centered}

또한 위 그림처럼 **하나의 EC2 인스턴스에 여러 EBS를 연결하는 것도 가능하다**.

<br>
<hr/>
<hr/>

## 3. Amazon EBS 타입

총 5가지 타입을 제공한다.

    범용 (General Purpose of GP3) : SSD
    프로비저닝된 IOPS(Provisioned IOPS or io2) : SSD
    쓰루풋 최적화 (Throughput Optimized HDD or st1)
    콜드 HDD (SC1)
    마그네틱 (Standard)

![EBS_connect2](/assets/img/study_AWS/2022-06-09-[AWS]_Amazon_EBS_이해_Snapshot/EBS_types.png){:.centered}

위 그림은 EBS 타입들에 따른 사양이다.<br>
자세한 사항은 아래와 같다.

![ssd](/assets/img/study_AWS/2022-06-09-[AWS]_Amazon_EBS_이해_Snapshot/ssd.png){:.centered}

SSD
{:.figcaption}

![hdd](/assets/img/study_AWS/2022-06-09-[AWS]_Amazon_EBS_이해_Snapshot/hdd.png){:.centered}

HDD
{:.figcaption}

처리량 최적화(쓰루풋 최적화) HDD는 싼 가격으로 자주 접근되는 경우 사용된다.<br>
Cold HDD는 가장 싼 가격으로 상대적으로 덜 자주 사용되는 경우에 사용된다.

<br>
<hr/>
<hr/>

## 4. 스냅샷(Snapshot)

**스냅샷**이란 특정 시간의 EBS 상태의 저장본이다.<br>
EBS의 **사진을 찍어둔 개념**이라고 볼 수 있다.

필요시 스냅샷을 통해 **특정 시간의 EBS를 복구하는것이 가능**하다.

**S3**에 보관하며, **증분식**으로 저장한다.<br>
증분식이란, 모든 변화에 따른 상태 전체를 저장하는 것이 아닌, **변화된 부분만 저장**해 결과에 다다르도록 하는 저장 방식이다.

<br>
<hr/>
<hr/>
<br>

* Ref
  - [AWS Amazon EBS Userguide](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/AmazonEBS.html)
  - [Youtube](https://youtu.be/N8TB_6AbaM4)