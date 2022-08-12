---
layout: post
title: "[AWS-SAA] Examtopics 131~140"
subtitle: AWS
date: '2022-06-14 1:00:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-14-[AWS-SAA]_ExamTopics_131~140/logo.png
---

SAA Examtopics 131~140번 문제를 풀어보자.<br>
1차 6/10<br>
2차 7/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 131 ⭕⭕

사용자는 쿼리에서 최대 100밀리초의 지연을 예상하는 다양한 고객이 사용하는 MySQL 데이터베이스를 소유하고 있습니다. 항목이 데이터베이스에 기록되면 거의 수정되지 않습니다. 클라이언트는 한 번에 최대 하나의 레코드에 액세스할 수 있습니다.
증가하는 고객 요구로 인해 데이터베이스 액세스가 엄청나게 확장되었습니다. 결과적으로 결과 부하는 사용 가능한 가장 값비싼 하드웨어의 용량을 빠르게 능가합니다. 사용자는 AWS로 이동하기를 원하며 새로운 데이터베이스 시스템을 실험할 준비가 되어 있습니다.

데이터베이스 로드 문제를 해결하고 거의 무한한 미래 확장성을 제공하는 솔루션은 무엇입니까?

A. Amazon RDS

B. Amazon DynamoDB

C. Amazon Redshift

D. AWS Data Pipeline

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Amazon DynamoDB는 모든 규모에서 밀리초 단위의 단일 자릿수 성능을 제공하는 키 값 및 문서 데이터베이스입니다. <br>
이 데이터베이스는 인터넷 규모의 애플리케이션을 위한 내장형 보안, 백업 및 복원, 메모리 내 캐슁을 통해 완벽하게 관리되는 다중 영역, 다중 활성 및 내구성이 뛰어난 데이터베이스입니다. <br>
DynamoDB는 매일 10조 개 이상의 요청을 처리할 수 있으며 초당 2,000만 개 이상의 요청을 지원할 수 있습니다.

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 132 ⭕⭕

Amazon DynamoDB는 엔터테인먼트 회사에서 미디어 메타데이터를 저장하는 데 사용하고 있습니다. 응용 프로그램은 광범위한 읽기가 필요하며 종종 지연이 발생합니다. 조직에는 추가 운영 비용을 관리하는 데 필요한 인력이 부족하고 애플리케이션을 변경하지 않고 DynamoDB의 성능 효율성을 높여야 합니다.

이 요구 사항을 충족하려면 어떤 솔루션 아키텍처 접근 방식을 권장해야 합니까?

A. Redis에는 Amazon ElastiCache를 사용합니다.

B. DAX(Amazon DynamoDB Accelerator)를 사용합니다.

C. DynamoDB 글로벌 테이블을 사용하여 데이터를 복제합니다.

D. Auto Discovery가 활성화된 Memcached에 Amazon ElastiCache를 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B 맞음<br>
Answer : B 맞음<br>

해설 : 

DynamoDB는 일관된 단일 자릿수 밀리초 대기 시간을 제공하지만, DynamoDB + DAX는 읽기 집약적인 워크로드에 대해 초당 수백만 건의 요청에 대한 응답 시간을 마이크로초 단위로 단축하여 성능을 한 단계 높입니다. <br>
DAX를 사용하면 인기 있는 이벤트나 뉴스 스토리가 전례 없는 요청 볼륨을 원하는 방향으로 유도하는 경우에도 애플리케이션이 빠르고 신속하게 응답할 수 있습니다. 튜닝이 필요하지 않습니다.

1차 시도 : B
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 133 ❓❌

지점 사무실에서 회사는 가상화된 컴퓨팅 리소스가 없는 작은 데이터 클로짓(small data closet with no virtualized compute resource)에서 애플리케이션을 실행합니다. 애플리케이션의 데이터는 NFS(네트워크 파일 시스템) 볼륨에 저장됩니다. 규정 준수 요구 사항에 따라 NFS 볼륨의 일일 오프사이트 백업이 필요합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. 데이터를 Amazon S3에 복제하려면 온프레미스에 AWS Storage Gateway 파일 게이트웨이를 설치합니다.

