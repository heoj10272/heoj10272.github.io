---
layout: post
title: "[AWS] SAP-C02 ExamTopics 31~40"
subtitle: AWS
date: '2023-03-21 21:00:00 +0900'
category: study
tags: aws sap-c02
image:
  path: /assets/img/study_AWS/2023-03-21-[AWS]_SAP-C02_ExamTopics_31~40/logo.png
---

SAP-C02 기출 31~40번 문제를 풀어보자.<br>
1차 4/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 31 ❌
---

An enterprise company wants to allow its developers to purchase third-party software through AWS Marketplace. The company uses an AWS Organizations account structure with full features enabled, and has a shared services account in each organizational unit (OU) that will be used by procurement managers. The procurement team’s policy indicates that developers should be able to obtain third-party software from an approved list only and use Private Marketplace in AWS Marketplace to achieve this requirement. The procurement team wants administration of Private Marketplace to be restricted to a role named procurement-manager-role, which could be assumed by procurement managers. Other IAM users, groups, roles, and account administrators in the company should be denied Private Marketplace administrative access.<br>
What is the MOST efficient way to design an architecture to meet these requirements?

A. Create an IAM role named procurement-manager-role in all AWS accounts in the organization. Add the PowerUserAccess managed policy to the role. Apply an inline policy to all IAM users and roles in every AWS account to deny permissions on the AWSPrivateMarketplaceAdminFullAccess managed policy.

B. Create an IAM role named procurement-manager-role in all AWS accounts in the organization. Add the AdministratorAccess managed policy to the role. Define a permissions boundary with the AWSPrivateMarketplaceAdminFullAccess managed policy and attach it to all the developer roles.

C. Create an IAM role named procurement-manager-role in all the shared services accounts in the organization. Add the AWSPrivateMarketplaceAdminFullAccess managed policy to the role. Create an organization root-level SCP to deny permissions to administer Private Marketplace to everyone except the role named procurement-manager-role. Create another organization root-level SCP to deny permissions to create an IAM role named procurement-manager-role to everyone in the organization.

D. Create an IAM role named procurement-manager-role in all AWS accounts that will be used by developers. Add the AWSPrivateMarketplaceAdminFullAccess managed policy to the role. Create an SCP in Organizations to deny permissions to administer Private Marketplace to everyone except the role named procurement-manager-role. Apply the SCP to all the shared services accounts in the organization.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

1차 시도 : C <br>

해설 : 

SCP는 필터링 역할만 한다고 착각했다.<br>
그것은 허가 목록과 거부 목록에 한한 것이고, 이런식으로 따로 특정 IAM Role 만을 제외하고도 적용할 수 있는 SCP를 만들어 적용할 수 있다.<br>

</div>
</details>

<br>

## Prob. 32 ⭕️
---

A company is in the process of implementing AWS Organizations to constrain its developers to use only Amazon EC2, Amazon S3, and Amazon DynamoDB. The developers account resides in a dedicated organizational unit (OU). The solutions architect has implemented the following SCP on the developers account:

![1](/assets/img/study_AWS/2023-03-21-[AWS]_SAP-C02_ExamTopics_31~40/1.png)

When this policy is deployed, IAM users in the developers account are still able to use AWS services that are not listed in the policy.<br>
What should the solutions architect do to eliminate the developers’ ability to use services outside the scope of this policy?

A. Create an explicit deny statement for each AWS service that should be constrained.

B. Remove the FullAWSAccess SCP from the developers account’s OU.

C. Modify the FullAWSAccess SCP to explicitly deny all services.

D. Add an explicit deny statement using a wildcard to the end of the SCP.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : B <br>

해설 : 

기본적으로 적용되고 있는 `FullAWSAccess` SCP를 제거하면, 기본적으로 모두 묵시적으로 접근할 수 없는 상태가 되므로 위 `허가 목록` 에 명시된 서비스에만 접근할 수 있게 된다.

</div>
</details>

<br>

## Prob. 33 ❌
---

A company is hosting a monolithic REST-based API for a mobile app on five Amazon EC2 instances in public subnets of a VPC. Mobile clients connect to the API by using a domain name that is hosted on Amazon Route 53. The company has created a Route 53 multivalue answer routing policy with the IP addresses of all the EC2 instances. Recently, the app has been overwhelmed by large and sudden increases to traffic. The app has not been able to keep up with the traffic.
A solutions architect needs to implement a solution so that the app can handle the new and varying load.<br>
Which solution will meet these requirements with the LEAST operational overhead?

A. Separate the API into individual AWS Lambda functions. Configure an Amazon API Gateway REST API with Lambda integration for the backend. Update the Route 53 record to point to the API Gateway API.

B. Containerize the API logic. Create an Amazon Elastic Kubernetes Service (Amazon EKS) cluster. Run the containers in the cluster by using Amazon EC2. Create a Kubernetes ingress. Update the Route 53 record to point to the Kubernetes ingress.

