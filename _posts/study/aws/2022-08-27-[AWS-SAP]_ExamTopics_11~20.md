---
layout: post
title: "[AWS-SAP] ExamTopics 11~20"
subtitle: AWS
date: '2022-8-27 2:00:00 +0900'
category: study
tags: aws examtopics sap-c01
image:
  path: /assets/img/study_AWS/2022-08-27-[AWS-SAP]_ExamTopics_11~20/logo.png
---

SAP Examtopics 11~20번 문제를 풀어보자.<br>
1차 2/5<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 11 ⭕
---

귀사는 사내 멀티 티어 PHP 웹 애플리케이션을 보유하고 있으며, 최근 회사 발표로 인해 웹 트래픽의 대규모 폭발로 인해 다운타임이 발생했습니다. 앞으로 이와 유사한 발표가 유사한 예측 불가능한 폭발을 일으킬 것으로 예상하며, 인프라 성능을 신속하게 개선할 수 있는 방법을 모색하고 있습니다.트래픽의 예기치 않은 증가를 처리합니다.
현재 애플리케이션은 로드 밸런서와 여러 Linux Apache 웹 서버로 구성된 웹 계층과 MySQL 데이터베이스를 호스팅하는 Linux 서버를 호스팅하는 데이터베이스 계층 2개로 구성됩니다.

다음 중 필요한 짧은 시간에 애플리케이션의 기능을 향상시키면서 전체 사이트 기능을 제공하는 시나리오는 무엇입니까?

A. 페일오버 환경: S3 버킷을 생성하고 웹 사이트 호스팅용으로 구성합니다. 영역 파일 가져오기를 사용하여 DNS를 Route53으로 마이그레이션하고 Route53 DNS 페일오버를 활용하여 S3 호스팅 웹 사이트로 페일오버합니다.

B. 하이브리드 환경: EC2에서 웹 서버를 시작하는 데 사용할 수 있는 AMI를 만듭니다. AMI를 사용하여 들어오는 트래픽을 기준으로 웹 계층을 확장하는 자동 확장 그룹을 만듭니다. 탄력적 부하 분산을 활용하여 사내 웹 서버와 AWS에서 호스팅되는 웹 서버 간의 트래픽 균형을 조정합니다.

C. 사내 환경에서 트래픽 오프로드: CIoudFront 배포를 설정하고 사용자 지정 오리진의 개체를 캐시하도록 CloudFront를 구성합니다. 개체 캐시 동작을 사용자 지정하고 캐시에 개체가 있어야 하는 TTL을 선택합니다.

D. AWS로 마이그레이션: VM 가져오기/내보내기 기능을 사용하여 사내 웹 서버를 AMI로 빠르게 변환합니다. 가져온 AMI를 사용하여 들어오는 트래픽에 따라 웹 계층을 확장하는 자동 확장 그룹을 만듭니다. RDS 읽기 복제본을 생성하고 RDS 인스턴스와 사내 MySQL 서버 간에 복제를 설정하여 데이터베이스를 마이그레이션합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Your company has an on-premises multi-tier PHP web application, which recently experienced downtime due to a large burst in web traffic due to a company announcement Over the coming days, you are expecting similar announcements to drive similar unpredictable bursts, and are looking to find ways to quickly improve your infrastructures ability to handle unexpected increases in traffic.
The application currently consists of 2 tiers a web tier which consists of a load balancer and several Linux Apache web servers as well as a database tier which hosts a Linux server hosting a MySQL database.

Which scenario below will provide full site functionality, while helping to improve the ability of your application in the short timeframe required?

A. Failover environment: Create an S3 bucket and configure it for website hosting. Migrate your DNS to Route53 using zone file import, and leverage Route53 DNS failover to failover to the S3 hosted website.

B. Hybrid environment: Create an AMI, which can be used to launch web servers in EC2. Create an Auto Scaling group, which uses the AMI to scale the web tier based on incoming traffic. Leverage Elastic Load Balancing to balance traffic between on-premises web servers and those hosted in AWS.

C. Offload traffic from on-premises environment: Setup a CIoudFront distribution, and configure CloudFront to cache objects from a custom origin. Choose to customize your object cache behavior, and select a TTL that objects should exist in cache.