B. 데이터를 Amazon S3에 복제하려면 온프레미스에 AWS Storage Gateway 파일 게이트웨이 하드웨어 장치를 설치합니다.

C. 저장된 볼륨이 있는 AWS Storage Gateway 볼륨 게이트웨이를 온프레미스에 설치하여 데이터를 Amazon S3에 복제합니다.

D. 데이터를 Amazon S3에 복제하려면 온프레미스에서 캐시된 볼륨이 있는 AWS Storage Gateway 볼륨 게이트웨이를 설치합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 


1차 시도 : ? 모름<br>
2차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 134 ⭕⭕

한 비즈니스에서 AWS를 사용하여 전 세계 소비자를 위한 선거 보고 웹 사이트를 호스팅하고 있습니다. 웹 사이트는 웹 및 애플리케이션 계층용 Application Load Balancer가 있는 Auto Scaling 그룹의 Amazon EC2 인스턴스를 사용합니다. 데이터베이스 계층은 MySQL용 Amazon RDS로 구동됩니다. 웹사이트는 선거 결과로 한 시간에 한 번씩 업데이트되며 이전에는 수백 명의 개인이 데이터를 확인하는 것을 보았습니다.
이 회사는 많은 국가에서 임박한 선거의 결과로 앞으로 몇 달 동안 수요가 크게 증가할 것으로 예상합니다. 솔루션 설계자의 목표는 더 많은 EC2 인스턴스에 대한 요구 사항을 제한하면서 증가하는 수요를 관리할 수 있는 웹 사이트의 용량을 늘리는 것입니다.

어떤 솔루션이 이러한 기준을 충족할까요?

A. Amazon ElastiCache 클러스터를 시작하여 일반 데이터베이스 쿼리를 캐시합니다.

B. Amazon CloudFront 웹 배포를 시작하여 일반적으로 요청되는 웹 사이트 콘텐츠를 캐시합니다.

C. EC2 인스턴스에서 디스크 기반 캐싱을 활성화하여 일반적으로 요청된 웹 사이트 콘텐츠를 캐시합니다.

D. 일반적으로 요청된 웹 사이트 콘텐츠에 대해 캐싱이 활성화된 EC2 인스턴스를 사용하여 설계에 역방향 프록시를 배포합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

전세계 대상 = CloudFront<br>
EC2에 대한 요구사항 제한 -> ElastiCache 탈락

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 135 ❌⭕ 유념

Amazon S3는 기업에서 날씨 기록을 저장하는 데 사용됩니다. 기록은 회사 웹사이트의 도메인 이름을 참조하는 URL을 통해 액세스됩니다. 구독을 통해 전 세계 사용자가 이 자료에 액세스할 수 있습니다. 조직의 핵심 도메인 이름은 타사 운영자가 호스팅하지만 이 회사는 최근 일부 서비스를 Amazon Route 53으로 이전했습니다. 회사는 계약을 통합하고, 사용자 지연 시간을 최소화하고, 구독자에게 애플리케이션을 제공하는 비용을 낮추기를 원합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. Amazon CloudFront에서 웹 배포를 생성하여 애플리케이션의 S3 콘텐츠를 제공합니다. CloudFront 배포를 가리키는 Route 53 호스트 영역에 CNAME 레코드를 생성하여 응용 프로그램의 URL 도메인 이름을 확인합니다.

B. Amazon CloudFront에서 웹 배포를 생성하여 애플리케이션의 S3 콘텐츠를 제공합니다. Amazon Route 53 호스트 영역에 CloudFront 배포를 가리키는 ALIAS 레코드를 생성하여 애플리케이션의 URL 도메인 이름을 확인합니다.

C. 응용 프로그램에 대한 Route 53 호스트 영역에 A 레코드를 만듭니다. 웹 응용 프로그램에 대한 Route 53 트래픽 정책을 생성하고 지리적 위치 규칙을 구성합니다. 엔드포인트의 상태를 확인하고 엔드포인트가 비정상인 경우 DNS 쿼리를 다른 엔드포인트로 라우팅하도록 상태 검사를 구성합니다.

