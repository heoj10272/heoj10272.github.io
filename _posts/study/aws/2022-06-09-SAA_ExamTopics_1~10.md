---
layout: post
title: SAA Examtopics 1~10
subtitle: AWS
date: '2022-06-10 3:00:00 +0900'
category: study
tags: aws
image:
  path: /assets/img/study_AWS/SAA_ExamTopics_1~10/logo.png
---

SAA Examtopics 1~10번 문제를 풀어보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 1

한 회사가 새로운 serverless 워크로드를 배치하려고 합니다.
솔루션 아키텍트는 AWS Lambda 함수를 호출하기 위한 권한을 구성해야 합니다.
함수는 Amazon EventBridge (Amazon CloudWatch Events) 규칙에 따라 트리거 될 것입니다.
권한은 최소 권한 원칙을 사용하여 구생되어야 합니다.

어떤 솔루션이 요구사항을 충족합니까?

A. Add an execution role to the function with lambda:InvokeFunction as the action and * as the principal.

B. Add an execution role to the function with lambda:InvokeFunction as the action and Service:amazonaws.com as the principal.

C. Add a resource-based policy to the function with lambda:'* as the action and Service:events.amazonaws.com as the principal.

D. Add a resource-based policy to the function with lambda:InvokeFunction as the action and Service:events.amazonaws.com as the principal.

<br>
<hr/>
<br>

Answer : D

Add a resource-based policy to the function with lambda:InvokeFunction as the action and Service:events.amazonaws.com as the principal.

Amazon EventBridge로 Lambda함수를 호출하려면 아래와 같은 문구가 필요하다.

    "Action": "lambda:InvokeFunction" 
    "Principal": {
      "Service": "events.amazonaws.com"
    }

1차 시도 : 틀림

<br>
<hr/>
<hr/>

## Prob. 2-1

한 회사는 Amazon EBS(Amazon Elastic Block Store)가 지원하는 Amazon EC2 인스턴스에서 애플리케이션을 실행합니다.
인스턴스는 매일 12시간 사용 가능해야합니다.
이 회사는 애플리케이션에 필요한 창 밖으로 인스턴스를 만들어 비용을 절감하고자 합니다. 
그러나 인스턴스를 사용할 수 없을 때마다 메모리의 내용을 보존해야 합니다.

솔루션 아키텍트는 해당 요구사항을 충족시키기 위해서 무엇을 해야합니까?

A. Stop the instance outside the application's availability window. Start up the instance again when required.

B. Hibernate the instance outside the application's availability window. Start up the instance again when required.

C. Use Auto Scaling to scale down the instance outside the application's availability window. Scale up the instance when required.

D. Terminate the instance outside the application's availability window. Launch the instance by using a preconfigured Amazon Machine Image (AMI) when required.

<br>
<hr/>
<br>

Answer : B

최대 절전 모드(Hiberate)를 사용하면 인스턴스의 메모리를 보존한 채로 인스턴스를 중지시킬 수 있다.

또한 인스턴스가 최대 절전 모드일 때는 EBS 볼륨과 Elastic IP 주소에 대한 요금만 지불한다.

1차 시도 : B 맞음

<br>
<hr/>
<hr/>

## Prob. 2-2

한 온라인 사진 공유 회사가 us-west-1 Region에 있는 Amazon S3 버킷에 사진을 저장합니다. 
회사는 기존의 모든 사진과 새로운 사진의 복사본을 다른 지리적 위치에 저장해야 합니다.
운영 노력을 최소화하면서 이 요구 사항을 충족할 수 있는 솔루션은 무엇입니까?

A. Create a second S3 bucket in us-east-1. Enable S3 Cross-Region Replication from the existing S3 bucket to the second S3 bucket.

B. Create a cross-origin resource sharing (CORS) configuration of the existing S3 bucket. Specify us-east-1 in the CORS rule's AllowedOrigin element.

C. Create a second S3 bucket in us-east-1 across multiple Availability Zones. Create an S3 Lifecycle management rule to save photos into the second S3 bucket.

