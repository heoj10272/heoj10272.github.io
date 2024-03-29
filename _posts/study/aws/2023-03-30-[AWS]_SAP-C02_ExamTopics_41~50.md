---
layout: post
title: "[AWS] SAP-C02 ExamTopics 41~50"
subtitle: AWS
date: '2023-03-30 21:00:00 +0900'
category: study
tags: aws sap-c02
image:
  path: /assets/img/study_AWS/2023-03-30-[AWS]_SAP-C02_ExamTopics_41~50/logo.png
---

SAP-C02 기출 41~50번 문제를 풀어보자.<br>
1차 4/10<br>
2차 8/10<br>
3차 9/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 41 ⭕️⭕️⭕️
---

A company recently deployed an application on AWS. The application uses Amazon DynamoDB. The company measured the application load and configured the RCUs and WCUs on the DynamoDB table to match the expected peak load. The peak load occurs once a week for a 4-hour period and is double the average load. The application load is close to the average load for the rest of the week. The access pattern includes many more writes to the table than reads of the table.

A solutions architect needs to implement a solution to minimize the cost of the table.

Which solution will meet these requirements?

A. Use AWS Application Auto Scaling to increase capacity during the peak period. Purchase reserved RCUs and WCUs to match the average load.

B. Configure on-demand capacity mode for the table.

C. Configure DynamoDB Accelerator (DAX) in front of the table. Reduce the provisioned read capacity to match the new peak load on the table.

D. Configure DynamoDB Accelerator (DAX) in front of the table. Configure on-demand capacity mode for the table.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

1차 시도 : A <br>
2차 시도 : A <br>
3차 시도 : A <br>

해설 : 

일단 읽기보다 쓰기가 더 많기 때문에, 캐싱을 사용하는 DAX는 답이 될 수 없다.<br>
예측할 수 없는 워크로드에 쓰이는 on demand 보다는 예상 주기와 상승폭이 일정하므로 A, reserved를 고르는 것이 적절하다.

</div>
</details>

<br>

## Prob. 42 ❌⭕️⭕️
---

A solutions architect needs to advise a company on how to migrate its on-premises data processing application to the AWS Cloud. Currently, users upload input files through a web portal. The web server then stores the uploaded files on NAS and messages the processing server over a message queue. Each media file can take up to 1 hour to process. The company has determined that the number of media files awaiting processing is significantly higher during business hours, with the number of files rapidly declining after business hours.

What is the MOST cost-effective migration recommendation?

A. Create a queue using Amazon SQS. Configure the existing web server to publish to the new queue. When there are messages in the queue, invoke an AWS Lambda function to pull requests from the queue and process the files. Store the processed files in an Amazon S3 bucket.

B. Create a queue using Amazon MQ. Configure the existing web server to publish to the new queue. When there are messages in the queue, create a new Amazon EC2 instance to pull requests from the queue and process the files. Store the processed files in Amazon EFS. Shut down the EC2 instance after the task is complete.

C. Create a queue using Amazon MQ. Configure the existing web server to publish to the new queue. When there are messages in the queue, invoke an AWS Lambda function to pull requests from the queue and process the files. Store the processed files in Amazon EFS.

D. Create a queue using Amazon SQS. Configure the existing web server to publish to the new queue. Use Amazon EC2 instances in an EC2 Auto Scaling group to pull requests from the queue and process the files. Scale the EC2 instances based on the SQS queue length. Store the processed files in an Amazon S3 bucket.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

1차 시도 : A <br>
2차 시도 : D <br>
3차 시도 : D <br>

해설 : 

A가 안되는 이유 : 람다는 기본적으로 15분동안의 유지시간을 가지기 때문에, 파일을 업로드하는 시간이 최대 1시간이라고 하였으므로 틀렸다.

</div>
</details>

<br>

## Prob. 43 ⭕️⭕️⭕️
---

A company is using Amazon OpenSearch Service to analyze data. The company loads data into an OpenSearch Service cluster with 10 data nodes from an Amazon S3 bucket that uses S3 Standard storage. The data resides in the cluster for 1 month for read-only analysis. After 1 month, the company deletes the index that contains the data from the cluster. For compliance purposes, the company must retain a copy of all input data.

The company is concerned about ongoing costs and asks a solutions architect to recommend a new solution.

Which solution will meet these requirements MOST cost-effectively?

A. Replace all the data nodes with UltraWarm nodes to handle the expected capacity. Transition the input data from S3 Standard to S3 Glacier Deep Archive when the company loads the data into the cluster.

B. Reduce the number of data nodes in the cluster to 2 Add UltraWarm nodes to handle the expected capacity. Configure the indexes to transition to UltraWarm when OpenSearch Service ingests the data. Transition the input data to S3 Glacier Deep Archive after 1 month by using an S3 Lifecycle policy.

