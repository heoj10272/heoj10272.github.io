---
layout: post
title: "[AWS-SAP] ExamTopics 411~420 구버전"
subtitle: AWS
date: '2022-08-13 04:00:00 +0900'
category: study
tags: aws examtopics sap-c01
image:
  path: /assets/img/study_AWS/2022-08-13-[AWS-SAP]_ExamTopics_411~420_구버전/logo.png
---

SAP Examtopics 411~420번 문제를 풀어보자.<br>
1차 3/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 411 ❓

Solutions Architect는 휴대폰 플랫폼에서 실행되는 성공적인 전세계 비디오 게임을 위해 고가용성 인프라를 개발하는 책임을 지고 있습니다. 애플리케이션은 애플리케이션 로드 밸런서를 통해 라우팅되는 Amazon EC2 인스턴스에 배포됩니다. 인스턴스는 자동 스케일링 그룹의 여러 가용성 영역에 분산됩니다. Amazon RDS MySQL Multi-AZ 인스턴스는 데이터베이스 계층 역할을 합니다. us-east-1과 eu-central-1 모두에서 전체 애플리케이션 스택이 배포됩니다. 지연 시간 기반 라우팅 전략을 사용하여 Amazon Route 53은 두 개의 설치로 트래픽을 라우팅합니다. Route 53에서는 한 지역의 설치가 응답하지 않을 경우 다른 지역으로의 장애 조치로서 가중 라우팅 정책이 구현됩니다.
재해 복구 테스트 중에 해당 영역에서 작동하는 모든 애플리케이션 인스턴스에서 eu-central-1의 Amazon RDS MySQL 인스턴스에 대한 액세스를 제한한 후입니다. 53번 도로는 us-east-1로 가는 모든 트래픽을 자동으로 페일오버하지 않습니다.

이러한 상황에서 인프라를 us-east-1로 페일오버할 수 있는 조정은 무엇입니까? (2개 선택)

A. Specify a weight of 100 for the record pointing to the primary Application Load Balancer in us-east-1 and a weight of 60 for the pointing to the primary Application Load Balancer in eu-central-1.

B. Specify a weight of 100 for the record pointing to the primary Application Load Balancer in us-east-1 and a weight of 0 for the record pointing to the primary Application Load Balancer in eu-central-1.

C. Set the value of Evaluate Target Health to Yes on the latency alias resources for both eu-central-1 and us-east-1.

D. Write a URL in the application that performs a health check on the database layer. Add it as a health check within the weighted routing policy in both regions.

E. Disable any existing health checks for the resources in the policies and set a weight of 0 for the records pointing to primary in both eu-central-1 and us-east-1, and set a weight of 100 for the primary Application Load Balancer only in the region that has healthy resources.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, D 비율 100%인데 B, C라는 의견도 있음

해설 : 


1차 시도 : 모르겠음 <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 412 ❓

기업은 애플리케이션 API의 일부를 Amazon EC2 인스턴스에서 서버리스 환경으로 이전하고 있습니다. 새로운 애플리케이션에는 Amazon API Gateway, AWS Lamda 및 Amazon DynamoDB를 사용했습니다. 람다 함수의 주요 작업은 타사 SaaS(Software as a Service) 공급자로부터 데이터를 가져오는 것입니다. 람다 함수는 일관성을 위해 원래 EC2 인스턴스와 동일한 VPC(Virtual Private Cloud)에 연결됩니다.
테스트 사용자가 새로 재배치된 기능에 액세스할 수 없다고 보고하고 조직에 API Gateway 5xx 문제가 발생하고 있습니다. SaaS 공급자의 모니터링 레코드는 쿼리가 해당 시스템에 도달하지 않았음을 나타냅니다. 조직은 람다 서비스가 Amazon CloudWatch 로그를 생성하고 있음을 발견했습니다. Amazon EC2 인스턴스에서 동일한 기능을 테스트하면 올바르게 작동합니다.

문제의 원인은 무엇입니까?

A. Lambda is in a subnet that does not have a NAT gateway attached to it to connect to the SaaS provider.

B. The end-user application is misconfigured to continue using the endpoint backed by EC2 instances.

C. The throttle limit set on API Gateway is too low and the requests are not making their way through.

D. API Gateway does not have the necessary permissions to invoke Lambda.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, D 중에 뭐가 답인지 확신이 서지 않음.

해설 : 

