---
layout: post
title: "[AWS-SAA] Examtopics 21~30"
subtitle: AWS
date: '2022-06-11 21:20:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-11-[AWS-SAA]_ExamTopics_21~30/logo.png
---

SAA Examtopics 21~30번 문제를 풀어보자.<br>
1차 5/10<br>
2차 9/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 21 ⭕⭕

관리는 예산 계획 프로세스의 일부로 사용자별로 분류된 AWS 청구 항목 요약이 필요합니다. 부서에 대한 예산은 데이터를 사용하여 생성됩니다. 솔루션 설계자는 이 보고서 데이터를 얻는 가장 효과적인 방법을 확인해야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. Amazon Athena에서 쿼리를 실행하여 보고서를 생성합니다.

B. 비용 탐색기에서 보고서를 만들고 보고서를 다운로드합니다.

C. 청구 대시보드에서 청구서 세부 정보에 액세스하고 청구서를 다운로드합니다.

D. AWS Budgets에서 Amazon Simple Email Service(Amazon SES)를 사용하여 경고하도록 비용 예산을 수정합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

비용 탐색기는 기본 리포트를 제공하지만 리포트를 생성하는 데 사용되는 필터 및 제약 조건을 변경할 수도 있습니다. <br>
비용 탐색기는 사용자가 만든 리포트를 저장하는 방법도 제공합니다. <br>
책갈피로 저장하거나 CSV 파일을 다운로드하거나 보고서로 저장할 수 있습니다.

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 22 ⭕⭕

솔루션 설계자는 클라이언트 사례 파일을 보관하기 위한 시스템을 만들어야 합니다. 파일은 중요한 기업 자산입니다. 파일 수는 시간이 지남에 따라 증가합니다. Amazon EC2 인스턴스에서 실행되는 여러 애플리케이션 서버는 파일에 동시에 액세스할 수 있어야 합니다. 솔루션에는 기본 제공 중복성이 있어야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. Amazon EFS(Amazon Elastic File System)

B. 아마존 엘라스틱 블록 스토어 (Amazon EBS)

C. Amazon S3 Glacier Deep Archive

D. AWS 백업

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A (and B) 중복 정답

해설 : 

EFS는 동시성을 지원하기 때문에 답은 A이다.

하지만 이 문제는 Amazon EBS Multi-Attach 가 업데이트되기 전에 나온 문제같다는 의견이 있다.
다음은 Multi-Attach에 대한 설명이다.

    Amazon EBS Multi-Attach를 사용하면 동일한 가용성 영역에 있는 여러 인스턴스에 단일 Provisioned IOPS SSD(i1 또는 io2) 볼륨을 연결할 수 있습니다. 여러 다중 연결 사용 볼륨을 인스턴스 또는 인스턴스 집합에 연결할 수 있습니다. 볼륨이 연결된 각 인스턴스에는 공유 볼륨에 대한 전체 읽기 및 쓰기 권한이 있습니다. Multi-Attach를 사용하면 동시 쓰기 작업을 관리하는 클러스터된 리눅스 애플리케이션에서 애플리케이션 가용성을 높일 수 있습니다.

1차 시도 : B 맞음<br>
2차 시도 : A 맞음<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 23 ❌⭕

기업은 직원에게 기밀 및 민감한 데이터에 대한 보안 액세스를 제공해야 합니다. 회사는 승인된 개인만 데이터에 액세스할 수 있도록 보장하기를 원합니다. 데이터는 작업자의 장치에 안전하게 다운로드되어야 합니다. 파일은 온프레미스 Windows 파일 서버에 보관됩니다. 그러나 원격 트래픽이 증가함에 따라 파일 서버의 용량이 고갈되고 있습니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. 파일 서버를 공용 서브넷의 Amazon EC2 인스턴스로 마이그레이션합니다. 인바운드 트래픽을 직원의 IP 주소로 제한하도록 보안 그룹을 구성합니다.

B. 파일을 Amazon FSX for 윈도우즈 File Server 파일 시스템으로 마이그레이션합니다. Amazon FSX 파일 시스템을 사내 Active Directory와 통합합니다. AWS 클라이언트 VPN을 구성합니다.

C. 파일을 Amazon S3로 마이그레이션하고 전용 VPC 엔드포인트를 생성합니다. 서명된 URL을 만들어 다운로드를 허용합니다.