C. Reduce the number of data nodes in the cluster to 2. Add UltraWarm nodes to handle the expected capacity. Configure the indexes to transition to UltraWarm when OpenSearch Service ingests the data. Add cold storage nodes to the cluster Transition the indexes from UltraWarm to cold storage. Delete the input data from the S3 bucket after 1 month by using an S3 Lifecycle policy.

D. Reduce the number of data nodes in the cluster to 2. Add instance-backed data nodes to handle the expected capacity. Transition the input data from S3 Standard to S3 Glacier Deep Archive when the company loads the data into the cluster.
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : B<br>
2차 시도 : B<br>
3차 시도 : B<br>

해설 : 

옵션 B는 요구사항을 충족하는 가장 비용 효율적인 솔루션입니다. 
클러스터의 데이터 노드 수를 줄이고 UltraWarm 노드를 추가하면 OpenSearch 서비스 클러스터를 실행하는 데 드는 지속적인 비용을 절감할 수 있습니다. 
OpenSearch Service가 데이터를 수집할 때 인덱스를 UltraWarm으로 전환하도록 구성하면 비용이 더욱 절감됩니다. 
또한 S3 라이프사이클 정책을 사용하여 1개월 후에 입력 데이터를 S3 Glacier Deep Archive로 전환하면 규정 준수를 위해 입력 데이터를 보관하는 스토리지 비용이 절감됩니다.
</div>
</details>

<br>

## Prob. 44 ❌❌❌
---

A company has 10 accounts that are part of an organization in AWS Organizations. AWS Config is configured in each account. All accounts belong to either the Prod OU or the NonProd OU.

The company has set up an Amazon EventBridge rule in each AWS account to notify an Amazon Simple Notification Service (Amazon SNS) topic when an Amazon EC2 security group inbound rule is created with 0.0.0.0/0 as the source. The company’s security team is subscribed to the SNS topic.

For all accounts in the NonProd OU, the security team needs to remove the ability to create a security group inbound rule that includes 0.0.0.0/0 as the source.

Which solution will meet this requirement with the LEAST operational overhead?

A. Modify the EventBridge rule to invoke an AWS Lambda function to remove the security group inbound rule and to publish to the SNS topic. Deploy the updated rule to the NonProd OU.

B. Add the vpc-sg-open-only-to-authorized-ports AWS Config managed rule to the NonProd OU.

C. Configure an SCP to allow the ec2:AuthorizeSecurityGroupIngress action when the value of the aws:SourceIp condition key is not 0.0.0.0/0. Apply the SCP to the NonProd OU.

D. Configure an SCP to deny the ec2:AuthorizeSecurityGroupIngress action when the value of the aws:SourceIp condition key is 0.0.0.0/0. Apply the SCP to the NonProd OU.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

1차 시도 : D<br>
2차 시도 : D<br>
3차 시도 : B<br>

해설 : 

D라고 생각했는데, AuthorizeSecurityGroupIngress 에는 ip 주소의 인바운드/아웃바운드를 제어하는 옵션이 없다고 한다.

3차 - B라고 생각했는데, 안되는 이유는 모르겠다 ... A는 아무리 봐도 억지같은데 ...

</div>
</details>

<br>

## Prob. 45 ❌⭕️⭕️
---

A company hosts a Git repository in an on-premises data center. The company uses webhooks to invoke functionality that runs in the AWS Cloud. The company hosts the webhook logic on a set of Amazon EC2 instances in an Auto Scaling group that the company set as a target for an Application Load Balancer (ALB). The Git server calls the ALB for the configured webhooks. The company wants to move the solution to a serverless architecture.

Which solution will meet these requirements with the LEAST operational overhead?

A. For each webhook, create and configure an AWS Lambda function URL. Update the Git servers to call the individual Lambda function URLs.

B. Create an Amazon API Gateway HTTP API. Implement each webhook logic in a separate AWS Lambda function. Update the Git servers to call the API Gateway endpoint.

C. Deploy the webhook logic to AWS App Runner. Create an ALB, and set App Runner as the target. Update the Git servers to call the ALB endpoint.

D. Containerize the webhook logic. Create an Amazon Elastic Container Service (Amazon ECS) cluster, and run the webhook logic in AWS Fargate. Create an Amazon API Gateway REST API, and set Fargate as the target. Update the Git servers to call the API Gateway endpoint.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : A<br>
2차 시도 : B<br>
3차 시도 : B<br>

해설 : 

람다 + API 게이트웨이를 활용하면 webhook을 쉽게 구현할 수 있다고 한다.

