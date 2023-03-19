---
layout: post
title: "[AWS] SAP-C02 ExamTopics 11~20"
subtitle: AWS
date: '2023-03-15 21:30:00 +0900'
category: study
tags: aws sap-c02
image:
  path: /assets/img/study_AWS/2023-03-15-[AWS]_SAP-C02_ExamTopics_11~20/logo.png
---

SAP-C02 기출 11~20번 문제를 풀어보자.<br>
1차 3/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 11 ❌
---

A company has many AWS accounts and uses AWS Organizations to manage all of them. A solutions architect must implement a solution that the company can use to share a common network across multiple accounts.
The company’s infrastructure team has a dedicated infrastructure account that has a VPC. The infrastructure team must use this account to manage the network. Individual accounts cannot have the ability to manage their own networks. However, individual accounts must be able to create AWS resources within subnets.
Which combination of actions should the solutions architect perform to meet these requirements? (Choose two.)

A. Create a transit gateway in the infrastructure account.

B. Enable resource sharing from the AWS Organizations management account.

C. Create VPCs in each AWS account within the organization in AWS Organizations. Configure the VPCs to share the same CIDR range and subnets as the VPC in the infrastructure account. Peer the VPCs in each individual account with the VPC in the infrastructure account.

D. Create a resource share in AWS Resource Access Manager in the infrastructure account. Select the specific AWS Organizations OU that will use the shared network. Select each subnet to associate with the resource share.

E. Create a resource share in AWS Resource Access Manager in the infrastructure account. Select the specific AWS Organizations OU that will use the shared network. Select each prefix list to associate with the resource share.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, D

해설 : 

B는 조직이 계정 간에 리소스를 공유할 수 있도록 지원하기 때문에 필요합니다.<br>
D는 인프라 계정이 조직의 다른 계정과 특정 서브넷을 공유할 수 있게 해주기 때문에 다른 계정이 자체 네트워크를 관리하지 않고도 해당 서브넷 내에 리소스를 생성할 수 있습니다.

1차 시도 : A, D <br>
</div>
</details>

<br>

## Prob. 12 ❌
---

A company wants to use a third-party software-as-a-service (SaaS) application. The third-party SaaS application is consumed through several API calls. The third-party SaaS application also runs on AWS inside a VPC.
The company will consume the third-party SaaS application from inside a VPC. The company has internal security policies that mandate the use of private connectivity that does not traverse the internet. No resources that run in the company VPC are allowed to be accessed from outside the company’s VPC. All permissions must conform to the principles of least privilege.
Which solution meets these requirements?

A. Create an AWS PrivateLink interface VPC endpoint. Connect this endpoint to the endpoint service that the third-party SaaS application provides. Create a security group to limit the access to the endpoint. Associate the security group with the endpoint.

B. Create an AWS Site-to-Site VPN connection between the third-party SaaS application and the company VPC. Configure network ACLs to limit access across the VPN tunnels.

C. Create a VPC peering connection between the third-party SaaS application and the company VPC. Update route tables by adding the needed routes for the peering connection.

D. Create an AWS PrivateLink endpoint service. Ask the third-party SaaS provider to create an interface VPC endpoint for this endpoint service. Grant permissions for the endpoint service to the specific account of the third-party SaaS provider.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : A

이 솔루션은 트래픽이 인터넷을 통과하지 않고 회사의 VPC와 타사 SaaS 애플리케이션 VPC 간에 안전하고 개인적인 연결을 만드는 AWS PrivateLink를 사용합니다. 보안 그룹을 사용하고 엔드포인트 서비스에 대한 액세스를 제한하는 것은 최소 권한의 원칙을 준수합니다

1차 시도 : C <br>
</div>
</details>

<br>

## Prob. 13 ❓
---

A company needs to implement a patching process for its servers. The on-premises servers and Amazon EC2 instances use a variety of tools to perform patching. Management requires a single report showing the patch status of all the servers and instances.
Which set of actions should a solutions architect take to meet these requirements?

A. Use AWS Systems Manager to manage patches on the on-premises servers and EC2 instances. Use Systems Manager to generate patch compliance reports.

B. Use AWS OpsWorks to manage patches on the on-premises servers and EC2 instances. Use Amazon QuickSight integration with OpsWorks to generate patch compliance reports.