[Discussion](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional/view/42/) 참조

1차 시도 : D <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 413 ⭕

기업에는 100개 이상의 AWS 계정이 있으며, 각 계정이 자체 VPC를 가지고 있으며, 이 계정에는 인터넷에 대한 아웃바운드 HTTPS 통신이 필요합니다. 현재 각 VPC에는 AZ(Availability Zone)당 하나의 NAT 게이트웨이가 있습니다. 비용을 절감하고 외부 트래픽에 대한 가시성을 확보하기 위해 경영진은 새로운 인터넷 액세스 아키텍처를 요청했습니다.

기존 요구사항을 충족하고 더 많은 계정을 제공하면서 비용을 절감하는 솔루션은 무엇입니까?

A. Create a transit VPC across two AZs using a third-party routing appliance. Create a VPN connection to each VPC. Default route internet traffic to the transit VPC.

B. Create multiple hosted-private AWS Direct Connect VIFs, one per account, each with a Direct Connect gateway. Default route internet traffic back to an on- premises router to route to the internet.

C. Create a central VPC for outbound internet traffic. Use VPC peering to default route to a set of redundant NAT gateway in the central VPC.

D. Create a proxy fleet in a central VPC account. Create an AWS PrivateLink endpoint service in the central VPC. Use PrivateLink interface for internet connectivity through the proxy fleet.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Answer is: "D"<br>
user proxy fleet over PrivateLink. As explained in this AWS website:
https://aws.amazon.com/blogs/networking-and-content-delivery/how-to-use-aws-privatelink-to-secure-and-scale-web-filtering-using-explicit-proxy/<br>
A: does not provide a full solution, only showing transit VPC, and VPN but without the exiting solution to internet. Also, it is a costly solution.<br>
B: This would work, but it will send traffic to on-premise, and the question does not show that the company is having on-premise network!<br>
C: can not work, because VPC-Peering can not be used for transit traffic over Net Gateway.<br>

D<br>
A: You can use VPC peering, there is no need to use VPN.<br>
B: This will create unnecessary load on the Direct Connect and your on premise internet connection.<br>
C: You cannot route traffic to a NAT gateway through a VPC peering connection, a Site-to-Site VPN connection, or AWS Direct Connect. A NAT gateway cannot be used by resources on the other side of these connections. https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html<br>
D: https://aws.amazon.com/blogs/networking-and-content-delivery/how-to-use-aws-privatelink-to-secure-and-scale-web-filtering-using-explicit-proxy/<br>

No one explained why A is incorrect properly. So let me do that. The method in A is valid, however it is far more expensive than D. Cause VPN traffic between VPCs traverses internet which is AWS to Internet traffic. And that is more expensive then D.

`proxy fleet`에 대해서 공부해보자.
1차 시도 : D <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 414 ❌

A 기업은 많은 AWS 계정을 가지고 있습니다. 개발 팀은 현재 클라우드 거버넌스 및 교정 절차를 자동화하기 위해 노력하고 있습니다. 자동화 프레임워크는 중앙에서 관리되는 AWS 람다 서비스를 사용합니다. 솔루션 설계자는 회사의 각 AWS 계정에서 람다 함수가 최소한의 권한으로 실행될 수 있도록 하는 정책을 개발해야 합니다.

어떤 조치의 조합이 이러한 기준을 충족합니까? (2개를 선택합니다.)

A. In the centralized account, create an IAM role that has the Lambda service as a trusted entity. Add an inline policy to assume the roles of the other AWS accounts.

B. In the other AWS accounts, create an IAM role that has minimal permissions. Add the centralized account's Lambda IAM role as a trusted entity.

C. In the centralized account, create an IAM role that has roles of the other accounts as trusted entities. Provide minimal permissions.

D. In the other AWS accounts, create an IAM role that has permissions to assume the role of the centralized account. Add the Lambda service as a trusted entity.

E. In the other AWS accounts, create an IAM role that has minimal permissions. Add the Lambda service as a trusted entity.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B

해설 : 

AB - create a role that assumes a role in other account - need to add a trust entity for it

Create a role in central account for Lambda and allow it to assume roles in other acc.<br>
In other accounts create a role with trusted policy for a role in central account and give it actual permissions.

Lambda function located in centralized account - Lambda execution roles should assume a role in Managed accounts.<br>
Managed Account IAM role should have minimum permission and lambda execution role as trusted entity.