</div>
</details>

<br>

## Prob. 46 ⭕️❌⭕️
---

A company is planning to migrate 1,000 on-premises servers to AWS. The servers run on several VMware clusters in the company’s data center. As part of the migration plan, the company wants to gather server metrics such as CPU details, RAM usage, operating system information, and running processes. The company then wants to query and analyze the data.

Which solution will meet these requirements?

A. Deploy and configure the AWS Agentless Discovery Connector virtual appliance on the on-premises hosts. Configure Data Exploration in AWS Migration Hub. Use AWS Glue to perform an ETL job against the data. Query the data by using Amazon S3 Select.

B. Export only the VM performance information from the on-premises hosts. Directly import the required data into AWS Migration Hub. Update any missing information in Migration Hub. Query the data by using Amazon QuickSight.

C. Create a script to automatically gather the server information from the on-premises hosts. Use the AWS CLI to run the put-resource-attributes command to store the detailed server data in AWS Migration Hub. Query the data directly in the Migration Hub console.

D. Deploy the AWS Application Discovery Agent to each on-premises server. Configure Data Exploration in AWS Migration Hub. Use Amazon Athena to run predefined queries against the data in Amazon S3.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

1차 시도 : D<br>
2차 시도 : C<br>
3차 시도 : D<br>

해설 : 

1000개의 온프레미스 서버에 각각 Discovery Agent를 배포한다는게 좋지 않은 방법이라고 생각했으나 ... D가 정답이었다.
데이터를 분석하는것도 Athena에 걸맞다.
의심하지 말아야겠다.

A. Agentless는 프로세스를 수집할 수 없다고 한다. CPU/RAM, disk IO 만 읽을 수 있다고 함.

</div>
</details>

<br>

## Prob. 47 ❌⭕️⭕️
---

A company is building a serverless application that runs on an AWS Lambda function that is attached to a VPC. The company needs to integrate the application with a new service from an external provider. The external provider supports only requests that come from public IPv4 addresses that are in an allow list.

The company must provide a single public IP address to the external provider before the application can start using the new service.

Which solution will give the application the ability to access the new service?

A. Deploy a NAT gateway. Associate an Elastic IP address with the NAT gateway. Configure the VPC to use the NAT gateway.

B. Deploy an egress-only internet gateway. Associate an Elastic IP address with the egress-only internet gateway. Configure the elastic network interface on the Lambda function to use the egress-only internet gateway.

C. Deploy an internet gateway. Associate an Elastic IP address with the internet gateway. Configure the Lambda function to use the internet gateway.

D. Deploy an internet gateway. Associate an Elastic IP address with the internet gateway. Configure the default route in the public VPC route table to use the internet gateway.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A 

1차 시도 : D<br>
2차 시도 : A<br>
3차 시도 : A<br>

해설 : 

일단 Internet Gateway는 EIP를 가질 수 없다고 한다.<br>
또한 Engress는 IPv6으로 통신하다고 한다.

"기본적으로 람다 함수는 공용 인터넷에 액세스할 수 있습니다. VPC 중 하나에 액세스할 수 있도록 구성된 경우에는 그렇지 않습니다. 인터넷의 리소스에 계속 액세스해야 하는 경우 NAT 인스턴스 또는 Amazon NAT 게이트웨이를 설정합니다. 또는 VPC 엔드포인트를 사용하여 VPC와 지원되는 AWS 서비스 간의 프라이빗 통신을 지원할 수도 있습니다."


</div>
</details>

<br>

## Prob. 48 ❌⭕️⭕️
---

A solutions architect has developed a web application that uses an Amazon API Gateway Regional endpoint and an AWS Lambda function. The consumers of the web application are all close to the AWS Region where the application will be deployed. The Lambda function only queries an Amazon Aurora MySQL database. The solutions architect has configured the database to have three read replicas.

During testing, the application does not meet performance requirements. Under high load, the application opens a large number of database connections. The solutions architect must improve the application’s performance.

Which actions should the solutions architect take to meet these requirements? (Choose two.)

A. Use the cluster endpoint of the Aurora database.

B. Use RDS Proxy to set up a connection pool to the reader endpoint of the Aurora database.

C. Use the Lambda Provisioned Concurrency feature.

D. Move the code for opening the database connection in the Lambda function outside of the event handler.

E. Change the API Gateway endpoint to an edge-optimized endpoint.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, D

1차 시도 : 모름<br>
2차 시도 : B, D<br>
3차 시도 : B, D<br>

해설 : 

RDS Proxy와 Lambda function을 사용한다.

RDX proxy & connecting outside the handler method is up to 5 times faster than connecting inside.

</div>
</details>

<br>