C. Create an Auto Scaling group. Place all the EC2 instances in the Auto Scaling group. Configure the Auto Scaling group to perform scaling actions that are based on CPU utilization. Create an AWS Lambda function that reacts to Auto Scaling group changes and updates the Route 53 record.

D. Create an Application Load Balancer (ALB) in front of the API. Move the EC2 instances to private subnets in the VPC. Add the EC2 instances as targets for the ALB. Update the Route 53 record to point to the ALB.
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : D<br>

해설 : 

C의 경우, `Auto Scaling group` 에 변화나 업데이트가 있다면 그 때마다 람다 함수가 반응하게 되므로, 이는 곧 문제에서 요구하는 LEAST operational overhead를 위배하게 된다.

D의 경우, EC2 인스턴스가 public 서브넷에 존재하기 때문에 이를 private으로 옮기면 NAT gateway와 같은 추가적인 overhead를 발생시킨다.

B의 경우, EKS를 활용하는것은 부담스럽다.

A는 아키텍쳐를 갈앙벗는 것이지만, serverless 서비스인 람다 함수와 API Gateway를 활용하는 것이므로 운영적인 측면에서 최소한의 overhead를 가질것이다.

</div>
</details>

<br>

## Prob. 34 ⭕️
---

A company has created an OU in AWS Organizations for each of its engineering teams. Each OU owns multiple AWS accounts. The organization has hundreds of AWS accounts.
A solutions architect must design a solution so that each OU can view a breakdown of usage costs across its AWS accounts.<br>
Which solution meets these requirements?

A. Create an AWS Cost and Usage Report (CUR) for each OU by using AWS Resource Access Manager. Allow each team to visualize the CUR through an Amazon QuickSight dashboard.

B. Create an AWS Cost and Usage Report (CUR) from the AWS Organizations management account. Allow each team to visualize the CUR through an Amazon QuickSight dashboard.

C. Create an AWS Cost and Usage Report (CUR) in each AWS Organizations member account. Allow each team to visualize the CUR through an Amazon QuickSight dashboard.

D. Create an AWS Cost and Usage Report (CUR) by using AWS Systems Manager. Allow each team to visualize the CUR through Systems Manager OpsCenter dashboards.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : B<br>

해설 : 

B가 정답이야. 해결책은 AWS 조직 관리 계정에서 AWS 비용 및 사용 보고서(CUR)를 만드는 것입니다. 이를 통해 관리 계정은 모든 회원 계정의 사용 비용을 볼 수 있으며, 팀은 Amazon QuickSight 대시보드를 통해 CUR을 시각화할 수 있습니다. 이것은 조직이 비용 내역을 볼 수 있는 중앙 집중식 장소를 가질 수 있게 하고 팀은 비용 내역에 쉽게 접근할 수 있게 해준다.

</div>
</details>

<br>

## Prob. 35 ⭕️
---

A company is storing data on premises on a Windows file server. The company produces 5 GB of new data daily.
The company migrated part of its Windows-based workload to AWS and needs the data to be available on a file system in the cloud. The company already has established an AWS Direct Connect connection between the on-premises network and AWS.<br>
Which data migration strategy should the company use?

A. Use the file gateway option in AWS Storage Gateway to replace the existing Windows file server, and point the existing file share to the new file gateway.

B. Use AWS DataSync to schedule a daily task to replicate data between the on-premises Windows file server and Amazon FSx.

C. Use AWS Data Pipeline to schedule a daily task to replicate data between the on-premises Windows file server and Amazon Elastic File System (Amazon EFS).

D. Use AWS DataSync to schedule a daily task to replicate data between the on-premises Windows file server and Amazon Elastic File System (Amazon EFS).

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : B<br>

해설 : 

B와 D 둘 다 유효하나, 윈도우 파일 시스템에는 아무래도 `FSx` 가 어울릴 것이다.

</div>
</details>

<br>

## Prob. 36 ❌
---

A company’s solutions architect is reviewing a web application that runs on AWS. The application references static assets in an Amazon S3 bucket in the us-east-1 Region. The company needs resiliency across multiple AWS Regions. The company already has created an S3 bucket in a second Region.
Which solution will meet these requirements with the LEAST operational overhead?

A. Configure the application to write each object to both S3 buckets. Set up an Amazon Route 53 public hosted zone with a record set by using a weighted routing policy for each S3 bucket. Configure the application to reference the objects by using the Route 53 DNS name.

B. Create an AWS Lambda function to copy objects from the S3 bucket in us-east-1 to the S3 bucket in the second Region. Invoke the Lambda function each time an object is written to the S3 bucket in us-east-1. Set up an Amazon CloudFront distribution with an origin group that contains the two S3 buckets as origins.

