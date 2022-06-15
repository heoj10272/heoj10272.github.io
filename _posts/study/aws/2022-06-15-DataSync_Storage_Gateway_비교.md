---
layout: post
title: DataSync와 Storage Gateway 비교
subtitle: AWS
date: '2022-06-15 18:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-15-AWS_Storage_Gateway_이해/logo.png
---

AWS의 **DataSync, Storage Gateway**를 이해하고 비교해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## 1-1. AWS DataSync 개요

아래는 AWS에서 소개하는 Storage Gateway 설명이다.

> **AWS DataSync**는 온프레미스와 AWS 스토리지 서비스 사이에서 데이터 이동을 자동화 및 가속화하는 안전한 온라인 서비스입니다. DataSync는 NFS(Network File System) 공유, SMB(Server Message Block) 공유, Hadoop 분산 파일 시스템(HDFS), 자체 관리형 객체 스토리지, AWS Snowcone, Amazon S3 버킷, Amazon EFS 파일 시스템 및 Amazon FSx for Windows File Server 파일 시스템 간에 데이터를 복사할 수 있습니다.

<br>
<hr/>
<hr/>

## 1-2. AWS DataSync 개념

* AWS안에서 혹은 온프레미스에서 데이터를 이동하기 위한 서비스
    + AWS 스토리지 -> AWS 스토리지
    + 온프레미스 -> AWS 스토리지

* 다양한 AWS 스토리지를 지원
    + S3, EFS, FSx, SnowCone

* Agent를 사용
    + 데이터센터에 설치되어 가상머신(VM)으로 데이터의 소스를 읽어 AWS의 데이터 저장 서비스로 데이터를 전송
    + 동일한 AWS 계정에서 데이터를 전송할 땐 사용하지 않음 = 다른 계정으로 옮길때는 필요(주로 EC2에 설치)

* 지원 프로토콜
    + NFS, SMB, HDFS, S3 API


<br>
<hr/>
<hr/>

## 1-3. AWS DataSync 아키텍쳐

### I. 온프레미스 -> AWS 스토리지

![archi](/assets/img/study_AWS/2022-06-15-DataSync_Storage_Gateway_비교/archi.png)

온프레미스에서 AWS 스토리지로 데이터를 옮기고 싶을 때의 상황이다.<br>
온프레미스 서버에 Agent를 설치하고, DataSync로 데이터를 전송하면 DataSync에서 각 서비스로 데이터를 전송하게 된다.

<br>
<hr/>

### II. AWS 스토리지 -> AWS 스토리지

![archi2](/assets/img/study_AWS/2022-06-15-DataSync_Storage_Gateway_비교/archi2.png)

AWS 스토리지에서 AWS 스토리지로 데이터를 옮기고 싶을 때의 상황이다.<br>
해당 그림은 다른 리전에서의 데이터 전송이지만, 같은 리전에서도 가능하다.<br>
동일한 AWS 계정 내에서의 데이터 전송이므로 Agent는 필요하지 않다.<br>
DataSync 서비스끼리 서로 싱크를 맞춰서 자동으로 해당 리전으로 데이터를 전송한다.

<br>
<hr/>
<hr/>

## 1-4. AWS DataSync 기능

* 데이터의 전송 전 필터 적용 가능
    + 어떤 데이터를 제외하거나 포함할지 설정 가능
        - 예 : JPG 확장자인 데이터만 전송

* 스케줄 설정 가능
    + 일정 스케줄마다 데이터를 전송 및 동기화

* 데이터 무결성 검사
    + 데이터의 손상이나 누락을 검사할 수 있음

* 동시에 여러 소스에서 하나의 대상으로 전송 가능
    + 예 : 여러 Agent에서 하나의 S3 버킷으로 전송

* 전송 실패시 재전송

즉 DataSync는 주로 데이터의 전송 및 이동을 목적으로 하는 서비스이다.

<br>
<hr/>
<hr/>

## 2. AWS Storage Gateway 개요

[AWS Storage Gateway](https://heoj10272.github.io/study/DataSync_Storage_Gateway_비교.html) 참조

<br>
<hr/>
<hr/>
<br>

* Ref
  - [Youtube](https://youtu.be/gjlRurFnYeg)