D. 응용 프로그램에 대한 Route 53 호스트 영역에 A 레코드를 만듭니다. 웹 응용 프로그램에 대한 Route 53 트래픽 정책을 생성하고 지리적 근접성 규칙을 구성합니다. 엔드포인트의 상태를 확인하고 엔드포인트가 비정상인 경우 DNS 쿼리를 다른 엔드포인트로 라우팅하도록 상태 검사를 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

CNAME은 실제 DNS 서버를 위한 것입니다.<br>
ALIAS는 DNS이지만 특히 AWS용입니다. AWS용 특수 레코드입니다. 정답은 B입니다.


1차 시도 : A 틀림<br>
1차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 136 ⭕⭕

기업은 인터넷을 통해 액세스할 수 있는 웹 응용 프로그램을 개발 중입니다. 애플리케이션은 Amazon RDS MySQL 다중 AZ DB 인스턴스를 활용하여 민감한 사용자 데이터를 저장하는 Linux 인스턴스용 Amazon EC2에서 호스팅됩니다. 퍼블릭 서브넷은 EC2 인스턴스에 사용되는 반면 프라이빗 서브넷은 RDS DB 인스턴스에 사용됩니다. 보안 팀은 데이터베이스 인스턴스에 대한 웹 기반 공격을 방지할 것을 요구했습니다.

솔루션 설계자는 어떤 권장 사항을 제시해야 합니까?

A. EC2 인스턴스가 자동 확장 그룹에 속해 있고 애플리케이션 로드 밸런서 뒤에 있는지 확인합니다. 의심스러운 웹 트래픽을 삭제하도록 EC2 인스턴스 iptables 규칙을 구성합니다. DB 인스턴스에 대한 Security Group을 생성합니다. 개별 EC2 인스턴스의 포트 3306 인바운드만 허용하도록 RDS 보안 그룹을 구성합니다.

B. EC2 인스턴스가 자동 확장 그룹에 속해 있고 애플리케이션 로드 밸런서 뒤에 있는지 확인합니다. DB 인스턴스를 EC2 인스턴스와 동일한 서브넷으로 이동합니다. DB 인스턴스에 대한 Security Group을 생성합니다. 개별 EC2 인스턴스의 포트 3306 인바운드만 허용하도록 RDS 보안 그룹을 구성합니다.

C. EC2 인스턴스가 자동 확장 그룹에 속해 있고 애플리케이션 로드 밸런서 뒤에 있는지 확인합니다. AWS WAF를 사용하여 인바운드 웹 트래픽에서 위협을 모니터링합니다. 웹 응용 프로그램 서버에 대한 Security Group과 DB 인스턴스에 대한 Security Group을 생성합니다. 웹 응용 프로그램 서버 보안 그룹에서 포트 3306 인바운드만 허용하도록 RDS 보안 그룹을 구성합니다.

D. EC2 인스턴스가 자동 확장 그룹에 속해 있고 애플리케이션 로드 밸런서 뒤에 있는지 확인합니다. AWS WAF를 사용하여 인바운드 웹 트래픽에서 위협을 모니터링합니다. 트래픽이 많은 경우 새 DB 인스턴스를 자동으로 생성하도록 자동 확장 그룹을 구성합니다. RDS DB 인스턴스에 대한 Security Group을 생성합니다. 포트 3306 인바운드만 허용하도록 RDS 보안 그룹을 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

A는 틀렸습니다. <br>
iptables를 사용하여 의심스러운 웹 트래픽을 "폐기"하는 방법은 무엇입니까? IP 주소를 지정해야 합니다.

B가 잘못되었습니다. <br>
"DB 인스턴스를 EC2 인스턴스가 위치한 동일한 서브넷으로 이동"은 모든 것이 공용 서브넷에 있으며 이는 "중요한 사용자 데이터" 스토리지 원칙을 위반한다는 의미입니다.

"포트 3306 인바운드 허용"이 어느 소스에서 지정되지 않았으므로 D가 잘못되었습니다.

정답은 C입니다.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 137 ⭕⭕

솔루션 설계자는 온프레미스에서 AWS로 영구 데이터베이스를 마이그레이션하기 위한 솔루션 설계를 담당합니다. 데이터베이스 관리자에 따르면 데이터베이스에는 64,000 IOPS가 필요합니다. 가능한 경우 데이터베이스 관리자는 단일 Amazon Elastic Block Store(Amazon EBS) 볼륨에서 데이터베이스 인스턴스를 호스팅하려고 합니다.

