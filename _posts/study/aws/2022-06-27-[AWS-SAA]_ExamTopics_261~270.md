---
layout: post
title: "[AWS-SAA] Examtopics 261~270"
subtitle: AWS
date: '2022-06-27 16:00:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-27-[AWS-SAA]_ExamTopics_261~270/logo.png
---

SAA Examtopics 261~270번 문제를 풀어보자.<br>
1차 9/10<br>
2차 7/10<br>
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 261 ⭕⭕

비즈니스는 매일 데이터를 처리합니다. 프로세스의 출력은 Amazon S3 버킷에 보관되어 일주일 동안 매일 검사한 다음 임시 검사(adhoc)를 위해 즉시 사용할 수 있어야 합니다.

기존 구성에 대한 가장 비용 효율적인 대안은 무엇입니까?

A. Configure a lifecycle policy to delete the objects after 30 days.

B. Configure a lifecycle policy to transition the objects to Amazon S3 Glacier after 30 days.

C. Configure a lifecycle policy to transition the objects to Amazon S3 Standard-Infrequent Access (S3 Standard-IA) after 30 days.

D. Configure a lifecycle policy to transition the objects to Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA) after 30 days.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C(56%) or D(44%) / 답 D로 확정

해설 : 

Standard iA와 One Zone IA에서 갈림.

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 262 ⭕❌

비즈니스에서 애플리케이션을 개발 중입니다. 이 프로그램은 Amazon API Gateway를 통해 데이터를 수신하고 AWS Lambda 함수를 사용하여 Amazon Aurora PostgreSQL 데이터베이스에 저장합니다.
개념 증명 단계에서 회사는 데이터베이스에 로드해야 하는 많은 양의 데이터를 관리하기 위해 Lambda 할당량을 대폭 늘려야 합니다. 솔루션 설계자는 확장성을 최대화하고 설정 노력을 줄이는 새로운 설계에 대한 권장 사항을 제공해야 합니다.

어떤 솔루션이 이러한 기준을 충족할까요?

A. Refactor the Lambda function code to Apache Tomcat code that runs on Amazon EC2 instances. Connect the database by using native Java Database Connectivity (JDBC) drivers.

B. Change the platform from Aurora to Amazon DynamoDB. Provision a DynamoDB Accelerator (DAX) cluster. Use the DAX client SDK to point the existing DynamoDB API calls at the DAX cluster.

C. Set up two Lambda functions. Configure one function to receive the information. Configure the other function to load the information into the database. Integrate the Lambda functions by using Amazon Simple Notification Service (Amazon SNS).

D. Set up two Lambda functions. Configure one function to receive the information. Configure the other function to load the information into the database. Integrate the Lambda functions by using an Amazon Simple Queue Service (Amazon SQS) queue.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

scalability(확장성) = SQS

1차 시도 : D 맞음<br>
2차 시도 : C 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 263 ⭕⭕

기업에서 온프레미스 MySQL 데이터베이스를 Amazon Web Services(AWS)로 마이그레이션하려고 합니다. 클라이언트 대면 애플리케이션에서 정기적으로 가져오면 데이터베이스에서 엄청난 양의 쓰기 작업이 발생합니다. 조직은 트래픽 양이 애플리케이션의 성능에 영향을 미칠 수 있다고 우려하고 있습니다.

솔루션 설계자는 AWS 아키텍처 설계에 어떻게 접근해야 합니까?

A. Provision an Amazon RDS for MySQL DB instance with Provisioned IOPS SSD storage. Monitor write operation metrics by using Amazon CloudWatch. Adjust the provisioned IOPS if necessary.

B. Provision an Amazon RDS for MySQL DB instance with General Purpose SSD storage. Place an Amazon ElastiCache cluster in front of the DB instance. Configure the application to query ElastiCache instead.

C. Provision an Amazon DocumentDB (with MongoDB compatibility) instance with a memory optimized instance type. Monitor Amazon CloudWatch for performance-related issues. Change the instance class if necessary.

D. Provision an Amazon Elastic File System (Amazon EFS) file system in General Purpose performance mode. Monitor Amazon CloudWatch for IOPS bottlenecks. Change to Provisioned Throughput performance mode if necessary.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

엄청난 양의 처리가 필요하므로 Provisioned IOPS SSD가 가장 적절할것.

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 264 ❌⭕

한 회사에서 AWS를 사용하여 인스턴스 간에 짧은 지연 시간이 필요한 다중 인스턴스 애플리케이션을 만들고 있습니다.

솔루션 설계자는 어떤 권장 사항을 제시해야 합니까?

A. Use an Auto Scaling group with a cluster placement group.

B. Use an Auto Scaling group with single Availability Zone in the same AWS Region.

C. Use an Auto Scaling group with multiple Availability Zones in the same AWS Region.

D. Use a Network Load Balancer with multiple Amazon EC2 Dedicated Hosts as the targets.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

Cluster group은 지연 시간을 줄일 수 있다.

1차 시도 : D 틀림<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 265 ⭕❌

지난 15년 동안 기업은 온프레미스 데이터 센터에서 Oracle 관계형 데이터베이스를 사용하여 웹 애플리케이션을 운영해 왔습니다. 회사의 데이터베이스를 AWS로 마이그레이션해야 합니다. 기업은 애플리케이션의 코드를 수정하지 않고 운영 비용을 절감하기를 원합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. Use AWS Database Migration Service (AWS DMS) to migrate the database servers to Amazon RDS.

B. Use Amazon EC2 instances to migrate and operate the database servers.

C. Use AWS Database Migration Service (AWS DMS) to migrate the database servers to Amazon DynamoDB.

