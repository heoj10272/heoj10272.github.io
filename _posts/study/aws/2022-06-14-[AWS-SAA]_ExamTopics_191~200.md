---
layout: post
title: "[AWS-SAA] Examtopics 191~200"
subtitle: AWS
date: '2022-06-14 2:00:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-14-[AWS-SAA]_ExamTopics_191~200/logo.png
---

SAA Examtopics 191~200번 문제를 풀어보자.<br>
1차 5/10<br>
2차 6/10<br>
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 191 ⭕⭕

Amazon EC2에서 비즈니스는 전자 상거래 애플리케이션을 호스팅합니다. 애플리케이션은 실행을 위해 최소 10개의 인스턴스와 최대 250개의 인스턴스가 필요한 상태 비저장 웹 계층으로 구성됩니다. 80%의 경우 프로그램에는 50개의 인스턴스가 필요합니다.

비용을 줄이려면 어떤 솔루션을 채택해야 합니까?

A. 250개 인스턴스를 대상으로 예약 인스턴스를 구입하십시오.

B. 예약 인스턴스를 구입하여 80개의 인스턴스를 포함합니다. 나머지 인스턴스를 포함하려면 스팟 인스턴스를 사용합니다.

C. 40개의 인스턴스를 포함하는 온디맨드 인스턴스를 구입합니다. 나머지 인스턴스를 포함하려면 스팟 인스턴스를 사용합니다.

D. 예약 인스턴스를 구입하여 50개의 인스턴스를 포함합니다. 온디맨드 및 스팟 인스턴스를 사용하여 나머지 인스턴스를 포함합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

D. Reserved instances for the 50 that are up most of the time, Spot fleet (mix of on-demand and spot) for the others

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 192 ❓❌

비즈니스에서 Amazon Aurora 기반 Amazon RDS 데이터베이스 인스턴스를 설치하려고 합니다. 조직에는 90일 백업 보존 정책이 있습니다.

솔루션 아키텍트가 제안해야 하는 솔루션은 무엇입니까?

A. RDS DB 인스턴스를 생성할 때 백업 보존 기간을 90일로 설정하십시오.

B. 수명 주기 정책이 90일 후에 삭제되도록 설정된 사용자 관리 Amazon S3 버킷에 자동 스냅샷을 복사하도록 RDS를 구성합니다.

C. 보존 기간이 90일로 설정된 RDS 데이터베이스의 일일 스냅샷을 수행하는 AWS 백업 계획을 생성합니다. AWS 백업 작업을 생성하여 매일 백업 계획 실행을 예약합니다.

D. Amazon CloudWatch 이벤트와 함께 매일 예약된 이벤트를 사용하여 RDS 자동 스냅샷의 복사본을 만드는 사용자 지정 AWS Lambda 기능을 실행합니다. 90일이 지난 스냅샷을 정리합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

For me answer is C. how can one store RDS automated snapshots to a user-managed S3 bucket as far as I know RDS store manual and automated snapshots in its own managed S3 bucket which cannot be seen so how we can set a lifecycle policy on that. On the other hand we can control how frequently to take backup and how long to retain that backup in the backup plan.


1차 시도 : B 모름<br>
2차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 193 ⭕⭕

솔루션 설계자는 공용 및 사설 서브넷으로 가상 사설 클라우드(VPC)를 구성하고 있습니다. VPC 및 서브넷은 IPv4 CIDR 블록을 사용하여 구성됩니다. 3개의 가용 영역(AZ) 각각에는 하나의 퍼블릭 서브넷과 하나의 프라이빗 서브넷이 있습니다. 인터넷 게이트웨이는 퍼블릭 서브넷을 인터넷에 연결하는 데 사용됩니다. Amazon EC2 인스턴스가 소프트웨어 업그레이드를 받으려면 프라이빗 서브넷이 인터넷에 연결되어 있어야 합니다.

솔루션 설계자는 프라이빗 서브넷이 인터넷에 연결되도록 허용하려면 어떻게 해야 합니까?

