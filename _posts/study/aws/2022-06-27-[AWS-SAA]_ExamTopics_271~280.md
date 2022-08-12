---
layout: post
title: "[AWS-SAA] Examtopics 271~280"
subtitle: AWS
date: '2022-06-27 18:00:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-27-[AWS-SAA]_ExamTopics_271~280/logo.png
---

SAA Examtopics 271~280번 문제를 풀어보자.<br>
1차 6/10<br>
2차 5/10<br>
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 271 ⭕⭕

비즈니스에서 신용 카드 결제 처리를 위해 3계층 웹 애플리케이션을 운영하고 있습니다. 정적 웹 사이트는 프런트 엔드 사용자 인터페이스를 구성합니다. 애플리케이션 계층에는 긴 절차가 포함될 수 있습니다. MySQL은 데이터베이스 계층에서 사용됩니다.
현재 애플리케이션은 하나의 거대한 범용 Amazon EC2 머신에서 실행되고 있습니다. 솔루션 설계자는 웹 애플리케이션의 가용성을 극대화하기 위해 서비스를 분리해야 합니다.

다음 솔루션 중 가장 높은 수준의 가용성을 제공하는 솔루션은 무엇입니까?

A. Move static assets to Amazon CloudFront. Leave the application in EC2 in an Auto Scaling group. Move the database to Amazon RDS to deploy Multi-AZ.

B. Move static assets and the application into a medium EC2 instance. Leave the database on the large instance. Place both instances in an Auto Scaling group.

C. Move static assets to Amazon S3. Move the application to AWS Lambda with the concurrency limit set. Move the database to Amazon DynamoDB with on- demand enabled.

D. Move static assets to Amazon S3. Move the application to Amazon Elastic Container Service (Amazon ECS) containers with Auto Scaling enabled. Move the database to Amazon RDS to deploy Multi-AZ.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

D - Static assets to S3; ECS Autho Scaling; RDS Multi-AZ --> HA.

And C is eliminated because of the keyword 'lengthy procedures'.<br>
Lambda has max limit of 15 minutes.<br>
Concurrency limit only helps with no of parallel executions ,not duration.

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 272 ⭕⭕

기업의 보안 팀은 네트워크 트래픽이 VPC Flow Logs에 기록되기를 원합니다. 로그는 90일 동안 자주 조회된 후 삭제됩니다.

이러한 요구 사항을 충족하도록 로그를 사용자 지정할 때 솔루션 설계자는 무엇을 해야 합니까?

A. Use Amazon CloudWatch as the target. Set the CloudWatch log group with an expiration of 90 days.

B. Use Amazon Kinesis as the target. Configure the Kinesis stream to always retain the logs for 90 days.

C. Use AWS CloudTrail as the target. Configure CloudTrail to save to an Amazon S3 bucket, and enable S3 Intelligent-Tiering.

D. Use Amazon S3 as the target. Enable an S3 Lifecycle policy to transition the logs to S3 Standard-Infrequent Access (S3 Standard-IA) after 90 days.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

문제가 좀 이상한듯?

문제 원문 :<br>
The security team of a corporation wants that network traffic be logged in VPC Flow Logs. The logs will be viewed often for 90 days and then deleted.
occasionally.

What should a solutions architect do when customizing the logs to satisfy these requirements?

뒤에 ocassionally가 단독으로 나온 의미가 무엇인가?<br>
그냥 삭제되는거라면 A가 맞을 것.<br>
가끔 삭제되는 거라면 D가 맞을 것.<br>
하지만 ocassionally를 무시하고 A를 고르는게 합리적으로 보임.

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 273 ⭕⭕

Amazon S3는 솔루션 설계자가 새로운 디지털 미디어 애플리케이션을 위한 스토리지 아키텍처를 개발하는 데 사용하고 있습니다. 미디어 파일은 가용 영역에 장애가 발생한 경우에도 견고해야 합니다. 특정 파일은 일상적으로 방문하는 반면 다른 파일은 드물게 예기치 않은 방식으로 조회됩니다. 솔루션 설계자는 미디어 파일을 저장하고 검색하는 비용을 최소화해야 합니다.

이러한 기준을 충족하는 스토리지 선택은 무엇입니까?

A. S3 Standard

B. S3 Intelligent-Tiering

C. S3 Standard-Infrequent Access (S3 Standard-IA)

D. S3 One Zone-Infrequent Access (S3 One Zone-IA)

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

S3 Intelligent-Tiering - Perfect use case when you don't know the frequency of access or irregular patterns of usage.

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 274 ❌❌

월별 보고서는 회사의 재무 애플리케이션에서 Amazon S3 버킷에 저장합니다. 재무 담당 부사장은 이러한 보고서에 대한 모든 액세스와 로그 파일에 대한 조정을 문서화하도록 지시했습니다.

