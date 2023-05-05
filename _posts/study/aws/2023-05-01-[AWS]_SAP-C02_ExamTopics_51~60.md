---
layout: post
title: "[AWS] SAP-C02 ExamTopics 51~60"
subtitle: AWS
date: '2023-05-01 19:00:00 +0900'
category: study
tags: aws sap-c02
image:
  path: /assets/img/study_AWS/2023-05-01-[AWS]_SAP-C02_ExamTopics_51~60/logo.png
---

SAP-C02 기출 51~60번 문제를 풀어보자.<br>
1차 4/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 51 ❌
---

A health insurance company stores personally identifiable information (PII) in an Amazon S3 bucket. The company uses server-side encryption with S3 managed encryption keys (SSE-S3) to encrypt the objects. According to a new requirement, all current and future objects in the S3 bucket must be encrypted by keys that the company’s security team manages. The S3 bucket does not have versioning enabled.

Which solution will meet these requirements?

A. In the S3 bucket properties, change the default encryption to SSE-S3 with a customer managed key. Use the AWS CLI to re-upload all objects in the S3 bucket. Set an S3 bucket policy to deny unencrypted PutObject requests.

B. In the S3 bucket properties, change the default encryption to server-side encryption with AWS KMS managed encryption keys (SSE-KMS). Set an S3 bucket policy to deny unencrypted PutObject requests. Use the AWS CLI to re-upload all objects in the S3 bucket.

C. In the S3 bucket properties, change the default encryption to server-side encryption with AWS KMS managed encryption keys (SSE-KMS). Set an S3 bucket policy to automatically encrypt objects on GetObject and PutObject requests.

D. In the S3 bucket properties, change the default encryption to AES-256 with a customer managed key. Attach a policy to deny unencrypted PutObject requests to any entities that access the S3 bucket. Use the AWS CLI to re-upload all objects in the S3 bucket.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : D <br>

해설 : 

내 생각엔 분명 D 인 것 같은데 ... B라고 한다.

</div>
</details>

<br>

## Prob. 52 ❌
---

A company is running a web application in the AWS Cloud. The application consists of dynamic content that is created on a set of Amazon EC2 instances. The EC2 instances run in an Auto Scaling group that is configured as a target group for an Application Load Balancer (ALB).

The company is using an Amazon CloudFront distribution to distribute the application globally. The CloudFront distribution uses the ALB as an origin. The company uses Amazon Route 53 for DNS and has created an A record of www.example.com for the CloudFront distribution.

A solutions architect must configure the application so that itis highly available and fault tolerant.

Which solution meets these requirements?

A. Provision a full, secondary application deployment in a different AWS Region. Update the Route 53 A record to be a failover record. Add both of the CloudFront distributions as values. Create Route 53 health checks.

B. Provision an ALB, an Auto Scaling group, and EC2 instances in a different AWS Region. Update the CloudFront distribution, and create a second origin for the new ALCreate an origin group for the two origins. Configure one origin as primary and one origin as secondary.

C. Provision an Auto Scaling group and EC2 instances in a different AWS Region. Create a second target for the new Auto Scaling group in the ALB. Set up the failover routing algorithm on the ALB.

D. Provision a full, secondary application deployment in a different AWS Region. Create a second CloudFront distribution, and add the new application setup as an origin. Create an AWS Global Accelerator accelerator. Add both of the CloudFront distributions as endpoints.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : A <br>

해설 : 

일단 A인 R53 페일오버 솔루션보단 B가 더 HA인 솔루션이라고 한다.

C에서 ALB는 지역 서비스이기 때문에, ALB도 추가되어야 한다고 한다.



</div>
</details>

<br>

## Prob. 53 ❌
---

A company has an organization in AWS Organizations that has a large number of AWS accounts. One of the AWS accounts is designated as a transit account and has a transit gateway that is shared with all of the other AWS accounts. AWS Site-to-Site VPN connections are configured between all of the company’s global offices and the transit account. The company has AWS Config enabled on all of its accounts.

The company’s networking team needs to centrally manage a list of internal IP address ranges that belong to the global offices. Developers will reference this list to gain access to their applications securely.

