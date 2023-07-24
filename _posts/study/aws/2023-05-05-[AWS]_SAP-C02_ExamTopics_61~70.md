---
layout: post
title: "[AWS] SAP-C02 ExamTopics 61~70"
subtitle: AWS
date: '2023-05-05 17:00:00 +0900'
category: study
tags: aws sap-c02
image:
  path: /assets/img/study_AWS/2023-05-05-[AWS]_SAP-C02_ExamTopics_61~70/logo.png
---

SAP-C02 기출 61~70번 문제를 풀어보자.<br>
1차 ?/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 61 ❌
---

A finance company hosts a data lake in Amazon S3. The company receives financial data records over SFTP each night from several third parties. The company runs its own SFTP server on an Amazon EC2 instance in a public subnet of a VPC. After the files are uploaded, they are moved to the data lake by a cron job that runs on the same instance. The SFTP server is reachable on DNS sftp.example.com through the use of Amazon Route 53.

What should a solutions architect do to improve the reliability and scalability of the SFTP solution?

A. Move the EC2 instance into an Auto Scaling group. Place the EC2 instance behind an Application Load Balancer (ALB). Update the DNS record sftp.example.com in Route 53 to point to the ALB.

B. Migrate the SFTP server to AWS Transfer for SFTP. Update the DNS record sftp.example.com in Route 53 to point to the server endpoint hostname.

C. Migrate the SFTP server to a file gateway in AWS Storage Gateway. Update the DNS record sftp.example.com in Route 53 to point to the file gateway endpoint.

D. Place the EC2 instance behind a Network Load Balancer (NLB). Update the DNS record sftp.example.com in Route 53 to point to the NLB.
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : C<br>

해설 : 

A=ALB cannot be used with SFTP 

B = Correct 

C=Storage Gateway is not an SFTP Server

D=NLB can be used with SFTP, but EC2 is single
</div>
</details>

<br>

## Prob. 62 ❌
---

A company wants to migrate an application to Amazon EC2 from VMware Infrastructure that runs in an on-premises data center. A solutions architect must preserve the software and configuration settings during the migration.

What should the solutions architect do to meet these requirements?

A. Configure the AWS DataSync agent to start replicating the data store to Amazon FSx for Windows File Server. Use the SMB share to host the VMware data store. Use VM Import/Export to move the VMs to Amazon EC2.

B. Use the VMware vSphere client to export the application as an image in Open Virtualization Format (OVF) format. Create an Amazon S3 bucket to store the image in the destination AWS Region. Create and apply an IAM role for VM Import. Use the AWS CLI to run the EC2 import command.

C. Configure AWS Storage Gateway for files service to export a Common Internet File System (CIFS) share. Create a backup copy to the shared folder. Sign in to the AWS Management Console and create an AMI from the backup copy. Launch an EC2 instance that is based on the AMI.

D. Create a managed-instance activation for a hybrid environment in AWS Systems Manager. Download and install Systems Manager Agent on the on-premises VM. Register the VM with Systems Manager to be a managed instance. Use AWS Backup to create a snapshot of the VM and create an AMI. Launch an EC2 instance that is based on the AMI
<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : C<br>

해설 : 

Use VM Import/Export. B is correct . https://aws.amazon.com/ec2/vm-import/

https://docs.aws.amazon.com/vm-import/latest/userguide/vmimport-image-import.html 

Prerequisites 

Create an Amazon S3 bucket for storing the exported images or choose an existing bucket. <br>
The bucket must be in the Region where you want to import your VMs. <br>
For more information about S3 buckets, see the Amazon Simple Storage Service User Guide.  <br>
Create an IAM role named vmimport. <br>
For more information, see Required service role. <br>
 If you have not already installed the AWS CLI on the computer you'll use to run the import commands, see the AWS Command Line Interface User Guide.
</div>
</details>

<br>

## Prob. 63 ⭕️
---

A video processing company has an application that downloads images from an Amazon S3 bucket, processes the images, stores a transformed image in a second S3 bucket, and updates metadata about the image in an Amazon DynamoDB table. The application is written in Node.js and runs by using an AWS Lambda function. The Lambda function is invoked when a new image is uploaded to Amazon S3.