솔루션 설계자는 이러한 요구 사항을 준수하기 위해 어떤 활동을 수행할 수 있습니까?

A. Use S3 server access logging on the bucket that houses the reports with the read and write data events and log file validation options enabled.

B. Use S3 server access logging on the bucket that houses the reports with the read and write management events and log file validation options enabled.

C. Use AWS CloudTrail to create a new trail. Configure the trail to log read and write data events on the S3 bucket that houses the reports. Log these events to a new bucket, and enable log file validation.

D. Use AWS CloudTrail to create a new trail. Configure the trail to log read and write management events on the S3 bucket that houses the reports. Log these events to a new bucket, and enable log file validation.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

C is the right answer because the question specifically asking logs for following events.
Access, modifications and deletions which are all DATA EVENTS.


1차 시도 : D 틀림<br>
1차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 275 ⭕❌

온라인 게임을 전문으로 하는 비즈니스는 전 세계적으로 매우 인기가 있을 것으로 예상되는 게임을 개발하고 있습니다. 솔루션 설계자는 각 참가자의 게임 데이터는 물론 세계 상위 25명의 플레이어 이름을 한 번에 캡처하고 표시할 수 있는 AWS 클라우드 아키텍처를 생성해야 합니다.

이러한 요구 사항을 충족하려면 어떤 AWS 데이터베이스 솔루션 및 구성을 사용해야 합니까?

A. Use Amazon RDS for MySQL as the data store for player activity. Configure the RDS DB instance for Multi-AZ support.

B. Use Amazon DynamoDB as the data store for player activity. Configure DynamoDB Accelerator (DAX) for the player data.

C. Use Amazon DynamoDB as the data store for player activity. Configure global tables in each required AWS Region for the player data.

D. Use Amazon RDS for MySQL as the data store for player activity. Configure cross-Region read replicas in each required AWS Region based on player proximity.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Answer should be (C). Since we are talking about providing a game that is popular around the world to provide near-real-time recording, we want to use DynamoDB and use global tables to replicate the player data with consistency providing single-digit-millisecond latency.


1차 시도 : C 맞음<br>
2차 시도 : D 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 276 ⭕❌ 유념

한 기업에서 사용자가 실시간 게임 통계에 참여할 수 있는 서버리스 웹 애플리케이션을 구축하고 있습니다. 게임에서 생성된 데이터는 라이브로 전송되어야 합니다. 비즈니스에는 사용자 데이터를 위한 강력하고 대기 시간이 짧은 데이터베이스 솔루션이 필요합니다. 회사는 응용 프로그램의 예상 사용자 기반에 대해 확신하지 못합니다. 모든 설계 고려 사항은 애플리케이션이 성장함에 따라 한 자릿수 밀리초 응답 속도를 보장해야 합니다.

이러한 요구 사항에 맞는 AWS 서비스 조합은 무엇입니까? (2개를 선택하세요.)

A. Amazon CloudFront

B. Amazon DynamoDB

C. Amazon Kinesis

D. Amazon RDS

E. AWS Global Accelerator

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, C

해설 : 

kinesis = think real time, dynamodb = serverless

1차 시도 : B, C 맞음<br>
2차 시도 : A, B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 277 ❌⭕

솔루션 설계자는 사용자가 사진 모음을 탐색하고 사용자 지정 이미지를 요청할 수 있는 솔루션을 개발하고 있습니다. 이미지 사용자 지정을 위한 파라미터는 AWS API Gateway API에 대한 각 요청에 포함됩니다. 맞춤형 사진은 요청 시 생성되며 소비자는 이를 보거나 다운로드할 수 있는 링크를 받게 됩니다. 솔루션은 사진을 보고 수정하는 측면에서 매우 사용자 친화적이어야 합니다.

이러한 요구 사항을 충족하는 데 가장 비용 효율적인 접근 방식은 무엇입니까?

A. Use Amazon EC2 instances to manipulate the original image into the requested customizations. Store the original and manipulated images in Amazon S3. Configure an Elastic Load Balancer in front of the EC2 instances.

B. Use AWS Lambda to manipulate the original image to the requested customizations. Store the original and manipulated images in Amazon S3. Configure an Amazon CloudFront distribution with the S3 bucket as the origin.

C. Use AWS Lambda to manipulate the original image to the requested customizations. Store the original images in Amazon S3 and the manipulated images in Amazon DynamoDB. Configure an Elastic Load Balancer in front of the Amazon EC2 instances.

D. Use Amazon EC2 instances to manipulate the original image into the requested customizations. Store the original images in Amazon S3 and the manipulated images in Amazon DynamoDB. Configure an Amazon CloudFront distribution with the S3 bucket as the origin.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

ELIMINATING THE ANSWERS

So the important parts in the question is:
- there's a need for a service which can do image the manipulation
- original and processed image should be stored somewhere
- solution must be highly-available and cost-effective