Which solution meets these requirements with the LEAST amount of operational overhead?

A. Create a JSON file that is hosted in Amazon S3 and that lists all of the internal IP address ranges. Configure an Amazon Simple Notification Service (Amazon SNS) topic in each of the accounts that can be invoked when the JSON file is updated. Subscribe an AWS Lambda function to the SNS topic to update all relevant security group rules with the updated IP address ranges.

B. Create a new AWS Config managed rule that contains all of the internal IP address ranges. Use the rule to check the security groups in each of the accounts to ensure compliance with the list of IP address ranges. Configure the rule to automatically remediate any noncompliant security group that is detected.

C. In the transit account, create a VPC prefix list with all of the internal IP address ranges. Use AWS Resource Access Manager to share the prefix list with all of the other accounts. Use the shared prefix list to configure security group rules in the other accounts.

D. In the transit account, create a security group with all of the internal IP address ranges. Configure the security groups in the other accounts to reference the transit account’s security group by using a nested security group reference of “/sg-1a2b3c4d”.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : A <br>

해설 : 

prefix list와 RAM을 이용하는것이 정답

</div>
</details>

<br>

## Prob. 54 ⭕️
---

A company runs a new application as a static website in Amazon S3. The company has deployed the application to a production AWS account and uses Amazon CloudFront to deliver the website. The website calls an Amazon API Gateway REST API. An AWS Lambda function backs each API method.

The company wants to create a CSV report every 2 weeks to show each API Lambda function’s recommended configured memory, recommended cost, and the price difference between current configurations and the recommendations. The company will store the reports in an S3 bucket.

Which solution will meet these requirements with the LEAST development time?

A. Create a Lambda function that extracts metrics data for each API Lambda function from Amazon CloudWatch Logs for the 2-week period. Collate the data into tabular format. Store the data as a .csv file in an S3 bucket. Create an Amazon EventBridge rule to schedule the Lambda function to run every 2 weeks.

B. Opt in to AWS Compute Optimizer. Create a Lambda function that calls the ExportLambdaFunctionRecommendations operation. Export the .csv file to an S3 bucket. Create an Amazon EventBridge rule to schedule the Lambda function to run every 2 weeks.

C. Opt in to AWS Compute Optimizer. Set up enhanced infrastructure metrics. Within the Compute Optimizer console, schedule a job to export the Lambda recommendations to a .csv file. Store the file in an S3 bucket every 2 weeks.

D. Purchase the AWS Business Support plan for the production account. Opt in to AWS Compute Optimizer for AWS Trusted Advisor checks. In the Trusted Advisor console, schedule a job to export the cost optimization checks to a .csv file. Store the file in an S3 bucket every 2 weeks.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : B <br>

해설 : 

AWS Compute Optimizer와 Lambda을 사용한다.

그리고 Recommendation을 위해서는 람다를 사용해야한다.

</div>
</details>

<br>

## Prob. 55 ⭕️
---

A company’s factory and automation applications are running in a single VPC. More than 20 applications run on a combination of Amazon EC2, Amazon Elastic Container Service (Amazon ECS), and Amazon RDS.

The company has software engineers spread across three teams. One of the three teams owns each application, and each time is responsible for the cost and performance of all of its applications. Team resources have tags that represent their application and team. The teams use IAM access for daily activities.

The company needs to determine which costs on the monthly AWS bill are attributable to each application or team. The company also must be able to create reports to compare costs from the last 12 months and to help forecast costs for the next 12 months. A solutions architect must recommend an AWS Billing and Cost Management solution that provides these cost reports.

Which combination of actions will meet these requirements? (Choose three.)

A. Activate the user-define cost allocation tags that represent the application and the team.

B. Activate the AWS generated cost allocation tags that represent the application and the team.

C. Create a cost category for each application in Billing and Cost Management.

D. Activate IAM access to Billing and Cost Management.

E. Create a cost budget.

F. Enable Cost Explorer.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 : A, C, F <br>

해설 : 

Enabling Cost Explorer at the management account level enables Cost Explorer for all of your organization accounts. All accounts in the organization are granted access, and you can't grant or deny access individually.

A, F는 답이 확정인데 C냐 D냐에 대해 의견이 분분하다.<br>
일단 나는 C로 ..

