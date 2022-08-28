---
layout: post
title: "[AWS-SAP] ExamTopics 21~30"
subtitle: AWS
date: '2022-08-27 2:40:00 +0900'
category: study
tags: aws examtopics sap-c01
image:
  path: /assets/img/study_AWS/2022-08-27-[AWS-SAP]_ExamTopics_21~30/logo.png
---

SAP Examtopics 21~30번 문제를 풀어보자.<br>
1차 3/8<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 21 ❌ SKIP
---

다음은 AWS 스토리지 서비스입니까? (두 개를 선택하십시오.)

A. AWS Relational Database Service (AWS RDS)

B. AWS ElastiCache

C. AWS Glacier

D. AWS Import/Export

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
The following are AWS Storage services? (Choose two.)

A. AWS Relational Database Service (AWS RDS)

B. AWS ElastiCache

C. AWS Glacier

D. AWS Import/Export
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, D

해설 : 

문제를 잘못 읽었다.
스토리지 서비스는 C와 D이다.

1차 시도 : A, B <br>
</div>
</details>

<br>
 
## Prob. 22 ⭕ SKIP
---

AWS는 전통적인 IT 컴퓨팅 환경의 다른 벤더와 어떻게 쉽게 구별됩니까?

A. Experienced. Scalable and elastic. Secure. Cost-effective. Reliable

B. Secure. Flexible. Cost-effective. Scalable and elastic. Global

C. Secure. Flexible. Cost-effective. Scalable and elastic. Experienced

D. Flexible. Cost-effective. Dynamic. Secure. Experienced.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
How is AWS readily distinguished from other vendors in the traditional IT computing landscape?

A. Experienced. Scalable and elastic. Secure. Cost-effective. Reliable

B. Secure. Flexible. Cost-effective. Scalable and elastic. Global

C. Secure. Flexible. Cost-effective. Scalable and elastic. Experienced

D. Flexible. Cost-effective. Dynamic. Secure. Experienced.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

뭐 이런 문제가 다 있나 싶다 ...

1차 시도 : B 맞음<br>
</div>
</details>

<br>


## Prob. 23 ⭕
---

500GB EBS Provisioned IOPS 볼륨 4개가 연결된 EC2 인스턴스를 시작했습니다. EC2 인스턴스는 EBS 최적화이며 EC2와 EBS 사이의 500Mbps 처리량을 지원합니다. 4개의 EBS 볼륨이 단일 RAID 0 장치로 구성되며, 각 프로비저닝된 IOPS 볼륨은 4,000 IOPS(4,000 16KB 읽기 또는 쓰기)로 프로비저닝되어 인스턴스에서 총 16,000개의 랜덤 IOPS를 제공합니다. EC2 인스턴스는 처음에 예상된 16,000 IOPS 랜덤 읽기 및 쓰기 성능을 제공합니다. 잠시 후 인스턴스의 총 랜덤 I/O 성능을 높이기 위해 500GB EBS Provisioned IOPS 볼륨 2개를 RAID에 추가합니다. 각 볼륨은 원래 4개의 IOP와 같이 4,000개의 IOPS로 프로비저닝되어 EC2 인스턴스에서 총 24,000개의 IOPS가 제공됩니다. 모니터링 결과 EC2 인스턴스 CPU 활용률은 50%에서 70%로 증가했지만 인스턴스 수준에서 측정된 총 랜덤 IOPS는 전혀 증가하지 않습니다.

무엇이 문제이고 유효한 해결책입니까?

A. EBS 최적화 처리량은 사용할 수 있는 총 IOPS를 제한합니다. 더 큰 처리량을 제공하는 EBS 최적화 인스턴스를 사용하십시오.

B. 블록 크기가 작으면 성능이 저하되어 I/O 처리량이 제한됩니다. 64KB 블록을 사용하여 처리량을 늘리도록 인스턴스 장치 드라이버 및 파일 시스템을 구성합니다.

C. 표준 EBS 인스턴스 루트 볼륨은 총 IOPS 속도를 제한합니다. 인스턴스 루트 볼륨도 500GB 4,000 프로비저닝된 IOPS 볼륨으로 변경합니다.

D. 더 큰 스토리지 볼륨은 더 높은 프로비저닝 IOPS 속도를 지원합니다. 6개의 EBS 볼륨 각각에 대한 프로비저닝된 볼륨 스토리지를 1TB로 늘립니다.

