---
layout: post
title: "[AWS-SAA] Examtopics 51~60"
subtitle: AWS
date: '2022-06-11 21:50:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-11-[AWS-SAA]_ExamTopics_51~60/logo.png
---

SAA Examtopics 51~60번 문제를 풀어보자.<br>
1차 4/10<br>
2차 5/10<br>
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 51 ⭕❌

거대한 Amazon EC2 인스턴스 집합에서 기업은 애플리케이션을 실행합니다. 이 프로그램은 Amazon에서 호스팅하는 DynamoDB 데이터베이스에 항목을 읽고 씁니다. DynamoDB 데이터베이스의 크기는 정기적으로 증가하지만 애플리케이션에는 이전 30일 동안의 데이터만 필요합니다. 조직은 구현하기에 비용 효율적이고 시간 효율적인 솔루션이 필요합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. AWS CloudFormation 템플릿을 사용하여 전체 솔루션을 구축합니다. CloudFormation 스택을 30일마다 다시 배포하고 원래 스택을 삭제합니다.

B. AWS Marketplace에서 모니터링 응용 프로그램을 실행하는 EC2 인스턴스를 사용합니다. 테이블에 새 항목이 생성될 때 Amazon DynamoDB Streams를 사용하여 타임스탬프를 저장하도록 모니터링 응용 프로그램을 구성합니다. EC2 인스턴스에서 실행되는 스크립트를 사용하여 타임스탬프가 30일보다 오래된 항목을 삭제합니다.

C. 테이블에 새 항목이 생성될 때 AWS Lambda 함수를 호출하도록 Amazon DynamoDB Streams를 구성합니다. 30일이 지난 테이블의 항목을 삭제하도록 람다 기능을 구성합니다.

D. 응용 프로그램을 확장하여 현재 타임스탬프 값에 테이블에 생성되는 각 새 항목에 30일을 더한 속성을 추가합니다. 속성을 TTL 속성으로 사용하도록 DynamoDB를 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

D가 정답입니다. 
TTL(Amazon DynamoDB Time to Live)을 사용하면 항목별 타임스탬프를 정의하여 항목이 더 이상 필요하지 않은 시기를 결정할 수 있습니다. 
지정한 타임스탬프의 날짜 및 시간이 지나면 DynamoDB는 쓰기 처리량을 사용하지 않고 테이블에서 항목을 삭제합니다. TTL은 워크로드 요구사항에 맞게 최신 상태로 유지되는 항목만 유지하여 저장된 데이터 볼륨을 줄이기 위한 수단으로 추가 비용 없이 제공됩니다.

TTL은 특정 시간 후에 관련성이 손실된 항목을 저장할 때 유용합니다. 다음은 TTL 사용 사례의 예입니다.

응용 프로그램에서 1년 동안 사용하지 않은 사용자 또는 센서 데이터를 제거합니다.

만료된 항목을 Amazon DynamoDB Streams 및 AWS Lambda를 통해 Amazon S3 데이터 레이크에 아카이브합니다.

계약 또는 규제 의무에 따라 중요한 데이터를 일정 기간 동안 보관합니다.<br>
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/TTL.html

1차 시도 : D 맞음 <br>
2차 시도 : C 틀림 <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 52 ❓❓

이전에는 기업에서 데이터 웨어하우징 솔루션을 AWS로 이전했습니다. 또한 회사에는 AWS Direct Connect 연결이 있습니다. 회사 사무실의 사용자는 시각화 도구를 사용하여 데이터 웨어하우스를 쿼리할 수 있습니다. 데이터 웨어하우스에서 응답하는 각 쿼리의 크기는 평균 50MB인 반면 시각화 도구에서 제공하는 각 웹 페이지의 크기는 약 500KB입니다. 데이터 웨어하우스는 반환하는 결과 집합을 캐시하지 않습니다.

회사의 가장 낮은 발신 데이터 전송 비용을 초래하는 접근 방식은 무엇입니까?

A. 사내에서 시각화 도구를 호스팅하고 인터넷을 통해 직접 데이터 웨어하우스를 쿼리합니다.

