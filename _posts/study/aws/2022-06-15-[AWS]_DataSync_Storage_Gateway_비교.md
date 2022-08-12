---
layout: post
title: "[AWS] DataSync와 Storage Gateway 비교"
subtitle: AWS
date: '2022-06-15 18:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-15-[AWS]_DataSync_Storage_Gateway_비교/logo.png
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

![archi](/assets/img/study_AWS/2022-06-15-[AWS]_DataSync_Storage_Gateway_비교/archi.png)

온프레미스에서 AWS 스토리지로 데이터를 옮기고 싶을 때의 상황이다.<br>
온프레미스 서버에 Agent를 설치하고, DataSync로 데이터를 전송하면 DataSync에서 각 서비스로 데이터를 전송하게 된다.

<br>
<hr/>

### II. AWS 스토리지 -> AWS 스토리지

![archi2](/assets/img/study_AWS/2022-06-15-[AWS]_DataSync_Storage_Gateway_비교/archi2.png)

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

[AWS Storage Gateway](https://heoj10272.github.io/study/AWS_Storage_Gateway_%EC%9D%B4%ED%95%B4.html) 참조

<br>
<hr/>
<hr/>

## 3. DataSync와 Storage Gateway 비교

![compare](/assets/img/study_AWS/2022-06-15-[AWS]_DataSync_Storage_Gateway_비교/compare.png)

DataSync의 경우 `AWS안에서 혹은 온프레미스`에서 데이터를 `이동`하기 위한 서비스이고<br>
Storage Gateway의 경우 `하이브리드환경의 온프레미스`에서 클라우드의 저장 서비스를 `연동`하기 위한 서비스이다.

DataSync는 `전송 필터`가 가능하고<br>
Storage Gateway는 `불가능`하다.

DataSync와 Storage Gateway 모두 `NFS, SBM`을 지원한다.<br>
하지만<br>
DataSync는 `HDFS`, `S3 API`를 지원하는 반면<br>
Storage Gateway는 `iSCSI`를 지원한다.

DataSync와 Storage Gateway 모두 `S3`로의 전송이 가능하다.<br>
DataSync는 여기에 추가로 `EFS`, `FSx`로의 전송도 가능하다.<br>
Storage Gateway는 `S3`만 전송 가능하다.

DataSync와 Storage Gateway 모두 `온프레미스 -> AWS` 전송이 가능하다.<br>
DataSync는 여기에 추가로 `AWS -> AWS` 전송 또한 가능하다.<br>
Storage Gateway는 `온프레미스 -> AWS` 전송만 가능하다.

DataSync는 `Glacier/DA`로의 전송이 `직접적`으로 지원된다.<br>
Storage Gateway는 일단 S3에 저장하고, 이후 `LifeCycle`로 `Glacier/DA`로의 전송이 `간접적`으로 가능하다.

DataSync는 `실패시 재전송` 기능이 있지만<br>
Storage Gateway는 `불가능`하다.

DataSync는 최대 `10GB/sec` 처리량을 지원한다.<br>
Storage Gateway는 최대 `500MB/sec` 처리량을 지원한다.

DataSync는 `데이터 액세스`가 `불가능`하지만<br>
Storage Gateway는 `File Gateway`로 `데이터 액세스`가 가능하다.

## 4. 결론

* DataSync : **데이터의 전송을 위한 서비스**
    + 데이터를 잘 전달하기 위한 기능으로 구성
        - 데이터 필터, 무결성 검사, 스케줄링, 재시도 등
    + 다양한 서비스/주체간 데이터 전송 지원

* Storage Gateway : **온프레미스 환경에서 AWS의 스토리지를 이용(주로 백업)하기 위한 서비스**
    + 데이터를 클라우드에 저장하고 사용하거나 백업하기 위한 기능
        - 온프레미스에서 클라우드 환경의 데이터를 액세스 가능
    + 테이프 기반(혹은 레거시 환경) 백업 어플리케이션 지원

DataSync와 Storage Gateway는 상호 배타적인 서비스가 아니다.<br>
둘 다 사용하는 아키텍쳐또한 많다.

<br>
<hr/>
<hr/>
<br>

* Ref
  - [Youtube](https://youtu.be/gjlRurFnYeg)