E. RAID 0은 약 4개의 디바이스로만 선형적으로 확장됩니다. RAID 0은 4개의 EBS Provisioning IOPS 볼륨과 함께 사용되지만 각 Provisioning IOPS EBS 볼륨은 6,000 IOPS로 증가합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You have launched an EC2 instance with four (4) 500 GB EBS Provisioned IOPS volumes attached. The EC2 instance is EBS-Optimized and supports 500 Mbps throughput between EC2 and EBS. The four EBS volumes are configured as a single RAID 0 device, and each Provisioned IOPS volume is provisioned with 4,000 IOPS (4,000 16KB reads or writes), for a total of 16,000 random IOPS on the instance. The EC2 instance initially delivers the expected 16,000 IOPS random read and write performance. Sometime later, in order to increase the total random I/O performance of the instance, you add an additional two 500 GB EBS Provisioned IOPS volumes to the RAID. Each volume is provisioned to 4,000 IOPs like the original four, for a total of 24,000 IOPS on the EC2 instance. Monitoring shows that the EC2 instance CPU utilization increased from 50% to 70%, but the total random IOPS measured at the instance level does not increase at all.

What is the problem and a valid solution?

A. The EBS-Optimized throughput limits the total IOPS that can be utilized; use an EBSOptimized instance that provides larger throughput.

B. Small block sizes cause performance degradation, limiting the I/O throughput; configure the instance device driver and filesystem to use 64KB blocks to increase throughput.

C. The standard EBS Instance root volume limits the total IOPS rate; change the instance root volume to also be a 500GB 4,000 Provisioned IOPS volume.

D. Larger storage volumes support higher Provisioned IOPS rates; increase the provisioned volume storage of each of the 6 EBS volumes to 1TB.

E. RAID 0 only scales linearly to about 4 devices; use RAID 0 with 4 EBS Provisioned IOPS volumes, but increase each Provisioned IOPS EBS volume to 6,000 IOPS.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

