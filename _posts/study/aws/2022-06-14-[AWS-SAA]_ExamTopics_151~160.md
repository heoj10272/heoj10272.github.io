---
layout: post
title: "[AWS-SAA] Examtopics 151~160"
subtitle: AWS
date: '2022-06-14 1:20:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-14-[AWS-SAA]_ExamTopics_151~160/logo.png
---

SAA Examtopics 151~160번 문제를 풀어보자.<br>
1차 4/10<br>
2차 9/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 151 ❌⭕

솔루션 설계자는 작업자와 파트너 간의 파일 교환을 가능하게 하는 온프레미스 시스템에 대한 완전 관리형 대안을 제공해야 합니다. 온프레미스 시스템, 원격 직원 및 외부 파트너에서 연결하는 작업자는 솔루션에 쉽게 액세스할 수 있어야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. AWS Transfer for SFTP를 사용하여 Amazon S3로 파일을 전송하거나 내보냅니다.

B. 로컬 스토리지 및 대규모 데이터 전송에는 AWS Snowball Edge를 사용하십시오.

C. Amazon FSX를 사용하여 파일을 저장하고 전송하여 파일을 원격으로 사용할 수 있습니다.

D. AWS 스토리지 게이트웨이를 사용하여 파일을 저장하고 Amazon S3로 전송할 볼륨 게이트웨이를 생성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

AWS 전송 제품군은 Amazon S3 또는 Amazon EFS로 직접 주고받는 파일 전송을 완벽하게 관리합니다. SFTP(Secure File Transfer Protocol), FTP(File Transfer Protocol over SSL) 및 FTP(File Transfer Protocol)를 지원하는 AWS 전송 제품군은 기존 인증 시스템과 통합하고 Amazon Route 53과 DNS 라우팅을 제공하여 사용자의 파일 전송 워크플로우를 AWS로 원활하게 마이그레이션할 수 있도록 지원합니다.고객 및 파트너, 또는 이들의 애플리케이션에 대한 정보를 제공합니다.

AWS 전송 제품군을 사용하면 기존 데이터 교환 프로세스를 보존하면서 Amazon S3 또는 Amazon EFS의 우수한 경제성, 데이터 내구성 및 보안을 활용할 수 있습니다.

1차 시도 : D 틀림<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 152 ❌⭕

기업은 프라이빗 서브넷의 Amazon EC2 인스턴스에서 애플리케이션을 운영하고 있습니다. 프로그램은 Amazon S3에서 데이터를 저장하고 검색할 수 있어야 합니다. 비용을 절감하기 위해 회사는 AWS 리소스 구성을 최적화하려고 합니다.

비즈니스는 이 작업을 어떻게 수행해야 합니까?

A. NAT 게이트웨이를 배포하여 S3 버킷에 액세스합니다.

B. AWS 스토리지 게이트웨이를 배포하여 S3 버킷에 액세스합니다.

C. S3 게이트웨이 끝점을 배포하여 S3 버킷에 액세스합니다.

D. S3 인터페이스 끝점을 배포하여 S3 버킷에 액세스합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

게이트웨이 끝점은 지원되는 서비스에 연결할 수 있도록 라우팅 테이블 내에서 사용되는 대상이며, 현재 게이트웨이 끝점을 사용하는 지원되는 서비스는 Amazon S3 및 Dynamo뿐입니다.

1차 시도 : A 틀림<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 153 ⭕⭕

AWS는 기업에서 사용자 데이터를 저장하는 데 사용합니다. 데이터는 지속적으로 액세스되며 작업 시간 동안 최대 사용량이 발생합니다. 액세스 패턴은 다양하며 일부 데이터는 액세스하지 않고 몇 개월이 걸립니다. 솔루션 설계자는 높은 수준의 가용성을 유지하면서 비용 효율적이고 내구성 있는 솔루션을 선택해야 합니다.

이 기준을 충족하는 스토리지 옵션은 무엇입니까?

A. Amazon S3 Standard

B. Amazon S3 Intelligent-Tiering

C. Amazon S3 Glacier Deep Archive

D. Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA)

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

• S3 Standard와 동일한 낮은 지연 시간 및 높은 처리 성능입니다.
• 월별 모니터링 및 자동 계층화 비용이 적습니다.
• 다음을 기반으로 두 액세스 계층 간에 개체를 자동으로 이동합니다.
액세스 패턴을 변경합니다.
• 여러 개체에 걸쳐 99.999999999%의 내구성을 제공하도록 설계되었습니다.
가용성 영역입니다.
• 전체 가용성 영역에 영향을 미치는 이벤트에 대해 탄력적으로 대처합니다.
• 특정 연도에 99.9%의 가용성을 제공하도록 설계되었습니다.

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 154 ❌❌

