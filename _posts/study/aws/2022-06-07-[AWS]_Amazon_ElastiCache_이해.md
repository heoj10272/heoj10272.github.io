---
layout: post
title: "[AWS] Amazon ElastiCache 이해"
subtitle: AWS
date: '2022-06-07 6:30:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-07-[AWS]_Amazon_ElastiCache_이해/logo.png
---

AWS에서 제공하는 **Amazon ElastiCache**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>
<hr/>

## 1. Amazon ElastiCache 개요

아래는 AWS에서의 **Amazon ElastiCache**에 대한 설명이다.

> **Amazon ElastiCache**는 클라우드에서 **분산된 인 메모리 데이터 스토어** 또는 **캐시 환경**을 손쉽게 설정, 관리 및 확장할 수 있는 웹 서비스입니다. <br>
> 확장 가능하고 비용 효율적인 고성능 캐싱 솔루션을 제공합니다. 또한 분산된 캐시 환경의 배포 및 관리와 관련된 복잡성을 해소할 수 있습니다.

**인 메모리 캐시**는 **모든 데이터를 메모리(RAM)에만 올려놓고 사용하는 데이터베이스**의 일종이다.

즉 **Amazon ElastiCache**는 클라우드 환경에서 **느린 디스크 기반 데이터베이스**에 의존하는 것보다 더 **빠른 인 메모리 데이터 스토어**를 사용해 데이터 집약적 앱을 구축하거나 기존 데이터베이스 성능을 강화할 수 있게 해준다.

하지만 **응답 시간은 마이크로초 대기 시간을 일관되게 유지할 수 없다**.

<br>
<hr/>
<hr/>

## 2. Amazon ElastiCache 엔진

**Amazon ElastiCache**는 다음과 같은 두 가지 **오픈 소스 인 메모리 엔진**을 지원한다.


* **Memcached**
    + **널리 채택된 메모리 객체 캐싱 시스템**
    + ElastiCache는 Memcached와 프로토콜이 호환되므로 **기존 Memcached 환경에서 사용하는 주요 도구가 ElastiCache에서 거의 수정되지 않고 작동함**
    + **Memcached 클러스터**는 **리전의 가용 영역 별로 생성 가능**
    + 클러스터 내에 **노드를 추가할 수록 데이터 저장 공간이 늘어남**
    + **스냅샷**과 **Read Replica**를 **지원하지 않음**
    + MultiThreaded architecture이다.

* **Redis**
    + **빠른 오픈 소스 인 메모리 데이터 스토어 및 캐시**
    + 다양한 데이터 형식을 제공하는 **키-값(Key-Value) 데이터 저장소**
    + **스냅샷**과 **Read Replica**를 **지원함**
    + 마스터 노드에 장애가 발생할 경우 자동으로 Read Replica를 마스터로 승격시키는 **Failover 기능 지원**
    + **클러스터 구성 불가**, 따라서 노드를 추가해도 전체 메모리 용량이 늘어나지 않으므로 **데이터 저장 용량은 각 캐시 노드의 메모리 용량에 한함**
    + 캐시 노드의 메모리 용량을 넘어서는 데이터를 저장하기 위해서는 **애플리케이션 레벨에서의 샤딩 구현 필요**
    + **한 리전 안의 여러 가용 영역에 생성 가능**
    + Redis용 ElastiCache는 확장 가능하고 안전한 완전관리형 서비스로서, 웹, 모바일 앱, 게임, 광고 기술 및 IoT와 같은 고성능 사용 사례에 지원하는 데 매우 적합한 서비스
    + MultiThreaded architecture가 아니다.


## 3. Amazon ElastiCache 기능

ElastiCache Redis/Memcached와 같은 In-Memory Key/Value 저장소를 활용하여 세션 데이터를 관리하고 저장할 수 있다.

세션 데이터는 어플리케이션 계층에서 관리되기 때문에, 분산 캐시(distribued cache)가 사용되어야 한다.

<br>
<hr/>
<hr/>
<br>

* Ref
  - [AWS Amazon ElastiCache Userguide](https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/mem-ug/WhatIs.html)
  - [blog](https://sarc.io/index.php/aws/656-aws-amazon-elasticache)