1차 시도 : C, D 틀림, 모르겠음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 415 ❌

A 기업은 주문 시스템을 위해 이벤트 중심 아키텍처를 채택했습니다. 시스템이 첫 번째 테스트 중에 주문 처리를 중지했습니다. 추가 로그 검사 결과 Amazon SQS(Amazon SQS) 표준 대기열의 단일 주문 메시지가 백엔드 문제를 트리거하고 추가 주문 메시지가 처리되지 않는 것으로 나타났습니다. 대기열의 가시성 시간 초과는 30초이고 백엔드 처리 시간 초과는 10초입니다. 솔루션 설계자는 잘못된 주문 메시지를 평가하고 후속 메시지가 시스템에서 처리되도록 보장해야 합니다.

솔루션 설계자는 이러한 요구사항을 충족하기 위해 어떤 접근 방식을 사용해야 합니까?

A. Increase the backend processing timeout to 30 seconds to match the visibility timeout.

B. Reduce the visibility timeout of the queue to automatically remove the faulty message.

C. Configure a new SQS FIFO queue as a dead-letter queue to isolate the faulty messages.

D. Configure a new SQS standard queue as a dead-letter queue to isolate the faulty messages.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

You need a dead-letter queue with a type that matches the queue. So a DLQ for a standard queue must be a standard queue. Hence D.<br>
Ref: https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html

`dead-letter queue`가 faulty messages를 처리할 수 있다고 한다.<br>
`dead-letter queue`에 대해 공부해보자.

1차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 416 ❌

한 기업이 최대한 짧은 복구 시간(RTO)의 목표를 충족하기 위해 애플리케이션이 온프레미스 및 AWS에서 작동하는 다중 사이트 솔루션(multi-site solution)을 구현하고 있습니다.

다음 구성 중 다중 사이트 솔루션과 관련된 시나리오의 기준과 일치하지 않는 구성은 무엇입니까?

A. Configure data replication based on RTO.

B. Keep an application running on premise as well as in AWS with full capacity.

C. Setup a single DB instance which will be accessed by both sites.

D. Setup a weighted DNS service like Route 53 to route traffic across sites.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Question is about multi site solution where you need one to one copy of your infrastructure that's why its C only one site db will not work

We talk about disaster recovery system design. Single DB has HA issue.

1차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 417 ⭕

A사는 사내 인프라에서 AWS 클라우드로 앱을 이전하고 있습니다. 이러한 앱은 회사 내부 웹 양식의 토대 역할을 합니다. 이러한 온라인 양식은 분기별로 특정 사건에 대한 데이터를 수집합니다. 간단한 SQL 문은 웹 양식을 사용하여 로컬 관계형 데이터베이스에 데이터를 저장하는 데 사용됩니다.
각 이벤트는 데이터를 생성하며, 대부분의 시간 동안 온프레미스 서버는 유휴 상태로 유지됩니다. 회사의 목표는 온라인 양식을 지원하는 유휴 인프라의 양을 줄이는 것입니다.

어떤 솔루션이 이러한 기준을 충족시킬까요?

A. Use Amazon EC2 Image Builder to create AMIs for the legacy servers. Use the AMIs to provision EC2 instances to recreate the applications in the AWS Cloud. Place an Application Load Balancer (ALB) in front of the EC2 instances. Use Amazon Route 53 to point the DNS names of the web forms to the ALB.

B. Create one Amazon DynamoDB table to store data for all the data input. Use the application form name as the table key to distinguish data items. Create an Amazon Kinesis data stream to receive the data input and store the input in DynamoDB. Use Amazon Route 53 to point the DNS names of the web forms to the Kinesis data stream's endpoint.

C. Create Docker images for each server of the legacy web form applications. Create an Amazon Elastic Container Service (Amazon EC2) cluster on AWS Fargate. Place an Application Load Balancer in front of the ECS cluster. Use Fargate task storage to store the web form data.

D. Provision an Amazon Aurora Serverless cluster. Build multiple schemas for each web form's data storage. Use Amazon API Gateway and an AWS Lambda function to recreate the data input forms. Use Amazon Route 53 to point the DNS names of the web forms to their corresponding API Gateway endpoint.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Serverless API + Serverless Business Logic + Serverless DB

Because of "respond to each event" and "minimize the amount of idle infrastructure"

