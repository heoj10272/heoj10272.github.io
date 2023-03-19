---
layout: post
title: "[AWS] SAP-C02 ExamTopics 21~30"
subtitle: AWS
date: '2023-03-19 21:30:00 +0900'
category: study
tags: aws sap-c02
image:
  path: /assets/img/study_AWS/2023-03-19-[AWS]_SAP-C02_ExamTopics_21~30/logo.png
---

SAP-C02 기출 21~30번 문제를 풀어보자.<br>
1차 x/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 21 ❓
---

A company is using an on-premises Active Directory service for user authentication. The company wants to use the same authentication service to sign in to the company’s AWS accounts, which are using AWS Organizations. AWS Site-to-Site VPN connectivity already exists between the on-premises environment and all the company’s AWS accounts.
The company’s security policy requires conditional access to the accounts based on user groups and roles. User identities must be managed in a single location.
Which solution will meet these requirements?

A. Configure AWS IAM Identity Center (AWS Single Sign-On) to connect to Active Directory by using SAML 2.0. Enable automatic provisioning by using the System for Cross-domain Identity Management (SCIM) v2.0 protocol. Grant access to the AWS accounts by using attribute-based access controls (ABACs).

B. Configure AWS IAM Identity Center (AWS Single Sign-On) by using IAM Identity Center as an identity source. Enable automatic provisioning by using the System for Cross-domain Identity Management (SCIM) v2.0 protocol. Grant access to the AWS accounts by using IAM Identity Center permission sets.

C. In one of the company’s AWS accounts, configure AWS Identity and Access Management (IAM) to use a SAML 2.0 identity provider. Provision IAM users that are mapped to the federated users. Grant access that corresponds to appropriate groups in Active Directory. Grant access to the required AWS accounts by using cross-account IAM users.

D. In one of the company’s AWS accounts, configure AWS Identity and Access Management (IAM) to use an OpenID Connect (OIDC) identity provider. Provision IAM roles that grant access to the AWS account for the federated users that correspond to appropriate groups in Active Directory. Grant access to the required AWS accounts by using cross-account IAM roles.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

1차 시도 : B <br>

해설 : 

AWS SSO(Single Sign-On)는 여러 AWS 계정 및 비즈니스 애플리케이션에 대한 액세스를 관리하도록 설계되었으며, 사용자가 Active Directory의 자격 증명을 포함하여 기존 자격 증명을 사용하여 한 번 로그인할 수 있도록 합니다. SAML 2.0을 사용하여 Active Directory에 연결하도록 AWS SSO를 구성하면 사용자 ID를 단일 위치에서 관리할 수 있습니다. 또한 SCIM(System for Cross-Domain Identity Management) v2.0 프로토콜을 사용하여 자동 프로비저닝을 사용하도록 설정할 수 있습니다. 이렇게 하면 Active Directory의 변경 사항에 따라 AWS SSO에서 사용자를 생성하고 업데이트할 수 있습니다.

</div>
</details>

<br>

## Prob. 22 ❌
---

A software company has deployed an application that consumes a REST API by using Amazon API Gateway, AWS Lambda functions, and an Amazon DynamoDB table. The application is showing an increase in the number of errors during PUT requests. Most of the PUT calls come from a small number of clients that are authenticated with specific API keys.
A solutions architect has identified that a large number of the PUT requests originate from one client. The API is noncritical, and clients can tolerate retries of unsuccessful calls. However, the errors are displayed to customers and are causing damage to the API’s reputation.
What should the solutions architect recommend to improve the customer experience?

A. Implement retry logic with exponential backoff and irregular variation in the client application. Ensure that the errors are caught and handled with descriptive error messages.

B. Implement API throttling through a usage plan at the API Gateway level. Ensure that the client application handles code 429 replies without error.

C. Turn on API caching to enhance responsiveness for the production stage. Run 10-minute load tests. Verify that the cache capacity is appropriate for the workload.

D. Implement reserved concurrency at the Lambda function level to provide the resources that are needed during sudden increases in traffic.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : A <br>

해설 : 

API 쓰로틀링은 API에 대한 요청 속도를 제어하는 데 사용할 수 있는 기술입니다. 이 기능은 적은 수의 클라이언트가 많은 수의 요청을 수행하여 오류를 발생시키는 상황에서 유용할 수 있습니다. 솔루션 설계자는 API 게이트웨이 수준에서 사용 계획을 통해 API 쓰로틀링을 구현하여 클라이언트가 수행할 수 있는 요청 수를 제한할 수 있으므로 오류 수를 줄이는 데 도움이 됩니다. 클라이언트 애플리케이션이 코드 429 응답을 오류 없이 처리하는 것이 중요합니다. 이는 고객에게 표시되는 오류 수를 줄여 고객 환경을 개선하는 데 도움이 됩니다. 또한 오류로 인해 API의 평판이 손상되는 것을 방지합니다.