D. Use an AWS Snowball Edge Storage Optimized device to migrate the data from Oracle to Amazon Aurora.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

A. is the answer.<br>
DMS can be used for database migration(supports cross database migration too).<br>
RDS supports MySQL, PostgreSQL, Microsoft SQL Server, Oracle.

B-does not talk about migration

C-Dynamo DB is NoSQL database,complete change of code needed.

D-Snowball is mainly to move data into S3.<br>
Further,Aurora supports only MySQL, PostgreSQL not Oracle.


1차 시도 : A 맞음<br>
2차 시도 : D 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 266 ⭕⭕

개발 팀은 구성 파일에 Amazon RDS MySQL DB 인스턴스의 사용자 이름과 암호를 보관합니다. 구성 파일은 팀의 Amazon EC2 인스턴스 루트 디바이스 디스크에 일반 텍스트로 저장됩니다. 팀의 응용 프로그램이 데이터베이스에 연결해야 하는 경우 파일을 읽고 자격 증명이 코드에 로드됩니다. 팀은 프로그램만 해당 내용에 액세스할 수 있도록 구성 파일의 권한을 조정했습니다. 솔루션 설계자의 주요 책임은 더 나은 보안 시스템을 구축하는 것입니다.

이 요구 사항을 충족하기 위해 솔루션 설계자는 어떤 조치를 취해야 합니까?

A. Store the configuration file in Amazon S3. Grant the application access to read the configuration file.

B. Create an IAM role with permission to access the database. Attach this IAM role to the EC2 instance.

C. Enable SSL connections on the database instance. Alter the database user to require SSL when logging in.

D. Move the configuration file to an EC2 instance store, and create an Amazon Machine Image (AMI) of the instance. Launch new instances from this AMI.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

It should be B. For EC2, IAM role is a secure way to connect RDS.

대체로 이런 문제들은 `IAM Role`이 정답이다.

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 267 ⭕⭕

비즈니스 애플리케이션이 VPC 내부에 포함된 Amazon EC2 인스턴스에서 작동하고 있습니다. 항목을 저장하고 검색하려면 앱 중 하나가 Amazon S3 API에 요청해야 합니다. 회사의 보안 규정은 프로그램이 인터넷에 연결된 트래픽을 보내는 것을 금지합니다.

보안을 유지하면서 이러한 요구를 충족할 조치는 무엇입니까?

A. Configure an S3 interface endpoint.

B. Configure an S3 gateway endpoint.

C. Create an S3 bucket in a private subnet.

D. Create an S3 bucket in the same Region as the EC2 instance.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Use Gateway Endpoint if the AWS service is either DynamoDB or S3.<br>
Use Interface Endpoint for everything else.


1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 268 ⭕⭕

MySQL 데이터베이스는 기업의 주문 이행 서비스에서 사용됩니다. 데이터베이스는 많은 양의 동시 요청 및 트랜잭션을 처리할 수 있어야 합니다. 데이터베이스는 개발자에 의해 패치되고 조정됩니다. 이로 인해 새로운 제품 기능의 도입이 지연됩니다.
조직은 이 새로운 어려움을 해결하는 데 도움이 되도록 클라우드 기반 서비스를 사용하기를 원합니다. 솔루션은 개발자가 코드를 거의 또는 전혀 수정하지 않고 데이터베이스를 이동할 수 있도록 해야 하며 성능을 최대화해야 합니다.

이러한 요구 사항을 달성하려면 어떤 솔루션 설계자 서비스를 사용해야 합니까?

A. Amazon Aurora

B. Amazon DynamoDB

C. Amazon ElastiCache

D. MySQL on Amazon EC2

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

Migrating a MySQL database to a more scalable service such as Amazon Aurora can be done with very little downtime for the application, and using native MySQL backup tools.

Amazon Aurora is fully managed DB and support MySQL database.

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 269 ⭕⭕

기업은 다중 지역 재해 복구를 위해 1초 RPO(복구 시점 목표) 및 1분 RTO(복구 시간 목표)를 사용하여 관계형 데이터베이스를 만들어야 합니다.

어떤 AWS 솔루션이 이 작업을 수행할 수 있습니까?

A. Amazon Aurora Global Database

B. Amazon DynamoDB global tables

C. Amazon RDS for MySQL with Multi-AZ enabled

D. Amazon RDS for MySQL with a cross-Region snapshot copy

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

[Amazon Aurora Global Database](https://heoj10272.github.io/study/Amazon_Aurora_%EC%9D%B4%ED%95%B4.html#4-aurora-global-database) 참조.

        1초의 RPO(Recovery Point Objective, 복구 목표 지점) - 1초 전까지의 데이터는 안전이 보장된다.
        1분 미만의 RTO(Recovery Time Objective, 복구 목표 시간) - 1분 내에 복구가 보장된다.

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 270 ⭕❌

솔루션 설계자는 새로운 정적 웹사이트의 구현을 설계하는 책임을 맡습니다. 솔루션은 비용 효율적이어야 하며 최소 99%의 가용성을 유지해야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. Deploy the application to an Amazon S3 bucket in one AWS Region that has versioning disabled.

B. Deploy the application to Amazon EC2 instances that run in two AWS Regions and two Availability Zones.

C. Deploy the application to an Amazon S3 bucket that has versioning and cross-Region replication enabled.

D. Deploy the application to an Amazon EC2 instance that runs in one AWS Region and one Availability Zone.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

versioning은 recovery를 위한 기능이다.<br>
S3는 단일 리전에 있더라도 99.99%의 가용성을 보장한다.

1차 시도 : A 맞음<br>
2차 시도 : C 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/27)