기업은 Amazon EC2 인스턴스를 사용하여 레거시 데이터 처리 애플리케이션을 운영합니다. 데이터는 순차적으로 처리되지만 결과의 순서는 중요하지 않습니다.
응용 프로그램은 모놀리식 방식으로 설계되었습니다. 비즈니스가 증가하는 수요에 대응하여 애플리케이션을 확장할 수 있는 유일한 방법은 인스턴스 크기를 늘리는 것입니다.
조직의 엔지니어는 Amazon Elastic Container Service(Amazon ECS)를 사용하는 마이크로서비스 아키텍처를 사용하여 프로그램을 재설계하기로 결정했습니다.

솔루션 설계자는 마이크로서비스 간 통신을 위해 무엇을 제안해야 합니까?

A. Amazon SQS(Simple Queue Service) 대기열을 생성합니다. 데이터 생성자에 코드를 추가하고 데이터를 대기열로 보냅니다. 큐의 데이터를 처리하기 위해 데이터 소비자에 코드를 추가합니다.

B. Amazon Simple Notification Service(Amazon SNS) 항목을 만듭니다. 데이터 생성자에 코드를 추가하고 항목에 알림을 게시합니다. 데이터 소비자에 코드를 추가하여 주제에 가입합니다.

C. 메시지를 전달할 AWS Lambda 함수를 만듭니다. 데이터 생성자에 코드를 추가하여 데이터 개체로 람다 함수를 호출합니다. 데이터 소비자에 코드를 추가하여 람다 함수에서 전달되는 데이터 개체를 수신합니다.

D. Amazon DynamoDB 테이블을 생성합니다. DynamoDB 스트림을 사용합니다. 데이터 생성자에 코드를 추가하여 데이터를 테이블에 삽입합니다. 데이터 소비자에 코드를 추가하여 DynamoDB Streams API를 사용하여 새 테이블 항목을 탐지하고 데이터를 검색합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

"조사 결과의 순서는 관련이 없습니다." - AWS 모범 사례인 애플리케이션을 분리할 수 있습니다.
D 또한 좋아 보이지만, 주요 질문에서 약간 벗어난 주제입니다.

1차 시도 : C 틀림<br>
1차 시도 : C 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 155 ⭕⭕

한 기업이 클래식 애플리케이션을 AWS로 마이그레이션하는 것을 고려하고 있습니다. 현재 애플리케이션은 NFS를 통해 온프레미스 스토리지 시스템과 통신합니다. NFS 이외의 다른 통신 프로토콜을 사용하여 이 기능을 수행하도록 프로그램을 변경할 수 없습니다.

솔루션 설계자는 마이그레이션 후 사용을 위해 어떤 스토리지 솔루션을 제안해야 합니까?

A. AWS DataSync

B. Amazon Elastic Block Store (Amazon EBS)

C. Amazon Elastic File System (Amazon EFS)

D. Amazon EMR File System (Amazon EMRFS)

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Amazon EFS(Amazon Elastic File System)는 스토리지를 프로비저닝하거나 관리하지 않고도 파일 데이터를 공유할 수 있는 단순하고 서버 없는 탄력적인 파일 시스템을 제공합니다. AWS 클라우드 서비스 및 사내 리소스와 함께 사용할 수 있으며, 애플리케이션을 중단하지 않고 온디맨드 방식으로 페타바이트로 확장할 수 있도록 설계되었습니다. Amazon EFS를 사용하면 파일을 추가 및 제거할 때 파일 시스템을 자동으로 확장 및 축소할 수 있으므로 성장에 맞춰 용량을 프로비저닝하고 관리할 필요가 없습니다.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 156 ⭕⭕


기업은 확장성 및 가용성 요구 사항을 충족하기 위해 컨테이너에서 미션 크리티컬 앱을 실행하려고 합니다. 회사는 오히려 주요 애플리케이션 유지 관리에 집중할 것입니다. 회사는 컨테이너화된 워크로드의 기본 인프라 프로비저닝 및 유지 관리에 대한 책임을 원하지 않습니다.

이러한 기준을 충족하기 위해 솔루션 설계자는 어떤 조치를 취해야 합니까?