When we see cost-effective, this would immediately rule out any option that has EC2 instances as instances incur much higher cost.<br>
So rule out A and D, which leaves us with B and C.

Now if you'll read closely, option C has an EC2 instance and an ELB as well, which makes it more pricey. <br>
So this option can be eliminated too.

Now to verify if option does solve the requirement:

Lambda can do the manipulation. It is also cost-effective as you only pay when your function is running. <br>
It also scales well as demand increases/decreases.

Both the original and processed images can be stored in S3, but in different buckets. <br>
This is a highly-available service and also scalable.

CloudFront makes it easy to deliver the images to the user through the use of it's multiple Edge locations.

Correct answer: B

1차 시도 : C 틀림<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 278 ❌⭕

기업은 프라이빗 서브넷에서 Amazon EC2 인스턴스를 실행하고 패치 및 업그레이드를 받으려면 퍼블릭 웹사이트에 액세스해야 합니다. 조직은 다른 웹사이트가 EC2 인스턴스의 IP 주소를 보거나 연결을 시작하는 것을 원하지 않습니다.

솔루션 설계자는 이 목표를 어떻게 달성할 수 있습니까?

A. Create a site-to-site VPN connection between the private subnet and the network in which the public site is deployed.

B. Create a NAT gateway in a public subnet. Route outbound traffic from the private subnet through the NAT gateway.

C. Create a network ACL for the private subnet where the EC2 instance deployed only allows access from the IP address range of the public website.

D. Create a security group that only allows connections from the IP address range of the public website. Attach the security group to the EC2 instance.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Typical requirement for Nat Gateway. So answer is B.

왠지 site-to-site VPN 이라는 이름이 딱 맞아 보였다 ...<br>
문항들을 보기도 전에 NAT Gateway를 떠올렸는데 아쉽다.

1차 시도 : A 틀림<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 279 ⭕❌

비즈니스는 AWS를 사용하여 웹 사이트를 호스팅합니다. 웹 사이트는 HTTP 및 HTTPS 트래픽을 독립적으로 관리하도록 구성된 ALB(Application Load Balancer)에 의해 보호됩니다.
회사는 HTTPS를 통해 모든 쿼리를 웹사이트로 라우팅하려고 합니다.

솔루션 설계자는 이 기준을 충족하기 위해 어떤 솔루션을 구현해야 합니까?

A. Update the ALB's network ACL to accept only HTTPS traffic.

B. Create a rule that replaces the HTTP in the URL with HTTPS.

C. Create a listener rule on the ALB to redirect HTTP traffic to HTTPS.

D. Replace the ALB with a Network Load Balancer configured to use Server Name Indication (SNI).

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

HTTP 요청을 HTTPS로 리디렉션하는 HTTP 리스너 규칙을 생성할 수 있다.<br>
[참조 링크](https://aws.amazon.com/ko/premiumsupport/knowledge-center/elb-redirect-http-to-https-using-alb/)

1차 시도 : C 맞음<br>
2차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 280 ❌❌

기업은 ALB(Application Load Balancer)로 보호되는 Amazon EC2 인스턴스 집합을 사용하여 다국어 웹 사이트를 호스팅합니다. 이 설계는 현재 us-west-1 지역에서 작동하고 있지만 전 세계 다른 지역의 고객에게는 상당한 요청 지연이 있습니다.
웹사이트는 위치에 관계없이 사용자 쿼리에 빠르고 효과적으로 응답해야 합니다. 그러나 조직은 현재 인프라를 여러 지역에 복제하는 것을 원하지 않습니다.

솔루션 아키텍트가 이 작업을 어떻게 수행합니까?

A. Replace the existing architecture with a website served from an Amazon S3 bucket. Configure an Amazon CloudFront distribution with the S3 bucket as the origin.

B. Configure an Amazon CloudFront distribution with the ALB as the origin. Set the cache behavior settings to only cache based on the Accept-Language request header.

C. Set up Amazon API Gateway with the ALB as an integration. Configure API Gateway to use an HTTP integration type. Set up an API Gateway stage to enable the API cache.

D. Launch an EC2 instance in each additional Region and configure NGINX to act as a cache server for that Region. Put all the instances plus the ALB behind an Amazon Route 53 record set with a geolocation routing policy.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

If you want CloudFront to cache different versions of your objects based on the language specified in the request, configure CloudFront to forward the Accept-Language header to your origin.

world wide users -> CF<br>
multi-language -> Accept-Language Request Header.<br>
Does not recreate -> Not A (Replace) - 이 해설은 납득되지 않음. 문제에서는 현재 인프라를 재구축하면 안된다는 것이 아니라 다른 지역에 인프라를 복제하지 않기를 원하고 있음.

1차 시도 : A 틀림<br>
2차 시도 : A 틀림<br>
</div>
</details>


<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/28)
