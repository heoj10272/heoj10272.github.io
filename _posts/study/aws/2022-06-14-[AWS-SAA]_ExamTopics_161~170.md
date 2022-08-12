---
layout: post
title: "[AWS-SAA] Examtopics 161~170"
subtitle: AWS
date: '2022-06-14 1:30:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-14-[AWS-SAA]_ExamTopics_161~170/logo.png
---

SAA Examtopics 161~170번 문제를 풀어보자.<br>
1차 8/10<br>
2차 8/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 161 ⭕⭕

비즈니스는 두 개의 Amazon EC2 인스턴스를 사용하여 동적 웹 애플리케이션을 실행합니다. 조직에는 각 인스턴스에서 SSL 종료를 완료하는 데 사용되는 자체 SSL 인증서가 있습니다. 최근 트래픽이 증가하고 있으며, 운영팀은 SSL 암호화 및 복호화로 인해 웹 서버의 컴퓨팅 용량이 한도를 초과한다는 결론을 내렸습니다.

솔루션 설계자는 애플리케이션의 성능을 최적화하기 위해 무엇을 해야 합니까?

A. AWS 인증서 관리자(ACM)를 사용하여 새 SSL 인증서를 생성합니다. 각 인스턴스에 ACM 인증서를 설치합니다.

B. Amazon S3 버킷을 생성합니다. SSL 인증서를 S3 버킷으로 마이그레이션합니다. SSL 종료를 위해 버킷을 참조하도록 EC2 인스턴스를 구성합니다.

C. 프록시 서버로 다른 EC2 인스턴스를 만듭니다. SSL 인증서를 새 인스턴스로 마이그레이션하고 기존 EC2 인스턴스에 직접 연결하도록 구성합니다.

D. SSL 인증서를 AWS Certificate Manager(ACM)로 가져옵니다. ACM의 SSL 인증서를 사용하는 HTTPS 수신기를 사용하여 애플리케이션 로드 밸런서를 생성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

able to import own SSL to AWS

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 162 ⭕❓

한 기업이 AWS Well-Architected 프레임워크를 사용하여 AWS에 배치된 기존 워크로드를 평가하고 있습니다. 평가 결과 다른 AWS 서비스를 지원하기 위해 새로 설치된 Microsoft Active Directory 도메인 컨트롤러와 동일한 Amazon EC2 인스턴스에서 작동하는 공개 웹 사이트를 발견했습니다. ( The evaluation discovered a public-facing website operating on the same Amazon EC2 instance as a freshly installed Microsoft Active Directory domain controller to support other AWS services.) 솔루션 설계자는 아키텍처의 보안을 강화하고 IT 작업자의 관리 부담을 줄이는 새로운 설계를 제공해야 합니다.

솔루션 설계자는 어떤 권장 사항을 제시해야 합니까?

A. AWS 디렉토리 서비스를 사용하여 관리되는 Active Directory를 생성합니다. 현재 EC2 인스턴스에서 Active Directory를 제거합니다.

B. 동일한 서브넷에 다른 EC2 인스턴스를 만들고 해당 인스턴스에 Active Directory를 다시 설치합니다. Active Directory를 제거합니다.

C. AWS 디렉터리 서비스를 사용하여 Active Directory 커넥터를 생성합니다. Proxy Active Directory는 현재 EC2 인스턴스에서 실행되고 있는 Active domain contorller에 요청합니다.

D. 현재 Active Directory 컨트롤러와 SAML(Security Assertion Markup Language) 2.0 연합을 사용하여 AWS SSO(Single Sign-On)를 사용하도록 설정합니다. EC2 인스턴스의 보안 그룹을 수정하여 Active Directory에 대한 공용 액세스를 거부합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

