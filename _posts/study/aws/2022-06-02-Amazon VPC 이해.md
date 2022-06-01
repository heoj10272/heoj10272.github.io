---
layout: post
title: Amazon VPC 이해
subtitle: AWS
date: '2022-06-02 5:45:00 +0900'
category: study
tags: aws
image:
  path: /assets/img/study_AWS/aws_logo.png
---

**Amazon VPC**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

## 1. Amazon VPC 개요

**Amazon Virtual Private Cloud(Amazon VPC)**는 AWS 클라우드 내에서 사용자의 논리적으로 격리된 공간에 virtual private cloud(vpc)라고 불리는 가상 네트워크를 정의할 수 있게 해준다.<br>
Amazon EC2 인스턴스와 같은 AWS 리소스를 사용자 VPC의 서브넷에서 만들 수 있다.<br>
이 가상 네트워크는 사용자의 자체(자신의) 데이터 센터에서 운영하는 기존 네트워크와 매우 흡사하며 AWS의 가변(Scalable) 인프라를 사용한다는 이점이 있다.<br>
사용자는 VPC의 IP주소 범위를 선택하고, 서브넷을 만든 후 라우팅 테이블, 네트워크 게이트웨이 및 보안 설정을 구성하여 VPC를 구성할 수 있다.<br>
사용자는 자신의 VPC에 있는 인스턴스를 인터넷에 연결하거나 자체 데이터센터에 연결할 수 있다.

<hr/>

## 2. Amazon VPC 개념

**Amazon VPC**는 Amazon EC2의 네트워킹 계층이다.
다음은 VPC의 핵심 개념이다.

* **Virtual Private Cloud(VPC)**
  - 사용자의 AWS계정 전용 가상 네트워크
* **Subnet**
  - VPC의 IP 주소 범위
* **CIDR(Classless Inter-Domain Routing) block**
  - 클래스 없는 도메인간 라우팅 기법을 이용한 IP address들의 그룹
  - 인터넷 프로토콜 주소 할당 및 라우팅 집계 방법
* **Routing Table**
  - 네트워크 트래픽을 전달할 위치를 결정하는데 사용하는 라우팅이라는 이름의 규칙 집합
* **DHCP option sets**
  - VPC 서브넷으로 시작될 때 EC2 인스턴스로 전달되는 구성 정보
  - 예 : 도메인 이름 및 도메인 이름 서버
* **Internet Gatway(IGA)**
  - VPC의 리소스와 인터넷 간의 통신을 활성화하기 위해 VPC에 연결하는 게이트웨이
* **Egress-only internet gateways**
  - 송신 전용 인터넷 게이트웨이
  - 서브넷의 EC2 인스턴스가 인터넷에 엑세스 할 수 있도록 허용하지만 인터넷의 리소스가 인스턴스와의 통신을 시작하지 못하도록 하는 인터넷 게이트웨이 유형
* **VPC endpoint**
  - 인터넷 게이트웨이, NAT 디바이스, VPN 연결 또는 AWS Direct Connect 연결을 필요로 하지 않고 PrivateLink 구동 지원 AWS 서비스 및 VPC 엔드포인트 서비스에 VPC를 비공개로 연결할 수 있음
  - VPC의 인스턴스는 서비스의 리소스와 통신하는데 퍼블릭 IP 주소를 필요로 하지 않음
* **NAT gateway**
  - 프라이빗 서브넷의 EC2 인스턴스가 인터넷, 다른 VPC 또는 온프레미스 네트워크에 연결되도록 허용하는 관리형 AWS 서비스
* **NAT instance**
  - 프라이빗 서브넷의 인스턴스가 인터넷, 다른 VPC 또는 온프레미스 네트워크에 연결되도록 허용하는 퍼블릭 서브넷의 EC2 인스턴스
* **Carrier gateways**
  - Wavelength Zone의 서브넷의 경우 이 유형의 게이트웨이는 특정 위치에 있는 캐리어 네트워크에서의 인바운드 트래픽과 캐리어 네트워크 및 인터넷으로의 아웃바운드 트래픽을 허용함
* **Prefix lists**
  - 접두사 목록
  - VPC 보안 그룹, VPC 라우팅 테이블 및 AWS Transit Gateway 라우팅 테이블을 구성하는데 사용할 수 있으며, RAM(Resource Access Manager)을 사용하여 다른 AWS 계정과 공유될 수 있는 CIDR 블록 모음
* **Security groups**
  - EC2 인스턴스 등의 AWS 리소스에 대한 인바운드 및 아웃바운드 트래픽을 제어하는 가상 방화벽 역할을 함
  - 각 VPC는 기본 보안 그룹과 함께 제공되며 추가 보안 그룹을 생성할 수 있음
  - 보안 그룹은 보안 그룹이 생성된 VPC에서만 사용할 수 있음
* **Network ACLs**
  - 서브넷에서 들어오고 나가는 트래픽을 제어하기 위해 방화벽 역할을 수행하는 VPC에 대한 선택적 보안 계층

<hr/>

## 2. Amazon VPC 액세스

다음 인터페이스 중 하나를 사용하여 VPC를 생성하고, 액세스하고, 관리할 수 있음

* **AWS Management Console**
  + VPC에 액세스 할 때 사용할 수 있는 웹 인터페이스를 제공
* **AWS Command Line Interface(AWS CLI)**
  + Amazon VPC를 포함한 다양한 AWS 서비스에서 사용되는 명령을 제공하며 Windows, macOS 및 Linux에서 지원됨
* **AWS SDK**
  + 언어별 API를 제공하고, 서명 계산, 요청 재시도 처리 및 오류 처리와 같은 많은 연결 세부정보를 관리
* **Query API**
  + HTTPS 요청을 사용하여 호출하는 하위 수준의 API 작업을 제공
  + Query API 사용이 Amazon VPC에 액세스하는 가장 직접적인 방법이지만, 어플리케이션에서 요청에 서명할 해시 생성 및 오류 처리와 같은 하위 수준의 세부 정보를 처리해야 함

<hr/>

* Ref
  - [AWS UserGuide amazon vpc](https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/what-is-amazon-vpc.html)
  - [AWS UserGuide using vpc](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/using-vpc.html)
  - [Developers](https://dev.classmethod.jp/articles/vpc-3/)
  - [Medium](https://medium.com/harrythegreat/aws-%EA%B0%80%EC%9E%A5%EC%89%BD%EA%B2%8C-vpc-%EA%B0%9C%EB%85%90%EC%9E%A1%EA%B8%B0-71eef95a7098)