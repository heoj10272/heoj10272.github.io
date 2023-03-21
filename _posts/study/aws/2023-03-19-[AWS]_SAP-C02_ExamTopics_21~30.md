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
1차 6/10<br>

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

## Prob. 26 ⭕
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
Answer : A

1차 시도 : A <br>

해설 : 

Secrets manager는 암호 순환만 지원할 수 있으며 parameter store는 지원하지 않습니다. parameter store는 이름이 나타내는 대로 다른 곳에서 참조하거나 참조하는 위치일 뿐입니다. B,D가 제거됩니다.이벤트 브리지 규칙이 알려진 90일 트리거를 캡처할 필요가 없기 때문에 C가 잘못되었습니다. Secrets manager에서 비밀을 구성할 때는 순환 예약을 이미 사용할 수 있습니다. 그러면 옵션 A가 올바른 상태로 유지됩니다.

</div>
</details>

<br>

## Prob. 27 ❌
---

A company is storing data in several Amazon DynamoDB tables. A solutions architect must use a serverless architecture to make the data accessible publicly through a simple API over HTTPS. The solution must scale automatically in response to demand.
Which solutions meet these requirements? (Choose two.)

A. Create an Amazon API Gateway REST API. Configure this API with direct integrations to DynamoDB by using API Gateway’s AWS integration type.

B. Create an Amazon API Gateway HTTP API. Configure this API with direct integrations to Dynamo DB by using API Gateway’s AWS integration type.

C. Create an Amazon API Gateway HTTP API. Configure this API with integrations to AWS Lambda functions that return data from the DynamoDB tables.

D. Create an accelerator in AWS Global Accelerator. Configure this accelerator with AWS Lambda@Edge function integrations that return data from the DynamoDB tables.

E. Create a Network Load Balancer. Configure listener rules to forward requests to the appropriate AWS Lambda functions.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

1차 시도 : C, E <br>

해설 : 

Option B: HTTP APIs do not currently support integrations with DynamoDB, and therefore this solution would not work. 

Option D: AWS Global Accelerator and AWS Lambda@Edge, which both involve infrastructure management. 

Option E: NLB does not meet the requirement of being serverless

Api gateway REST APis support direct integration with DynamoDb T

he same can be achieved with HTTP APIs using a lambda between the two

</div>
</details>

<br>

## Prob. 28 ❌
---

A company has registered 10 new domain names. The company uses the domains for online marketing. The company needs a solution that will redirect online visitors to a specific URL for each domain. All domains and target URLs are defined in a JSON document. All DNS records are managed by Amazon Route 53.
A solutions architect must implement a redirect service that accepts HTTP and HTTPS requests.
Which combination of steps should the solutions architect take to meet these requirements with the LEAST amount of operational effort? (Choose three.)

A. Create a dynamic webpage that runs on an Amazon EC2 instance. Configure the webpage to use the JSON document in combination with the event message to look up and respond with a redirect URL.

B. Create an Application Load Balancer that includes HTTP and HTTPS listeners.

C. Create an AWS Lambda function that uses the JSON document in combination with the event message to look up and respond with a redirect URL.

D. Use an Amazon API Gateway API with a custom domain to publish an AWS Lambda function.

E. Create an Amazon CloudFront distribution. Deploy a Lambda@Edge function.

F. Create an SSL certificate by using AWS Certificate Manager (ACM). Include the domains as Subject Alternative Names.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, E, F

1차 시도 : C, D, E <br>

해설 : 

C: 솔루션 설계자는 AWS 람다 기능을 생성하여 JSON 문서를 사용하여 각 도메인의 대상 URL을 검색하고 적절한 리디렉션 URL로 응답할 수 있습니다. 이러한 방식으로, 솔루션은 리디렉션을 처리하기 위해 웹 서버에 의존할 필요가 없으므로 운영 작업이 줄어듭니다.

E: 솔루션 설계자는 Amazon CloudFront 배포판을 생성하여 각 도메인에 대한 대상 URL을 검색하고 적절한 리디렉션 URL로 응답할 수 있는 Lambda@Edge 기능을 배포할 수 있습니다. 이러한 방식으로 CloudFront는 리디렉션을 처리할 수 있으므로 운영 노력을 줄일 수 있습니다. 