D. Migrate to AWS: Use VM Import/Export to quickly convert an on-premises web server to an AMI. Create an Auto Scaling group, which uses the imported AMI to scale the web tier based on incoming traffic. Create an RDS read replica and setup replication between the RDS instance and on-premises MySQL server to migrate the database.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Answer is C

A: This works if the website is static but we don’t know enough about it to determine if S3 can host it<br>
B: ELB can not be used with resources outside of AWS<br>
C: CloudFront works with custom origins, in this case the external PHP web app. CloudFront is a good choice for handling the traffic spike in a short time<br>
D: The scenario does not say the on-prem app is in a VM, this is not an option<br>
https://acloud.guru/forums/aws-certified-solutions-architect-professional/discussion/-KF5MzPkMfG_IyE2jkG1/load-balancing-to-balance-traffic-between-on-premises-web-servers-and-those-host


ELB에는 온프레미스 환경의 서버가 속할 수 없음을 명심하자.<br>
하지만 CF는 custom origin으로서 외부 PHP 웹 애플리케이션과 사용될 수 있다.<br>
CF는 트래픽 스파이크에 좋은 솔루션이다.

1차 시도 : C 맞음<br>
</div>
</details>

<br>

## Prob. 12 ❓
---
AWS Direct Connect를 구현하고 있습니다. AWS Direct Connect 링크를 통해 Amazon S3와 같은 AWS 퍼블릭 서비스 엔드포인트를 사용하려고 합니다. 다른 인터넷 트래픽이 인터넷 서비스 공급자에 대한 기존 링크를 사용하도록 하려는 경우입니다.

아마존 S3와 같은 서비스에 액세스하기 위해 AWS Direct connect를 구성하는 올바른 방법은 무엇입니까?

A. AWS Direct Connect 링크에서 공용 인터페이스를 구성합니다. Amazon S3를 가리키는 AWS Direct Connect 링크를 통해 정적 경로를 구성합니다. BGP를 사용하여 AWS에 기본 경로를 보급합니다.

B. AWS Direct Connect 링크에 개인 인터페이스를 만듭니다. Amazon S3를 가리키는 AWS Direct connect 링크를 통해 정적 경로를 구성합니다. VPC에서 네트워크에 대한 특정 경로를 구성합니다.

C. AWS Direct Connect 링크에 공용 인터페이스를 만듭니다. BGP 경로를 기존 라우팅 인프라로 재배포하고 네트워크에 대한 특정 경로를 AWS에 알립니다.

D. AWS Direct connect 링크에 개인 인터페이스를 만듭니다. BGP 경로를 기존 라우팅 인프라로 재배포하고 기본 경로를 AWS에 보급합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You are implementing AWS Direct Connect. You intend to use AWS public service end points such as Amazon S3, across the AWS Direct Connect link. You want other Internet traffic to use your existing link to an Internet Service Provider.

What is the correct way to configure AWS Direct connect for access to services such as Amazon S3?

A. Configure a public Interface on your AWS Direct Connect link. Configure a static route via your AWS Direct Connect link that points to Amazon S3. Advertise a default route to AWS using BGP.

B. Create a private interface on your AWS Direct Connect link. Configure a static route via your AWS Direct connect link that points to Amazon S3. Configure specific routes to your network in your VPC.

C. Create a public interface on your AWS Direct Connect link. Redistribute BGP routes into your existing routing infrastructure; advertise specific routes for your network to AWS.

D. Create a private interface on your AWS Direct connect link. Redistribute BGP routes into your existing routing infrastructure and advertise a default route to AWS.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : C

일단 S3와 같은 퍼블릭 서비스는 private이 아닌 public virtual interface로 접근해야 한다.
private으로는 vpc에 접근할 수 있다.

또한 BGP는 동적 라우팅을 위한 프로토콜이므로, A에서는의 정적 라우팅은 해당되지 않는다.

BGP(Border Gateway Protocol) : 서로 다른 AS(Autonomous System - 네트워크 집단)를 연결해 주는 경계 게이트웨이 프로토콜.

1차 시도 : 모름 <br>
</div>
</details>

<br>