## Prob. 49 ❌⭕️⭕️
---

A company is planning to host a web application on AWS and wants to load balance the traffic across a group of Amazon EC2 instances. One of the security requirements is to enable end-to-end encryption in transit between the client and the web server.

Which solution will meet this requirement?

A. Place the EC2 instances behind an Application Load Balancer (ALB). Provision an SSL certificate using AWS Certificate Manager (ACM), and associate the SSL certificate with the ALB. Export the SSL certificate and install it on each EC2 instance. Configure the ALB to listen on port 443 and to forward traffic to port 443 on the instances.

B. Associate the EC2 instances with a target group. Provision an SSL certificate using AWS Certificate Manager (ACM). Create an Amazon CloudFront distribution and configure it to use the SSL certificate. Set CloudFront to use the target group as the origin server.

C. Place the EC2 instances behind an Application Load Balancer (ALB) Provision an SSL certificate using AWS Certificate Manager (ACM), and associate the SSL certificate with the ALB. Provision a third-party SSL certificate and install it on each EC2 instance. Configure the ALB to listen on port 443 and to forward traffic to port 443 on the instances.

D. Place the EC2 instances behind a Network Load Balancer (NLB). Provision a third-party SSL certificate and install it on the NLB and on each EC2 instance. Configure the NLB to listen on port 443 and to forward traffic to port 443 on the instances.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : A<br>
2차 시도 : C<br>
3차 시도 : C<br>

해설 : 

[https://repost.aws/knowledge-center/acm-ssl-certificate-ec2-elb](https://repost.aws/knowledge-center/acm-ssl-certificate-ec2-elb)

EC2에는 public certificates를 설치할 수 없다고 한다.<br>
따라서, 써드파티 certificate를 EC2에 설치한다. 그리고 써드파티 certificate를 AWS Certificate Manager를 통해 import 함으로써 로드밸런서와 연결시킨다.

D가 답이라는 의견도 많지만... 일단 C로 한다.
</div>
</details>

<br>

## Prob. 50 ⭕️⭕️⭕️
---

A company wants to migrate its data analytics environment from on premises to AWS. The environment consists of two simple Node.js applications. One of the applications collects sensor data and loads it into a MySQL database. The other application aggregates the data into reports. When the aggregation jobs run, some of the load jobs fail to run correctly.

The company must resolve the data loading issue. The company also needs the migration to occur without interruptions or changes for the company’s customers.

What should a solutions architect do to meet these requirements?

A. Set up an Amazon Aurora MySQL database as a replication target for the on-premises database. Create an Aurora Replica for the Aurora MySQL database, and move the aggregation jobs to run against the Aurora Replica. Set up collection endpoints as AWS Lambda functions behind a Network Load Balancer (NLB), and use Amazon RDS Proxy to write to the Aurora MySQL database. When the databases are synced, disable the replication job and restart the Aurora Replica as the primary instance. Point the collector DNS record to the NLB.

B. Set up an Amazon Aurora MySQL database. Use AWS Database Migration Service (AWS DMS) to perform continuous data replication from the on-premises database to Aurora. Move the aggregation jobs to run against the Aurora MySQL database. Set up collection endpoints behind an Application Load Balancer (ALB) as Amazon EC2 instances in an Auto Scaling group. When the databases are synced, point the collector DNS record to the ALDisable the AWS DMS sync task after the cutover from on premises to AWS.

C. Set up an Amazon Aurora MySQL database. Use AWS Database Migration Service (AWS DMS) to perform continuous data replication from the on-premises database to Aurora. Create an Aurora Replica for the Aurora MySQL database, and move the aggregation jobs to run against the Aurora Replica. Set up collection endpoints as AWS Lambda functions behind an Application Load Balancer (ALB), and use Amazon RDS Proxy to write to the Aurora MySQL database. When the databases are synced, point the collector DNS record to the ALB. Disable the AWS DMS sync task after the cutover from on premises to AWS.

D. Set up an Amazon Aurora MySQL database. Create an Aurora Replica for the Aurora MySQL database, and move the aggregation jobs to run against the Aurora Replica. Set up collection endpoints as an Amazon Kinesis data stream. Use Amazon Kinesis Data Firehose to replicate the data to the Aurora MySQL database. When the databases are synced, disable the replication job and restart the Aurora Replica as the primary instance. Point the collector DNS record to the Kinesis data stream.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : C<br>
2차 시도 : C<br>
3차 시도 : C<br>

해설 : 

마이그레이션을 위해서 AWS Database Migration Service를 이용한다.<br>
그리고 Aggregation은 읽는 작업이므로 Aurora Replica를 생성하여 읽기 작업을 시킨다.


</div>
</details>

<br>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/11/)