B. 시각화 도구를 데이터 웨어하우스와 동일한 AWS 영역에 호스팅합니다. 인터넷을 통해 접속합니다.

C. 사내에서 시각화 도구를 호스팅하고 동일한 AWS 영역에 있는 Direct Connect 연결을 통해 직접 데이터 웨어하우스를 쿼리합니다.

D. 시각화 도구를 데이터 웨어하우스와 동일한 AWS 영역에 호스팅하고 동일한 영역의 위치에 있는 DirectConnect 연결을 통해 액세스합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Should be D<br>
https://aws.amazon.com/directconnect/pricing/<br>
https://aws.amazon.com/blogs/aws/aws-data-transfer-prices-reduced/

"Data transfer pricing over Direct Connect is lower than data transfer pricing over the internet"

A and B are out

I would take D over C as transfer from AWS to on-premises would cost more than transfer from AWS to AWS

1차 시도 : 모름<br>
2차 시도 : 모름<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 53 ❓❌

비즈니스에서 많은 마이크로서비스로 구성된 애플리케이션을 개발 중입니다. 조직은 컨테이너 기술을 통해 AWS에 소프트웨어를 배포하기로 결정했습니다. 비즈니스에는 유지 관리 및 성장을 위해 지속적인 작업이 거의 필요하지 않은 솔루션이 필요합니다. 추가 인프라는 비즈니스에서 관리할 수 없습니다.

이러한 요구 사항을 충족하기 위해 솔루션 설계자는 어떤 단계를 함께 수행해야 합니까? (2개를 선택하세요.)

A. Amazon ECS(Elastic Container Service) 클러스터를 배포합니다.

B. 여러 가용성 영역에 걸쳐 있는 Amazon EC2 인스턴스에 Kubernetes 컨트롤 플레인을 배포합니다.

C. Amazon EC2 시작 유형이 있는 Amazon ECS(Amazon Elastic Container Service) 서비스를 배포합니다. 2보다 크거나 같은 작업 번호 수준을 지정합니다.

D. Fargate 시작 유형이 있는 Amazon ECS(Elastic Container Service) 서비스를 배포합니다. 2보다 크거나 같은 작업 번호 수준을 지정합니다.

E. 여러 가용성 영역에 걸쳐 있는 Amazon EC2 인스턴스에 Kubernetes 작업자 노드를 배포합니다. 각 마이크로 서비스에 대해 둘 이상의 복제본을 지정하는 배포를 만듭니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, D

해설 : 

It should be A and D. <br>
The question repeatedly says managing infrastructure must not be an option so EC2 is off the topic. <br>
Also can user fargate with micro services without any issue. 

(https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/deploy-java-microservices-on-amazon-ecs-using-aws-fargate.html)


관리형 : EC2<br>
완전 관리형 : RDS, DynamoDB, ElastiCache, Redshift, SNS

1차 시도 : 모름 <br>
2차 시도 : 틀림 <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 54 ❌⭕

The following policy was developed by an Amazon EC2 administrator and assigned to an IAM group including numerous users:

![prob_54](/assets/img/study_AWS/2022-06-11-[AWS-SAA]_ExamTopics_51~60/prob_54.png)

What impact does this policy have?

A. 사용자는 us-east-1을 제외한 모든 AWS 영역에서 EC2 인스턴스를 종료할 수 있습니다.

B. 사용자는 us-east-1 영역에서 IP 주소가 10.100.100.1인 EC2 인스턴스를 종료할 수 있습니다.

C. 사용자의 원본 IP가 10.100.100.254일 때 사용자는 us-east-1 영역에서 EC2 인스턴스를 종료할 수 있습니다.

D. 사용자의 원본 IP가 10.100.100.254인 경우 사용자는 us-east-1 영역에서 EC2 인스턴스를 종료할 수 없습니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

10.100.100.1은 예약된 IP 주소이다.

0 : 네트워크 어드레스<br>
1 : VPC Router<br>
2 : DNS<br>
3 : Future use<br>
4 : Broadcast<br>

1차 시도 : B 틀림<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 55 ⭕⭕

