---
layout: post
title: "[AWS-SAA] Examtopics 171~180"
subtitle: AWS
date: '2022-06-14 1:40:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-14-[AWS-SAA]_ExamTopics_171~180/logo.png
---

SAA Examtopics 171~180번 문제를 풀어보자.<br>
1차 4/10<br>
2차 8/10<br>
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 171 ❌❌

기업은 여러 AWS 리전에서 ALB(Application Load Balancer)를 활용합니다. ALB는 일년 내내 변동하는 트래픽을 경험합니다. 회사의 네트워킹 담당자는 온프레미스 방화벽을 통해 ALB의 IP 주소를 허용하여 연결을 활성화해야 합니다.

어떤 솔루션이 가장 확장 가능하고 설정 변경이 가장 적게 필요합니까?

A. AWS Lambda 스크립트를 작성하여 서로 다른 영역에 있는 ALB의 IP 주소를 가져옵니다. 사내 방화벽의 규칙을 업데이트하여 ALB의 IP 주소를 허용합니다.

B. 서로 다른 영역의 모든 ALB를 NLB(네트워크 로드 밸런서)로 마이그레이션합니다. 온프레미스 방화벽의 규칙을 업데이트하여 모든 NLB의 Elastic IP 주소를 허용합니다.

C. AWS Global Accelerator를 시작합니다. 서로 다른 영역의 ALB를 액셀러레이터에 등록합니다. 가속기와 연결된 정적 IP 주소를 허용하도록 온프레미스 방화벽의 규칙을 업데이트합니다.

D. 한 리전에서 NLB(네트워크 로드 밸런서)를 시작합니다. 다른 리전에 있는 ALB의 개인 IP 주소를 NLB에 등록합니다. 사내 방화벽의 규칙을 업데이트하여 NLB에 연결된 Elastic IP 주소를 허용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

GA provides static IP which we can bind in the firewall, and GA can be associated with ALB.

1차 시도 : A 틀림<br>
1차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 172 ❌❌

매달 기업은 판매 보고서를 작성해야 합니다. 매월 1일에 보고 절차가 20개의 Amazon EC2 인스턴스를 시작합니다. 절차는 7일 동안 지속되며 일시 중지할 수 없습니다. 회사는 비용을 낮게 유지하기를 원합니다.

기업은 어떤 가격 전략을 추구해야 합니까?

A. Reserved Instances

B. Spot Block Instances

C. On-Demand Instances

D. Scheduled Reserved Instances

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Reserved Instance는 일주일 정도의 짧은 기간에는 맞지 않는 스토리지 클래스이다.

D가 안되는 이유<br>
지금은 Scheduled Reserved Instances를 구입할 수 없습니다. AWS에는 Scheduled Reserved Instances에 사용할 수 있는 용량이 없거나 향후 사용할 계획이 없습니다. 용량을 예약하려면 온디맨드 용량 예약을 대신 사용하십시오. 할인된 요금의 경우 할인 혜택을 이용하십시오.


1차 시도 : A 틀림<br>
2차 시도 : D 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 173 ❌⭕

기업은 모든 모바일 장치에서 사용할 수 있도록 비디오 자료를 업로드하고 트랜스코딩하는 온라인 서비스를 제공합니다. 애플리케이션 설계는 Amazon Elastic File System(Amazon EFS) 표준을 사용하여 수많은 Amazon EC2 Linux 인스턴스에서 처리할 수 있도록 영화를 수집하고 저장합니다. 서비스의 인기가 높아짐에 따라 스토리지 비용이 엄청나게 비쌌습니다.

가장 저렴한 스토리지 옵션은 무엇입니까?

A. AWS Storage Gateway for files를 사용하여 비디오 콘텐츠를 저장하고 처리할 수 있습니다.

B. AWS Storage Gateway for volumes를 사용하여 비디오 콘텐츠를 저장하고 처리합니다.

C. 비디오 콘텐츠를 저장하려면 Amazon EFS(Amazon Elastic File System)를 사용합니다. 처리가 완료되면 Amazon Elastic Block Store(Amazon EBS)로 파일을 전송합니다.

D. 비디오 콘텐츠를 저장하기 위해 Amazon S3를 사용합니다. 처리할 파일을 서버에 연결된 Amazon EBS(Amazon Elastic Block Store) 볼륨으로 임시 이동합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A or D // D
Discussion에서 엄청 갈리는데 마지막 줄이 경험상 가장 중요한 판단 요인이기 때문에, 답을 D로 생각하도록 함.

해설 : 

Discussion 참조

1차 시도 : B 틀림<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 174 ⭕⭕

기업은 매일 단일 공장에 있는 많은 기계에서 10테라바이트의 계측 데이터를 얻습니다. 데이터는 공장 온프레미스 데이터 센터 내부의 SAN(Storage Area Network)에서 JSON 파일로 저장됩니다. 조직은 이 데이터를 Amazon S3에 업로드하여 중요한 거의 실시간 분석을 수행하는 다른 여러 시스템에서 액세스할 수 있도록 하려고 합니다. 데이터는 민감한 것으로 간주되기 때문에 안전한 전송이 중요합니다.