C. Use an Amazon EventBridge rule to apply patches by scheduling an AWS Systems Manager patch remediation job. Use Amazon Inspector to generate patch compliance reports.

D. Use AWS OpsWorks to manage patches on the on-premises servers and EC2 instances. Use AWS X-Ray to post the patch status to AWS Systems Manager OpsCenter to generate patch compliance reports.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

A가 맞습니다. AWS 시스템 매니저는 사내 서버와 EC2 인스턴스 모두에서 패치를 관리하고 패치 준수 보고서를 생성할 수 있습니다. AWS OpsWorks 및 Amazon Inspector는 패치 관리를 위해 특별히 설계되지 않았으므로 이 사용 사례에 가장 적합한 선택은 아닙니다. Amazon EventBridge 규칙 및 AWS X-Ray를 사용하여 패치 준수 보고서를 생성하는 것은 패치 관리 보고용으로 설계되지 않았기 때문에 실용적인 솔루션이 아닙니다.

1차 시도 : ? <br>
</div>
</details>

<br>

## Prob. 14 ❓
---

A company is running an application on several Amazon EC2 instances in an Auto Scaling group behind an Application Load Balancer. The load on the application varies throughout the day, and EC2 instances are scaled in and out on a regular basis. Log files from the EC2 instances are copied to a central Amazon S3 bucket every 15 minutes. The security team discovers that log files are missing from some of the terminated EC2 instances.
Which set of actions will ensure that log files are copied to the central S3 bucket from the terminated EC2 instances?

A. Create a script to copy log files to Amazon S3, and store the script in a file on the EC2 instance. Create an Auto Scaling lifecycle hook and an Amazon EventBridge rule to detect lifecycle events from the Auto Scaling group. Invoke an AWS Lambda function on the autoscaling:EC2_INSTANCE_TERMINATING transition to send ABANDON to the Auto Scaling group to prevent termination, run the script to copy the log files, and terminate the instance using the AWS SDK.

B. Create an AWS Systems Manager document with a script to copy log files to Amazon S3. Create an Auto Scaling lifecycle hook and an Amazon EventBridge rule to detect lifecycle events from the Auto Scaling group. Invoke an AWS Lambda function on the autoscaling:EC2_INSTANCE_TERMINATING transition to call the AWS Systems Manager API SendCommand operation to run the document to copy the log files and send CONTINUE to the Auto Scaling group to terminate the instance.

C. Change the log delivery rate to every 5 minutes. Create a script to copy log files to Amazon S3, and add the script to EC2 instance user data. Create an Amazon EventBridge rule to detect EC2 instance termination. Invoke an AWS Lambda function from the EventBridge rule that uses the AWS CLI to run the user-data script to copy the log files and terminate the instance.

D. Create an AWS Systems Manager document with a script to copy log files to Amazon S3. Create an Auto Scaling lifecycle hook that publishes a message to an Amazon Simple Notification Service (Amazon SNS) topic. From the SNS notification, call the AWS Systems Manager API SendCommand operation to run the document to copy the log files and send ABANDON to the Auto Scaling group to terminate the instance.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

이 접근 방식은 자동 스케일링 수명 주기 후크를 사용하여 인스턴스가 종료되기 전에 로그 파일을 S3에 복사하는 스크립트를 실행하여 종료된 인스턴스에서 모든 로그 파일이 복사되도록 합니다.

즉 이 문제에서 중점으로 물어보는건, 종료되는 EC2로부터 어떻게 로그 파일을 복사하느냐는 것이다.