The application ran without incident for a while. However, the size of the images has grown significantly. The Lambda function is now failing frequently with timeout errors. The function timeout is set to its maximum value. A solutions architect needs to refactor the application’s architecture to prevent invocation failures. The company does not want to manage the underlying infrastructure.

Which combination of steps should the solutions architect take to meet these requirements? (Choose two.)

A. Modify the application deployment by building a Docker image that contains the application code. Publish the image to Amazon Elastic Container Registry (Amazon ECR).

B. Create a new Amazon Elastic Container Service (Amazon ECS) task definition with a compatibility type of AWS Fargate. Configure the task definition to use the new image in Amazon Elastic Container Registry (Amazon ECR). Adjust the Lambda function to invoke an ECS task by using the ECS task definition when a new file arrives in Amazon S3.

C. Create an AWS Step Functions state machine with a Parallel state to invoke the Lambda function. Increase the provisioned concurrency of the Lambda function.

D. Create a new Amazon Elastic Container Service (Amazon ECS) task definition with a compatibility type of Amazon EC2. Configure the task definition to use the new image in Amazon Elastic Container Registry (Amazon ECR). Adjust the Lambda function to invoke an ECS task by using the ECS task definition when a new file arrives in Amazon S3.

E. Modify the application to store images on Amazon Elastic File System (Amazon EFS) and to store metadata on an Amazon RDS DB instance. Adjust the Lambda function to mount the EFS file share.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B

1차 시도 : A, B<br>

해설 : 

A: create Docker image and save it to ECR <br>
B: run this image on Fargate  <br>
No answer should have Lambda the will be time out<br>

Based on Serverless solutions used, need to go with Fargate in combination with either ECS/EC2.<br>
As company does not want to manage infra, we go for because Fargate-ECS combo as Fargate-EC2 needs more maintenance .<br>
That means D is out.<br>
E is obviously out EFS does not contribute to lambda invocation timeouts. <br>
C is wrong because, increased concurrency (more lambda versions) won't solve timeouts. <br>
That leaves A and B as right answers.

</div>
</details>

<br>

## Prob. 64 ❌
---

A company has an organization in AWS Organizations. The company is using AWS Control Tower to deploy a landing zone for the organization. The company wants to implement governance and policy enforcement. The company must implement a policy that will detect Amazon RDS DB instances that are not encrypted at rest in the company’s production OU.

Which solution will meet this requirement?

A. Turn on mandatory guardrails in AWS Control Tower. Apply the mandatory guardrails to the production OU.

B. Enable the appropriate guardrail from the list of strongly recommended guardrails in AWS Control Tower. Apply the guardrail to the production OU.

C. Use AWS Config to create a new mandatory guardrail. Apply the rule to all accounts in the production OU.

D. Create a custom SCP in AWS Control Tower. Apply the SCP to the production OU.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

1차 시도 : A<br>

해설 : 

Mandatory controls are owned by AWS Control Tower, and they apply to every OU on your landing zone. <br>
These controls are applied by default when you set up your landing zone, and they can't be deactivated. <br>
The solution requirement falls under a proactive(Recommended Control). <br>
https://docs.aws.amazon.com/controltower/latest/userguide/rds-rules.html#ct-rds-pr-16-description 
<br>
Optional controls are OU specific.

</div>
</details>

<br>

## Prob. 65 ❌
---

A startup company hosts a fleet of Amazon EC2 instances in private subnets using the latest Amazon Linux 2 AMI. The company’s engineers rely heavily on SSH access to the instances for troubleshooting.

The company’s existing architecture includes the following:

• A VPC with private and public subnets, and a NAT gateway.
• Site-to-Site VPN for connectivity with the on-premises environment.
• EC2 security groups with direct SSH access from the on-premises environment.

The company needs to increase security controls around SSH access and provide auditing of commands run by the engineers.

Which strategy should a solutions architect use?

