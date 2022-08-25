---
layout: post
title: "[AWS-SAP] ExamTopics 391~400 구버전"
subtitle: AWS
date: '2022-08-10 23:00:00 +0900'
category: study
tags: aws examtopics sap-c01
image:
  path: /assets/img/study_AWS/2022-08-10-[AWS-SAP]_ExamTopics_391~400_구버전/logo.png
---

SAP Examtopics 391~400번 문제를 풀어보자.<br>
1차 5/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 391 ❌

AWS 서비스에 액세스하기 위해 현재 회사의 AWS 아키텍처는 각 인스턴스에 저장된 액세스 키와 비밀 액세스 키에 의존합니다. 각 인스턴스의 데이터베이스 인증 정보는 하드 코딩됩니다. SSH 키는 명령줄 원격 액세스를 지원하는 보안 Amazon S3 버킷에 보관됩니다. 조직은 솔루션 설계자에게 운영 복잡성을 늘리지 않고 아키텍처의 보안 상태를 개선하는 업무를 맡겼습니다.

이를 달성하기 위해 솔루션 설계자는 어떤 조치를 취해야 합니까? (3개를 선택합니다.)

A. Use Amazon EC2 instance profiles with an IAM role

B. Use AWS Secrets Manager to store access keys and secret access keys

C. Use AWS Systems Manager Parameter Store to store database credentials

D. Use a secure fleet of Amazon EC2 bastion hosts for remote access

E. Use AWS KMS to store database credentials

F. Use AWS Systems Manager Session Manager for remote access

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C, F

해설 : 

A - roles and instance profiles attached to an instance defining who and what access is a best practice

B - not required if your using SSM session manager so you would not need access keys for instances

C - parameter store can be used to store secrets so we are green better option would be secrets manager which password rotation

D - not wrong but why would you when you can use session manager?

E - just wrong

F - no brainer https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html

A. Use Amazon EC2 instance profiles with an IAM role<br>
C. Use AWS Systems Manager Parameter Store to store database credentials<br>
F. Use AWS Systems Manager Session Manager for remote access<br>

1차 시도 : A, B, E 틀림 <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 392 ⭕

AWS에서 비즈니스는 .NET 3계층 웹 어플리케이션을 운영하고 있습니다. 이 팀은 현재 XL 스토리지에 최적화된 인스턴스를 통해 웹 사이트의 사진 및 비디오 자산을 로컬 인스턴스 스토리지에 저장하고 제공하고 있습니다. 이 기업은 복제 및 인스턴스 장애로 인해 데이터 손실을 경험했습니다. Solutions Architect는 비용 효율적인 아키텍처를 유지하면서 신뢰성을 높이기 위해 이 애플리케이션을 재설계하는 작업을 수행했습니다.

어떤 솔루션이 이러한 기준을 충족시킬까요?

A. Set up a new Amazon EFS share, move all image and video files to this share, and then attach this new drive as a mount point to all existing servers. Create an Elastic Load Balancer with Auto Scaling general purpose instances. Enable Amazon CloudFront to the Elastic Load Balancer. Enable Cost Explorer and use AWS Trusted Advisor checks to continue monitoring the environment for future savings.

B. Implement Auto Scaling with general purpose instance types and an Elastic Load Balancer. Enable an Amazon CloudFront distribution to Amazon S3 and move images and video files to Amazon S3. Reserve general purpose instances to meet base performance requirements. Use Cost Explorer and AWS Trusted Advisor checks to continue monitoring the environment for future savings.

C. Move the entire website to Amazon S3 using the S3 website hosting feature. Remove all the web servers and have Amazon S3 communicate directly with the application servers in Amazon VPC.

D. Use AWS Elastic Beanstalk to deploy the .NET application. Move all images and video files to Amazon EFS. Create an Amazon CloudFront distribution that points to the EFS share. Reserve the m4.4xl instances needed to meet base performance requirements.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