D. 파일을 Amazon S3로 마이그레이션하고 공용 VPC 엔드포인트를 생성합니다. 직원이 AWS Single Sign-On으로 로그온할 수 있도록 허용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

    Windows 파일 서버가 온프레미스이므로 데이터를 클라우드에 복제할 수 있는 방법이 필요하므로 Windows 파일 서버용 AWS FSx만 선택할 수 있습니다. 또한, 정보는 기밀이며 기밀이므로 적절한 사용자가 안전한 방법으로 정보에 액세스할 수 있도록 하고 싶습니다.

Windows file server + AD => FSx

"Windows 파일 시스템"이 사용됩니다. Windows 파일 서버용 S3와 FSX 사이에서 FSX는 기존 on-prem 파일 시스템을 더 잘 대체합니다. --> 우리를 A와 B로 제한합니다.
보안 그룹(A)을 통한 IP 화이트리스트는 직원 공용 IPv4가 변경되거나 디바이스가 손상될 수 있으므로 위험합니다.
보안 인증 시스템(B)을 사용하는 것이 더 안전합니다.

1차 시도 : C 틀림<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 24 ❌⭕

법률 회사는 대중과 소통해야 합니다. 수백 개의 파일에 공개적으로 액세스할 수 있어야 합니다. 누구든지 지정된 미래 날짜 이전에 파일을 수정하거나 삭제할 수 없습니다.

가능한 가장 안전한 방법으로 이러한 기준을 충족하는 솔루션은 무엇입니까?

A. 정적 웹 사이트 호스팅을 위해 구성된 Amazon S3 버킷에 모든 파일을 업로드합니다. 지정된 날짜까지 S3 버킷에 액세스하는 모든 AWS 주체에 읽기 전용 IAM 사용 권한을 부여합니다.

B. S3 Versioning을 사용하도록 설정된 새 Amazon S3 버킷을 생성합니다. S3 Object Lock을 지정된 날짜에 따라 보존 기간과 함께 사용합니다. 정적 웹 사이트 호스팅을 위해 S3 버킷을 구성합니다. 개체에 대한 읽기 전용 액세스를 허용하도록 S3 버킷 정책을 설정합니다.

C. S3 Versioning을 사용하도록 설정된 새 Amazon S3 버킷을 생성합니다. 개체 수정 또는 삭제 시 AWS 람다 기능을 실행하도록 이벤트 트리거를 구성합니다. 개체를 전용 S3 버킷의 원래 버전으로 바꾸도록 람다 기능을 구성합니다.

D. 정적 웹 사이트 호스팅을 위해 구성된 Amazon S3 버킷에 모든 파일을 업로드합니다. 파일이 들어 있는 폴더를 선택하십시오. S3 Object Lock은 지정된 날짜에 따라 보존 기간과 함께 사용합니다. S3 버킷에 액세스하는 모든 AWS 주체에 읽기 전용 IAM 사용 권한을 부여합니다.


<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

다수를 위한 읽기 전용 액세스는 버킷 정책으로 구현해야 한다.

버킷을 생성하는 동안 개체 잠금이 사용하도록 설정된 새 버킷을 생성해야 합니다.
기존 버킷(옵션 D의 경우처럼)에 대해 개체 잠금을 사용할 수 없습니다(생성 시 구성되지 않은 경우).

또한 Object lock이 활성화된 상태에서 새 버킷을 생성하려고 했는데 다음 메시지가 표시됩니다.
"개체 잠금이 활성화되어 있으면 버킷 버전 관리를 비활성화할 수 없습니다."

즉, 새 버킷을 생성해야 합니다(버전링이 자동으로 활성화됨).
또한 IAM 권한이 아니라 버킷 정책일 수 있으므로 이 경우에도 D는 제외됩니다.

1차 시도 : A 틀림<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 25 ❌⭕

기업은 10Gbps AWS Direct Connect 연결을 통해 온프레미스 서버를 AWS에 연결합니다. 연결의 작업 부하가 중요합니다. 조직에는 기존 연결 대역폭을 최소화하면서 최대한 탄력적인 재해 복구 접근 방식이 필요합니다.

솔루션 설계자는 어떤 권장 사항을 제시해야 합니까?

A. 다른 AWS 영역에 새 Direct Connect 연결을 설정합니다.

B. 다른 AWS 영역에 새 AWS 관리 VPN 연결을 설정합니다.

C. 두 개의 새 직접 연결(현재 AWS 영역과 다른 영역에 하나씩)을 설정합니다.

D. AWS 관리 VPN 연결 두 개를 새로 설정합니다. 하나는 현재 AWS 영역에 있고 다른 하나는 다른 영역에 있습니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