A. 각 AZ의 각 공용 서브넷에 대해 하나씩 3개의 NAT 게이트웨이를 생성합니다. 비 VPC 트래픽을 해당 AZ의 NAT 게이트웨이로 전달하는 각 AZ에 대한 전용 경로 테이블을 생성합니다.

B. 각 AZ의 각 프라이빗 서브넷에 대해 하나씩 3개의 NAT 인스턴스를 생성합니다. 비 VPC 트래픽을 해당 AZ의 NAT 인스턴스로 전달하는 각 AZ에 대한 전용 경로 테이블을 생성합니다.

C. 개인 서브넷 중 하나에 두 번째 인터넷 게이트웨이를 만듭니다. 비 VPC 트래픽을 개인 인터넷 게이트웨이로 전달하는 개인 서브넷의 경로 테이블을 업데이트합니다.

D. 공용 서브넷 중 하나에 송신 전용 인터넷 게이트웨이를 만듭니다. 비 VPC 트래픽을 송신 전용 인터넷 게이트웨이로 전달하는 개인 서브넷의 경로 테이블을 업데이트합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

Two things to remember regarding NAT Gateway :<br>
#1) It is always placed in Public Subnet<br>
#2 in the event of AZ failure the NAT gateway becomes unavailable and the resources within other Availability Zones loose internet access. To create a fault-tolerant architecture, make sure that your AWS NAT gateways are deployed in at least two Availability Zones (AZs) OR More...


1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 194 ❌❌

현재 한 기업에서 공급업체별 형식을 사용하여 Amazon S3에 250TB의 백업 데이터를 저장했습니다. 이 회사는 Amazon S3에서 파일을 추출하여 업계 표준 형식으로 변환한 다음 Amazon S3에 다시 업로드하려고 합니다. 회사는 이 세션의 데이터 전송과 관련된 비용을 줄이기를 원합니다.

솔루션 설계자는 이를 달성하기 위해 어떤 조치를 취해야 합니까?

A. 변환 소프트웨어를 Amazon S3 배치 작업으로 설치하여 데이터가 Amazon S3에서 벗어나지 않고 변환되도록 합니다.

B. 변환 소프트웨어를 사내 가상 시스템에 설치합니다. 변환을 수행하고 가상 시스템에서 Amazon S3로 파일을 다시 업로드합니다.

C. AWS Snowball Edge 장치를 사용하여 데이터를 내보내고 변환 소프트웨어를 장치에 설치합니다. 데이터 변환을 수행하고 Snowball Edge 디바이스에서 Amazon S3로 파일을 다시 업로드합니다.

D. Amazon S3와 동일한 영역에서 Amazon EC2 인스턴스를 시작하고 인스턴스에 변환 소프트웨어를 설치합니다. 변환을 수행하고 EC2 인스턴스에서 Amazon S3로 파일을 다시 업로드합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Data is already in S3. Snowball is to transfer data from data center to AWS. Hence B & C are wrong<br>
Lambda doesn't let you install custom software. So batch processing on S3 is not possible.<br>
As question asked to minimize the data transfer cost. D makes sense as you install EC2 in same region as S3


1차 시도 : A 틀림<br>
2차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 195 ❌⭕

비즈니스 애플리케이션은 온프레미스 서버에서 호스팅됩니다. 회사는 스토리지 용량을 빠르게 고갈시키고 있습니다. 프로그램은 블록 및 네트워크 파일 저장소를 모두 사용합니다. 기업은 현재 애플리케이션을 다시 설계할 필요 없이 로컬 캐싱을 가능하게 하는 고성능 솔루션이 필요합니다.

이러한 요구 사항을 충족하기 위해 솔루션 설계자는 어떤 단계를 함께 수행해야 합니까? (2개를 선택하세요.)

A. 온프레미스 서버에 파일 시스템으로 Amazon S3를 마운트합니다.

B. NFS 스토리지를 대체할 AWS Storage Gateway 파일 게이트웨이를 배포합니다.

C. AWS Snowball Edge를 구축하여 사내 서버에 NFS 마운트를 프로비저닝합니다.

D. 블록 스토리지를 교체할 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.

E. Amazon EFS(Elastic Fife System) 볼륨을 배포하고 이를 사내 서버에 마운트합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B, D