A: EFS is more than 10 times more expensive than S3 although it has better performance. This is where CloudFront comes in to mitigate the performance impact caused by S3.<br>
C: S3 does not suppose server side scripting (.net).<br>
D: Cloudfront origin must be S3 or HTTP based. EFS is not HTTP.
[docs](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)

1차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 393 ❌

AWS IAM에서 다음 사전 설정된 정책 조건 키 중 요청을 수행하는 데 사용된 MFA에서 확인된 보안 자격 증명이 얼마나 최근에 발급되었는지 검사하는 키(초)는 무엇입니까?

A. aws:MultiFactorAuthAge

B. aws:MultiFactorAuthLast

C. aws:MFAAge

D. aws:MultiFactorAuthPrevious

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

[aws:MultiFactorAuthAge docs](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-multifactorauthage)

1차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 394 ⭕

소셜 네트워킹 사이트를 만들고 분산 서비스 거부(DDoS) 공격으로부터 보호하는 방법을 고려하고 있습니다.

다음 중 적절한 완화 전략은 무엇입니까? (3개를 선택합니다.)

A. Add multiple elastic network interfaces (ENIs) to each EC2 instance to increase the network bandwidth.

B. Use dedicated instances to ensure that each instance has the maximum performance possible.

C. Use an Amazon CloudFront distribution for both static and dynamic content.

D. Use an Elastic Load Balancer with auto scaling groups at the web, app and Amazon Relational Database Service (RDS) tiers

E. Add alert Amazon CloudWatch to look for high Network in and CPU utilization.

F. Create processes and capabilities to quickly add and remove rules to the instance OS firewall.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, E, F 

해설 : 

왜 WAF Shield가 옵션으로 없을까? DDos하면 Shield인데...

A, B : 완화 전략에는 도움이 되지 않고, 성능만을 향상시킨다.<br>
D : RDS는 ELB를 지원하지 않는다.

AWS Shield는 ELB와 CloudFront에 디폴트로 적용된다는 말이 있다.

1차 시도 : C, E, F 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 395 ⭕

Amazon ElastiCache에서 적절한 설명을 선택합니다.

A. It makes it easy to set up, manage, and scale a distributed in-memory cache environment in the cloud.

B. It allows you to quickly deploy your cache environment only if you install software.

C. It does not integrate with other Amazon Web Services.

D. It cannot run in the Amazon Virtual Private Cloud (Amazon VPC) environment.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

굉장히 쉬운 문제.<br>
진짜로 Pro시험에 나올까 싶을 정도.


1차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 396 ❌

IAM Secure and Scalable은 고객에게 확장 가능하고 안전한 SaaS를 제공하는 회사입니다. AWS VPC에서 웹 서버와 애플리케이션 서버를 별개의 계층으로 실행하려고 합니다. 기업은 애플리케이션 서버(중간 계층)에 자동 확장 및 로드 밸런서를 구현하여 확장성을 달성하고자 합니다.

다음 중 고객의 요구를 가장 잘 충족하는 선택은 무엇입니까?

A. Since ELB is internet facing, it is recommended to setup HAProxy as the Load balancer within the VPC.

B. Create an Internet facing ELB with VPC and configure all the App servers with it.

C. The user should make ELB with EC2-CLASSIC and enable SSH with it for security.

D. Create an Internal Load balancer with VPC and register all the App servers with it.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

App tier does not needs to be exposed to the internet so it's common to use an internal load balancer for it.

1차 시도 : C 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 397 ❌

한 의료 기업은 AWS 클라우드를 사용하여 애플리케이션을 호스팅하고 있습니다. 그 프로그램은 의약품을 개발하는 것의 영향을 복제합니다.

설정 및 시뮬레이션이라는 두 가지 구성 요소가 응용 프로그램을 구성합니다. 애플리케이션의 구성 부분은 Amazon Elastic Container Service(Amazon ECS) 클러스터 내의 AWS Fargate 컨테이너에서 실행됩니다. 시뮬레이션 구성 요소는 대규모로 병렬화된 Amazon EC2 인스턴스에서 실행됩니다. 시뮬레이션이 중단되면 다시 시작될 수 있습니다.