F: ACM을 사용하여 SSL 인증서를 만들고 도메인을 주체 대체 이름으로 포함함으로써 솔루션 설계자는 리디렉션 서비스가 회사에서 필요로 하는 HTTP 및 HTTPS 요청을 모두 처리할 수 있도록 보장할 수 있습니다.

A와 B는 리디렉션을 처리하기 위해 웹 서버를 구성하고 유지 관리해야 하기 때문에 올바른 답이 아닙니다. 

D는 API Gateway API를 생성해야 하기 때문에 올바른 대답이 아니며, 이는 운영 노력을 증가시킵니다.

</div>
</details>

<br>

## Prob. 29 ⭕
---

A company that has multiple AWS accounts is using AWS Organizations. The company’s AWS accounts host VPCs, Amazon EC2 instances, and containers.
The company’s compliance team has deployed a security tool in each VPC where the company has deployments. The security tools run on EC2 instances and send information to the AWS account that is dedicated for the compliance team. The company has tagged all the compliance-related resources with a key of “costCenter” and a value or “compliance”.
The company wants to identify the cost of the security tools that are running on the EC2 instances so that the company can charge the compliance team’s AWS account. The cost calculation must be as accurate as possible.
What should a solutions architect do to meet these requirements?

A. In the management account of the organization, activate the costCenter user-defined tag. Configure monthly AWS Cost and Usage Reports to save to an Amazon S3 bucket in the management account. Use the tag breakdown in the report to obtain the total cost for the costCenter tagged resources.

B. In the member accounts of the organization, activate the costCenter user-defined tag. Configure monthly AWS Cost and Usage Reports to save to an Amazon S3 bucket in the management account. Schedule a monthly AWS Lambda function to retrieve the reports and calculate the total cost for the costCenter tagged resources.

C. In the member accounts of the organization activate the costCenter user-defined tag. From the management account, schedule a monthly AWS Cost and Usage Report. Use the tag breakdown in the report to calculate the total cost for the costCenter tagged resources.

D. Create a custom report in the organization view in AWS Trusted Advisor. Configure the report to generate a monthly billing summary for the costCenter tagged resources in the compliance team’s AWS account.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : C <br>

해설 : 

지불을 위한 커스텀 태그는 관리 계정에 의해서만 활성화할 수 있다는 말이 있다.<br>
사실 이게 아니더라도 C처럼 일일히 모든 계정에 태그를 적용하는 것 보다는 관리 계정에 적용하여 한 번에 모든 멤버 계정이 영향을 받도록 하는것이 나아 보인다.


</div>
</details>

<br>

## Prob. 30 ⭕
---

A company has 50 AWS accounts that are members of an organization in AWS Organizations. Each account contains multiple VPCs. The company wants to use AWS Transit Gateway to establish connectivity between the VPCs in each member account. Each time a new member account is created, the company wants to automate the process of creating a new VPC and a transit gateway attachment.
Which combination of steps will meet these requirements? (Choose two.)

A. From the management account, share the transit gateway with member accounts by using AWS Resource Access Manager.

B. From the management account, share the transit gateway with member accounts by using an AWS Organizations SCP.

C. Launch an AWS CloudFormation stack set from the management account that automatically creates a new VPC and a VPC transit gateway attachment in a member account. Associate the attachment with the transit gateway in the management account by using the transit gateway ID.

D. Launch an AWS CloudFormation stack set from the management account that automatically creates a new VPC and a peering transit gateway attachment in a member account. Share the attachment with the transit gateway in the management account by using a transit gateway service-linked role.

E. From the management account, share the transit gateway with member accounts by using AWS Service Catalog.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

1차 시도 : A, C <br>

해설 : 

A : Resource Access Manager를 사용하여 관리 계정에서 transit gateway를 member accounts가 공유할 수 있도록 구현한다.<br>
C : transit gateway ID를 통해 관리 계정에서 transit gateway를 연결하는것이 맞아 보인다.

</div>
</details>

<br>


<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/6/)

