---
layout: post
title: "[AWS] Amazon RDS 이해"
subtitle: AWS
date: '2022-08-13 05:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-08-13-[AWS]_Amazon_RDS_이해/logo.png
---

AWS 서비스 중 하나인 **RDS**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>

# 1. RDS 개요
---

추후 작성 예정

<br>

# RDS Proxy
---

RDS Proxy는 완전 관리형, 고가용성의 사용이 간편한 Amazon RDS의 데이터베이스 프록시 기능이다.

## RDS Proxy 특징
---

1. 데이터베이스 연결을 풀링(pooling) 및 공유(sharing)하여 확장성을 높인다.
2. 데이터베이스 페일오버 시간을 최대 66% 단축하고 페일오버 중에도 애플리케이션 연결을 보존하여 가용성을 향상시킨다.
3. 선택적으로 데이터베이스에 AWS IAM 인증을 적용하고 AWS Secrets Manager에 자격 증명을 안전하게 저장함으로써 보안을 강화할 수 있다.

## RDS Proxy address의 Use Case
---

1. 예측할 수 없는 워크로드가 있는 애플리케이션

2. 데이터베이스 연결을 자주 열고 닫는 애플리케이션

3. 연결은 되어 있지만 유휴 상태인 애플리케이션

4. 일시적인 장애에 대한 가용성을 필요로 하는 애플리케이션

5. 보안 강화 및 중앙 집중식 자격 증명 관리 - IAM, Secrets Manager 사용


* Ref
  - [AWS Docs](https://aws.amazon.com/ko/rds/proxy/faqs/)