애플리케이션의 설정 부분은 일정한 로드로 24시간 실행됩니다. 시뮬레이션 부분은 다양한 부하 조건에서 매일 밤 몇 시간 동안 실행됩니다. 이 회사는 시뮬레이션 결과를 Amazon S3에 보관하고 있으며 연구진은 이를 활용할 수 있는 기간이 30일입니다. 회사는 최소 10년 동안 시뮬레이션을 유지해야 하며 5시간 이내에 복구할 수 있어야 합니다.

비용 효율성 측면에서 이러한 기준에 가장 적합한 옵션은 무엇입니까?

A. Purchase an EC2 Instance Savings Plan to cover the usage for the configuration part. Run the simulation part by using EC2 Spot Instances. Create an S3 Lifecycle policy to transition objects that are older than 30 days to S3 Intelligent-Tiering.

B. Purchase an EC2 Instance Savings Plan to cover the usage for the configuration part and the simulation part. Create an S3 Lifecycle policy to transition objects that are older than 30 days to S3 Glacier.

C. Purchase Compute Savings Plans to cover the usage for the configuration part. Run the simulation part by using EC2 Spot Instances. Create an S3 Lifecycle policy to transition objects that are older than 30 days to S3 Glacier.

D. Purchase Compute Savings Plans to cover the usage for the configuration part. Purchase EC2 Reserved Instances for the simulation part. Create an S3 Lifecycle policy to transition objects that are older than 30 days to S3 Glacier Deep Archive.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

A is wrong: "older than 30 days to S3 Intelligent-Tiering."- Good for unpredictable retrieval requirements. Not cost effective.<br>
B is wrong: Savings Plan to cover also for simulation part which can be interrupted and restarted - Not cost effective.<br>
D is wrong: "be able to recover them within five hours". Glacier Deep Archive retrieval time within 12 hours. Does not meet the requirements.<br>

시뮬레이션 파트는 중단되어도 다시 시작할 수 있기 때문에 Savings Plan으로 커버하지 않아도 되고, 같은 이유로 예약 인스턴스보다 싼 스팟 인스턴스를 사용해도 된다.

1차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 398 ⭕

Amazon Web Services(AWS)에서 앱을 운영하는 한 회사가 새로운 서비스형 데이터(SaaS) 제공업체에 가입했습니다. 벤더는 벤더가 AWS에서 호스팅하는 REST API를 통해 데이터를 제공합니다. 공급업체는 API를 위한 다양한 연결 옵션을 제공하며 최적의 연결 방법을 결정하기 위해 회사와 협력하고 있습니다.

이 회사의 AWS(Amazon Web Services) 계정은 AWS 환경 내에서 아웃바운드 인터넷 연결을 허용하지 않습니다. 벤더 서비스는 벤더의 앱과 동일한 영역의 AWS에서 호스팅됩니다.
솔루션 설계자는 회사의 VPC(Virtual Private Cloud) 내에서 API에 액세스할 수 있도록 공급업체의 API에 대한 연결을 통합해야 합니다.

어떤 솔루션이 이러한 기준을 충족시킬까요?

A. Connect to the vendor's public API address for the data service

B. Connect to the vendor by way of a VPC peering connection between the vendor's VPC and the company's VPC

C. Connect to the vendor by way of a VPC endpoint service that uses AWS PrivateLink

D. Connect to a public bastion host that the vendor provides. Tunnel the API traffic

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

C : With AWS PrivateLink, you can create an endpoint within your Amazon Virtual Private Cloud (Amazon VPC) that provides access to SaaS applications over a secure, private connection that eliminates the exposure of private data to the public internet.