## Prob. 13 ⭕
---
애플리케이션은 데이터 지속성을 위해 2개의 AZ에 걸쳐 구축된 웹/애플리케이션 서버의 자동 확장 그룹 앞에 ELB를 사용하고 있습니다.
데이터베이스 CPU 사용률이 80%를 넘는 경우가 많으며 데이터베이스의 I/O 작업 중 90%가 읽힙니다. 성능 향상을 위해 최근에 자주 발생하는 DB 쿼리 결과를 캐시하기 위한 단일 노드 Memcached ElastiCache Cluster를 추가했습니다. 향후 몇 주 동안 전체 워크로드가 30% 증가할 것으로 예상됩니다.

고가용성 또는 예상되는 추가 로드가 있는 애플리케이션을 유지하기 위해 아키텍처에서 변경해야 할 사항이 있습니까? 그 이유는 무엇입니까?

A. 예. 캐시 노드에 장애가 발생하면 RDS 인스턴스가 로드를 처리할 수 없으므로 두 개의 Memcached ElastiCache 클러스터를 서로 다른 AZ에 배포해야 합니다.

B. 아니요. 캐시 노드가 실패할 경우 언제든지 가용성에 영향을 주지 않고 DB에서 동일한 데이터를 가져올 수 있습니다.

C. 아니요. 캐시 노드가 실패할 경우 자동화된 ElastiCache 노드 복구 기능이 가용성에 영향을 주지 않습니다.

D. 예, 하나의 캐시 노드에 장애가 발생할 경우 로드를 처리하려면 RDS DB 마스터 인스턴스와 동일한 AZ에 두 개의 노드를 포함하는 Memcached ElastiCache 클러스터를 배포해야 합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Your application is using an ELB in front of an Auto Scaling group of web/application servers deployed across two AZs and a Multi-AZ RDS Instance for data persistence.
The database CPU is often above 80% usage and 90% of I/O operations on the database are reads. To improve performance you recently added a single-node Memcached ElastiCache Cluster to cache frequent DB query results. In the next weeks the overall workload is expected to grow by 30%.

Do you need to change anything in the architecture to maintain the high availability or the application with the anticipated additional load? Why?

A. Yes, you should deploy two Memcached ElastiCache Clusters in different AZs because the RDS instance will not be able to handle the load if the cache node fails.

B. No, if the cache node fails you can always get the same data from the DB without having any availability impact.

C. No, if the cache node fails the automated ElastiCache node recovery feature will prevent any availability impact.

D. Yes, you should deploy the Memcached ElastiCache Cluster with two nodes in the same AZ as the RDS DB master instance to handle the load if one cache node fails.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

고가용성을 위해서 Memcached 클러스터를 서로 다른 AZ에 배포하도록 하자.

1차 시도 : A 맞음<br>
</div>
</details>

<br>

## Prob. 14 ❌
---
ERP 애플리케이션은 단일 영역에서 여러 AZ에 걸쳐 구축됩니다. 장애가 발생할 경우 RTO(복구 시간 목표)는 3시간 미만이어야 하며 RPO(복구 시점 목표)는 15분 미만이어야 합니다. 고객은 약 1.5시간 전에 데이터 손상이 발생했다는 사실을 인지하고 있습니다.

이러한 유형의 장애 발생 시 이러한 RTO 및 RPO를 달성하는 데 사용할 수 있는 DR 전략은 무엇입니까?

A. Take hourly DB backups to S3, with transaction logs stored in S3 every 5 minutes.

B. Use synchronous database master-slave replication between two availability zones.

C. Take hourly DB backups to EC2 Instance store volumes with transaction logs stored in S3 every 5 minutes.

D. Take 15 minute DB backups stored in Glacier with transaction logs stored in S3 every 5 minutes.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
An ERP application is deployed across multiple AZs in a single region. In the event of failure, the Recovery Time Objective (RTO) must be less than 3 hours, and the Recovery Point Objective (RPO) must be 15 minutes. The customer realizes that data corruption occurred roughly 1.5 hours ago.

What DR strategy could be used to achieve this RTO and RPO in the event of this kind of failure?

A. Take hourly DB backups to S3, with transaction logs stored in S3 every 5 minutes.

B. Use synchronous database master-slave replication between two availability zones.

C. Take hourly DB backups to EC2 Instance store volumes with transaction logs stored in S3 every 5 minutes.

D. Take 15 minute DB backups stored in Glacier with transaction logs stored in S3 every 5 minutes.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

The only answer we can be assured of working is A.