정답은 C: 두 가지 키워드는 "maximum resiliency"과 "재해 복구"입니다. 한 영역에 2개의 서로 다른 연결이 있으면 maximum resiliency가 보장됩니다. 서로 다른 영역에 서로 연결하면 재해/재해 복구가 포함됩니다.
또한 동일한 영역에 새 연결이 있으면 연결 로드를 공유하므로 기존 연결에서 "트래픽 대역폭"이 감소합니다.

1차 시도 : B 틀림<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 26 ❓❌

기업에는 관리 및 프로덕션이라는 레이블이 붙은 두 개의 가상 사설 클라우드(VPC)가 있습니다. 관리 VPC는 ​​고객 게이트웨이를 통해 VPN을 사용하여 데이터 센터의 단일 장치에 연결합니다. 프로덕션 VPC는 ​​가상 프라이빗 게이트웨이를 통해 두 개의 AWS Direct Connect 연결을 통해 AWS에 연결됩니다. 관리 및 프로덕션 VPC는 ​​모두 단일 VPC 피어링 연결을 통해 서로 통신합니다.

아키텍처의 단일 실패 지점을 최소화하기 위해 솔루션 설계자는 무엇을 해야 합니까?

A. 관리 VPC와 운영 VPC 사이에 VPN 집합을 추가합니다.

B. 두 번째 가상 프라이빗 게이트웨이를 추가하고 관리 VPC에 연결합니다.

C. 두 번째 고객 게이트웨이 디바이스에서 Management VPC에 두 번째 VPN 집합을 추가합니다.

D. 관리 VPC와 운영 VPC 사이에 두 번째 VPC 피어링 연결을 추가합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

A 탈락 - VPC 피어링에 대해 "통신에 대한 단일 장애 지점 또는 대역폭 병목 현상이 없습니다." 따라서 VPC 피어링이 이미 설치되어 있으면 이중화 메커니즘을 생성할 필요가 없습니다.
https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html

B 탈락 - "VPC에 가상 프라이빗 게이트웨이를 한 번에 하나씩 연결할 수 있습니다."
https://docs.aws.amazon.com/vpn/latest/s2svpn/vpn-limits.html

D 탈락 - VPC 한 쌍당 VPC 피어링을 하나만 가질 수 있습니다. "VPC 피어링 연결은 두 VPC 간의 일대일 관계입니다."
VPC https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-basics.html

C 정답 - "고객 게이트웨이 디바이스를 사용할 수 없게 될 경우 연결이 끊어지는 것을 방지하기 위해 두 번째 고객 게이트웨이 디바이스를 사용하여 VPC 및 가상 프라이빗 게이트웨이에 대한 두 번째 사이트 간 VPN 연결을 설정할 수 있습니다."
https://docs.aws.amazon.com/vpn/latest/s2svpn/vpn-redundant-connection.html

1차 시도 : 모름<br>
2차 시도 : 틀림, 모름<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 27 ⭕⭕

AWS는 회사의 거의 실시간 스트리밍 애플리케이션을 호스팅합니다. 데이터가 수집되는 동안 완료하는 데 30분이 걸리는 작업이 수행됩니다. 방대한 양의 수신 데이터로 인해 워크로드는 정기적으로 상당한 대기 시간에 직면합니다. 성능을 최적화하기 위해 솔루션 설계자는 확장 가능한 서버리스 시스템을 구축해야 합니다.

솔루션 아키텍트는 어떤 조치를 취해야 합니까? (2개를 선택하세요.)

A. Amazon Kinesis Data Firehose를 사용하여 데이터를 수집합니다.

B. AWS Step Functions와 함께 AWS Lambda를 사용하여 데이터를 처리합니다.

C. AWS DMS(데이터베이스 마이그레이션 서비스)를 사용하여 데이터를 수집합니다.

D. Auto Scaling 그룹의 Amazon EC2 인스턴스를 사용하여 데이터를 처리합니다.

E. AWS Fargate with Amazon Elastic Container Service(Amazon ECS)를 사용하여 데이터를 처리합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, E

해설 : 

답은 A와 E이다.

2개의 수집기와 3개의 처리기가 있습니다.
`거의 실시간(near realtime)`이므로 A. Firehose를 골라야한다.

처리기 B, D, E가 남아 있다.

람다는 최대 15분 동안 실행될 수 있고, 작업이 30분이기 때문에 람다는 쓸 수 없다.
https://aws.amazon.com/lambda/faqs/#:~:text=AWS%20Lambda%20functions%20can%20be,1%20second%20and%2015%20minutes.

남은건 D와 E다.
둘 다 작동하지만 문제에서 서버리스가 지정되어 있으므로 E이다.
https://aws.amazon.com/fargate/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc&fargate-blogs.sort-by=item.additionalFields.createdDate&fargate-blogs=derd=dateTime