정답은 AWS 디렉토리 서비스를 사용하여 관리되는 Active Directory를 생성하고 현재 인스턴스를 제거할 수 있다는 것입니다. 관리형 서비스를 사용하면 IT 직원의 관리 요구도 줄어듭니다.
옵션 B&D는 IT 직원의 관리 수요를 증가시키기 때문에 잘못된 것입니다.
옵션 C는 보안을 향상시키지 않기 때문에 틀렸습니다.

I thought this was 'A'. I think Active Directory connector is only for ON-PREM AD. The one they have exists in the cloud already.

1차 시도 : A 맞음<br>
2차 시도 : D 모름<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 163 ⭕⭕

Amazon Aurora는 최근 회사의 전 세계 전자 상거래 플랫폼을 위한 데이터 리포지토리로 선택되었습니다. 개발자가 광범위한 보고서를 실행할 때 전자 상거래 애플리케이션의 성능이 좋지 않음을 발견합니다. 월별 보고서를 수행할 때 솔루션 설계자는 ReadIOPS 및 CPU Utilization 메트릭이 급증하는 것을 확인합니다.

어떤 접근 방식이 가장 비용 효율적입니까?

A. 월간 보고를 Amazon Redshift로 마이그레이션합니다.

B. 월간 보고를 Aurora Replica로 마이그레이션합니다.

C. Aurora 데이터베이스를 더 큰 인스턴스 클래스로 마이그레이션합니다.

D. Aurora 인스턴스에서 프로비저닝된 IOPS를 높입니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

오로라 Replica에는 두 가지 주요 목적이 있습니다. 쿼리를 실행하여 응용 프로그램의 읽기 작업 크기를 조정할 수 있습니다. 일반적으로 클러스터의 판독기 엔드포인트에 연결하여 이 작업을 수행합니다. 이렇게 하면 Aurora는 읽기 전용 연결에 대한 로드를 클러스터에 있는 것만큼 많은 Aurora 복제본에 분산시킬 수 있습니다. 또한 Aurora Replica는 가용성을 높이는 데 도움이 됩니다. 클러스터에서 작성기 인스턴스를 사용할 수 없는 경우, Aurora는 자동으로 독서기 인스턴스 중 하나를 새 작성기로 승격합니다.

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 164 ⭕⭕

기업의 백업 데이터는 총 700TB이며 데이터 센터의 NAS(Network Attached Storage)에 보관됩니다. 이 백업 데이터는 규제 관련 문의가 있을 경우 사용할 수 있어야 하며 7년 동안 보존해야 합니다. 조직은 백업 데이터를 온프레미스 데이터 센터에서 Amazon Web Services(AWS)로 재배치하기로 결정했습니다. 한 달 이내에 마이그레이션을 완료해야 합니다. 회사의 공용 인터넷 연결은 500Mbps의 데이터 전송 전용 용량을 제공합니다.

가장 낮은 비용으로 데이터를 마이그레이션하고 저장하기 위해 솔루션 설계자는 무엇을 해야 합니까?

A. AWS Snowball 장치를 주문하여 데이터를 전송합니다. 수명 주기 정책을 사용하여 파일을 Amazon S3 Glacier Deep Archive로 전환합니다.

B. 데이터 센터와 Amazon VPC 간에 VPN 연결을 배포합니다. AWS CLI를 사용하여 사내에서 Amazon S3 Glacier로 데이터를 복사합니다.

C. 500Mbps AWS Direct Connect 연결을 프로비저닝하고 데이터를 Amazon S3로 전송합니다. 수명 주기 정책을 사용하여 파일을 Amazon S3 Glacier Deep Archive로 전환합니다.

D. AWS DataSync를 사용하여 데이터를 전송하고 사내에서 DataSync 에이전트를 배포합니다. DataSync 작업을 통해 사내 NAS 스토리지에서 Amazon S3 Glacier로 파일을 복사할 수 있습니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

나머지 방법들은 현실성이 없다.

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 165 ⭕⭕