데이터베이스 관리자의 요구 사항을 가장 효과적으로 충족시키는 옵션은 무엇입니까?

A. I3 I/O 최적화 제품군의 인스턴스를 사용하고 로컬 사용 후 삭제 스토리지를 활용하여 IOPS 요구 사항을 충족합니다.

B. Amazon EBS(Elastic Block Store) Provisioned IOPS SSD(io1) 볼륨이 연결된 Nitro 기반 Amazon EC2 인스턴스를 생성합니다. 64,000 IOPS가 되도록 볼륨을 구성합니다.

C. Amazon EFS(Elastic File System) 볼륨을 생성하여 데이터베이스 인스턴스에 매핑하고 이 볼륨을 사용하여 데이터베이스에 필요한 IOPS를 달성합니다.

D. 두 볼륨을 프로비저닝하고 각각 32,000 IOPS를 할당합니다. 운영 체제 수준에서 논리적 볼륨을 생성하여 두 볼륨을 모두 집계하여 IOPS 요구 사항을 충족합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

프로비저닝된 IOPS SSD 볼륨은 한 볼륨당 최대 64,000 IOPS 및 1,000MB/s의 처리량을 제공하도록 설계되었습니다.

EBS io1은 기본 32000 IOPS, Nitro 기반일 경우에만 64000 IOPS를 제공한다고 한다.

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 138 ❌❌

솔루션 아키텍트는 AWS 클라우드에 배포할 새 애플리케이션에 대한 아키텍처를 생성하는 책임이 있습니다. Amazon EC2 온디맨드 인스턴스는 애플리케이션을 실행하는 데 사용되며 다른 가용 영역에서 자동으로 확장됩니다. 하루 종일 EC2 인스턴스는 주기적으로 확장 및 축소됩니다. 부하 분산은 ALB(Application Load Balancer)에서 처리합니다. 아키텍처는 분산된 세션 데이터를 관리할 수 있어야 합니다. 회사는 코드에 필요한 조정을 할 준비가 되어 있습니다.

설계에서 분산 세션 데이터 관리가 가능하도록 하는 솔루션 설계자의 책임은 무엇입니까?

A. Amazon ElastiCache를 사용하여 세션 데이터를 관리하고 저장합니다.

B. ALB의 세션 선호도(스틱 세션)를 사용하여 세션 데이터를 관리합니다.

C. AWS Systems Manager의 Session Manager를 사용하여 세션을 관리합니다.

D. GetSession을 사용합니다.AWS Security Token Service(AWS STS)에서 토큰 API 작업을 수행하여 세션을 관리합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

Distributed Session Management<br>
주소 확장성을 해결하고 개별 웹 서버에서 액세스할 수 있는 세션에 대한 공유 데이터 저장소를 제공하기 위해 웹 서버 자체에서 HTTP 세션을 추상화할 수 있습니다. <br>
이를 위한 일반적인 솔루션은 Redis 및 Memcached와 같은 In-Memory Key/Value 저장소를 활용하는 것입니다.


A. Use Amazon ElastiCache to manage and store session data.
- Correct. Session data is managed at the application-layer, and a distributed cache should be used

B. Use session affinity (sticky sessions) of the ALB to manage session data.
- Wrong. This tightly couples the individual EC2 instances to the session data, and requires additional logic in the ALB. When scale-in happens, the session data stored on individual EC2 instances is destroyed

C. Use Session Manager from AWS Systems Manager to manage the session.
- Wrong. Session Manager is to manage EC2 instances and other devices, servers, and VMs you operate (https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html), NOT for storing (application) session info

D. Use the GetSessionToken API operation in AWS Security Token Service (AWS STS) to manage the session
- Wrong. STS is to request temporary credentials for IAM users - https://docs.aws.amazon.com/STS/latest/APIReference/welcome.html

1차 시도 : C 맞음<br>
2차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 139 ⭕❌

여러 Amazon EC2 Linux 인스턴스는 계층적 디렉터리 구조가 필요한 애플리케이션을 실행하기 위해 VPC의 비즈니스에서 사용됩니다. 앱은 빠르고 동시에 공유 저장소에 액세스하고 쓸 수 있어야 합니다.