A. Install and configure EC2 Instance Connect on the fleet of EC2 instances. Remove all security group rules attached to EC2 instances that allow inbound TCP on port 22. Advise the engineers to remotely access the instances by using the EC2 Instance Connect CLI.

B. Update the EC2 security groups to only allow inbound TCP on port 22 to the IP addresses of the engineer’s devices. Install the Amazon CloudWatch agent on all EC2 instances and send operating system audit logs to CloudWatch Logs.

C. Update the EC2 security groups to only allow inbound TCP on port 22 to the IP addresses of the engineer’s devices. Enable AWS Config for EC2 security group resource changes. Enable AWS Firewall Manager and apply a security group policy that automatically remediates changes to rules.

D. Create an IAM role with the AmazonSSMManagedInstanceCore managed policy attached. Attach the IAM role to all the EC2 instances. Remove all security group rules attached to the EC2 instances that allow inbound TCP on port 22. Have the engineers install the AWS Systems Manager Session Manager plugin for their devices and remotely access the instances by using the start-session API call from Systems Manager. 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

1차 시도 : C<br>

해설 : 

A is wrong because Instance connect does not provided auditing<br>
B is wrong because it mentions OS audit logs. we need to audit SSH trafic<br>
C is wrong because we want to audit not remediate as asked in question. config service is to record using predefined rules and remediate as well

D is correct because,<br>
By attaching the AmazonSSMManagedInstanceCore policy to an IAM role, EC2 instances can be controlled and monitored through the Systems Manager service, enabling capabilities such as remote instance management, patching, and compliance reporting. 

</div>
</details>

<br>

## Prob. 66
---

A company that usese AWS Organizations allows developers to experiment on AWS. AS part of the landing zone that the company has deployed, develipers use their company email adderss to request an account. The company
wants to ensure that developers are not launching costly services or running services unnecessarily. The company must give devlopers a fied monthly budget to limit their AWS costs.

A company that users AWS Organizations allows developers to experimnet on AWS. AS part of the landing zone that the company has deployed, develipers use their company email adderess to request an acocount./ The comapny wants to ensure that developers are not launcing costly services or runnign services unnecessarily. The company must give devlopers a fixed montlhhy budget to limit their AWS costs.

A company that uses AWS Organizations allows developers to experiment on AWSW. As part of the landing zone that the company ahs deployed, developers use their company email adderess to request an account. The company wants to ensure that devlopers are not laun ching costly services or running services unnecesarily.

A company that uses AWS Organizations allows developers to experiment on AWS. As part of the landing zone that the company has deployed, developers use their company email address to request an account. The company wants to ensure that developers are not launching costly services or running services unnecessarily. The company must give developers a fixed monthly budget to limit their AWS costs.

Which combination of steps will meet these requirements? (Choose three.)

A. Create an SCP to set a fixed monthly account usage limit. Apply the SCP to the developer accounts.

B. Use AWS Budgets to create a fixed monthly budget for each developer’s account as part of the account creation process.

C. Create an SCP to deny access to costly services and components. Apply the SCP to the developer accounts.

D. Create an IAM policy to deny access to costly services and components. Apply the IAM policy to the developer accounts.

E. Create an AWS Budgets alert action to terminate services when the budgeted amount is reached. Configure the action to terminate all services.

F. Create an AWS Budgets alert action to send an Amazon Simple Notification Service (Amazon SNS) notification when the budgeted amount is reached. Invoke an AWS Lambda function to terminate all services.

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 : <br>

해설 : 

내 생각엔 

</div>
</details>

<br>

## Prob. 67
---

A health insurance company stores 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 : <br>

해설 : 

내 생각엔 

</div>
</details>

<br>

## Prob. 68
---

A health insurance company stores 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 : <br>

해설 : 

내 생각엔 

</div>
</details>

<br>

## Prob. 69
---

A health insurance company stores 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 : <br>

해설 : 

내 생각엔 

</div>
</details>

<br>

## Prob. 70
---

A health insurance company stores 

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

1차 시도 : <br>

해설 : 

내 생각엔 

</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/13/)