클라이언트 애플리케이션의 기하급수적인 백오프 및 불규칙한 변동을 이용한 리트라이 로직이나 프로덕션 단계에 대한 응답성을 높이기 위해 API 캐싱을 설정하는 등의 다른 솔루션이 고객 환경을 개선하고 오류를 줄이는 데 도움이 될 수 있다는 점에 유의해야 합니다, 그러나 소수의 클라이언트에서 대량의 요청이 발생하는 문제의 근본 원인을 해결하지는 못합니다. 예약된 동시성을 람다 함수 수준에서 구현하면 트래픽이 갑자기 증가할 때 필요한 리소스를 제공할 수 있지만 클라이언트가 많은 수의 요청을 수행하고 오류를 발생시키는 문제를 해결하지는 못합니다.

</div>
</details>

<br>

## Prob. 23 ⭕
---

A company is running a data-intensive application on AWS. The application runs on a cluster of hundreds of Amazon EC2 instances. A shared file system also runs on several EC2 instances that store 200 TB of data. The application reads and modifies the data on the shared file system and generates a report. The job runs once monthly, reads a subset of the files from the shared file system, and takes about 72 hours to complete. The compute instances scale in an Auto Scaling group, but the instances that host the shared file system run continuously. The compute and storage instances are all in the same AWS Region.
A solutions architect needs to reduce costs by replacing the shared file system instances. The file system must provide high performance access to the needed data for the duration of the 72-hour run.
Which solution will provide the LARGEST overall cost reduction while meeting these requirements?

A. Migrate the data from the existing shared file system to an Amazon S3 bucket that uses the S3 Intelligent-Tiering storage class. Before the job runs each month, use Amazon FSx for Lustre to create a new file system with the data from Amazon S3 by using lazy loading. Use the new file system as the shared storage for the duration of the job. Delete the file system when the job is complete.

B. Migrate the data from the existing shared file system to a large Amazon Elastic Block Store (Amazon EBS) volume with Multi-Attach enabled. Attach the EBS volume to each of the instances by using a user data script in the Auto Scaling group launch template. Use the EBS volume as the shared storage for the duration of the job. Detach the EBS volume when the job is complete.

C. Migrate the data from the existing shared file system to an Amazon S3 bucket that uses the S3 Standard storage class. Before the job runs each month, use Amazon FSx for Lustre to create a new file system with the data from Amazon S3 by using batch loading. Use the new file system as the shared storage for the duration of the job. Delete the file system when the job is complete.

D. Migrate the data from the existing shared file system to an Amazon S3 bucket. Before the job runs each month, use AWS Storage Gateway to create a file gateway with the data from Amazon S3. Use the file gateway as the shared storage for the job. Delete the file gateway when the job is complete.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

1차 시도 : A <br>

해설 : 

A: Lazy loading is cost-effective because only a subset of data is used at every job 

B: There are hundreds of EC2 instances using the volume which is not possible (one EBS volume is limited to 16 nitro instances attached) 

C: Batching would load too much data 

D: storage gateway is used for on premises data access, I don't know is you can install a gateway in AWS, but Amazon would never advise this

</div>
</details>

<br>

## Prob. 24 ⭕
---

A company is developing a new service that will be accessed using TCP on a static port. A solutions architect must ensure that the service is highly available, has redundancy across Availability Zones, and is accessible using the DNS name my.service.com, which is publicly accessible. The service must use fixed address assignments so other companies can add the addresses to their allow lists.
Assuming that resources are deployed in multiple Availability Zones in a single Region, which solution will meet these requirements?

A. Create Amazon EC2 instances with an Elastic IP address for each instance. Create a Network Load Balancer (NLB) and expose the static TCP port. Register EC2 instances with the NLB. Create a new name server record set named my.service.com, and assign the Elastic IP addresses of the EC2 instances to the record set. Provide the Elastic IP addresses of the EC2 instances to the other companies to add to their allow lists.

B. Create an Amazon ECS cluster and a service definition for the application. Create and assign public IP addresses for the ECS cluster. Create a Network Load Balancer (NLB) and expose the TCP port. Create a target group and assign the ECS cluster name to the NLCreate a new A record set named my.service.com, and assign the public IP addresses of the ECS cluster to the record set. Provide the public IP addresses of the ECS cluster to the other companies to add to their allow lists.

C. Create Amazon EC2 instances for the service. Create one Elastic IP address for each Availability Zone. Create a Network Load Balancer (NLB) and expose the assigned TCP port. Assign the Elastic IP addresses to the NLB for each Availability Zone. Create a target group and register the EC2 instances with the NLB. Create a new A (alias) record set named my.service.com, and assign the NLB DNS name to the record set.

