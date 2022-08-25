---
layout: post
title: "[AWS-SAP] ExamTopics 401~410 구버전"
subtitle: AWS
date: '2022-08-13 04:00:00 +0900'
category: study
tags: aws examtopics sap-c01
image:
  path: /assets/img/study_AWS/2022-08-13-[AWS-SAP]_ExamTopics_401~410_구버전/logo.png
---

SAP Examtopics 401~410번 문제를 풀어보자.<br>
1차 6/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 401 ❌

한 인사말 카드 회사는 최근 고객들이 회사의 플랫폼을 사용하여 그들이 좋아하는 연예인들에게 카드를 보낼 수 있다고 광고했습니다. 광고가 공개된 이후, 이 사이트는 매초마다 10,000명의 고유 사용자들로부터 지속적으로 트래픽을 수신하고 있습니다.
플랫폼은 m5.xlarge로 구동됩니다. 애플리케이션 로드 밸런서 뒤에 Amazon EC2 인스턴스(ALB)가 있습니다. 인스턴스는 자동 확장 그룹에 속하며 Amazon Linux 기반 사용자 지정 AMI에서 작동합니다. 이 플랫폼은 접근성이 높은 메인 및 리더 엔드포인트가 있는 Amazon Aurora MySQL DB 클러스터를 사용합니다. 또한 플랫폼에서는 클러스터 끝점을 통해 액세스할 수 있는 Redis용 Amazon ElastiCache 클러스터를 사용합니다.
각 클라이언트에는 고유한 프로세스가 할당되며, 플랫폼은 고객의 세션 기간 동안 MySQL에 대한 개방형 데이터베이스 연결을 유지합니다. 그러나 플랫폼은 리소스를 거의 소비하지 않습니다.
플랫폼에 연결하는 동안 수많은 클라이언트가 연결 문제를 겪고 있습니다. 로그에 표시된 것처럼 Aurora 데이터베이스에 대한 연결이 실패합니다. Amazon CloudWatch 데이터는 플랫폼의 CPU 로드가 최소이며 ALB를 통해 플랫폼에 대한 연결이 성공적으로 설정되었음을 나타냅니다.

오류를 가장 효과적으로 해결할 수 있는 옵션은 무엇입니까?

A. Amazon CloudFront 배포를 설정합니다. ALB를 오리진으로 설정합니다. 모든 고객 트래픽을 CloudFront 배포 끝점으로 이동합니다.

B. Amazon RDS Proxy를 사용합니다. 프록시를 사용하도록 데이터베이스 연결을 다시 구성하십시오.

C. Aurora MySQL 클러스터의 판독기 노드 수를 늘립니다.

D. Redis용 ElastiCache 클러스터의 노드 수를 늘립니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

