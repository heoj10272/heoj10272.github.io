---
layout: post
title: "[AWS] Amazon VPC 이해"
subtitle: AWS
date: '2022-06-02 5:45:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-02-[AWS]_Amazon_VPC_이해/logo.png
---

**Amazon VPC**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

# 1. Amazon VPC 개요
---

**Amazon Virtual Private Cloud(Amazon VPC)**는 AWS 클라우드 내에서 사용자의 논리적으로 격리된 공간에 virtual private cloud(vpc)라고 불리는 가상 네트워크를 정의할 수 있게 해준다.<br>
Amazon EC2 인스턴스와 같은 AWS 리소스를 사용자 VPC의 서브넷에서 만들 수 있다.<br>
이 가상 네트워크는 사용자의 자체(자신의) 데이터 센터에서 운영하는 기존 네트워크와 매우 흡사하며 AWS의 가변(Scalable) 인프라를 사용한다는 이점이 있다.<br>
사용자는 VPC의 IP주소 범위를 선택하고, 서브넷을 만든 후 라우팅 테이블, 네트워크 게이트웨이 및 보안 설정을 구성하여 VPC를 구성할 수 있다.<br>
사용자는 자신의 VPC에 있는 인스턴스를 인터넷에 연결하거나 자체 데이터센터에 연결할 수 있다.


# 2. Amazon VPC 개념
---

**Amazon VPC**는 Amazon EC2의 네트워킹 계층이다.
다음은 VPC의 핵심 개념이다.

* **Virtual Private Cloud(VPC)**
  - 사용자의 AWS계정 전용 가상 네트워크
* **Subnet**
  - VPC의 IP 주소 범위
* **CIDR(Classless Inter-Domain Routing) block**
  - 클래스 없는 도메인간 라우팅 기법을 이용한 IP address들의 그룹
  - 인터넷 프로토콜 주소 할당 및 라우팅 집계 방법
  - 모든 서브넷에서 처음 4개 IP 주소와 마지막 IP 주소는 예약되어 있어서 인스턴스에 할당할 수 없음
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
  - NAT gateway는 항상 public subnet에 위치하여야 함
  - 가용 영역에 failure가 발생할 경우 그에 위치한 NAT gateway는 사용할 수 없게 되고, 다른 가용 영역이 인터넷을 사용할 수 없게 됨. 이를 보완하기 위해서 NAT gateway는 최소 두 가용 영역에 deploy 되어야 함
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
  - 허용 규칙만 지원함
  - 보안 그룹은 보안 그룹이 생성된 VPC에서만 사용할 수 있음
* **Network ACLs**
  - 보안 그룹보다 좀 더 큰 개념
  - 보안 그룹은 인스턴스 레벨, Network ACLs는 서브넷 레벨로 서브넷 간의 통신 규칙을 관리
  - 허용 및 거부 규칙을 모두 지원
  - 서브넷에서 들어오고 나가는 트래픽을 제어하기 위해 방화벽 역할을 수행하는 VPC에 대한 선택적 보안 계층



# 3. Amazon VPC 액세스
---

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


# 4. VPC Peering
---

VPC Peering Connection은 서로 다른 두 VPC 간에 트래픽을 라우팅할 수 있도록 하는 네트워킹 연결이다.

VPC 피어링 연결은 원활한 데이터 전송에 많은 도움이 된다.<br>
예를 들어 AWS 계정이 두 개 이상인 경우 이들 계정을 대상으로 VPC를 피어링하여 파일 공유 네트워크를 만들 수 있다.<br>
VPC 피어링 연결을 사용하여 다른 VPC가 사용자의 VPC 중 하나에 있는 리소스에 액세스 하도록 허용할 수도 있다.<br>

피어링은 항상 가능한 것이 아니다.<br>
다음과 같은 상황에서는 피어링 구성이 지원되지 않는다.

* 겹치는 CIDR 블록
  + 중첩되는 CIDR 블록이 있을 경우 VPC 피어링 연결을 만들 수 없음

* 전이적 피어링(transive peering)
  + A-B-C로 연결되어 있을 때, VPC B를 통해 VPC A에서 VPC C로 직접 패킷을 라우팅 할 수 없음

* 게이트웨이 또는 private 연결을 통한 엣지 간 라우팅
  + A-B 연결에서 B에 인터넷 게이트웨이를 통한 인터넷 연결, AWS Direct Connect 연결, 프라이빗 서브넷에서 NAT 디바이스를 통한 인터넷 연결 등이 있는 경우, A에서 해당 외부 연결에 있는 리소스에 액세스할 수 없음

[Transit Gateway 이해](https://heoj10272.github.io/study/AWS-_Transit_Gateway_%EC%9D%B4%ED%95%B4.html) <- 링크에서 `Transit Gateway`와 `VPC Peering`에 대한 자세한 사항 확인 가능

# 5. Site-to-Site VPN vs AWS Client VPN
---

> AWS VPN은 AWS Site-to-Site VPN 및 AWS Client VPN이라는 두 가지 서비스로 구성됩니다. <br>
> AWS Site-to-Site VPN을 사용하면 온프레미스 네트워크 또는 지사 사이트를 Amazon Virtual Private Cloud(Amazon VPC)에 안전하게 연결할 수 있습니다. <br>
> AWS Client VPN을 사용하면 사용자를 AWS 또는 온프레미스 네트워크에 안전하게 연결할 수 있습니다.

[AWS VPN FAQ](https://aws.amazon.com/vpn/faqs/#:~:text=AWS%20VPN%20%EC%9D%80) 참고

아래는 ExamTopics 문제 중 한 유저의 해설 발췌이다.

**Site-to-Site VPN** 

- 사내 네트워크 또는 지사 사이트를 Amazon Virtual Private Cloud(Amazon VPC)에 안전하게 연결할 수 있다.
- AWS Site-to-Site VPN 연결은 연결이 활성 상태인 각 시간에 대해 시간당 요금이 부과된다. 이 AWS 지역의 경우 요금은 시간당 0.05달러이다. 처음 1GB는 무료.

**AWS Clinet VPN** 

- 시간당 요금: AWS Client VPN endpoint과의 연결 비용은 매 시간마다 청구(요금은 시간당 $0.10)


# Ref
---
  - [AWS UserGuide amazon vpc](https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/what-is-amazon-vpc.html)
  - [AWS UserGuide using vpc](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/using-vpc.html)
  - [Developers](https://dev.classmethod.jp/articles/vpc-3/)
  - [Medium](https://medium.com/harrythegreat/aws-%EA%B0%80%EC%9E%A5%EC%89%BD%EA%B2%8C-vpc-%EA%B0%9C%EB%85%90%EC%9E%A1%EA%B8%B0-71eef95a7098)
  - [Tistory](https://arisu1000.tistory.com/27744)