해설 : 

for block storage - volume gateway, for NFS - file gateway

Requirements: High Performance with local caching without re-architecting solution

Distractors: A/B/C

A is completely wrong as s3 is a block storage and cannot be mounted as FS
B is probably one of the reasonable solution but it is not better when we have EFS in the options for NFS mount command has an option of fsc – which enables local file caching, without changing NFS cache coherency, and reducing latencies so a distractor

C is a migration service S3 service

D/E
D is the best solution for caching block storage data on prem and also backing up to AWS similarly as mentioned in point B it is the convenient solution for NFS local caching and storage

1차 시도 : A, B 틀림<br>
2차 시도 : B, D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 196 ❓❓

비즈니스는 Application Load Balancer를 통해 라우팅되는 Amazon EC2 인스턴스에서 웹 서비스를 호스팅합니다. 인스턴스는 Amazon EC2 Auto Scaling 그룹을 통해 2개의 가용 영역에 분산됩니다. 기업은 비용을 낮게 유지하면서 필요한 SLA(서비스 수준 계약) 요구 사항을 달성하기 위해 항상 최소 4개의 인스턴스가 필요합니다.

가용 영역에 장애가 발생하는 경우 조직은 어떻게 SLA 준수를 유지할 수 있습니까?

A. 냉각 시간이 짧은 대상 추적 스케일링 정책을 추가합니다.

B. 더 큰 인스턴스 유형을 사용하도록 자동 스케일링 그룹 시작 구성을 변경합니다.

C. 세 개의 가용 영역에서 6대의 서버를 사용하도록 자동 확장 그룹을 변경합니다.

D. 두 개의 가용 영역에서 8개의 서버를 사용하도록 자동 확장 그룹을 변경합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : Discussion 참조

해설 : 

1차 시도 : A 모름<br>
2차 시도 : ? 모름<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 197 ❓⭕

한 회사에서 AWS 클라우드를 사용하여 3계층 전자상거래 애플리케이션을 실행하고 있습니다. 이 회사는 Amazon S3에서 웹사이트를 호스팅하고 이를 판매 API와 결합합니다. API는 ALB(Application Load Balancer)를 통해 연결된 3개의 Amazon EC2 인스턴스에서 회사에서 호스팅합니다. API는 정적 및 동적 프런트 엔드 콘텐츠와 판매 요청을 비동기적으로 실행하는 백엔드 작업자로 구성됩니다.
회사는 신제품 출시를 축하하는 이벤트 기간 동안 판매 요청이 갑자기 급증할 것으로 예상합니다.

솔루션 설계자는 모든 요청의 효과적인 처리를 보장하기 위해 무엇을 처방해야 합니까?

A. 동적 콘텐츠에 대한 Amazon CloudFront 배포를 추가합니다. 트래픽 증가를 처리할 EC2 인스턴스 수를 늘립니다.

B. 정적 콘텐츠에 대한 Amazon CloudFront 배포를 추가합니다. EC2 인스턴스를 자동 확장 그룹에 배치하여 네트워크 트래픽을 기반으로 새 인스턴스를 시작합니다.

C. 동적 콘텐츠에 대한 Amazon CloudFront 배포를 추가합니다. ALB 앞에 Amazon ElastiCache 인스턴스를 추가하여 API가 처리할 트래픽을 줄입니다.

D. 정적 콘텐츠에 대한 Amazon CloudFront 배포를 추가합니다. EC2 인스턴스가 나중에 처리할 수 있도록 웹 사이트에서 요청을 수신하려면 Amazon SQS(Simple Queue Service) 대기열을 추가합니다.


<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

D - CORRECT; although B could work, it does say "abrupt change in sales" so more unpredictable and scaling the EC2 instances in ASG does not help as not only takes time but might also lose the unprocessed data. B would work if they prepare in advance with more instances "pre-warmed" before the sale day but still D is going to solve the unpredictability better.


1차 시도 : B 틀림<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 198 ⭕⭕

Amazon EC2 인스턴스는 애플리케이션을 실행하는 데 사용됩니다. 애플리케이션의 민감한 데이터는 Amazon S3 버킷에 보관됩니다. 버킷은 인터넷 액세스로부터 보호되는 동시에 VPC 내부 서비스에 대한 액세스를 허용해야 합니다.