[Run code before terminating an EC2 Auto Scaling instance](https://aws.amazon.com/ko/blogs/infrastructure-and-automation/run-code-before-terminating-an-ec2-auto-scaling-instance/) 해당 링크를 참고하자.

즉 순서는 이렇다.

1. S3에 로그 파일을 복사해줄 `System Manager` 문서를 만든다.
2. `Auto Scailing lifecycle hook`을 만든다.
    * [lifecycle hook](https://docs.aws.amazon.com/autoscaling/ec2/userguide/lifecycle-hooks.html)은 Auto Scaling group에 속하는 인스턴스들의 라이프사이클(terminate, scale out 등) 상태 변화에 이벤트들에 대한 액션을 취할 수 있도록 해준다. 해당 액션이 완료될 때 까지의 시간(기본 1시간)도 제공한 후, 완료되면 예정된 단계로 넘어가게 된다.
    * 해당 액션은 `CloudWatch` , `EventBridge` 등으로 감지할 수 있다.
3. 해당 라이프사이클 훅을 감지할 `EventBridge` 규칙을 설정한다.
4. EventBridge가 감지하면 이를 받아줄 `Lambda function` 을 만들고, `System Manager` 문서를 실행하도록 한다.

이렇게 하면, 라이프사이클 훅에 따라 인스턴스는 종료되기 직전에 멈추게 되고, 그 동안 람다 함수 - 시스템 매니저를 통해 로그 파일을 S3로 복사, 완료되면 `CONTINUE` 신호를 통해 인스턴스를 종료하는 과정을 거치게 된다.

1차 시도 : D <br>
</div>
</details>

<br>

## Prob. 15 ❌
---

A company is using multiple AWS accounts. The DNS records are stored in a private hosted zone for Amazon Route 53 in Account A. The company’s applications and databases are running in Account B.
A solutions architect will deploy a two-tier application in a new VPC. To simplify the configuration, the db.example.com CNAME record set for the Amazon RDS endpoint was created in a private hosted zone for Amazon Route 53.
During deployment, the application failed to start. Troubleshooting revealed that db.example.com is not resolvable on the Amazon EC2 instance. The solutions architect confirmed that the record set was created correctly in Route 53.
Which combination of steps should the solutions architect take to resolve this issue? (Choose two.)

A. Deploy the database on a separate EC2 instance in the new VPC. Create a record set for the instance’s private IP in the private hosted zone.

B. Use SSH to connect to the application tier EC2 instance. Add an RDS endpoint IP address to the /etc/resolv.conf file.

C. Create an authorization to associate the private hosted zone in Account A with the new VPC in Account B.

D. Create a private hosted zone for the example com domain in Account B. Configure Route 53 replication between AWS accounts.

E. Associate a new VPC in Account B with a hosted zone in Account A. Delete the association authorization in Account A.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, E

해설 : 

[Associating an Amazon VPC and a private hosted zone that you created with different AWS accounts](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zone-private-associate-vpcs-different-accounts.html)

현재 A 계정의 프라이빗 호스팅 존에 Route 53이 있고,<br>
B 계정의 새 VPC에 2티어 어플리케이션을 만들었다.<br>
DB의 CNAME이 A계정의 Route 53에 만들어졌으나, 배포에 실패한 상황이다.

당연히 Route53과 새 VPC가 연결이 되어있지 않으니 발생한 일이기 때문에, 연결을 해줘야 하므로

1. 호스팅 존을 가진 계정(A)에서 VPC의 접근을 승인한다.
2. VPC를 가진 계정(B)에서 A의 호스팅 존에 접근한다.
3. A에 있는 B에 대한 접근 승인을 삭제한다.
    * 삭제해도 이미 연결된 상태에는 아무런 영향이 없다.
    * 삭제해야 미래에 VPC가 호스팅 존에 재접근 하는 것을 방지할 수 있다.
    * 만약 재접근이 필요하다면, 1번과 2번을 다시 수행한다.



1차 시도 : B, C <br>
</div>
</details>

<br>

## Prob. 16 ⭕
---

A company used Amazon EC2 instances to deploy a web fleet to host a blog site. The EC2 instances are behind an Application Load Balancer (ALB) and are configured in an Auto Scaling group. The web application stores all blog content on an Amazon EFS volume.
The company recently added a feature for bloggers to add video to their posts, attracting 10 times the previous user traffic. At peak times of day, users report buffering and timeout issues while attempting to reach the site or watch videos.
Which is the MOST cost-efficient and scalable deployment that will resolve the issues for users?

A. Reconfigure Amazon EFS to enable maximum I/O.

B. Update the blog site to use instance store volumes for storage. Copy the site contents to the volumes at launch and to Amazon S3 at shutdown.

C. Configure an Amazon CloudFront distribution. Point the distribution to an S3 bucket, and migrate the videos from EFS to Amazon S3.

D. Set up an Amazon CloudFront distribution for all site contents, and point the distribution at the ALB.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : C<br>

해설 : 

CloudFront로 배포하면 사용자의 근처에 있는 엣지 로케이션에 캐시하여 버퍼링과 타임아웃을 줄일 수 있다.

</div>
</details>

<br>

## Prob. 17 ❌
---

A company with global offices has a single 1 Gbps AWS Direct Connect connection to a single AWS Region. The company’s on-premises network uses the connection to communicate with the company’s resources in the AWS Cloud. The connection has a single private virtual interface that connects to a single VPC.
A solutions architect must implement a solution that adds a redundant Direct Connect connection in the same Region. The solution also must provide connectivity to other Regions through the same pair of Direct Connect connections as the company expands into other Regions.
Which solution meets these requirements?

A. Provision a Direct Connect gateway. Delete the existing private virtual interface from the existing connection. Create the second Direct Connect connection. Create a new private virtual interface on each connection, and connect both private virtual interfaces to the Direct Connect gateway. Connect the Direct Connect gateway to the single VPC.

B. Keep the existing private virtual interface. Create the second Direct Connect connection. Create a new private virtual interface on the new connection, and connect the new private virtual interface to the single VPC.

C. Keep the existing private virtual interface. Create the second Direct Connect connection. Create a new public virtual interface on the new connection, and connect the new public virtual interface to the single VPC.

D. Provision a transit gateway. Delete the existing private virtual interface from the existing connection. Create the second Direct Connect connection. Create a new private virtual interface on each connection, and connect both private virtual interfaces to the transit gateway. Associate the transit gateway with the single VPC.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

1차 시도 : C <br>

해설 : 

`Direct Connect Gateway` 를 사용하는것이 올바른 정답이라고 한다.

D의 `Transit Gateway` 의 경우, 리전별 서비스이기 때문에 하나의 TGW로는 다른 리전간의 접속이 불가능하다. 다른 리전간의 접속이 필요한 경우 다른 리전에 있는 TGW를 통해서 접속해야 하므로 옳지 않다.

</div>
</details>

<br>

## Prob. 18 ⭕
---

A company has a web application that allows users to upload short videos. The videos are stored on Amazon EBS volumes and analyzed by custom recognition software for categorization.
The website contains static content that has variable traffic with peaks in certain months. The architecture consists of Amazon EC2 instances running in an Auto Scaling group for the web application and EC2 instances running in an Auto Scaling group to process an Amazon SQS queue. The company wants to re-architect the application to reduce operational overhead using AWS managed services where possible and remove dependencies on third-party software.
Which solution meets these requirements?

A. Use Amazon ECS containers for the web application and Spot instances for the Auto Scaling group that processes the SQS queue. Replace the custom software with Amazon Rekognition to categorize the videos.

B. Store the uploaded videos in Amazon EFS and mount the file system to the EC2 instances for the web application. Process the SQS queue with an AWS Lambda function that calls the Amazon Rekognition API to categorize the videos.

C. Host the web application in Amazon S3. Store the uploaded videos in Amazon S3. Use S3 event notification to publish events to the SQS queue. Process the SQS queue with an AWS Lambda function that calls the Amazon Rekognition API to categorize the videos.

D. Use AWS Elastic Beanstalk to launch EC2 instances in an Auto Scaling group for the web application and launch a worker environment to process the SQS queue. Replace the custom software with Amazon Rekognition to categorize the videos.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : C <br>

해설 : 

문제에 AWS의 관리형 서비스를 이용하라는 문구가 있으므로, S3, SQS, Lambda, Rekognition를 활용하는것이 좋아보인다.<br>
또한 Amazon Rekognition API 로 비디오 컨텐츠 또한 카테고라이징 할 수 있다.

</div>
</details>

<br>

## Prob. 19 ⭕
---

A company has a serverless application comprised of Amazon CloudFront, Amazon API Gateway, and AWS Lambda functions. The current deployment process of the application code is to create a new version number of the Lambda function and run an AWS CLI script to update. If the new function version has errors, another CLI script reverts by deploying the previous working version of the function. The company would like to decrease the time to deploy new versions of the application logic provided by the Lambda functions, and also reduce the time to detect and revert when errors are identified.
How can this be accomplished?

A. Create and deploy nested AWS CloudFormation stacks with the parent stack consisting of the AWS CloudFront distribution and API Gateway, and the child stack containing the Lambda function. For changes to Lambda, create an AWS CloudFormation change set and deploy; if errors are triggered, revert the AWS CloudFormation change set to the previous version.

B. Use AWS SAM and built-in AWS CodeDeploy to deploy the new Lambda version, gradually shift traffic to the new version, and use pre-traffic and post-traffic test functions to verify code. Rollback if Amazon CloudWatch alarms are triggered.

C. Refactor the AWS CLI scripts into a single script that deploys the new Lambda version. When deployment is completed, the script tests execute. If errors are detected, revert to the previous Lambda version.

D. Create and deploy an AWS CloudFormation stack that consists of a new API Gateway endpoint that references the new Lambda version. Change the CloudFront origin to the new API Gateway endpoint, monitor errors and if detected, change the AWS CloudFront origin to the previous API Gateway endpoint.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : B <br>

해설 : 

AWS SAM(Serverless Application Model)은 서버리스 애플리케이션을 구축, 테스트 및 배포하는 데 도움이 되는 프레임워크입니다. 클라우드 포메이션을 사용하므로 클라우드 포메이션 템플릿을 생성, 업데이트 및 배포하는 프로세스를 단순화할 수 있습니다. CodeDeploy는 사내 인스턴스 및 람다 함수를 포함하여 모든 인스턴스에 대한 코드 배포를 자동화하는 서비스입니다. AWS SAM을 사용하면 내장된 CodeDeploy를 사용하여 새 버전의 Lambda 함수를 배포하고, 트래픽을 점차 새 버전으로 이동하며, 사전 트래픽 및 사후 트래픽 테스트 기능을 사용하여 코드를 확인할 수 있습니다. 또한 CloudWatch 경보를 정의하여 문제가 발생할 경우 롤백을 트리거할 수 있습니다. 이를 통해 배포 프로세스를 보다 빠르고 효율적으로 수행할 수 있을 뿐만 아니라 오류가 식별될 때 보다 안정적인 롤백 프로세스를 수행할 수 있습니다. 이렇게 하면 배포 속도를 높이고 오류가 식별될 때 검색하고 복구하는 시간을 줄일 수 있습니다.


</div>
</details>

<br>

## Prob. 20 ❌
---

A company is planning to store a large number of archived documents and make the documents available to employees through the corporate intranet. Employees will access the system by connecting through a client VPN service that is attached to a VPC. The data must not be accessible to the public.
The documents that the company is storing are copies of data that is held on physical media elsewhere. The number of requests will be low. Availability and speed of retrieval are not concerns of the company.
Which solution will meet these requirements at the LOWEST cost?

A. Create an Amazon S3 bucket. Configure the S3 bucket to use the S3 One Zone-Infrequent Access (S3 One Zone-IA) storage class as default. Configure the S3 bucket for website hosting. Create an S3 interface endpoint. Configure the S3 bucket to allow access only through that endpoint.

B. Launch an Amazon EC2 instance that runs a web server. Attach an Amazon Elastic File System (Amazon EFS) file system to store the archived data in the EFS One Zone-Infrequent Access (EFS One Zone-IA) storage class Configure the instance security groups to allow access only from private networks.

C. Launch an Amazon EC2 instance that runs a web server Attach an Amazon Elastic Block Store (Amazon EBS) volume to store the archived data. Use the Cold HDD (sc1) volume type. Configure the instance security groups to allow access only from private networks.

D. Create an Amazon S3 bucket. Configure the S3 bucket to use the S3 Glacier Deep Archive storage class as default. Configure the S3 bucket for website hosting. Create an S3 interface endpoint. Configure the S3 bucket to allow access only through that endpoint.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

1차 시도 : D <br>

해설 : 

A와 D를 고민을 많이 했지만, 답은 A가 맞는 것 같다.

일단 AWS에서 Glacier를 아무리 조회 빈도가 낮다지만 조회를 위한 서비스에 권장하지는 않을 것 같고,<br>
Glacier의 경우 web hosting이 불가하다는 글이 있다.

</div>
</details>

<br>


<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/3/)