A. Amazon EC2 인스턴스를 사용하고 인스턴스에 Docker를 설치합니다.

B. Amazon EC2 작업자 노드에서 Amazon ECS(Amazon Elastic Container Service)를 사용합니다.

C. AWS Fargate에서 Amazon Elastic Container Service(Amazon ECS)를 사용합니다.

D. Amazon ECS(Amazon Elastic Container Service)에 최적화된 AMI(Amazon 시스템 이미지)의 Amazon EC2 인스턴스를 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

A) not correct -> company does not want to be responsible fot the provisioning and managing<br>
B) same as A; here you also have to manage it<br>
C) CORRECT -> Fargate is aws service where you only run things and AWS manages it<br>
D) same thing as A and B -> criteria is not to be responsible for provisioning and managing

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 157 ⭕⭕

기업은 이벤트 데이터를 생성하는 서비스를 운영합니다. 회사는 이벤트 데이터를 수신하는 대로 처리하기 위해 AWS를 사용하고자 합니다. 데이터는 처리 중에 보존되어야 하는 특정 순서로 구조화됩니다. 회사는 가능한 가장 낮은 운영 비용으로 솔루션을 배포하기를 원합니다.

솔루션 아키텍트가 이 작업을 어떻게 수행합니까?

A. 메시지를 보관할 Amazon SQS(Amazon Simple Queue Service) FIFO 대기열을 만듭니다. 대기열에서 메시지를 처리하도록 AWS 람다 기능을 설정합니다.

B. 처리할 페이로드를 포함하는 통지를 배달하는 Amazon SNS(Amazon Simple Notification Service) 항목을 만듭니다. AWS 람다 기능을 구독자로 구성합니다.

C. 메시지를 보관할 Amazon SQS(Simple Queue Service) 표준 대기열을 만듭니다. 대기열의 메시지를 독립적으로 처리하도록 AWS 람다 기능을 설정합니다.

D. 처리할 페이로드를 포함하는 통지를 배달하는 Amazon SNS(Amazon Simple Notification Service) 항목을 만듭니다. Amazon SQS(Simple Queue Service) 대기열을 구독자로 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

FIFO(First-In-First-Out) 대기열은 작업 및 이벤트의 순서가 중요하거나 중복을 허용할 수 없는 경우 애플리케이션 간의 메시징을 향상시키도록 설계되었습니다. FIFO 대기열을 사용할 수 있는 상황의 예는 다음과 같습니다.
사용자가 입력한 명령이 올바른 순서로 실행되는지 확인합니다.
올바른 순서로 가격 수정 사항을 전송하여 올바른 제품 가격을 표시합니다.
학생이 계정을 등록하기 전에 과정에 등록하지 못하도록 합니다.

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 158 ❌⭕

비즈니스 데이터베이스는 Amazon Aurora MySQL DB 클러스터의 us-east-1 리전에서 호스팅됩니다. 데이터베이스 크기는 약 4TB입니다. 회사의 재해 복구 계획은 us-west-2 지역을 포함하도록 확장되어야 합니다. 회사는 15분 RTO(복구 시간 목표) 내에 us-west-2로 장애 조치할 수 있어야 합니다.

솔루션 설계자는 이러한 요구 사항을 충족하기 위해 어떤 권장 사항을 제시해야 합니까?

A. us-east-1 및 us-west-2에 Multi-Region Aurora MySQL DB 클러스터를 생성합니다. Amazon Route 53 상태 점검을 사용하여 us-east-1을 모니터링하고 실패 시 us-west-2로 페일오버합니다.

B. us-east-1에서 DB 클러스터의 스냅샷을 만듭니다. 리소스 이벤트를 수신할 때 AWS Lamda 함수를 호출하는 Amazon EventBridge(Amazon CloudWatch Events) 규칙을 구성합니다. 장애가 감지되면 스냅샷을 us-west-2로 복사하고 us-west-2에서 스냅샷을 복원하도록 람다 기능을 구성합니다.

C. AWS CloudFormation 스크립트를 생성하여 오류 발생 시 us-west-2에 다른 Aurora MySQL DB 클러스터를 생성합니다. 리소스 이벤트를 수신할 때 AWS Lamda 함수를 호출하는 Amazon EventBridge(Amazon CloudWatch Events) 규칙을 구성합니다. 장애가 감지되면 us-west-2에 AWS CloudFormation 스택을 배포하도록 Lambda 기능을 구성합니다.