기업의 주요 데이터 센터와 보조 데이터 센터는 500마일(804.7km) 떨어져 있으며 고속 광섬유 케이블로 연결되어 있습니다. 미션 크리티컬 워크로드의 경우 조직은 데이터 센터와 AWS VPC 간에 가용성이 높고 안전한 네트워크 링크가 필요합니다. 솔루션 설계자는 최대한 탄력적인 연결 솔루션을 선택해야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. 기본 데이터 센터에서 두 개의 AWS Direct Connect 연결이 두 개의 개별 장치에서 두 개의 Direct Connect 위치에서 종료됩니다.

B. 기본 및 보조 데이터 센터의 단일 AWS Direct Connect 연결이 동일한 디바이스의 한 Direct Connect 위치에서 종료됩니다.

C. 기본 및 보조 데이터 센터 각각에서 두 개의 AWS Direct Connect 연결이 두 개의 개별 장치에서 두 개의 Direct Connect 위치에서 종료됩니다.

D. 각 기본 및 보조 데이터 센터의 단일 AWS Direct Connect 연결이 두 개의 개별 장치에 있는 하나의 Direct Connect 위치에서 종료됩니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

둘 이상의 위치에 있는 개별 장치에서 종료되는 개별 연결을 통해 최대 복원력을 얻을 수 있습니다. 이 구성은 고객에게 장애에 대한 최대 복원력을 제공합니다. 위 그림에서 보듯이 이러한 토폴로지는 장치 장애, 연결 장애 및 전체 위치 장애에 대한 복원력을 제공합니다. AWS Direct Connect 게이트웨이를 사용하여 AWS Direct Connect 위치에서 AWS 지역(중국의 AWS 지역 제외)에 액세스할 수 있습니다.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 166 ⭕❌

비즈니스의 동적 웹 사이트는 미국 내에서 호스팅됩니다. 이 회사는 유럽 전역으로 확장하고 있으며 새로운 유럽 방문자를 위해 사이트 로딩 속도를 줄이기를 원합니다. 웹사이트의 백본은 미국에 있어야 합니다. 이제 며칠 후면 제품이 출시될 예정인데, 즉석 답변이 필요합니다.

솔루션 설계자는 어떤 권장 사항을 제시해야 합니까?

A. us-east-1에서 Amazon EC2 인스턴스를 시작하고 해당 인스턴스로 사이트를 마이그레이션합니다.

B. Amazon S3로 웹 사이트를 이동합니다. 영역 간에 교차 영역 복제를 사용합니다.

C. 온프레미스 서버를 가리키는 사용자 지정 오리진에서 Amazon CloudFront를 사용합니다.

D. 온프레미스 서버를 가리키는 Amazon Route 53 지역근접 라우팅 정책을 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 :

Amazon CloudFront는 정적 및 동적 컨텐츠의 원래 최종 버전을 보관하는 모든 오리진 서버와 함께 작동합니다. 커스텀 오리진 이용 시 추가 요금이 부과되지 않습니다.

1차 시도 : C 맞음<br>
2차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 167 ⭕⭕

한 기업에서 AWS Direct Connect 연결을 사용하여 코로케이션 시설에서 us-east-1 리전의 Amazon S3 버킷으로 1PB의 데이터를 복사했습니다. 이제 비즈니스는 us-west-2 리전에 있는 다른 S3 버킷에 데이터를 복제하려고 합니다. AWS Snowball은 코로케이션 시설에서 허용되지 않습니다.

솔루션 설계자는 이를 달성하기 위한 수단으로 무엇을 제안해야 합니까?

A. Snowball Edge 장치를 주문하여 한 영역에서 다른 영역으로 데이터를 복사합니다.

B. S3 콘솔을 사용하여 소스 S3 버킷에서 대상 S3 버킷으로 콘텐츠를 전송합니다.

C. aWS S3 sync 명령을 사용하여 소스 버킷에서 대상 버킷으로 데이터를 복사합니다.

D. 영역 간 복제 구성을 추가하여 서로 다른 영역의 S3 버킷에 개체를 복사합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