I think the key here is 16,000 IOPS was working fine, then when adding more disks (IOPS) it didnt go any higher. As noted at the [link](https://aws.amazon.com/ebs/volume-types/) GP2 and GP3 max out at 16000 IOPS per volume. To go beyond this (64000 IOPS)we need to use IO1/IO2/IO2 Block Express, which should be used with EBS optimised instances [link2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-optimized.html). Therefore the instance is our bottleneck, and should be changed (Answer A).

1차 시도 : A 맞음<br>
</div>
</details>

<br>

## Prob. 24 ❌
---

귀사는 전송 중 및 유휴 상태에서 암호화해야 하는 수천 개의 100GB 파일에 걸쳐 수백만 개의 중요한 트랜잭션을 저장하고 있습니다. 분석가는 동시에 최대 5TB의 공간을 사용할 수 있는 파일의 하위 집합에 의존하여 비즈니스 의사 결정을 내리는 데 사용할 수 있는 시뮬레이션을 생성합니다.
데이터의 장기 스토리지 및 실행 중인 하위 집합을 비용 효율적으로 수용할 수 있는 AWS 솔루션을 설계해야 합니다.

어떤 접근 방식이 이러한 목표를 충족시킬 수 있습니까?

A. 서버 측 암호화와 함께 Amazon Simple Storage Service(S3)를 사용하고 Amazon EC2에서 사용 후 삭제 드라이브의 하위 집합에 대해 시뮬레이션을 실행합니다.

B. 서버 측 암호화와 함께 Amazon S3를 사용하고 Amazon EC2의 메모리 내 하위 집합에 대해 시뮬레이션을 실행합니다.

C. Amazon EMR에서 HDFS를 사용하고 Amazon EC2에서 사용 후 삭제 드라이브의 하위 집합에 대해 시뮬레이션을 실행합니다.

D. Amazon Elastic MapReduce(EMR)에서 HDFS를 사용하고 Amazon Elastic Compute Cloud(EC2)의 메모리 내 하위 집합에서 시뮬레이션을 실행합니다.

E. 전체 데이터 세트를 암호화된 EBS(Amazon Elastic Block Store) 볼륨에 저장하고 EC2 워크스테이션에 복제할 수 있는 스냅샷을 정기적으로 캡처합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Your company is storing millions of sensitive transactions across thousands of 100-GB files that must be encrypted in transit and at rest. Analysts concurrently depend on subsets of files, which can consume up to 5 TB of space, to generate simulations that can be used to steer business decisions.
You are required to design an AWS solution that can cost effectively accommodate the long-term storage and in-flight subsets of data.

Which approach can satisfy these objectives?

A. Use Amazon Simple Storage Service (S3) with server-side encryption, and run simulations on subsets in ephemeral drives on Amazon EC2.

B. Use Amazon S3 with server-side encryption, and run simulations on subsets in-memory on Amazon EC2.

C. Use HDFS on Amazon EMR, and run simulations on subsets in ephemeral drives on Amazon EC2.

D. Use HDFS on Amazon Elastic MapReduce (EMR), and run simulations on subsets in-memory on Amazon Elastic Compute Cloud (EC2).

E. Store the full data set in encrypted Amazon Elastic Block Store (EBS) volumes, and regularly capture snapshots that can be cloned to EC2 workstations.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

EMR을 사용한 HDFS는 긴 기간 사용하기에는 적절하지 않다.<br>
S3가 EMR에 비해 비용효율적이다.

B가 안되는 이유는 데이터 크기가 5TB이기 때문이라는데 ... 잘 모르겠다.

encryption at rest - with S3 server side encryption.<br>
encryption in transit - between S3 & EC2 encrypted with HTTPS; between EC2 and instance store also encrypted.

1차 시도 : D 틀림<br>
</div>
</details>

<br>

## Prob. 25 ⭕
---

고객은 로그 스트림(액세스 로그, 애플리케이션 로그, 보안 로그 등)을 단일 시스템에 통합할 의사가 있습니다. 통합되면 고객은 이러한 로그를 휴리스틱을 기반으로 실시간으로 분석하고자 합니다. 때때로 고객은 지난 12시간 동안 추출한 데이터 샘플로 돌아가야 하는 휴리스틱을 검증해야 합니다.

고객의 요구사항을 충족하는 가장 좋은 방법은 무엇입니까?

A. 모든 로그 이벤트를 Amazon SQS로 보내고 로그를 사용하고 휴리스틱을 적용할 EC2 서버의 자동 스케일링 그룹을 설정합니다.

B. 모든 로그 이벤트를 Amazon Kinesis로 보내고 로그에 휴리스틱을 적용할 클라이언트 프로세스를 개발합니다.

C. 사용자 지정 로그를 수신하도록 Amazon CloudTrail을 구성하고 EMR을 사용하여 휴리스틱 로그를 적용합니다.

D. EC2 syslogd 서버의 자동 확장 그룹을 설정하고, 로그를 S3에 저장하고, EMR을 사용하여 로그에 휴리스틱을 적용합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Your customer is willing to consolidate their log streams (access logs, application logs, security logs, etc.) in one single system. Once consolidated, the customer wants to analyze these logs in real time based on heuristics. From time to time, the customer needs to validate heuristics, which requires going back to data samples extracted from the last 12 hours.

What is the best approach to meet your customer's requirements?

A. Send all the log events to Amazon SQS, setup an Auto Scaling group of EC2 servers to consume the logs and apply the heuristics.

B. Send all the log events to Amazon Kinesis, develop a client process to apply heuristics on the logs.

C. Configure Amazon CloudTrail to receive custom logs, use EMR to apply heuristics the logs.

D. Setup an Auto Scaling group of EC2 syslogd servers, store the logs on S3, use EMR to apply heuristics on the logs.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

C is for API calls,

ec2 doesn't make any sense<br>
most effective is Kinesis B

1차 시도 : B 맞음<br>
</div>
</details>

<br>

## Prob. 26 ❌
---

한 신문사는 자체 애플리케이션을 통해 대중이 자신의 백 카탈로그를 검색하고 자바 언어로 작성된 웹 사이트를 통해 개별 신문 페이지를 검색할 수 있도록 합니다. 그들은 오래된 신문을 JPEG(약 17TB)로 스캔했고 OCR(광학 문자 인식)을 사용하여 상용 검색 제품을 채웠습니다. 호스팅 플랫폼과 소프트웨어는 이제 수명이 다했으며 조직은 아카이브를 AWS로 마이그레이션하여 비용 효율적인 아키텍처를 구축하면서도 가용성과 내구성을 유지하도록 설계하기를 원합니다.

어떤 것이 가장 적절한가요?

A. reduced redundancy S3를 사용하여 검색된 파일을 저장하고 제공하고, EC2 인스턴스에 상용 검색 애플리케이션을 설치하고, 자동 확장 및 Elastic Load Balancer로 구성합니다.

B. CloudFormation을 사용하여 환경을 모델링합니다. Apache 웹 서버와 오픈 소스 검색 응용 프로그램을 실행하는 EC2 인스턴스를 사용하여 여러 표준 EBS 볼륨을 스트라이핑하여 JPEG와 검색 색인을 저장합니다.

C. 표준 이중화를 사용하여 검색된 파일을 저장하고 서비스하고, 쿼리 처리를 위해 클라우드 검색을 사용하고, 여러 가용성 영역에서 웹 사이트를 호스팅하는 데 Elastic Beanstalk를 사용합니다.

D. 단일 AZ RDS MySQL 인스턴스를 사용하여 검색 인덱스 33d를 저장합니다. JPEG 이미지는 EC2 인스턴스를 사용하여 웹 사이트를 서비스하고 사용자 쿼리를 SQL로 변환합니다.

E. CloudFront 다운로드 배포를 사용하여 최종 사용자에게 JPEG를 제공하고 현재 상용 검색 제품을 Java Container와 함께 설치하거나 EC2 인스턴스에 웹 사이트를 설치하고 DNS 라운드 로빈과 함께 Route53을 사용합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A newspaper organization has an on-premises application which allows the public to search its back catalogue and retrieve individual newspaper pages via a website written in Java. They have scanned the old newspapers into JPEGs (approx 17TB) and used Optical Character Recognition (OCR) to populate a commercial search product. The hosting platform and software are now end of life and the organization wants to migrate its archive to AWS and produce a cost efficient architecture and still be designed for availability and durability.

Which is the most appropriate?

A. Use S3 with reduced redundancy lo store and serve the scanned files, install the commercial search application on EC2 Instances and configure with auto- scaling and an Elastic Load Balancer.

B. Model the environment using CloudFormation use an EC2 instance running Apache webserver and an open source search application, stripe multiple standard EBS volumes together to store the JPEGs and search index.

C. Use S3 with standard redundancy to store and serve the scanned files, use CloudSearch for query processing, and use Elastic Beanstalk to host the website across multiple availability zones.

D. Use a single-AZ RDS MySQL instance lo store the search index 33d the JPEG images use an EC2 instance to serve the website and translate user queries into SQL.

E. Use a CloudFront download distribution to serve the JPEGs to the end users and Install the current commercial search product, along with a Java Container Tor the website on EC2 instances and use Route53 with DNS round-robin.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Answer is C<br>
A. Use S3 with RRS: RRS is not high availability<br>
B. An EC2 instance and stripe multiple standard EBS volumes together: Not HA too<br>
D. Use a single-AZ RDS MySQL : Not HA also RDS is not using for store image<br>
E. Use a CloudFront: Missing CloudFront origin. Also using an EC2 will not HA

As S3 to serve the static content. Cloud search is managed service to setup, manage and scale a search solution. Combination of 2 AWS service suffice the purpose.

1차 시도 : E 틀림<br>
</div>
</details>

<br>

## Prob. 27 ❌
---

A사는 글로벌 확장성과 성능을 위해 Amazon CloudFront를 활용하는 복잡한 웹 애플리케이션을 보유하고 있습니다. 시간이 지남에 따라 사용자는 웹 응용 프로그램의 속도가 느려지고 있다고 보고합니다.
이 회사의 운영 팀은 CloudFront 캐시 적중률이 꾸준히 감소하고 있다고 보고합니다. 캐시 메트릭 보고서에 따르면 일부 URL의 쿼리 문자열 순서가 일관되지 않으며 대소문자로 지정되기도 하고 소문자로 지정되기도 합니다.

캐시 적중률을 최대한 빠르게 높이기 위해 솔루션 설계자가 취해야 할 조치는 무엇입니까?

A. Lambda@Edge 함수를 배포하여 이름별로 파라미터를 정렬하고 강제로 소문자로 만듭니다. CloudFront 뷰어 요청 트리거를 선택하여 기능을 호출합니다.

B. 쿼리 문자열 매개 변수를 기반으로 캐시를 사용하지 않도록 CloudFront 배포를 업데이트합니다.

C. 로드 밸런서가 애플리케이션의 내보낸 URL을 후처리하여 URL 문자열을 강제로 소문자로 만들도록 한 후 역방향 프록시를 배포합니다.

D. CloudFront 배포를 업데이트하여 대소문자를 구분하지 않는 쿼리 문자열 처리를 지정합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company has a complex web application that leverages Amazon CloudFront for global scalability and performance. Over time, users report that the web application is slowing down.
The company's operations team reports that the CloudFront cache hit ratio has been dropping steadily. The cache metrics report indicates that query strings on some URLs are inconsistently ordered and are specified sometimes in mixed-case letters and sometimes in lowercase letters.

Which set of actions should the solutions architect take to increase the cache hit ratio as quickly possible?

A. Deploy a Lambda@Edge function to sort parameters by name and force them to be lowercase. Select the CloudFront viewer request trigger to invoke the function.

B. Update the CloudFront distribution to disable caching based on query string parameters.

C. Deploy a reverse proxy after the load balancer to post process the emitted URLs in the application to force the URL strings to be lowercase.

D. Update the CloudFront distribution to specify case-insensitive query string processing.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

A. Before CloudFront serves content from the cache it will trigger any Lambda function associated with the Viewer Request, in which we can normalize parameters.

1차 시도 : C 틀림<br>
</div>
</details>

<br>

## Prob. 28 ❌
---

개발(Dev) 및 테스트 환경을 AWS로 마이그레이션하려고 합니다. 각 환경을 호스팅하기 위해 별도의 AWS 계정을 사용하기로 결정했습니다.
통합 청구서를 사용하여 각 계정 청구서를 마스터 AWS 계정에 연결할 계획입니다. 예산 범위 내에서 유지하려면 마스터 계정의 관리자가 개발 계정과 테스트 계정 모두에서 리소스를 중지, 삭제 및/또는 종료할 수 있는 액세스 권한을 갖도록 하는 방법을 구현하려고 합니다.

이 목표를 달성하는 데 어떤 옵션을 사용할 수 있는지 확인하십시오.

A. 마스터 계정에 전체 관리자 권한을 가진 IAM 사용자를 만듭니다. 개발 및 테스트 계정에 교차 계정 역할을 생성하여 마스터 계정에서 권한을 상속하여 계정의 리소스에 대한 액세스 권한을 부여합니다.

B. 개발 및 테스트 계정에 전체 관리자 권한을 부여하는 IAM 사용자와 교차 계정 역할을 마스터 계정에 만듭니다.

C. 마스터 계정에 IAM 사용자를 만듭니다. 전체 관리자 권한을 가진 개발 및 테스트 계정에서 교차 계정 역할을 생성하고 마스터 계정 액세스 권한을 부여합니다.

D. 통합 청구를 사용하여 계정을 연결합니다. 이렇게 하면 마스터 계정의 IAM 사용자가 개발 및 테스트 계정의 리소스에 액세스할 수 있습니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You are looking to migrate your Development (Dev) and Test environments to AWS. You have decided to use separate AWS accounts to host each environment.
You plan to link each accounts bill to a Master AWS account using Consolidated Billing. To make sure you keep within budget you would like to implement a way for administrators in the Master account to have access to stop, delete and/or terminate resources in both the Dev and Test accounts.

Identify which option will allow you to achieve this goal.

A. Create IAM users in the Master account with full Admin permissions. Create cross-account roles in the Dev and Test accounts that grant the Master account access to the resources in the account by inheriting permissions from the Master account.

B. Create IAM users and a cross-account role in the Master account that grants full Admin permissions to the Dev and Test accounts.

C. Create IAM users in the Master account. Create cross-account roles in the Dev and Test accounts that have full Admin permissions and grant the Master account access.

D. Link the accounts using Consolidated Billing. This will give IAM users in the Master account access to resources in the Dev and Test accounts
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Cross-account-roles가 뭘까...?

1차 시도 : A 틀림<br>
</div>
</details>

<br>

## Prob. 29 ⭕
---

x86이 아닌 하드웨어에 종속되어 있기 때문에 애플리케이션을 온프레미스에서 실행하고 있으며 데이터 백업에 AWS를 사용하려고 합니다. 백업 애플리케이션은 POSIX 호환 블록 기반 스토리지에만 쓸 수 있습니다. 140TB의 데이터를 가지고 있으며 파일 서버에 단일 폴더로 마운트하려고 합니다. 사용자는 백업이 수행되는 동안 이 데이터의 일부에 액세스할 수 있어야 합니다.

이 사용 사례에 가장 적합한 백업 솔루션은 무엇입니까?

A. 스토리지 게이트웨이를 사용하고 게이트웨이 캐시된 볼륨을 사용하도록 구성합니다.

B. S3를 데이터 백업 대상으로 사용하도록 백업 소프트웨어를 구성합니다.

C. Glacier를 데이터 백업 대상으로 사용하도록 백업 소프트웨어를 구성합니다.

D. 스토리지 게이트웨이를 사용하고 게이트웨이 저장 볼륨을 사용하도록 구성합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You're running an application on-premises due to its dependency on non-x86 hardware and want to use AWS for data backup. Your backup application is only able to write to POSIX-compatible block-based storage. You have 140TB of data and would like to mount it as a single folder on your file server. Users must be able to access portions of this data while the backups are taking place.

What backup solution would be most appropriate for this use case?

A. Use Storage Gateway and configure it to use Gateway Cached volumes.

B. Configure your backup software to use S3 as the target for your data backups.

C. Configure your backup software to use Glacier as the target for your data backups.

D. Use Storage Gateway and configure it to use Gateway Stored volumes.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

[Storage Gateway](https://heoj10272.github.io/study/AWS-_Storage_Gateway_%EC%9D%B4%ED%95%B4.html#ii-volume-gatewayiscsi)를 참고하자.

일부 액세스 할 수 있어야 하는 데이터는 로컬에 남겨두고 백업하면 되므로 Cached Volume이 적절할 것이다.

1차 시도 : A 맞음<br>
</div>
</details>

<br>

## Prob. 30 ❌
---

인기 있는 제품에 대한 웹 트래픽을 제공하기 위해 재무 담당 최고 책임자와 IT 책임자가 10개의 m1.large heavy utilization Reserved Instances(RIs)를 구입했으며, 두 개의 가용성 영역에 고르게 분산됩니다. Route 53은 트래픽을 ELB(Elastic Load Balancer)로 전달하는 데 사용됩니다. 몇 달이 지나면 제품의 인기가 더욱 높아지므로 추가 용량이 필요합니다. 결과적으로, 귀사는 2개의 C3.2xlarge medium utilization RIs를 구입합니다. 당신은 두 개의 c3.2xlarge instances를 ELB에 등록하고 m1.large instances의 capacity가 100%이고 c3.2xlarge instances에 사용되지 않은 상당한 용량이 있음을 빠르게 알아냈습니다.

다음 중 가장 비용 효율적이고 EC2 용량을 가장 효과적으로 사용하는 옵션은 무엇입니까?

A. Cloudwatch에 의해 트리거될 때 최대 10개의 주문형 m1.large instances를 추가하도록 자동 확장 그룹 및 ELB를 사용하여 Launch Configuration을 구성합니다. c3.xlarge instances를 종료합니다.

B. 두 개의 c3.2xlarge instances로 ELB를 구성하고 두 개의 추가 c3.xlarge instances로 온디맨드 자동 확장 그룹을 사용합니다.

C. Route 53 지연 시간 기반 라우팅 및 상태 검사를 사용하여 EC2 m1.large instances 및 c3.xlarge instances에 트래픽을 라우팅합니다. ELB를 종료합니다.

D. 각 인스턴스 유형에 대해 별도의 ELB를 사용하고 Route 53 가중 라운드 로빈이 있는 ELB에 부하를 분산합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
To serve Web traffic for a popular product your chief financial officer and IT director have purchased 10 m1.large heavy utilization Reserved Instances (RIs), evenly spread across two availability zones; Route 53 is used to deliver the traffic to an Elastic Load Balancer (ELB). After several months, the product grows even more popular and you need additional capacity. As a result, your company purchases two C3.2xlarge medium utilization Ris. You register the two c3.2xlarge instances with your ELB and quickly find that the m1.large instances are at 100% of capacity and the c3.2xlarge instances have significant capacity that's unused.

Which option is the most cost effective and uses EC2 capacity most effectively?

A. Configure Autoscaling group and Launch Configuration with ELB to add up to 10 more on-demand m1.large instances when triggered by Cloudwatch. Shut off c3.2xlarge instances.

B. Configure ELB with two c3.2xlarge instances and use on-demand Autoscaling group for up to two additional c3.2xlarge instances. Shut off m1.large instances.

C. Route traffic to EC2 m1.large and c3.2xlarge instances directly using Route 53 latency based routing and health checks. Shut off ELB.

D. Use a separate ELB for each instance type and distribute load to ELBs with Route 53 weighted round robin.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

A, B if you have already purchase Reversed Instance (RIs) so if you shutdown either of them, you still lose the cost.

C. It does not work well, as Route53 can't route to EC2 unless it has EIP because its IP will change when rebooted. You will need EIPs for all EC2s. So it is impossible solution.

D make sense, the traffic for each instance was loaded-balance however the improper type between C2 and M1 cause the CPU on M1 meanwhile no load on C2. You need another ELB, one for C2 group and one for M1 group; then route the traffic 80% to C1 and 20% to C1 for example.


1차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional/view/3/)