비즈니스의 웹 애플리케이션은 데이터를 Amazon RDS PostgreSQL 데이터베이스 인스턴스에 저장합니다. 회계사는 결산 기간 중 매월 초에 대량 쿼리를 수행하며 과도한 활용으로 인해 데이터베이스 성능에 부정적인 영향을 미칩니다. 비즈니스는 온라인 지원에 대한 보고의 영향을 줄이기를 원합니다.

가능한 한 최소한의 작업으로 데이터베이스의 영향을 최소화하기 위해 솔루션 설계자는 무엇을 해야 합니까?

A. 읽기 복제본을 작성하고 복제본에 직접 트래픽을 보고합니다.

B. Multi-AZ 데이터베이스를 만들고 트래픽을 대기 상태로 전송합니다.

C. 교차 영역 읽기 복제본을 작성하고 복제본에 직접 트래픽을 보고합니다.

D. Amazon Redshift 데이터베이스를 생성하고 트래픽을 Amazon Redshift 데이터베이스로 직접 보고합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

An RDS read replica instance is an asynchronous read-only replica of a primary ("master") database instance located upstream. <br>
It can be used by your application for any query that does not require changing data, relieving the master of the load.

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 56 ❌⭕ 유념

한 기업이 Amazon RDS에 MySQL 데이터베이스를 구현했습니다. 데이터베이스 지원팀은 트랜잭션 증가로 인해 DB 인스턴스에 대한 읽기 지연이 발생했다고 보고하고 읽기 전용 복제본을 설치할 것을 권고하고 있습니다.

솔루션 설계자는 이 변경 사항을 배포하기 전에 어떤 활동을 수행해야 합니까? (2개를 선택하세요.)

A. RDS primary 노드에서 binlog 복제를 사용하도록 설정합니다.

B. 원본 DB 인스턴스에 대한 장애 조치 우선 순위를 선택합니다.

C. 원본 DB 인스턴스에서 장시간 실행되는 트랜잭션을 완료할 수 있게 허가합니다.

D. 글로벌 테이블을 만들고 테이블을 사용할 AWS 영역을 지정합니다.

E. 백업 보존 기간을 0이 아닌 값으로 설정하여 원본 인스턴스에서 자동 백업을 실행하십시오.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, E

해설 : 

"An active, long-running transaction can slow the process of creating the read replica. We recommend that you wait for long-running transactions to complete before creating a read replica. If you create multiple read replicas in parallel from the same source DB instance, Amazon RDS takes only one snapshot at the start of the first create action.

When creating a read replica, there are a few things to consider. First, you must enable automatic backups on the source DB instance by setting the backup retention period to a value other than 0. This requirement also applies to a read replica that is the source DB instance for another read replica"<br>
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html

1차 시도 : A, B
2차 시도 : C, E
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 57 ⭕⭕

사용자는 회사 웹사이트에서 과거 실적 보고서를 받을 수 있습니다. 웹 사이트에는 회사의 전세계 웹 사이트 요구 사항에 맞게 확장할 수 있는 솔루션이 필요합니다. 솔루션은 비용 효율적이고 인프라 리소스 프로비저닝을 최소화하며 실현 가능한 가장 빠른 반응 시간을 제공해야 합니다.

솔루션 설계자는 이러한 요구 사항을 충족하기 위해 어떤 기술 조합을 제안할 수 있습니까?

A. Amazon CloudFront and Amazon S3

B. AWS Lambda and Amazon DynamoDB

C. Application Load Balancer with Amazon EC2 Auto Scaling

D. Amazon Route 53 with internal Application Load Balancers

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

CloundFront와 S3의 조합은 신이다.

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 58 ❌⭕

솔루션 설계자는 Amazon Web Services(AWS) 클라우드에서 하이브리드 애플리케이션을 개발하고 있습니다. AWS Direct Link(DX)는 온프레미스 데이터 센터를 AWS에 연결하는 데 사용됩니다. AWS와 온프레미스 데이터 센터 간의 애플리케이션 연결은 매우 내구성이 있어야 합니다.

이러한 기준을 충족하려면 어떤 DX 설정을 사용해야 합니까?

A. VPN이 위에 있는 DX 연결을 구성합니다.