</div>
</details>

<br>

## Prob. 56 ⭕️
---

An AWS customer has a web application that runs on premises. The web application fetches data from a third-party API that is behind a firewall. The third party accepts only one public CIDR block in each client’s allow list.

The customer wants to migrate their web application to the AWS Cloud. The application will be hosted on a set of Amazon EC2 instances behind an Application Load Balancer (ALB) in a VPC. The ALB is located in public subnets. The EC2 instances are located in private subnets. NAT gateways provide internet access to the private subnets.

How should a solutions architect ensure that the web application can continue to call the third-party API after the migration?

A. Associate a block of customer-owned public IP addresses to the VPC. Enable public IP addressing for public subnets in the VPC.

B. Register a block of customer-owned public IP addresses in the AWS account. Create Elastic IP addresses from the address block and assign them to the NAT gateways in the VPC.

C. Create Elastic IP addresses from the block of customer-owned IP addresses. Assign the static Elastic IP addresses to the ALB.

D. Register a block of customer-owned public IP addresses in the AWS account. Set up AWS Global Accelerator to use Elastic IP addresses from the address block. Set the ALB as the accelerator endpoint.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : B<br>

해설 : 

중요한건 서드파티에서 허용하는 IP 주소로 접근하는 것이다.<br>
그러므로 customer-owned public IP를 AWS 계정에 등록하고, Elastic IP를 만들어서 NAT Gateway에 등록하면 된다.

</div>
</details>

<br>

## Prob. 57 ⭕️
---

A company with several AWS accounts is using AWS Organizations and service control policies (SCPs). An administrator created the following SCP and has attached it to an organizational unit (OU) that contains AWS account 1111-1111-1111:

![1](/assets/img/study_AWS/2023-05-01-[AWS]_SAP-C02_ExamTopics_51~60/1.png)

Developers working in account 1111-1111-1111 complain that they cannot create Amazon S3 buckets. How should the administrator address this problem?

A. Add s3:CreateBucket with “Allow” effect to the SCP.

B. Remove the account from the OU, and attach the SCP directly to account 1111-1111-1111.

C. Instruct the developers to add Amazon S3 permissions to their IAM entities.

D. Remove the SCP from account 1111-1111-1111.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

1차 시도 : C <br>

해설 : 

SCP는 Permission을 Grant 하지 않는다.<br>
즉, SCP는 허가/비허가를 위한 가드레일/Boundary 같은 역할을 하는 것이지, 실질적인 권한 부여는 IAM 사용자 또는 역할에 대한 정책 부여로 하는 것이다.

즉, SCP로 모든 리소스에 대한 모든 액션을 허가 하였더라도, 이는 권한 부여가 아닌 단순한 허가일 뿐이기 때문에, 위 상황과 같은 경우 S3 Bucket Creation에 대한 권한이 Developer가 속한 IAM에 없기 때문에 발생한 것이다.

</div>
</details>

<br>

## Prob. 58 ❌
---

A company has a monolithic application that is critical to the company’s business. The company hosts the application on an Amazon EC2 instance that runs Amazon Linux 2. The company’s application team receives a directive from the legal department to back up the data from the instance’s encrypted Amazon Elastic Block Store (Amazon EBS) volume to an Amazon S3 bucket. The application team does not have the administrative SSH key pair for the instance. The application must continue to serve the users.

Which solution will meet these requirements?

A. Attach a role to the instance with permission to write to Amazon S3. Use the AWS Systems Manager Session Manager option to gain access to the instance and run commands to copy data into Amazon S3.

B. Create an image of the instance with the reboot option turned on. Launch a new EC2 instance from the image. Attach a role to the new instance with permission to write to Amazon S3. Run a command to copy data into Amazon S3.

C. Take a snapshot of the EBS volume by using Amazon Data Lifecycle Manager (Amazon DLM). Copy the data to Amazon S3.

D. Create an image of the instance. Launch a new EC2 instance from the image. Attach a role to the new instance with permission to write to Amazon S3. Run a command to copy data into Amazon S3.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

1차 시도 : C <br>

해설 : 