C. Configure replication on the S3 bucket in us-east-1 to replicate objects to the S3 bucket in the second Region. Set up an Amazon CloudFront distribution with an origin group that contains the two S3 buckets as origins.

D. Configure replication on the S3 bucket in us-east-1 to replicate objects to the S3 bucket in the second Region. If failover is required, update the application code to load S3 objects from the S3 bucket in the second Region.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : B<br>

해설 : 

Amazon CloudFront를 구성하여 서로 다른 지역의 두 개의 다른 Amazon S3 버킷을 콘텐츠의 원본으로 사용할 수 있습니다. <br>
이렇게 하려면 CloudFront 배포 설정에 두 개의 별도 Amazon S3 버킷 오리진을 만들어야 하며, 각 오리진은 다른 지역의 다른 S3 버킷을 가리킵니다.<br>
CloudFront 배포를 만들 때 여러개의 오리진을 배포 구성에 추가할 수 있습니다.<br>
각 오리진마다 오리진 도메인 이름을 지정할 수 있습니다.<br>
이 도메인 이름은 오리진으로 사용할 S3 버킷의 도메인 이름에 해당합니다. <br>
또한 CloudFront가 HTTP 또는 HTTPS를 사용하여 오리진과 통신하는지 여부를 결정하는 오리진 프로토콜 정책을 지정할 수 있습니다. <br>
두 버킷의 내용을 동기화하려면 두 S3 버킷 간에 교차 영역 복제를 구성해야 합니다. <br>
또한 두 S3 버킷에 모두 공개적으로 액세스할 수 있는지, 또는 CloudFront가 버킷에 액세스할 수 있는 적절한 권한이 있는지 확인해야 합니다.


</div>
</details>

<br>

## Prob. 37 ❌
---

A company is hosting a three-tier web application in an on-premises environment. Due to a recent surge in traffic that resulted in downtime and a significant financial impact, company management has ordered that the application be moved to AWS. The application is written in .NET and has a dependency on a MySQL database. A solutions architect must design a scalable and highly available solution to meet the demand of 200,000 daily users.
Which steps should the solutions architect take to design an appropriate solution?

A. Use AWS Elastic Beanstalk to create a new application with a web server environment and an Amazon RDS MySQL Multi-AZ DB instance. The environment should launch a Network Load Balancer (NLB) in front of an Amazon EC2 Auto Scaling group in multiple Availability Zones. Use an Amazon Route 53 alias record to route traffic from the company’s domain to the NLB.

B. Use AWS CloudFormation to launch a stack containing an Application Load Balancer (ALB) in front of an Amazon EC2 Auto Scaling group spanning three Availability Zones. The stack should launch a Multi-AZ deployment of an Amazon Aurora MySQL DB cluster with a Retain deletion policy. Use an Amazon Route 53 alias record to route traffic from the company’s domain to the ALB.

C. Use AWS Elastic Beanstalk to create an automatically scaling web server environment that spans two separate Regions with an Application Load Balancer (ALB) in each Region. Create a Multi-AZ deployment of an Amazon Aurora MySQL DB cluster with a cross-Region read replica. Use Amazon Route 53 with a geoproximity routing policy to route traffic between the two Regions.

D. Use AWS CloudFormation to launch a stack containing an Application Load Balancer (ALB) in front of an Amazon ECS cluster of Spot instances spanning three Availability Zones. The stack should launch an Amazon RDS MySQL DB instance with a Snapshot deletion policy. Use an Amazon Route 53 alias record to route traffic from the company’s domain to the ALB.
 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : C<br>

해설 : 

B 맞습니다. <br>
솔루션 설계자는 AWS CloudFormation을 사용하여 세 개의 가용 영역에 걸쳐 있는 Amazon EC2 자동 확장 그룹 앞에 애플리케이션 로드 밸런서(ALB)가 포함된 스택을 시작해야 합니다. <br>
스택은 Retain 삭제 정책을 사용하여 Amazon Aurora MySQL DB 클러스터의 다중 AZ 배포를 시작해야 합니다.<br>
Amazon Route 53 별칭 레코드를 사용하여 회사 도메인에서 ALB로 트래픽을 라우팅합니다. <br>
이 솔루션은 트래픽 수요에 따라 자동으로 확장 및 확장할 수 있는 여러 가용성 영역에서 Application Load Balancer 및 Auto Scaling 그룹을 사용하여 웹 응용 프로그램의 확장 성 및고 가용성을 제공합니다. <br>
Multi-AZ Amazon Aurora MySQL DB 클러스터를 사용하면 데이터베이스 계층에 대한 높은 가용성을 제공하며 Retain 삭제 정책은 DB 인스턴스가 삭제되더라도 데이터가 유지되도록합니다. <br>
또한 별칭 레코드와 함께 Route 53을 사용하면 트래픽이 올바른 위치로 라우팅됩니다.