이를 위해 아카이브 솔루션은 어떤 활동을 수행해야 합니까? (2개를 선택하세요.)

A. Amazon S3에 대한 VPC 끝점을 생성합니다.

B. 버킷에서 서버 액세스 로깅을 사용합니다.

C. 버킷 정책을 적용하여 S3 끝점에 대한 액세스를 제한합니다.

D. 중요한 정보가 있는 버킷에 S3 ACL을 추가합니다.

E. IAM 정책을 사용하는 사용자가 특정 버킷을 사용하도록 제한합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

해설 : 

https://docs.aws.amazon.com/AmazonS3/latest/userguide/example-bucket-policies-vpc-endpoint.html:<br>
"You can use Amazon S3 bucket policies to control access to buckets from specific virtual private cloud (VPC) endpoints, or specific VPCs"

https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html:<br>
"A VPC endpoint enables private connections between your VPC and supported AWS services and VPC endpoint services powered by AWS PrivateLink. AWS PrivateLink is a technology that enables you to privately access services by using private IP addresses. Traffic between your VPC and the other service does not leave the Amazon network."

A and C

1차 시도 : A, C 맞음<br>
2차 시도 : A, C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 199 ⭕⭕

기업의 프로그램은 각각 크기가 약 5MB인 방대한 수의 파일을 생성합니다. Amazon S3는 파일을 저장하는 데 사용됩니다. 회사 정책에 따라 파일은 삭제되기 전에 4년 동안 보관되어야 합니다. 파일에는 복제하기 어려운 중요한 비즈니스 데이터가 포함되어 있기 때문에 즉각적인 액세스는 항상 필수적입니다. 파일은 일반적으로 항목 설정 후 처음 30일 이내에 조회되지만 해당 기간 이후에는 거의 액세스되지 않습니다.

가장 저렴한 스토리지 옵션은 무엇입니까?

A. S3 버킷 라이프사이클 정책을 생성하여 파일을 S3 Standard에서 S3 Glacier로 이동한 후 30일이 경과됩니다. 개체 생성 후 4년 후에 파일을 삭제합니다.

B. S3 Standard에서 S3 OneZone-Infrequent Access(S3 OneZone-IA)로 파일을 이동하려면 S3 버킷 수명 주기 정책을 생성합니다. 개체 생성 후 4년 후에 파일을 삭제합니다.

C. 파일을 S3 Standard에서 S3 Standard-Infrequent Access(S3 Standard-IA)로 이동하려면 S3 버킷 수명 주기 정책을 생성합니다. 개체 생성 후 4년 후에 파일을 삭제합니다.

D. S3 버킷 수명 주기 정책을 생성하여 파일을 개체 생성으로부터 30일 후에 S3 Standard-Infrequent Access(S3 Standard-IA)로 이동합니다. 객체 생성 후 4년 후 S3 Glacier로 파일을 이동합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

the files contain vital business data that is difficult to replicate.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 200 ⭕❌

비즈니스에 미션 크리티컬 데이터가 포함된 버킷이 Amazon S3에 있습니다. 회사는 의도하지 않은 삭제로부터 이 데이터를 보호하기를 원합니다. 데이터는 계속 사용할 수 있어야 하며 사용자는 의도적으로 데이터를 지울 수 있어야 합니다.

솔루션 설계자는 이를 달성하기 위해 어떤 조치를 함께 사용해야 합니까? (2개를 선택하세요.)

A. S3 버킷에서 버전 관리를 사용하도록 설정합니다.

B. S3 버킷에서 MFA 삭제를 활성화합니다.

C. S3 버킷에 버킷 정책을 생성합니다.

D. S3 버킷에서 기본 암호화를 사용합니다.

E. S3 버킷의 개체에 대한 수명 주기 정책을 생성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B

해설 : 

A. Enable versioning on the S3 bucket.<br>
B. Enable MFA Delete on the S3 bucket.

1차 시도 : A, B 맞음<br>
2차 시도 : A, C 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/20)