`Systems Manager Session Manager` 는 SSH 키 없이 IAM Role 등으로 인스턴스에 접근할 수 있으며, 한 번 접근하면 모든 커맨드를 사용할 수 있다고 한다.<br>
또한 EBS Snapshot, AMI를 생성할 수 있으며, 해당 작업을 할 때 인스턴스를 Shutdown 할 필요도 없다.<br>
따라서 스냅샷을 생성, 커맨드를 통해 S3로 보낼 수 있다.

DLM의 경우 ... 볼륨, 스냅샷을 생성하거나 하는 옵션들은 있지만 S3로 복사하는 옵션은 없다고 한다.<br>
있다는 말도 있는데, 이 경우 아마존이 관리하는 S3로의 전송은 되나 내가 관리할 수 없다고 한다.<br>

그런데 ... Discussion을 보다 보니 DLM이 EBS 볼륨을 다운타임 없이 백업하기 위한 서비스라고 하며, 딱 이런 케이스를 위한 것이라고 하는데 ...<br>
일단 A가 70%, C가 30% 정도의 비율이니 A로 가자.

</div>
</details>

<br>

## Prob. 59 ❌
---

A solutions architect needs to copy data from an Amazon S3 bucket m an AWS account to a new S3 bucket in a new AWS account. The solutions architect must implement a solution that uses the AWS CLI.

Which combination of steps will successfully copy the data? (Choose three.)

A. Create a bucket policy to allow the source bucket to list its contents and to put objects and set object ACLs in the destination bucket. Attach the bucket policy to the destination bucket.

B. Create a bucket policy to allow a user in the destination account to list the source bucket’s contents and read the source bucket’s objects. Attach the bucket policy to the source bucket.

C. Create an IAM policy in the source account. Configure the policy to allow a user in the source account to list contents and get objects in the source bucket, and to list contents, put objects, and set object ACLs in the destination bucket. Attach the policy to the user.

D. Create an IAM policy in the destination account. Configure the policy to allow a user in the destination account to list contents and get objects in the source bucket, and to list contents, put objects, and set objectACLs in the destination bucket. Attach the policy to the user.

E. Run the aws s3 sync command as a user in the source account. Specify the source and destination buckets to copy the data.

F. Run the aws s3 sync command as a user in the destination account. Specify the source and destination buckets to copy the data.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, D, F

1차 시도 : A, B, E <br>

해설 : 

데이터를 쓰는 사람의 관점에서 봐야한다.<br>
즉, 데이터를 쓰는(받아오는) 계정인 destination 계정에서는 source S3 bucket에 대한 접근 가능한 정책이 허용되어야 한다.<br>
다음으로, destination 계정이 source 버킷으로부터 데이터를 가져올 수 있도록 IAM 정책을 구성해야한다.<br>
F도 마찬가지다. 데이터를 쓰는 계정인 destination에서 실행해야한다.

</div>
</details>

<br>

## Prob. 60 ❌
---

A company built an application based on AWS Lambda deployed in an AWS CloudFormation stack. The last production release of the web application introduced an issue that resulted in an outage lasting several minutes. A solutions architect must adjust the deployment process to support a canary release.

Which solution will meet these requirements?

A. Create an alias for every new deployed version of the Lambda function. Use the AWS CLI update-alias command with the routing-config parameter to distribute the load.

B. Deploy the application into a new CloudFormation stack. Use an Amazon Route 53 weighted routing policy to distribute the load.

C. Create a version for every new deployed Lambda function. Use the AWS CLI update-function-configuration command with the routing-config parameter to distribute the load.

D. Configure AWS CodeDeploy and use CodeDeployDefault.OneAtATime in the Deployment configuration to distribute the load.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

1차 시도 : D <br>

해설 : 

aws update-alias command has routing-config option to route the weighted % traffic As is correct
 
https://aws.amazon.com/blogs/compute/implementing-canary-deployments-of-aws-lambda-functions-with-alias-traffic-shifting/ 

Point alias to new version, weighted at 5% (original version at 95% of traffic) aws lambda update-alias --function-name myfunction --name myalias --routing-config '{"AdditionalVersionWeights" : {"2" : 0.05} }'

</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/13/)