D. Create a second S3 bucket in us-east-1 to store the replicated photos. Configure S3 event notifications on object creation and update events that invoke an AWS Lambda function to copy photos from the existing S3 bucket to the second S3 bucket.

<br>
<hr/>
<br>

Answer : A

엑셀 상에서의 답은 A이지만 이유를 모르겠다.
추후 검토 예정

1차 시도 : D 틀림

<br>
<hr/>
<hr/>

## Prob. 3

회사는 회계 시스템을 온프레미스 데이터 센터에서 Amazon Web Services(AWS) 리전으로 마이그레이션하려고 합니다. 
데이터 보안과 변경 불가능한 감사 로그가 우선되어야 합니다. 
모든 AWS 활동은 규정 준수 감사를 받아야 합니다. 
비즈니스에서 AWS CloudTrail을 활성화했음에도 불구하고 이러한 요구 사항을 충족하는지 확인하려고 합니다.

CloudTrail을 보호하고 보호하기 위해 솔루션 설계자가 포함해야 하는 예방 조치 및 보안 절차는 무엇입니까? (2개 선택)

A. Enable CloudTrail log file validation.

B. Install the CloudTrail Processing Library.

C. Enable logging of Insights events in CloudTrail.

D. Enable custom logging from the on-premises resources.

E. Create an AWS Config rule to monitor whether CloudTrail is configured to use server-side encryption with AWS KMS 

<br>
<hr/>
<br>

Answer : A, E

A<br>
CloudTrail 로그 파일 유효성 검사를 실행한다.

E<br>
다음 보안 모범 사례에서는 CloudTrail의 데이터 보호도 해결한다 :<br>
AWS KMS 관리 키(SSE-KMS)로 CloudTrail 로그 파일 암호화<br>
CloudTrail에 대한 Amazon S3 버킷 정책<br>
CloudTrail 로그 파일 무결성에 대한 유효성 검토<br>
AWS 계정 간에 CloudTrail 로그 파일 공유


1차 시도 : C, E 틀림

<br>
<hr/>
<hr/>

## Prob. 4-1

 한 회사가 최근 의료 영상과 관련된 새로운 서비스를 출시했습니다. 
 회사는 이미지를 스캔하고 Amazon EC2 인스턴스에 대한 AWS Direct Connect 연결을 통해 온프레미스 데이터 센터에서 이미지를 보냅니다. 
 처리가 완료되면 이미지가 Amazon S3 버킷에 저장됩니다. 
 회사 요구 사항에 따르면 EC2 인스턴스는 인터넷을 통해 액세스할 수 없습니다. 
 EC2 인스턴스는 아웃바운드 인터넷 액세스를 위해 온프레미스 데이터 센터로 돌아가는 기본 경로가 있는 프라이빗 서브넷에서 실행됩니다. 
 새로운 서비스의 활용도가 급격히 증가하고 있습니다. 
 솔루션 설계자는 회사의 요구 사항을 충족하고 Direct Connect 요금을 줄이는 솔루션을 추천해야 합니다. 

 어떤 솔루션이 이러한 목표를 가장 비용 효율적으로 달성합니까?

A. Configure a VPC endpoint for Amazon S3. Add an entry to the private subnet's route table for the S3 endpoint.

B. Configure a NAT gateway in a public subnet. Configure the private subnet's route table to use the NAT gateway.

C. Configure Amazon S3 as a file system mount point on the EC2 instances. Access Amazon S3 through the mount.

D. Move the EC2 instances into a public subnet. Configure the public subnet route table to point to an internet gateway.

<br>
<hr/>
<br>

Answer : Discussion에서 A와 B를 두고 대치.


1차 시도 : B와 C 둘 중에 헷갈림.

<br>
<hr/>
<hr/>

## Prob. 4-2

회사는 웹사이트에서 검색 가능한 항목 목록을 유지 관리합니다. 
데이터는 천만 개 이상의 항목이 있는 테이블의 MySQL용 Amazon RDS 데이터베이스에 저장됩니다. 
데이터베이스는 2TB 범용 SSD(gp2) 어레이에 보관됩니다. 
이 회사의 웹사이트는 매일 수백만 건의 데이터 업데이트를 받습니다. 
기업은 일부 작업이 10초 이상 소요된다는 사실을 발견하고 병목 현상이 데이터베이스 스토리지 성능이라고 판단했습니다.

