---
layout: post
title: SES, SNS, SQS 비교
subtitle: AWS
date: '2022-06-15 19:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-15-SES_SNS_SQS_비교/logo.png
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

* 