이것은 어떻게 이루어지나요?

A. Amazon EFS(Elastic File System) 파일 시스템을 만들고 각 EC2 인스턴스에서 마운트합니다.

B. Amazon S3 버킷을 생성하고 VPC의 모든 EC2 인스턴스에서 액세스를 허용합니다.

C. Amazon EBS(Amazon Elastic Block Store) Provisioned IOPS SSD(io1) 볼륨에 파일 시스템을 생성합니다. 볼륨을 모든 EC2 인스턴스에 연결합니다.

D. 각 EC2 인스턴스에 연결된 Amazon EBS(Amazon Elastic Block Store) 볼륨에 파일 시스템을 생성합니다. 여러 EC2 인스턴스에서 Amazon EBS(Amazon Elastic Block Store) 볼륨을 동기화합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

S3와 EBS는 계층적 디렉토리 구조가 아니다.<br>
EBS는 Block-based 구조.

EFS는 동시성을 지원하며, Multi-attach EBS도 지원하긴 하지만 EFS는 Multi-AZ를 대상으로도 지원하는 반면 EBS는 단일 AZ를 대상으로만 지원한다.

EFS는 1000명 이상의 클라이언트로부터 동시성을 지원하지만, EBS는 16정도이다.

1차 시도 : A 맞음<br>
2차 시도 : C 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 140 ❌⭕ 유념

솔루션 설계자가 문서 관리 작업을 Amazon Web Services로 이전하는 중입니다. 워크로드는 공유 스토리지 파일 시스템 및 외부 데이터베이스에 7테라바이트의 계약 문서를 저장하고 추적합니다. 대부분의 기록은 보관되고 궁극적으로 나중에 참조할 수 있도록 복구됩니다. 마이그레이션 중에는 애플리케이션을 업데이트할 수 없으며 스토리지 솔루션은 고가용성이어야 합니다.
Amazon EC2의 Auto Scaling 그룹에 속한 웹 서버는 문서를 수집하고 저장합니다.(Web servers that are part of an Auto Scaling group on Amazon EC2 collect and store documents) Auto Scaling 그룹에는 최대 12개의 인스턴스가 있을 수 있습니다.

비용 효율성 측면에서 이러한 기준에 가장 적합한 옵션은 무엇입니까?

A. 공유 NFS 스토리지 시스템으로 작동하도록 네트워킹에 최적화된 향상된 EC2 인스턴스를 프로비저닝합니다.

B. S3 Standard-Infrequent Access(S3 Standard-IA) 스토리지 클래스를 사용하는 Amazon S3 버킷을 생성합니다. S3 버킷을 자동 스케일링 그룹의 EC2 인스턴스에 마운트합니다.

C. AWS Transfer for SFTP 및 Amazon S3 버킷을 사용하여 SFTP 서버 엔드포인트를 생성합니다. SFTP 서버에 연결하도록 자동 스케일링 그룹의 EC2 인스턴스를 구성합니다.

D. EFS Standard-Infrequent Access(EFS Standard-IA) 스토리지 클래스를 사용하는 Amazon EFS(Amazon Elastic File System) 파일 시스템을 만듭니다. 파일 시스템을 자동 스케일링 그룹의 EC2 인스턴스에 마운트합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

"Must be highly available" tells you need EFS across

    비즈니스 애플리케이션을 위한 많은 보고 시스템은 비즈니스 기능을 지원하기 위해 액세스 가능한 공유 파일 스토리지에 의존합니다. EFS Standard-IA 및 EFS OneZone-IA 스토리지 클래스를 사용하면 공유 파일 시스템에서 파일을 쉽고 경제적으로 저장하고 액세스할 수 있으므로 비용을 제어하기 위해 데이터를 관리할 필요가 없습니다. 나중에 보고서에 액세스하는 경우 EFS Intelligent-Tiering은 파일 시스템이 standard 또는 OneZone 스토리지 클래스를 사용하는지에 따라 액세스한 보고서를 EFS standard 또는 OneZone 원존 스토리지 클래스로 자동으로 이동할 수 있습니다.

1차 시도 : C 틀림<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/14)