다음 중 성능 요구 사항을 충족하는 옵션은 무엇입니까?

A. Change the storage type to Provisioned IOPS SSD (io1).

B. Change the instance to a memory-optimized instance class.

C. Change the instance to a burstable performance DB instance class.

D. Enable Multi-AZ RDS read replicas with MySQL native asynchronous 
replication.

<br>
<hr/>
<br>

Answer : A

문제상 병목 현상이 발생하는 이유는 스토리지 성능이다.
범용 SSD보다 더 성능이 좋은 프로비전된 IOPS SSD를 사용하면 병목 현상이 해결될 것이다.

1차 시도 : A 맞음

<br>
<hr/>
<hr/>

## Prob. 5

재난 대응 팀이 드론을 사용하여 최근 폭풍 피해의 이미지를 수집하고 있습니다. 
대응팀의 노트북에는 이미지를 전송하고 데이터를 처리할 수 있는 스토리지 및 컴퓨팅 용량이 부족합니다. 
팀에는 처리용 Amazon EC2 인스턴스와 저장용 Amazon S3 버킷이 있지만 네트워크 연결이 간헐적이고 안정적이지 않습니다. 
이미지는 손상을 피할 수 있도록 처리되어야 합니다. 

솔루션 아키텍트는 무엇을 추천해야 합니까?

A. Use AWS Snowball Edge devices to process and store the images.

B. Upload the images to Amazon Simple Queue Service (Amazon SQS) during intermittent connectivity to EC2 instances.

C. Configure Amazon Kinesis Data Firehose to create multiple delivery streams aimed separately at the S3 buckets for storage and the EC2 instances for processing the images.

D. Use AWS Storage Gateway pre-installed on a hardware appliance to cache the images locally for Amazon S3 to process the images when connectivity becomes available.

<br>
<hr/>
<br>

Answer : A

재해 상황이므로 데이터는 한 번 수집후 말 것이기 때문에, Snowball Edge device면 충분하다.<br>
또한 Storage Gateway에는 compute가 없지만 Snowball에는 있다는 말이 있음.

1차 시도 : A 맞음

<br>
<hr/>
<hr/>

## Prob. 6

회사에서 데이터 저장을 위해 Amazon DynamoDB 테이블을 사용할 계획입니다. 
회사는 비용 최적화에 대해 우려하고 있습니다. 이 테이블은 대부분의 아침 저녁에 사용되지 않습니다. 읽기 및 쓰기 트래픽은 종종 예측할 수 없습니다. 
트래픽 스파이크가 발생하면 매우 빠르게 발생합니다.
 
솔루션 아키텍트는 무엇을 추천해야 합니까?

A. Create a DynamoDB table in on-demand capacity mode.

B. Create a DynamoDB table with a global secondary Index.

C. Create a DynamoDB table with provisioned capacity and auto scaling.

D. Create a DynamoDB table in provisioned capacity mode, and configure it as a global table.

<br>
<hr/>
<br>

Answer : 

1차 시도 : 

<br>
<hr/>
<hr/>

## Prob. 

문제

<br>
<hr/>
<br>

Answer : 

1차 시도 : 

<br>
<hr/>
<hr/>

## Prob. 

문제

<br>
<hr/>
<br>

Answer : 

1차 시도 : 

<br>
<hr/>
<hr/>

## Prob. 

문제

<br>
<hr/>
<br>

Answer : 

1차 시도 : 

<br>
<hr/>
<hr/>

## Prob. 

문제

<br>
<hr/>
<br>

Answer : 

1차 시도 : 

<br>
<hr/>
<hr/>

## Prob. 

문제

<br>
<hr/>
<br>

Answer : 

1차 시도 : 

<br>
<hr/>
<hr/>

## Prob. 

문제

<br>
<hr/>
<br>

Answer : 

1차 시도 : 











<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/)