D. 기본 DB 클러스터가 us-east-1에 있고 보조 DB 클러스터가 us-west-2에 있는 Aurora 글로벌 데이터베이스로 데이터베이스를 재생성합니다. 리소스 이벤트를 수신할 때 AWS Lamda 함수를 호출하는 Amazon EventBridge(Amazon CloudWatch Events) 규칙을 구성합니다. 장애가 감지되면 us-west-2에서 DB 클러스터를 승격하도록 람다 기능을 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

여러 Amazon 영역에서 고가용성을 위해 Aurora 글로벌 데이터베이스를 설정할 수 있습니다. 각 Aurora 글로벌 데이터베이스는 여러 Amazon 영역에 걸쳐 있으므로 지연 시간이 짧은 글로벌 읽기 및 Amazon 영역 전체의 운영 중단 시 재해 복구가 가능합니다. Aurora는 기본 Amazon 영역에서 각 보조 영역으로 모든 데이터 및 업데이트 복제를 자동으로 처리합니다.
-> 수정. 답 A.
제 생각에는 A인걱 같습니다
D에 나와있는 마스터 승격은 굳이 람다가 없어도 되는것이고, db데이터를 넣을때마다 람다를 호출해서 마스터를 확인하는건 좋은 방법이 아닌것 같습니다.

그에 반해 A는 멀티 리전으로 만들고 route53에서만 설정하면 운영노력도 적게들고 딱히 부하도 많은거 같지 않습니다.<br>
[링크](https://aws.amazon.com/ko/blogs/database/deploy-multi-region-amazon-aurora-applications-with-a-failover-blueprint/)

1차 시도 : D 틀림<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 159 ❌⭕

기업에서 거의 실시간 스트리밍 데이터를 처리하는 애플리케이션을 설치하고 있습니다. 워크로드는 Amazon EC2 인스턴스에서 실행됩니다. 네트워크 아키텍처는 노드 간의 대기 시간이 가능한 한 최소화되도록 구성되어야 합니다.

이러한 요구 사항에 적합한 네트워크 솔루션 조합은 무엇입니까? (2개를 선택하세요.)

A. 각 EC2 인스턴스에서 고급(enhanced) 네트워킹을 사용하도록 설정하고 구성합니다.

B. EC2 인스턴스를 별도의 계정으로 그룹화합니다.

C. 클러스터 배치 그룹에서 EC2 인스턴스를 실행합니다.

D. 각 EC2 인스턴스에 여러 개의 탄력적인 네트워크 인터페이스를 연결합니다.

E. Amazon EBS(Amazon Elastic Block Store)에 최적화된 인스턴스 유형을 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

해설 : 

D. ENI는 네트워크 성능을 올리지 않는다.

클러스터 배치 그룹은 낮은 네트워크 지연 시간과 높은 네트워크 처리량의 이점을 제공하는 단일 가용성 영역 내의 인스턴스 논리적 그룹입니다.

향상된 네트워킹은 더 높은 대역폭, 더 높은 초당 패킷(PPS) 성능 및 더 낮은 인스턴스 간 지연 시간을 일관되게 제공합니다.

1차 시도 : D, E 틀림<br>
2차 시도 : A, C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 160 ❌⭕

기업은 시장 분석 관리를 제3자 파트너에게 아웃소싱합니다. 공급업체는 회사 계정의 리소스에 대한 제한된 프로그래밍 방식 액세스를 요구합니다. 허용 가능한 액세스를 보장하기 위해 필요한 모든 정책이 수립되었습니다.

공급업체에 계정에 대한 가장 안전한 액세스를 제공하는 새로운 구성 요소는 무엇입니까?

A. IAM 사용자를 만듭니다.

B. 서비스 제어 정책(SCP)을 구현합니다.

C. 외부 ID와 교차 계정 역할(cross-account role)을 사용합니다.

D. SSO(Single Sign-On) ID 제공자를 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

A. Create an IAM user.
- Wrong. We need to grant access to another AWS account, not to another IAM user (from the same account)

B. Implement a service control policy (SCP)
- Wrong. SCPs are organization-wide policies that apply to all AWS accounts belonging to an organization.

C. Use a cross-account role with an external ID.
- Correct. We need an "IAM role" that be shared across accounts

D. Configure a single sign-on (SSO) identity provider.
- Wrong.

1차 시도 : A 틀림<br>
1차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/16)