그래서 A와 E가 해결책이다.

1차 시도 : A, E 맞음<br>
2차 시도 : A, E 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 28 ⭕⭕

Amazon Elastic Block Store(Amazon EBS) 볼륨은 미디어 조직에서 비디오 자료를 저장하는 데 사용합니다. 특정 비디오 파일이 인기를 얻었고 현재 전 세계에서 많은 사람들이 이 파일을 보고 있습니다. 결과적으로 비용이 증가했습니다.

사용자 접근성을 위태롭게 하지 않으면서 비용을 절감할 수 있는 단계는 무엇입니까?

A. EBS 볼륨을 프로비저닝된 IOPS(PIOPS)로 변경합니다.

B. 비디오를 Amazon S3 버킷에 저장하고 Amazon CloudFront 배포를 생성합니다.

C. 비디오를 여러 개의 작은 세그먼트로 분할하여 사용자가 요청된 비디오 세그먼트로만 라우트되도록 합니다.

D. 각 영역에서 Amazon S3 버킷을 지우고(Clear) 비디오를 업로드하여 사용자가 가장 가까운 S3 버킷으로 라우팅되도록 합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

S3에 비디오를 저장하고 배포를 위해 Cloudfront를 사용한다. 

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 29 ⭕⭕

Amazon S3 버킷은 이미지 호스팅 회사에서 객체를 저장하는 데 사용합니다. 회사는 S3 버킷에 포함된 항목이 의도하지 않게 공개되는 것을 방지하고자 합니다. AWS 계정의 모든 S3 항목은 전체적으로 비공개로 유지되어야 합니다.

어떤 솔루션이 이러한 기준을 충족할까요?

A. Amazon GuardDuty를 사용하여 S3 버킷 정책을 모니터링합니다. AWS Lambda 함수를 사용하여 개체를 공개하는 변경 사항에 업데이트를 적용하는 자동 업데이트 적용 작업 규칙을 생성합니다.

B. AWS Trusted Advisor를 사용하여 공개적으로 액세스할 수 있는 S3 버킷을 찾습니다. 변경 사항이 감지되면 Trusted Advisor에서 이메일 알림을 구성합니다. 공개 액세스를 허용하는 경우 S3 버킷 정책을 수동으로 변경합니다.

C. AWS Resource Access Manager를 사용하여 공개적으로 액세스할 수 있는 S3 버킷을 찾습니다. 변경 사항이 감지되면 Amazon Simple Notification Service(Amazon SNS)를 사용하여 AWS Lambda 기능을 호출합니다. 변경 사항을 프로그래밍 방식으로 교정하는 람다 함수를 배포합니다.

D. 계정 수준에서 S3 공용 액세스 차단 기능을 사용합니다. AWS 조직을 사용하여 IAM 사용자가 설정을 변경할 수 없도록 하는 SCP(서비스 제어 정책)를 만듭니다. SCP를 계정에 적용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Answer is D ladies and gentlemen. While guard duty helps to monitor s3 for potential threats its a reactive action. We should always be proactive and not reactive in our solutions so D, block public access to avoid any possibility of the info becoming publicly accessible

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 30 ❌⭕

회사 웹 사이트는 Amazon RDS MySQL 다중 AZ DB 인스턴스에 트랜잭션 데이터를 저장합니다. 다른 내부 시스템은 이 데이터베이스 인스턴스를 쿼리하여 일괄 처리를 위한 데이터를 가져옵니다. 내부 시스템이 RDS DB 인스턴스에서 데이터를 요청하면 RDS DB 인스턴스가 급격히 느려집니다. 이는 웹사이트의 읽기 및 쓰기 성능에 영향을 미치므로 사용자의 응답 시간이 느려집니다.

어떤 접근 방식이 웹사이트 성능을 향상시킬까요?

A. MySQL 데이터베이스 대신 RDS Postgre DB를 사용합니다.

B. Amazon ElastiCache를 사용하여 웹 사이트에 대한 쿼리 응답을 캐시합니다.

C. 현재 RDS MySQL Multi-AZ DB 인스턴스에 가용 영역을 추가합니다.

D. RDS DB 인스턴스에 Read Replica를 추가하고 읽기 복제본을 쿼리하도록 내부 시스템을 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Performance(성능) = Read Replicas
MultiAZ= Disaster Recovery (DR)

Option A is wrong as changing DB would not help improve performance.
Option B is wrong as ElastiCache would only help for caching data from same queries.
Option C is wrong as Multi-AZ database spans across 2 AZs and its an high availability solution.

1차 시도 : B 틀림<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/3)