C의 sync는 아주 큰 데이터의 전송(PB 단위)의 경우 타임아웃이 일어날 수 있다.
D의 Cross region replication은 일반적으로 새 버킷을 대상으로만 가능하나, AWS Support에 문의시 존재하는 버킷을 대상으로도 사용 가능하다. 

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 168 ❌⭕

솔루션 설계자는 Amazon DynamoDB에 대한 API 요청이 VPC 내부의 Amazon EC2 인스턴스로부터의 인터넷을 통해 라우팅되지 않는지 확인해야 합니다.

이를 달성하기 위한 솔루션 설계자의 역할은 무엇입니까? (2개를 선택하세요.)

A. 엔드포인트에 대한 경로 테이블 엔트리를 만듭니다.

B. DynamoDB에 대한 게이트웨이 엔드포인트를 만듭니다.

C. 엔드포인트를 사용하는 새 DynamoDB 테이블을 만듭니다.

D. VPC의 각 서브넷에 엔드포인트에 대한 ENI를 생성합니다.

E. 기본 Security Group에 Security Group 항목을 만들어 액세스 권한을 제공합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B

해설 : 

Amazon DynamoDB 및 Amazon S3는 인터페이스 끝점이 아닌 게이트웨이 끝점을 지원합니다.<br>
게이트웨이 끝점을 사용하여 VPC에 끝점을 생성하고 서비스에 대한 액세스를 허용하는 정책을 연결합니다.<br>
그런 다음 경로 테이블 항목을 만들 경로 테이블을 지정하십시오.

1차 시도 : B, C 틀림<br>
2차 시도 : A, B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 169 ❌⭕

비즈니스 애플리케이션은 Elastic Load Balancer 뒤에 있는 Auto Scaling 그룹의 일부인 Amazon EC2 인스턴스에서 호스팅됩니다. 회사는 매년 애플리케이션 기록을 기반으로 휴일 동안 트래픽 증가를 예측합니다. 솔루션 설계자는 애플리케이션 사용자의 성능에 미치는 영향을 최소화하기 위해 Auto Scaling 그룹이 사전에 용량을 늘리도록 보장하는 계획을 개발해야 합니다.

어떤 솔루션이 이러한 기준을 충족할까요?

A. CPU 활용률이 90%를 초과할 경우 EC2 인스턴스를 확장하려면 Amazon CloudWatch 경보를 생성합니다.

B. 수요가 가장 많은 예상 기간 전에 자동 스케일링 그룹을 확장하는 반복 예약 작업(recurring scheduled action)을 만듭니다.

C. 최대 수요 기간 동안 자동 스케일링 그룹에서 EC2 인스턴스의 최소 및 최대 수를 늘립니다.

D.  EC2_INSTANCE_LAUNCH 이벤트의 자동 확장이 있을 때 경고를 보내도록 Amazon Simple Notification Service(Amazon SNS) 알림을 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

예정된 이벤트에 대한 사전 대처로는 반복 예약(scheduled) 작업이 적절하다.

Key line- anticipates traffic.<br>
Anticipating-Scheduled action.

1차 시도 : C 틀림<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 170 ⭕⭕

비즈니스에서 라이브 데이터 세트를 온프레미스 NFS 서버에서 DOC-EXAMPLE-BUCKET이라는 Amazon S3 버킷으로 온라인으로 마이그레이션하려고 합니다. 데이터 무결성 검증은 전송 중과 전송 후에 모두 필수적입니다. 또한 데이터를 암호화해야 합니다.
솔루션 설계자가 AWS 솔루션을 사용하여 데이터를 마이그레이션하고 있습니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. AWS Storage Gateway file gateway

B. S3 Transfer Acceleration

C. AWS DataSync

D. AWS Snowball Edge Storage Optimized

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Datasync is for MIGRATION while Storage Gateway is for INTEGRATION.

1차 시도 : C 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/17)