가장 안전한 데이터 전송 방법을 제공하는 옵션은 무엇입니까?

A. AWS DataSync over public internet

B. AWS DataSync over AWS Direct Connect

C. AWS Database Migration Service (AWS DMS) over public internet

D. AWS Database Migration Service (AWS DMS) over AWS Direct Connect

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

1) 이 회사는 이 데이터를 Amazon S3로 전송하여 중요한 실시간에 가까운 분석을 제공하는 여러 추가 시스템을 통해 액세스할 수 있기를 원합니다. -> DataSync는 S3(모든 스토리지 클래스)와 동기화할 수 있습니다.

2) 매일 10TB의 계측 데이터 -> DataSync를 사용하여 시간별, 일별, 주별로 복제 작업을 예약할 수 있습니다.

3) 이것은 데이터베이스 마이그레이션 시나리오가 아닌 이동 데이터 시나리오입니다.


1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 175 ❓⭕

데이터 과학 팀은 야간에 로그를 분석하기 위해 스토리지가 필요합니다. 로그의 양과 수는 불명확하나, 24시간 동안 보관됩니다.

어떤 접근 방식이 가장 비용 효율적입니까?

A. Amazon S3 Glacier

B. Amazon S3 Standard

C. Amazon S3 Intelligent-Tiering

D. Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA)

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : Discussion 참조

해설 : 
C는 최소 지불 단위가 30일이다.<br>
즉, 24시간 동안만 접근되는 데이터에는 맞지 않다.<br>

1차 시도 : C 틀림<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 176 ⭕⭕

개발 팀이 AWS에서 신제품을 출시하고 있으며 출시의 일환으로 AWS Lambda를 사용하고 있습니다. Lambda 함수 중 하나를 위해 팀은 512MB의 RAM을 할당합니다. 이 메모리 할당으로 함수는 2분 안에 완료됩니다. 함수는 월간 수백만 번 실행되고 개발 팀은 비용에 대해 걱정하고 있습니다. 팀은 다양한 Lambda 메모리 할당이 함수 비용에 미치는 영향을 확인하기 위해 실험을 수행합니다.

어떤 조치로 제품의 Lambda 비용이 감소합니까? (2개를 선택하세요.)

A. Increase the memory allocation for this Lambda function to 1,024 MB if this change causes the execution time of each function to be less than 1 minute.

B. Increase the memory allocation for this Lambda function to 1,024 MB if this change causes the execution time of each function to be less than 90 seconds.

C. Reduce the memory allocation for this Lambda function to 256 MB if this change causes the execution time of each function to be less than 4 minutes.

D. Increase the memory allocation for this Lambda function to 2,048 MB if this change causes the execution time of each function to be less than 1 minute.

E. Reduce the memory allocation for this Lambda function to 256 MB if this change causes the execution time of each function to be less than 5 minutes.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

해설 : 

If A is chosen, the memory used is double but the completion time is less than 2 minutes, not 2 minutes.<br>
Answer C is better and more efficient than answer E.

1차 시도 : A, C 맞음<br>
2차 시도 : A, C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 177 ❌⭕

기업은 중앙 집중식 Amazon Web Services 계정을 사용하여 많은 Amazon S3 버킷에 로그 데이터를 저장하고 있습니다. S3 버킷에 데이터를 업로드하기 전에 솔루션 설계자는 데이터가 암호화되어 있는지 확인해야 합니다. 또한 데이터는 전송 중에 암호화되어야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. 클라이언트 측 암호화를 사용하여 S3 버킷에 업로드 중인 데이터를 암호화합니다.

B. 서버측 암호화를 사용하여 S3 버킷에 업로드 중인 데이터를 암호화합니다.

C. S3 업로드용 S3 관리 암호화 키(SSE-S3)를 사용하여 서버 측 암호화를 사용해야 하는 버킷 정책을 생성합니다.

D. 기본 AWS KMS(키 관리 서비스) 키를 사용하여 S3 버킷을 암호화하려면 보안 옵션을 실행하십시오.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

전송 중 보호 = SSL/TLS 또는 클라이언트 측 암호화 데이터를 보호.
AWS Docs에서는 "데이터 보호란 전송 중(Amazon S3로 오가는 동안) 및 유휴 상태(Amazon S3 데이터 센터의 디스크에 저장되는 동안) 데이터를 보호하는 것을 의미합니다. SSL/TLS(Secure Socket Layer/Transport Layer Security) 또는 클라이언트 측 암호화를 사용하여 전송 중인 데이터를 보호할 수 있습니다."

서버측 암호화 – 개체를 데이터 센터의 디스크에 저장하기 전에 암호화한 다음 개체를 다운로드할 때 암호를 해독하도록 Amazon S3에 요청합니다.