B doesn't help for data corruption (question doesn't specify physical or logical so have to address both) as logical corruption will be replicated.<br>
C. We don't put backups on ephemeral storage.<br>
D. Glacier Standard retrieval is 3-5 hours, and whilst expedited can be used to retrieve within 5 minutes, this is only for archives up to 250MB - the question doesn't give the size of the database, so I think we should not choose this option.

문항 번역이 이상하게 되어서 그냥 원문으로 넣었다.

백업 데이터는 EC2와 같은 수명이 짧은? 서비스에는 보관하지 않는다고 한다.

D가 답이라는 말이 있는데, 이는 잘 모르겠다.

1차 시도 : B 틀림<br>
</div>
</details>

<br>

## Prob. 15 ❌
---
Amazon VPC에서 애플리케이션 서버의 네트워크 인프라를 설계하고 있습니다. 사용자는 온프레미스 네트워크뿐만 아니라 인터넷에서도 모든 애플리케이션 인스턴스에 액세스할 수 있습니다. 사내 네트워크는 AWS Direct Connect 링크를 통해 VPC에 연결됩니다.

위의 요구 사항을 충족하기 위해 라우팅을 어떻게 설계하시겠습니까?

A. 인터넷 게이트웨이를 통한 기본 라우트로 단일 라우팅 테이블을 구성합니다. AWS Direct Connect 고객 라우터에서 BGP를 통해 기본 경로를 전파합니다. 라우팅 테이블을 모든 VPC 서브넷과 연결합니다.

B. 인터넷 게이트웨이를 통한 기본 라우트로 단일 라우팅 테이블을 구성합니다. AWS Direct Connect 고객 라우터의 BGP를 통해 사내 네트워크에 대한 특정 경로를 전파합니다. 라우팅 테이블을 모든 VPC 서브넷과 연결합니다.

C. 인터넷 게이트웨이를 통해 인터넷에 접속하고 VPN 게이트웨이를 통해 사내 네트워크에 접속하는 두 가지 기본 경로로 단일 라우팅 테이블을 구성합니다. VPC의 모든 서브넷에서 이 라우팅 테이블을 사용합니다.

D. 인터넷 게이트웨이를 통한 기본 라우터가 있는 라우팅 테이블과 VPN 게이트웨이를 통한 기본 라우터가 있는 라우팅 테이블 두 개를 구성합니다. 두 라우팅 테이블을 각 VPC 서브넷에 연결합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You are designing the network infrastructure for an application server in Amazon VPC. Users will access all application instances from the Internet, as well as from an on-premises network. The on-premises network is connected to your VPC over an AWS Direct Connect link.

How would you design routing to meet the above requirements?

A. Configure a single routing table with a default route via the Internet gateway. Propagate a default route via BGP on the AWS Direct Connect customer router. Associate the routing table with all VPC subnets.

B. Configure a single routing table with a default route via the Internet gateway. Propagate specific routes for the on-premises networks via BGP on the AWS Direct Connect customer router. Associate the routing table with all VPC subnets.

C. Configure a single routing table with two default routes: on to the Internet via an Internet gateway, the other to the on-premises network via the VPN gateway. Use this routing table across all subnets in the VPC.

D. Configure two routing tables: on that has a default router via the Internet gateway, and other that has a default route via the VPN gateway. Associate both routing tables with each VPC subnet.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 :

Rolled out
A propagating default route would cause conflict.
C there cannot be 2 default routes
D as the instances has to be in public subnet and should have a single routing table associated with them

so B is right answer

해설을 봐도 모르겠다...

1차 시도 : D 틀림<br>
</div>
</details>

<br>

## Prob. 16 ⭕ SKIP
---
다음을 사용하여 S3 버킷 및 개체에 대한 액세스를 제어할 수 있습니다.

A. IAM(ID 및 액세스 관리) 정책을 참조하십시오.

B. ACL(액세스 제어 목록)입니다.

C. 버킷 정책을 참조하십시오.

D. 위의 모든 내용입니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You control access to S3 buckets and objects with:

A. Identity and Access Management (IAM) Policies.

B. Access Control Lists (ACLs).

C. Bucket Policies.

D. All of the above
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

IAM, ACL, Bucket policies + Block Public Access

1차 시도 : D 맞음<br>
</div>
</details>

<br>

