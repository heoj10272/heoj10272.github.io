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
1차 x/10<br>

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

## Prob. 32 ⭕️❌
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

A company is using an on-premises Active Directory service for user authentication. The company wants to use the same authentication service to sign in to the 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : B<br>

해설 : 



</div>
</details>

<br>

## Prob. 37 ❌
---

A company is using an on-premises Active Directory service for user authentication. The company wants to use the same authentication service to sign in to the 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : C<br>

해설 : 



</div>
</details>

<br>

## Prob. 38 ⭕️
---

A company is using an on-premises Active Directory service for user authentication. The company wants to use the same authentication service to sign in to the 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : C<br>

해설 : 



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



</div>
</details>

<br>

## Prob. 40 ⭕️❌
---

A company is using an on-premises Active Directory service for user authentication. The company wants to use the same authentication service to sign in to the 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 : <br>

해설 : 



</div>
</details>

<br>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/6/)