B. 여러 DX 위치에서 DX 연결을 구성합니다.

C. 가장 신뢰할 수 있는 DX 파트너를 사용하여 DX 연결을 구성합니다.

D. DX 연결 위에 여러 가상 인터페이스를 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Highly resilient, fault-tolerant network connections are key to a well-architected system. <br>
AWS recommends connecting from multiple data centers for physical location redundancy.

1차 시도 : A 틀림<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 59 ⭕❌

금융 기관은 AWS를 사용하여 웹 애플리케이션을 호스팅합니다. 이 프로그램은 Amazon API Gateway 지역 API 엔드포인트를 사용하여 현재 주가를 검색합니다. 조직의 보안 직원이 API 쿼리의 급증을 감지했습니다. 보안 팀은 HTTP flood 공격으로 인해 애플리케이션이 작동하지 않을 수 있다고 우려하고 있습니다.
솔루션 설계자는 이러한 형태의 공격에 대한 방어책을 만들어야 합니다.

다음 중 운영 오버헤드가 가장 적은 이 기준을 충족하는 방법은 무엇입니까?

A. API Gateway Regional API 엔드포인트 앞에 최대 TTL이 24시간인 Amazon CloudFront 배포를 생성합니다.

B. 속도 기반 규칙을 사용하여 지역 AWS WAF 웹 ACL을 만듭니다. 웹 ACL을 API 게이트웨이 단계에 연결합니다.

C. Amazon CloudWatch 메트릭을 사용하여 카운트 메트릭을 모니터링하고 미리 정의된 속도에 도달하면 보안 팀에 알립니다.

D. API Gateway Regional API 끝점 앞에 Lambda@Edge를 사용하여 Amazon CloudFront 배포를 생성합니다. 미리 정의된 속도를 초과하는 IP 주소의 요청을 차단하는 AWS Lambda 함수를 만듭니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Question is asking for DDoS protection<br>
This is a form of DDOS protection. So AWS WAF does the best with least efforts.<br>

API Gateway throttles requests by default (https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-request-throttling.html)

We need AWS Shield or WAF - https://aws.amazon.com/blogs/security/how-to-protect-dynamic-web-applications-against-ddos-attacks-by-using-amazon-cloudfront-and-amazon-route-53/

1차 시도 : B 맞음<br>
2차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 60 ❌❌

비즈니스에서 Amazon EC2 인스턴스의 보안 평가를 자동화하려고 합니다. 조직은 개발 프로세스가 보안 및 규정 준수 요구 사항을 준수하는지 확인하고 보여야 합니다.

이러한 기준이 충족되도록 솔루션 설계자는 어떤 조치를 취해야 합니까?

A. Amazon Macie를 사용하여 EC2 인스턴스를 자동으로 검색, 분류 및 보호할 수 있습니다.

B. Amazon GuardDuty를 사용하여 Amazon Simple Notification Service(Amazon SNS) 알림을 게시합니다.

C. Amazon CloudWatch와 함께 Amazon Inspector를 사용하여 Amazon Simple Notification Service(Amazon SNS) 알림 게시

D. Amazon EventBridge(Amazon CloudWatch Events)를 사용하여 AWS Trusted Advisor 확인의 상태 변화를 감지하고 대응합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Answer is C-Inspector.

Guard Duty:<br>
Aim is to analyze logs:<br>
-CloudTrail Logs: unusual API calls, unauthorized deployments<br>
-VPC Flow Logs: unusual internal traffic, unusual IP address<br>
-DNS Logs: compromised EC2 instances sending encoded data within DNS queries

Can protect against CryptoCurrency attacks (has a dedicated “finding” for it).<br>
It uses Machine Learning.

Macie helps identify and alert you to sensitive data, such as personally identifiable information (PII).<br>
Applies only for S3.

Inspector is specific to EC2.<br>
-Provides Automated Security Assessments for EC2 instances.<br>
-Requires agent installation on EC2 for Host(vulnerability assessment/best practices) OR can do NW Assessment for EC2 without installing agent

1차 시도 : B 틀림<br>
2차 시도 : D 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/6)