Main point is "The company's goal should be to reduce the quantity of idle infrastructure supporting online forms." => serverless or scheduled autoscaling, but has no option about autoscaling => answer is D

1차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 418 ❌

결과적으로 AWS 데이터 파이프라인 작업 중 하나가 실패하고 세 번 재시도한 후 하드 오류 상태에 도달했습니다.
당신은 그것을 다시 시도하고 싶습니다.

자동 재시도 횟수를 3회 이상으로 늘릴 수 있습니까?

A. Yes, you can increase the number of automatic retries to 6.

B. Yes, you can increase the number of automatic retries to indefinite number.

C. No, you cannot increase the number of automatic retries.

D. Yes, you can increase the number of automatic retries to 10.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

An activity fails if all of its activity attempts return with a failed state. By default, an activity retries three times before entering a hard failure state. You can increase the number of automatic retries to 10; however, the system does not allow indefinite retries. After an activity exhausts its attempts, it triggers any configured onFailure alarm and will not try to run again unless you manually issue a rerun command via the CLI, API, or console button.


1차 시도 : A? 모름 <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 419 ❌

기업은 단일 지역 사용자에게 서비스를 제공하는 애플리케이션 워크로드를 처리하기 위해 다중 계정 AWS 환경에 대한 연결을 준비하고 있습니다. 워크로드는 가용성이 높고 두 사이트에 분산되어 있는 사내 레거시 시스템에 의존합니다. 레거시 시스템에 대한 연결은 AWS 워크로드에 중요하며 최소 5Gbps의 대역폭이 필요합니다. 모든 AWS 애플리케이션 워크로드를 서로 연결해야 합니다.

어떤 솔루션이 이러한 기준을 충족시킬까요?

A. Configure multiple AWS Direct Connect (DX) 10 Gbps dedicated connections from a DX partner for each on-premises location. Create private virtual interfaces on each connection for each AWS account VPC. Associate the private virtual interface with a virtual private gateway attached to each VPC.

B. Configure multiple AWS Direct Connect (DX) 10 Gbps dedicated connections from two DX partners for each on-premises location. Create and attach a virtual private gateway for each AWS account VPC. Create a DX gateway in a central network account and associate it with the virtual private gateways. Create a public virtual interface on each DX connection and associate the interface with the DX gateway.

C. Configure multiple AWS Direct Connect (DX) 10 Gbps dedicated connections from two DX partners for each on-premises location. Create a transit gateway and a DX gateway in a central network account. Create a transit virtual interface for each DX interface and associate them with the DX gateway. Create a gateway association between the DX gateway and the transit gateway.

D. Configure multiple AWS Direct Connect (DX) 10 Gbps dedicated connections from a DX partner for each on-premises location. Create and attach a virtual private gateway for each AWS account VPC. Create a transit gateway in a central network account and associate it with the virtual private gateways. Create a transit virtual interface on each DX connection and attach the interface to the transit gateway.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

A - no, there is no connection between VPCs.<br>
B - no, bcz DX gateway doesn't support routing from one VPN to another ( https://docs.aws.amazon.com/directconnect/latest/UserGuide/direct-connect-gateways-intro.html )<br>
C - right answer. https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/aws-direct-connect-aws-transit-gateway.html<br>
D - no, you can not connect Direct Connect to the Transit gateway without Direct Connect gateway in the middle.

1차 시도 : D 틀림 <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 420 ⭕

Solutions Architect는 70TB의 정적 파일을 포함하고 공개 오픈 데이터 프로젝트를 지원하는 데 사용되는 기존 사내 웹 애플리케이션을 마이그레이션하는 업무를 담당합니다. 마이그레이션 프로세스의 일부로, 설계자는 호스트 운영 체제의 최신 버전으로 업데이트하려고 합니다.

가장 빠르고 비용 효율적인 마이그레이션 방법은 무엇입니까?

A. Run a physical-to-virtual conversion on the application server. Transfer the server image over the internet, and transfer the static data to Amazon S3.

B. Run a physical-to-virtual conversion on the application server. Transfer the server image over AWS Direct Connect, and transfer the static data to Amazon S3.

C. Re-platform the server to Amazon EC2, and use AWS Snowball to transfer the static data to Amazon S3.

D. Re-platform the server by using the AWS Server Migration Service to move the code and data to a new Amazon EC2 instance.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 


1차 시도 : C 맞음 <br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional/view/42/)