## Prob. 17 ❌ SKIP
---
AWS가 제공하는 AWS IT 인프라는 다음과 같은 IT 보안 표준을 준수합니다.

A. SOC 1/SSAE 16/ISAE 3402(구 SAS 70 Type II), SOC 2 및 SOC 3입니다.

B. FISMA, DIACAP 및 FedRAMP입니다.

C. PCI DSS 레벨 1, ISO 27001, ITAR 및 FIPS 140-2입니다.

D. HIPAA, 클라우드 보안 얼라이언스(CSA) 및 미국 영화 협회(MPAA)가 있습니다.

E. 위의 모든 것입니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
The AWS IT infrastructure that AWS provides, complies with the following IT security standards, including:

A. SOC 1/SSAE 16/ISAE 3402 (formerly SAS 70 Type II), SOC 2 and SOC 3

B. FISMA, DIACAP, and FedRAMP

C. PCI DSS Level 1, ISO 27001, ITAR and FIPS 140-2

D. HIPAA, Cloud Security Alliance (CSA) and Motion Picture Association of America (MPAA)

E. All of the above
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 

문제가 있는 문제인 것 같다.
패스하자.

1차 시도 : D <br>
</div>
</details>

<br>

## Prob. 18 ❌ SKIP
---
오토 스케일링 요청은 요청과 사용자의 프라이빗 키에서 계산된 ______ 서명으로 서명됩니다.

A. SSL입니다.

B. AES-256입니다

C. HMAC-SHA1입니다.

D. X.509입니다

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Auto Scaling requests are signed with a _________ signature calculated from the request and the user's private key.

A. SSL

B. AES-256

C. HMAC-SHA1

D. X.509
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 


1차 시도 : A 틀림<br>
</div>
</details>

<br>

## Prob. 19 ❌ SKIP
---
다음 정책을 IAM 그룹에 연결할 수 있습니다. 그러면 해당 그룹의 IAM 사용자가 콘솔을 사용하여 사용자 이름과 일치하는 AWS S3의 "홈 디렉토리"에 액세스할 수 있습니다.

```
{
  "Version": "2012-10-17",
  "Statement": 
  [
    {
      "Action": ["s3:*"],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::bucket-name"],
      "Condition":{"StringLike":{"s3:prefix":["home/${aws:username}/*"]}}
    },
    {
      "Action":["s3:*"],
      "Effect":"Allow",
      "Resource": ["arn:aws:s3:::bucket-name/home/${aws:username}/*"]
    }
  ]
}
```

A. 그렇습니다

B. 거짓입니다
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
The following policy can be attached to an IAM group. It lets an IAM user in that group access a "home directory" in AWS S3 that matches their user name using the console.

```
{
  "Version": "2012-10-17",
  "Statement": 
  [
    {
      "Action": ["s3:*"],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::bucket-name"],
      "Condition":{"StringLike":{"s3:prefix":["home/${aws:username}/*"]}}
    },
    {
      "Action":["s3:*"],
      "Effect":"Allow",
      "Resource": ["arn:aws:s3:::bucket-name/home/${aws:username}/*"]
    }
  ]
}
```

A. True

B. False
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Answer B:

explanation:<br>
https://aws.amazon.com/blogs/security/writing-iam-policies-grant-access-to-user-specific-folders-in-an-amazon-s3-bucket/

1차 시도 : A <br>
</div>
</details>

<br>

## Prob. 20 ⭕ SKIP
---
AWS에게 탄력성은 어떤 의미인가요?

A. 마찰을 최소화하면서 컴퓨팅 리소스를 쉽게 확장하고 지연 시간에 따라 축소할 수 있습니다.

B. 마찰을 최소화하면서 컴퓨팅 리소스를 쉽게 확장하거나 축소할 수 있습니다.

C. 미래의 수요를 예상하여 클라우드 컴퓨팅 리소스를 프로비저닝할 수 있는 기능입니다.

D. 마찰을 최소화하면서 비즈니스 연속성 이벤트로부터 복구할 수 있습니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
What does elasticity mean to AWS?

A. The ability to scale computing resources up easily, with minimal friction and down with latency.

B. The ability to scale computing resources up and down easily, with minimal friction.

C. The ability to provision cloud computing resources in expectation of future demand.

D. The ability to recover from business continuity events with minimal friction.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 


1차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional/view/2/)