클라이언트 측 암호화 – 클라이언트 측 데이터를 암호화하고 암호화된 데이터를 Amazon S3에 업로드합니다. 이 경우 암호화 프로세스, 암호화 키 및 관련 도구를 관리합니다.

정답은 A입니다.

1차 시도 : D 틀림<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 178 ⭕⭕

비즈니스에서는 Microsoft Windows 기반 애플리케이션을 AWS로 마이그레이션해야 합니다. 이 프로그램은 수많은 Amazon EC2 Windows 시스템에 연결된 공유 Windows 파일 시스템을 활용합니다.

솔루션 설계자는 이를 달성하기 위해 어떤 조치를 취해야 합니까?

A. Configure a volume using Amazon Elastic File System (Amazon EFS). Mount the EFS volume to each Windows instance.

B. Configure AWS Storage Gateway in Volume Gateway mode. Mount the volume to each Windows instance.

C. Configure Amazon FSx for Windows File Server. Mount the Amazon FSx volume to each Windows instance.

D. Configure an Amazon Elastic Block Store (Amazon EBS) volume with the required size. Attach each EC2 instance to the volume. Mount the file system within the volume to each Windows instance.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Windows = FSx

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 179 ⭕⭕

IAM 그룹은 다음 IAM 정책과 연결됩니다. 이것이 그 단체의 유일한 방침입니다.

![prob_179](/assets/img/study_AWS/2022-06-14-[AWS-SAA]_ExamTopics_171~180/prob_179.png)

그룹 구성원에 대한 정책의 유효한 IAM 권한은 무엇입니까?

A. Group members are permitted any Amazon EC2 action within the us-east-1 Region. Statements after the Allow permission are not applied.

B. Group members are denied any Amazon EC2 permissions in the us-east-1 Region unless they are logged in with multi-factor authentication (MFA).

C. Group members are allowed the ec2:StopInstances and ec2:TerminateInstances permissions for all Regions when logged in with multi-factor authentication (MFA). Group members are permitted any other Amazon EC2 action.

D. Group members are allowed the ec2:StopInstances and ec2:TerminateInstances permissions for the us-east-1 Region only when logged in with multi-factor authentication (MFA). Group members are permitted any other Amazon EC2 action within the us-east-1 Region.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

이제는 아주 쉬운 문제.

추가) 디폴트로 IAM 사용자는 EC2를 생성하거나 변경할 수 없고, EC2 API를 사용한 태스크를 수행할 수 없다.<br>
이를 허용하기 위해서는 IAM 정책을 만들어서 IAM 사용자에게 권한 부여를 해주어야 한다.

원문)
https://docs.aws.amazon.com/AWSEC2/latest/APIReference/ec2-api-permissions.html<br>
By default, AWS Identity and Access Management (IAM) users don't have permission to create or modify Amazon EC2 resources, or perform tasks using the Amazon EC2 API. To allow IAM users to create or modify resources and perform tasks, you must create IAM policies that grant IAM users permissions for the specific resources and API actions they'll need to use, and then attach those policies to the IAM users or groups that require those permissions.

1st part of policy allows all actions in us-east-1 Region<br>
2nd part deny stop and terminate in all regions for users without MFA

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 180 ❌⭕

한 비즈니스에서 아카이브된 뉴스 장면에서 생성된 비디오 아카이브를 AWS에 저장할 수 있는 솔루션을 찾고 있습니다. 기업은 비용을 절감해야 하며 이러한 데이터를 거의 복구할 필요가 없습니다. 파일이 필요한 경우 5분 이내에 제공해야 합니다.

어떤 접근 방식이 가장 비용 효율적입니까?

A. 비디오 아카이브를 Amazon S3 Glacier에 저장하고 Expedited 검색을 사용하십시오.

B. 비디오 아카이브를 Amazon S3 Glacier에 저장하고 Standard 검색어를 사용하십시오.

C. 비디오 아카이브를 Amazon S3 Standard-Infrequent Access(S3 Standard-IA)에 저장합니다.

D. 비디오 아카이브를 Amazon S3 One Zone-Infrequent Access(S3 One Zone-IA)에 저장합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

Expedited 검색 - 아카이브 하위 집합에 대한 긴급 요청이 필요할 때 신속하게 데이터에 액세스할 수 있습니다. 최대 규모(250MB 이상)를 제외한 모든 아카이브의 경우 Expedited 검색을 사용하여 액세스하는 데이터를 일반적으로 1-5분 이내에 사용할 수 있습니다. Provisioned Capacity는 필요할 때 신속한 검색을 위한 검색 용량을 제공합니다. 자세한 내용은 프로비저닝된 용량을 참조하십시오.

Standard 검색 — 표준 검색을 사용하면 몇 시간 내에 모든 아카이브에 액세스할 수 있습니다. 표준 검색은 일반적으로 3-5시간 내에 완료됩니다. 이 옵션은 검색 옵션을 지정하지 않은 검색 요청의 기본 옵션입니다.

1차 시도 : D 틀림<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/18)