</div>
</details>

<br>

## Prob. 38 ⭕️
---

A company is using AWS Organizations to manage multiple AWS accounts. For security purposes, the company requires the creation of an Amazon Simple Notification Service (Amazon SNS) topic that enables integration with a third-party alerting system in all the Organizations member accounts.
A solutions architect used an AWS CloudFormation template to create the SNS topic and stack sets to automate the deployment of CloudFormation stacks. Trusted access has been enabled in Organizations.
What should the solutions architect do to deploy the CloudFormation StackSets in all AWS accounts?

A. Create a stack set in the Organizations member accounts. Use service-managed permissions. Set deployment options to deploy to an organization. Use CloudFormation StackSets drift detection.

B. Create stacks in the Organizations member accounts. Use self-service permissions. Set deployment options to deploy to an organization. Enable the CloudFormation StackSets automatic deployment.

C. Create a stack set in the Organizations management account. Use service-managed permissions. Set deployment options to deploy to the organization. Enable CloudFormation StackSets automatic deployment.

D. Create stacks in the Organizations management account. Use service-managed permissions. Set deployment options to deploy to the organization. Enable CloudFormation StackSets drift detection.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : C<br>

해설 : 

가장 좋은 솔루션은 C인데, 이는 모든 구성원 계정의 중앙 통제 지점인 조직의 관리 계정에 스택 세트를 생성하는 것을 포함하기 때문입니다. <br>
이를 통해 솔루션 설계자는 단일 위치에서 모든 구성원 계정에 걸쳐 스택 세트의 배포를 관리할 수 있습니다. <br>
서비스 관리 권한이 사용되며, 이를 통해 CloudFormation 서비스가 스택 세트를 모든 멤버 계정에 배포할 수 있습니다. <br>
배포 옵션이 조직에 배포되도록 설정되고 자동 배포가 실행되므로 스택 세트가 관리 계정에 생성되는 즉시 모든 멤버 계정에 자동으로 배포됩니다.

</div>
</details>

<br>

## Prob. 39 ❌
---

A company is using an on-premises Active Directory service for user authentication. The company wants to use the same authentication service to sign in to the 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, D, E

1차 시도 : B, C, F<br>

해설 : 

해당 상황이 `AWS Discovery Agent` + `AWS Migration Hub` 를 이용하기 딱 좋은 상황이다.

Falls under the domain "Accelerate Workload Migration and Modernization"<br>
promoting MigrationHub<br>
Step 1 - Identify the apps<br>
Step 2 - Group them<br>
Step 3 - Before hand, find out what instance types would need to be in when
actual migration happens<br>

For OnPremises migrations, first phase is Discovery which can be done with Discovery agent , A

I wont go with Trusted Advisor although it advises how cost can be advised because- This applies for already aws available environment. <br>
Here, about to get migrated into AWS and Architects need to discover lot of info before hand to plan alot. So I choose E between E and F. <br>
My answer - A,D,E

참고 링크 - [AWS 한국 블로그](https://aws.amazon.com/ko/blogs/korea/aws-migration-hub-plan-track-enterprise-application-migration/)
</div>
</details>

<br>

## Prob. 40 ❌
---

A company is hosting an image-processing service on AWS in a VPC. The VPC extends across two Availability Zones. Each Availability Zone contains one public subnet and one private subnet.

The service runs on Amazon EC2 instances in the private subnets. An Application Load Balancer in the public subnets is in front of the service. The service needs to communicate with the internet and does so through two NAT gateways. The service uses Amazon S3 for image storage. The EC2 instances retrieve approximately 1 ТВ of data from an S3 bucket each day.

The company has promoted the service as highly secure. A solutions architect must reduce cloud expenditures as much as possible without compromising the service’s security posture or increasing the time spent on ongoing operations.

Which solution will meet these requirements?

A. Replace the NAT gateways with NAT instances. In the VPC route table, create a route from the private subnets to the NAT instances.

B. Move the EC2 instances to the public subnets. Remove the NAT gateways.

C. Set up an S3 gateway VPC endpoint in the VPC. Attach an endpoint policy to the endpoint to allow the required actions on the S3 bucket.

D. Attach an Amazon Elastic File System (Amazon EFS) volume to the EC2 instances. Host the images on the EFS volume.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : D<br>

해설 : 

The only reason for C is - Gateway endpoints are not Billed and so cost effective.<br>
[Link](https://docs.aws.amazon.com/AmazonS3/latest/userguide/privatelink-interface-endpoints.html#types-of-vpc-endpoints-for-s3) <br>

B는 프라이빗에 있던걸 퍼블릭으로 꺼내는 것이므로 보안상 적합하지 않을 것이다.

</div>
</details>

<br>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/8/)