[RDS Proxy](https://heoj10272.github.io/study/AWS-_Amazon_RDS_%EC%9D%B4%ED%95%B4.html#rds-proxy)를 사용해야 하는 경우이다.

1차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 402 ⭕

한 기업은 인적 자원(HR) 부서에 가상 사설 클라우드(VPC)를, 다른 기업은 행정(Admin) 부서에 가상 사설 클라우드(VPC)를 보유하고 있습니다. HR은 Admin VPC에서 작동하는 모든 인스턴스에 대한 액세스 권한이 필요한 반면, Admin 부서에서는 모든 HR 리소스에 대한 액세스 권한이 필요합니다.

이 상황이 조직 내부에서 어떻게 나타날 수 있을까요?

A. Setup VPC peering between the VPCs of Admin and HR.

B. Setup ACL with both VPCs which will allow traffic from the CIDR of the other VPC.

C. Setup the security group with each VPC which allows traffic from the CIDR of another VPC.

D. It is not possible to connect resources of one VPC from another VPC.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

쉬운 문제.<br>
`VPC Peering`을 통해 VPC간의 연결을 활성화 할 수 있다.

1차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 403 ❌

미국에 본사를 둔 한 회사가 유럽에서 사업을 매입했습니다. 두 기업 모두 AWS 클라우드에 의존합니다. 미국의 회사는 마이크로 서비스 아키텍처를 사용하여 새로운 애플리케이션을 개발했습니다. 미국에 본사를 둔 이 회사는 us-east-2 지역에 있는 5개의 VPC(Virtual Private Cloud)에서 애플리케이션을 호스팅합니다. 애플리케이션은 eu-west-1 영역의 단일 VPC에 포함된 리소스에 액세스할 수 있어야 합니다. 그러나 애플리케이션이 다른 VPC에 액세스할 수 없어야 합니다.

모든 지역의 VPC 간에 겹치는 CIDR 범위가 없습니다. AWS 조직에서는 모든 계정이 이미 단일 조직으로 통합되었습니다.

이러한 요구사항을 충족하는 데 가장 비용 효율적인 접근 방식은 무엇입니까?

A. Create one transit gateway in eu-west-1. Attach the VPCs in us-east-2 and the VPC in eu-west-1 to the transit gateway. Create the necessary route entries in each VPC so that the traffic is routed through the transit gateway.

B. Create one transit gateway in each Region. Attach the involved subnets to the regional transit gateway. Create the necessary route entries in the associated route tables for each subnet so that the traffic is routed through the regional transit gateway. Peer the two transit gateways.

C. Create a full mesh VPC peering connection configuration between all the VPCs. Create the necessary route entries in each VPC so that the traffic is routed through the VPC peering connection.

D. Create one VPC peering connection for each VPC in us-east-2 to the VPC in eu-west-1. Create the necessary route entries in each VPC so that the traffic is routed through the VPC peering connection.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

D - is the most cost effective

A - not possible you cant attach VPCs from multi-regions to one transit GW<br>
B - Can work but not cost effective you pay every hour for a transit GW attachments<br>
C - Can work but no need for full mesh, the requirement is for one VPC<br>

생각보다 `VPC peering`이 답이 되는 경우가 많은 것 같다.<br>
`transit GW`에 대해 다시 공부해보자.

1차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 404 ❌

여러 사업 부문이 거대한 글로벌 금융 서비스 법인으로 구성되어 있습니다. 조직은 개발자가 새로운 서비스를 실험하도록 권장하고 싶지만, 다양한 워크로드에 대한 규정 준수 요구 사항이 많습니다. 보안 팀은 사내 및 AWS 액세스 전략에 대해 우려하고 있습니다. 이들은 비즈니스 팀이 PCI(Payment Card Industry) 규정 준수와 같은 규제 워크로드를 관리하기 위해 사용하는 AWS 서비스에 대한 제어 권한을 부여하고자 합니다.

개발자가 새로운 서비스를 실험할 수 있도록 하는 동시에 보안 팀의 우려를 완화시킬 수 있는 옵션은 무엇입니까?

A. Implement a strong identity and access management model that includes users, groups, and roles in various AWS accounts. Ensure that centralized AWS CloudTrail logging is enabled to detect anomalies. Build automation with AWS Lambda to tear down unapproved AWS resources for governance.

B. Build a multi-account strategy based on business units, environments, and specific regulatory requirements. Implement SAML-based federation across all AWS accounts with an on-premises identity store. Use AWS Organizations and build organizational units (OUs) structure based on regulations and service governance. Implement service control policies across OUs.

C. Implement a multi-account strategy based on business units, environments, and specific regulatory requirements. Ensure that only PCI-compliant services are approved for use in the accounts. Build IAM policies to give access to only PCI-compliant services for governance.

D. Build one AWS account for the company for strong security controls. Ensure that all the service limits are raised to meet company scalability requirements. Implement SAML federation with an on-premises identity store, and ensure that only approved services are used in the account.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

A: Too reactive. The users will still be able to do what they want.<br>
B: Sounds feasible.<br>
C: SCP should be used because this is multi-account.<br>
D: Too restrictive and it does not address Developer’s needs.<br>

Two requirements<br>
1. The Security team is concerned about the access strategy for on-premises and AWS implementations.
→ I guess we need to use ID store on premise.
2. They would like to enforce governance for AWS services used by business team for regulatory workloads, including Payment Card Industry (PCI) requirements.
→ Organization and SCP are needed.

모르겠다 ...<br>
`SCP`, `OUs`가 무엇인지 알아보자.

1차 시도 : C 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 405 ⭕ 유념

A사는 AWS CodePipeline을 사용하여 Amazon EC2 AutoScaling 그룹에 대한 애플리케이션의 지속적인 통합 및 전달을 자동화하고 있습니다. AWS CloudFormation 템플릿은 모든 AWS 리소스를 지정합니다. 애플리케이션 아티팩트는 Amazon S3 버킷에 저장되고 인스턴스 사용자 데이터 스크립트를 사용하여 Auto Scaling 그룹에 배포됩니다.
애플리케이션의 복잡성 증가로 인해 CloudFormation 템플릿의 최근 리소스 수정으로 인해 의도하지 않은 다운타임이 발생했습니다.

솔루션 설계자는 어떻게 CI/CD 파이프라인을 최적화하여 템플릿 변경으로 인한 다운타임 위험을 최소화할 수 있습니까?

A. Adapt the deployment scripts to detect and report CloudFormation error conditions when performing deployments. Write test plans for a testing team to execute in a non-production environment before approving the change for production.

B. Implement automated testing using AWS CodeBuild in a test environment. Use CloudFormation change sets to evaluate changes before deployment. Use AWS CodeDeploy to leverage blue/green deployment patterns to allow evaluations and the ability to revert changes, if needed.

C. Use plugins for the integrated development environment (IDE) to check the templates for errors, and use the AWS CLI to validate that the templates are correct. Adapt the deployment code to check for error conditions and generate notifications on errors. Deploy to a test environment and execute a manual test plan before approving the change for production.

D. Use AWS CodeDeploy and a blue/green deployment pattern with CloudFormation to replace the user data deployment scripts. Have the operators log in to running instances and go through a manual test plan to verify the application is running as expected.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Why do manual testing in option D when it can be automated with CodeBuild? CF Change sets to preview changes, and CodeDeploy b/g deployment with ASG.<br>
[Link](https://aws.amazon.com/blogs/devops/performing-bluegreen-deployments-with-aws-codedeploy-and-auto-scaling-groups/)

B is right , this is straight forward question

B: fully automated, with ChangeSets, all other answers have way to much room for human errors.

잘 모르겠다.<br>
`AWS CodePipeline`, `CloudFormation`, `CodeBuild`, `CodeDeploy`에 대해 공부해보자.

1차 시도 : B 맞았는데 잘 모름<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 406 ❌

AWS에서 기업은 서버리스 멀티 테넌트(Multi-tenant) 콘텐츠 관리 시스템을 실행합니다. 웹 기반 프런트 엔드는 맞춤형 AWS 람다 인증자를 사용하여 Amazon API Gateway API와 통신합니다. 인증자는 테넌트 ID와 비교하여 사용자의 ID를 확인하고 정보를 JSON Web Token(JWT) 토큰에 저장합니다. 인증 후, API Gateway를 통해 이루어진 각 API 연결은 단일 Amazon DynamoDB 데이터베이스와 상호 작용하여 요청을 처리하는 람다 함수로 전송됩니다.

보안 요구 사항을 충족하기 위해 기업은 임대자 간의 더 큰 분리를 요구합니다. 첫 해 안에, 그 회사는 수백 명의 소비자를 갖게 될 것입니다.

운영 오버헤드가 가장 적은 이러한 기준을 충족하는 방법은 무엇입니까?

A. Create a DynamoDB table for each tenant by using the tenant ID in the table name. Create a service that uses the JWT token to retrieve the appropriate Lambda execution role that is tenant-specific. Attach IAM policies to the execution role to allow access only to the DynamoDB table for the tenant.

B. Add tenant ID information to the partition key of the DynamoDB table. Create a service that uses the JWT token to retrieve the appropriate Lambda execution role that is tenant-specific. Attach IAM policies to the execution role to allow access to items in the table only when the key matches the tenant ID.

C. Create a separate AWS account for each tenant of the application. Use dedicated infrastructure for each tenant. Ensure that no cross-account network connectivity exists.

D. Add tenant ID as a sort key in every DynamoDB table. Add logic to each Lambda function to use the tenant ID that comes from the JWT token as the sort key in every operation on the DynamoDB table.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

B. [Link](https://aws.amazon.com/blogs/apn/isolating-saas-tenants-with-dynamically-generated-iam-policies/)

Answer seems to be B. Rather than creating table for each tenant, its better to use partition key in the already available table. This can be achieved with the LEAST operational.

이미 존재하는 테이블을 대상으로는 partition key와 sort key를 업데이트 할 수 없다.


1차 시도 : D 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 407 ⭕ SKIP

Amazon DynamoDB에서 Amazon Redshift에 데이터를 넣을 수 있습니까?

A. No, you cannot load all the data from DynamoDB table to a Redshift table as it limited by size constraints.

B. No

C. No, DynamoDB data types do not correspond directly with those of Amazon Redshift.

D. Yes

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

SAP 문제가 아닌 듯 하다.<br>
스킵해도 무방.

1차 시도 : D 맞음 <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 408 ⭕ SKIP

기본적으로 Amazon Cognito는 가장 최근에 작성된 데이터 버전을 유지합니다. 이 동작을 프로그래밍 방식으로 변경하고 데이터 불일치를 처리할 수 있습니다.
또한 푸시 동기화를 사용하면 Amazon Cognito를 사용하여 새로운 데이터를 사용할 수 있을 때 ID와 연결된 모든 장치에 자동으로 알릴 수 있습니다.

A. get

B. post

C. pull

D. push

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

D <br>
[Link](https://aws.amazon.com/cognito/faqs/)<br>
Q: What is a silent push notification?<br>
Amazon Cognito uses the Amazon Simple Notification Service (SNS) to send silent push notifications to devices. A silent push notification is a push message that is received by your application on a user's device that will not be seen by the user.

Q: How do I use push synchronization?<br>
To enable push synchronization you need to declare a platform application using the Amazon SNS page in the AWS Management Console. Then, from the identity pool page in the Amazon Cognito page of the AWS Management Console, you can link the SNS platform application to your Cognito identity pool. Amazon Cognito automatically utilizes the SNS platform application to notify devices of changes.

Q: How is data synchronized with Amazon Cognito?<br>
You can programmatically trigger the sync of data sets between client devices and the Amazon Cognito sync store by using the synchronize() method in the AWS Mobile SDK. The synchronize() method reads the latest version of the data available in the Amazon Cognito sync store and compares it to the local, cached copy. After comparison, the synchronize() method writes the latest updates as necessary to the local data store and the Amazon Cognito sync store. By default Amazon Cognito maintains the last-written version of the data. You can override this behavior and resolve data conflicts programmatically. In addition, push synchronization allows you to use Amazon Cognito to send a silent push notification to all devices associated with an identity to notify them that new data is available.

1차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 409 ⭕

한 소매업체가 Amazon EC2 인스턴스로 구성된 Amazon Elastic Container Service(Amazon ECS) 클러스터에서 미션 크리티컬 온라인 서비스를 호스팅하고 있습니다. 웹 서비스는 최종 사용자의 POST 요청을 수락하고 자체 EC2 서버에서 실행되는 MySQL 데이터베이스에 데이터를 게시합니다. 기업은 데이터 손실을 방지하기 위해 예방 조치를 취해야 합니다.
현재 코드를 배포하는 프로세스에서는 ECS 서비스를 수동으로 변경해야 합니다. 최종 사용자는 최근 배포 중에 실제 웹 요청에 대한 응답으로 산발적으로 502 Bad Gateway failures가 발생했다고 보고했습니다.
조직은 이러한 상황이 재발하지 않도록 신뢰할 수 있는 솔루션을 개발하려고 합니다. 또한 조직은 코드 배포를 자동화하고자 합니다. 솔루션은 접근성과 비용 효율성이 뛰어나야 합니다.

어떤 조치의 조합이 이러한 기준을 충족합니까? (3개를 선택합니다.)

A. Run the web service on an ECS cluster that has a Fargate launch type. Use AWS CodePipeline and AWS CodeDeploy to perform a blue/green deployment with validation testing to update the ECS service.

B. Migrate the MySQL database to run on an Amazon RDS for MySQL Multi-AZ DB instance that uses Provisioned IOPS SSD (io2) storage.

C. Configure an Amazon Simple Queue Service (Amazon SQS) queue as an event source to receive the POST requests from the web service. Configure an AWS Lambda function to poll the queue. Write the data to the database.

D. Run the web service on an ECS cluster that has a Fargate launch type. Use AWS CodePipeline and AWS CodeDeploy to perform a canary deployment to update the ECS service.

E. Configure an Amazon Simple Queue Service (Amazon SQS) queue. Install the SQS agent on the containers that run in the ECS cluster to poll the queue. Write the data to the database.

F. Migrate the MySQL database to run on an Amazon RDS for MySQL Multi-AZ DB instance that uses General Purpose SSD (gp3) storage.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C, F

해설 : 

ACF -<br>
The only concern is about D which is more cost effective - however it may cause some users to report errors if.<br>
So if its a dependable solution it must be blue/green even its expensive no other choice as the question is not allowing failures.<br>
GP3 is + MultAZ will provide good cost effective solution For DB part<br>
And SQS will make sure no drop of data - you dont need to install an agent for this if using lambda.

1차 시도 : A, C, F <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 410 ⭕

AWS에서 각 사업부의 워크로드가 완전한 자율성과 작은 폭발 반경을 갖도록 보장해야 합니다. 보안 팀은 특정 서비스가 사업부에서 활용되는 것을 방지하기 위해 계정의 리소스와 서비스에 대한 액세스를 관리할 수 있어야 합니다.

Solutions Architect는 어떻게 모든 격리 기준을 충족할 수 있습니까?

A. Create individual accounts for each business unit and add the account to an OU in AWS Organizations. Modify the OU to ensure that the particular services are blocked. Federate each account with an IdP, and create separate roles for the business units and the Security team.

B. Create individual accounts for each business unit. Federate each account with an IdP and create separate roles and policies for business units and the Security team.

C. Create one shared account for the entire company. Create separate VPCs for each business unit. Create individual IAM policies and resource tags for each business unit. Federate each account with an IdP, and create separate roles for the business units and the Security team.

D. Create one shared account for the entire company. Create individual IAM policies and resource tags for each business unit. Federate the account with an IdP, and create separate roles for the business units and the Security team.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

A<br>
The best way is to use SCP and individual account.<br>
B: This is difficult to manage.<br>
C\D: Does not reduce the blast radius.<br>

A - SCP hidden deliberately, OU and multiaccount strategy is the key to reduce blast radius


1차 시도 : A <br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional/view/41/)