[Docs Link](https://aws.amazon.com/blogs/apn/using-aws-privatelink-integrations-to-access-saas-solutions-from-apn-partners/#:~:text=With%20AWS%20PrivateLink%2C%20you%20can,data%20to%20the%20public%20internet.)

주의 : Endpoint 연결은 같은 리전에서만 지원된다.

1차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 399 ❌

Solutions Architect는 회사의 Amazon Redshift 클러스터를 검사하는 임무를 맡았습니다. 이 클러스터는 빠르게 자사 기술의 핵심 요소가 되었고 중요한 비즈니스 프로세스를 지원합니다. Solutions Architect의 역할은 클러스터의 안정성과 가용성을 강화하고 문제가 발생할 경우 4시간 이내에 클러스터를 복원할 수 있는 대안을 제시하는 것입니다.

다음 중 가장 낮은 비용으로 비즈니스 요구사항을 가장 잘 충족하는 솔루션 대안은 무엇입니까?

A. Ensure that the Amazon Redshift cluster has been set up to make use of Auto Scaling groups with the nodes in the cluster spread across multiple Availability Zones.

B. Ensure that the Amazon Redshift cluster creation has been templated using AWS CloudFormation so it can easily be launched in another Availability Zone and data populated from the automated Redshift back-ups stored in Amazon S3.

C. Use Amazon Kinesis Data Firehose to collect the data ahead of ingestion into Amazon Redshift and create clusters using AWS CloudFormation in another region and stream the data to both clusters.

D. Create two identical Amazon Redshift clusters in different regions (one as the primary, one as the secondary). Use Amazon S3 cross-region replication from the primary to secondary region, which triggers an AWS Lambda function to populate the cluster in the secondary region.


<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

I do support answer "B".<br>
The question does not request availability on different AZ.<br>
The solution can tolerate 4 hours RTO. Therefore, CloudFront for Redshift, and backup stored in S3.<br>
[link](https://aws.amazon.com/blogs/big-data/building-multi-az-or-multi-region-amazon-redshift-clusters/)<br>
A: Redshift can not work on Multi AZ!<br>
C: Kinesis not meant for cross region population!<br>
D: is a perfect answer, but not cost effective. More redundant than required!<br>

1차 시도 : D 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 400 ⭕

웹 사이트에서 직원에게 주문형 교육 비디오를 제공하고 있습니다. 매월 고해상도 MP4 형식의 동영상이 업로드됩니다. 직원들은 비디오를 보기 위해 HTTP Live Streaming(HLS) 프로토콜이 필요한 회사에서 제공하는 태블릿을 사용하여 지리적으로 분산되어 있으며 이동 중인 경우가 많습니다. 귀사는 비디오 트랜스코딩에 대한 경험이 부족하므로 컨설턴트를 고용해야 할 수도 있습니다.

고가용성과 비디오 전송 품질을 유지하면서 가장 비용 효율적인 아키텍처를 구축하려면 어떻게 해야 합니까?

A. A video transcoding pipeline running on EC2 using SQS to distribute tasks and Auto Scaling to adjust the number of nodes depending on the length of the queue. EBS volumes to host videos and EBS snapshots to incrementally backup original files after a few days. CloudFront to serve HLS transcoded videos from EC2.

B. Elastic Transcoder to transcode original high-resolution MP4 videos to HLS. EBS volumes to host videos and EBS snapshots to incrementally backup original files after a few days. CloudFront to serve HLS transcoded videos from EC2.

C. Elastic Transcoder to transcode original high-resolution MP4 videos to HLS. S3 to host videos with Lifecycle Management to archive original files to Glacier after a few days. CloudFront to serve HLS transcoded videos from S3.

D. A video transcoding pipeline running on EC2 using SQS to distribute tasks and Auto Scaling to adjust the number of nodes depending on the length of the queue. S3 to host videos with Lifecycle Management to archive all files to Glacier after a few days. CloudFront to serve HLS transcoded videos from Glacier.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C 

해설 : 

Amazon Elastic Transcoder는 파이프라인을 사용하여 트랜스코딩 작업을 관리합니다. <br>
작업을 생성할 때 작업을 제출할 파이프라인을 지정합니다. <br>
파이프라인은 사용자가 지정한 S3 버킷에 밀접하게 연결되어 있습니다.<br>

Glacier 계층에 저장하는 것은 original files 이므로 비용적으로 문제가 없을 것이다.

1차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional/view/40/)