D. Create an Amazon ECS cluster and a service definition for the application. Create and assign public IP address for each host in the cluster. Create an Application Load Balancer (ALB) and expose the static TCP port. Create a target group and assign the ECS service definition name to the ALB. Create a new CNAME record set and associate the public IP addresses to the record set. Provide the Elastic IP addresses of the Amazon EC2 instances to the other companies to add to their allow lists.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : C <br>

해설 : 

Non http port like TCP should hint to NLB immediately.(ALB does not fit here) Sharing IP address of EC2 is not apt whether it is from individual EC2 instances or those from ECS cluster.this eliminates A,B.D, infact the NLB's address which stays in front of / associates to ec2 instances need to be shared. So, only solution is C

</div>
</details>

<br>

## Prob. 25 ⭕
---

A company uses an on-premises data analytics platform. The system is highly available in a fully redundant configuration across 12 servers in the company’s data center.
The system runs scheduled jobs, both hourly and daily, in addition to one-time requests from users. Scheduled jobs can take between 20 minutes and 2 hours to finish running and have tight SLAs. The scheduled jobs account for 65% of the system usage. User jobs typically finish running in less than 5 minutes and have no SLA. The user jobs account for 35% of system usage. During system failures, scheduled jobs must continue to meet SLAs. However, user jobs can be delayed.
A solutions architect needs to move the system to Amazon EC2 instances and adopt a consumption-based model to reduce costs with no long-term commitments. The solution must maintain high availability and must not affect the SLAs.
Which solution will meet these requirements MOST cost-effectively?

A. Split the 12 instances across two Availability Zones in the chosen AWS Region. Run two instances in each Availability Zone as On-Demand Instances with Capacity Reservations. Run four instances in each Availability Zone as Spot Instances.

B. Split the 12 instances across three Availability Zones in the chosen AWS Region. In one of the Availability Zones, run all four instances as On-Demand Instances with Capacity Reservations. Run the remaining instances as Spot Instances.

C. Split the 12 instances across three Availability Zones in the chosen AWS Region. Run two instances in each Availability Zone as On-Demand Instances with a Savings Plan. Run two instances in each Availability Zone as Spot Instances.

D. Split the 12 instances across three Availability Zones in the chosen AWS Region. Run three instances in each Availability Zone as On-Demand Instances with Capacity Reservations. Run one instance in each Availability Zone as a Spot Instance.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

1차 시도 : D <br>

해설 : 

D because of the 65% / 35% proportion. C seems to be good but with only 50% instances available we break the SLA

D has no long term commitment (e.g. saving plans) and has 75% on demand instances / 25% spot instances which is near the requirements

</div>
</details>

<br>

## Prob. 26 ⭕❌
---

A security engineer determined that an existing application retrieves credentials to an Amazon RDS for MySQL database from an encrypted file in Amazon S3. For the next version of the application, the security engineer wants to implement the following application design changes to improve security:
The database must use strong, randomly generated passwords stored in a secure AWS managed service.
The application resources must be deployed through AWS CloudFormation.
The application must rotate credentials for the database every 90 days.
A solutions architect will generate a CloudFormation template to deploy the application.
Which resources specified in the CloudFormation template will meet the security engineer’s requirements with the LEAST amount of operational overhead?

A. Generate the database password as a secret resource using AWS Secrets Manager. Create an AWS Lambda function resource to rotate the database password. Specify a Secrets Manager RotationSchedule resource to rotate the database password every 90 days.

B. Generate the database password as a SecureString parameter type using AWS Systems Manager Parameter Store. Create an AWS Lambda function resource to rotate the database password. Specify a Parameter Store RotationSchedule resource to rotate the database password every 90 days.

C. Generate the database password as a secret resource using AWS Secrets Manager. Create an AWS Lambda function resource to rotate the database password. Create an Amazon EventBridge scheduled rule resource to trigger the Lambda function password rotation every 90 days.

D. Generate the database password as a SecureString parameter type using AWS Systems Manager Parameter Store. Specify an AWS AppSync DataSource resource to automatically rotate the database password every 90 days.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 :  <br>

해설 : 


</div>
</details>

<br>

## Prob. 27 ⭕❌
---

A company has many AWS accounts and uses AWS Organizations to manage all of them. A solutions 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 :  <br>

해설 : 


</div>
</details>

<br>

## Prob. 28 ⭕❌
---

A company has many AWS accounts and uses AWS Organizations to manage all of them. A solutions 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 :  <br>

해설 : 


</div>
</details>

<br>

## Prob. 29 ⭕❌
---

A company has many AWS accounts and uses AWS Organizations to manage all of them. A solutions 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 :  <br>

해설 : 


</div>
</details>

<br>

## Prob. 30 ⭕❌
---

A company has many AWS accounts and uses AWS Organizations to manage all of them. A solutions 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 :  <br>

해설 : 


</div>
</details>

<br>


<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/3/)

