---
layout: post
title: "[AWS-SAA] Examtopics 141~150"
subtitle: AWS
date: '2022-06-14 1:10:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-14-[AWS-SAA]_ExamTopics_141~150/logo.png
---

SAA Examtopics 141~150번 문제를 풀어보자.<br>
1차 6/10<br>
2차 6/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 141 ⭕⭕

회사는 월별 전화 기록을 유지합니다. 통계적으로 기록된 데이터는 1년 이내에 무작위로 참조될 수 있지만 해당 기간을 초과하여 검색되는 경우는 거의 없습니다.
1년 미만의 파일은 즉시 쿼리하고 검색해야 합니다. 오래된 파일을 가져오는 데 지연이 있는 것은 괜찮습니다. 솔루션 설계자는 캡처된 데이터가 가능한 가장 낮은 비용으로 저장되도록 해야 합니다.

가장 저렴한 옵션은 무엇입니까?

A. 개별 파일을 Amazon S3 Glacier에 저장하고 검색 메타데이터를 S3 Glacier 쿼리 S3 Glacier 태그에서 만든 개체 태그에 저장하고 S3 Glacier에서 파일을 검색합니다.

B. 개별 파일을 Amazon S3에 저장(store)합니다. 라이프사이클 정책을 사용하여 1년 후 파일을 Amazon S3 Glacier로 이동합니다. Amazon S3 또는 S3 Glacier에서 파일을 쿼리하고 검색합니다.

C. 개별 파일을 보관하고 각 보관에 대한 검색 메타데이터를 Amazon S3에 저장합니다. 라이프사이클 정책을 사용하여 1년 후 파일을 Amazon S3 Glacier로 이동합니다. Amazon S3에서 메타데이터를 검색하여 파일을 쿼리하고 검색합니다.

D. Amazon S3에 개별 파일을 보관(archive)합니다. 라이프사이클 정책을 사용하여 1년 후 파일을 Amazon S3 Glacier로 이동합니다. 검색 메타데이터를 Amazon DynamoDB에 저장합니다. DynamoDB에서 파일을 쿼리하고 Amazon S3 또는 S3 Glacier에서 파일을 검색합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

D는 보관이기 때문에 답이 될 수 없다.<br>
또한 DynamoDB에 메타데이터를 저장하려면 Lambda가 필요하다.


1차 시도 : B<br>
2차 시도 : B<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 142 ❌❌

비즈니스에서 워크로드를 AWS로 이동하려고 합니다. 최고 정보 보안 책임자(CIO)는 클라우드에 저장된 모든 데이터를 미사용 시 암호화할 것을 요구합니다. 조직은 암호화 키 수명 주기 관리 프로세스를 완전히 제어하기를 원합니다.
조직은 AWS CloudTrail과 별도로 키 자료를 즉시 삭제하고 키 사용을 감사할 수 있어야 합니다. 선택한 서비스는 다른 AWS 스토리지 서비스와 인터페이스해야 합니다.

이러한 보안 표준을 준수하는 서비스는 무엇입니까?

A. AWS CloudHSM with the CloudHSM client

B. AWS Key Management Service (AWS KMS) with AWS CloudHSM

C. AWS Key Management Service (AWS KMS) with an external key material origin

D. AWS Key Management Service (AWS KMS) with AWS managed customer master keys (CMKs)

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

"You can store your KMS customer master keys (CMKs) in a custom key store instead of the standard KMS key store. Custom key stores are created using an AWS CloudHSM cluster that you own and manage. This provides direct control of the hardware security modules (HSMs) that generate the key material for your CMKs and perform cryptographic operations with them. Learn more to get started with custom key stores you first need to create a AWS CloudHSM cluster."


1차 시도 : C<br>
2차 시도 : C<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 143 ❌⭕

기업은 Amazon Web Services(AWS)에서 애플리케이션을 호스팅하고 Amazon DynamoDB를 데이터베이스로 활용합니다. 데이터베이스의 데이터를 처리하기 위해 조직은 Amazon EC2 인스턴스를 사설 네트워크에 추가합니다. 조직은 2개의 NAT 인스턴스를 사용하여 DynamoDB에 연결합니다.
회사는 NAT 인스턴스를 폐기하려고 합니다. 솔루션 설계자는 DynamoDB에 연결되고 자체 관리되는 솔루션을 개발해야 합니다.

이러한 요구 사항을 충족하는 측면에서 가장 비용 효율적인 접근 방식은 무엇입니까?

A. DynamoDB에 대한 연결을 제공할 게이트웨이 VPC 끝점을 만듭니다.

B. DynamoDB에 대한 연결을 제공하도록 관리되는 NAT 게이트웨이를 구성합니다.

C. 개인 네트워크와 DynamoDB 간에 AWS Direct Connect 연결을 설정합니다.

D. 개인 네트워크와 DynamoDB 사이에 AWS PrivateLink 엔드포인트 서비스를 배포합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

주요 아이디어는 AWS 내부의 DynamoBD와 AWS 외부의 조직 리소스와의 연결을 설정해야 한다는 것입니다.<br>
AWS 내부에 VPC 끝점을 하나만 추가하는 것만으로 이러한 작업을 수행할 수 없습니다(이렇게 하면 AWS 내부 리소스는 연결할 수 있지만 외부에서는 연결할 수 없습니다).<br>
이러한 이유로 NAT 게이트웨이(관리 솔루션)가 대체하기에 적합한 변종입니다.<br>
이 경우 C와 D는 오버헤드일 뿐이고 돈을 낭비합니다.


게이트웨이 끝점은 지원되는 서비스에 연결할 수 있도록 라우팅 테이블 내에서 사용되는 대상이며, 현재 게이트웨이 끝점을 사용하는 지원되는 서비스는 Amazon S3 및 DynamoDB 뿐입니다.

1차 시도 : C
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 144 ❌⭕

기업은 다양한 가용 영역에 걸쳐 있는 가상 사설 클라우드(VPC)에서 3계층 웹 애플리케이션을 호스팅합니다. 애플리케이션 계층의 경우 Amazon EC2 인스턴스는 Auto Scaling 그룹에 배포됩니다.
조직은 각 리소스에 대한 일일 및 주간 워크로드 패턴을 분석하는 자동화된 확장 전략을 개발해야 합니다. 설정은 소비의 예측 및 실제 변경 모두에 대응하여 리소스를 올바르게 확장해야 합니다.

이러한 요구 사항을 충족하기 위해 솔루션 설계자가 제안해야 하는 확장 접근 방식(있는 경우)은 무엇입니까?

A. EC2 인스턴스의 평균 CPU 활용률을 기반으로 단계적 확장을 통해 동적 확장을 구현합니다.

B. 예측 및 확장에 따른 예측 확장을 지원합니다. 대상 추적 기능을 사용하여 동적 스케일링을 구성합니다.

C. 웹 응용 프로그램의 트래픽 패턴을 기반으로 자동 예약 확장 작업을 만듭니다.

D. 단순 확장 정책을 설정합니다. EC2 인스턴스 시작 시간을 기준으로 냉각 기간을 늘립니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

예측 스케일링을 동적 스케일링과 함께 사용합니다. 동적 확장은 리소스 활용률의 실시간 변화에 따라 용량을 자동으로 확장하는 데 사용됩니다. 예측 스케일링과 함께 사용하면 애플리케이션의 수요 곡선을 면밀히 따를 수 있으며, 트래픽이 적을 때는 스케일링하고 트래픽이 예상보다 많을 때는 스케일아웃할 수 있습니다. 여러 확장 정책이 활성 상태인 경우 각 정책은 원하는 용량을 독립적으로 결정하고 원하는 용량은 이들 중 최대 용량으로 설정됩니다. 예를 들어, 대상 추적 확장 정책에서 10개의 인스턴스가 대상 활용률에 머물러야 하고 예측 확장 정책에서 8개의 인스턴스가 대상 활용률에 머물러야 하는 경우 그룹의 원하는 용량은 10으로 설정됩니다.

Forecast / Analysis / future adaptation = Predictive scaling

1차 시도 : A 틀림<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 145 ⭕⭕

기업은 MySQL 데이터베이스를 운영하도록 구성된 자체 Amazon EC2 인스턴스를 관리합니다. 회사는 수요가 증가하거나 감소함에 따라 수동으로 복제 및 확장을 관리합니다. 조직에는 필요에 따라 데이터베이스 계층에서 컴퓨팅 리소스를 더 쉽게 추가하거나 제거할 수 있는 새로운 솔루션이 필요합니다. 또한 솔루션은 운영 부분에서 거의 작업을 수행하지 않고도 속도, 확장성 및 내구성을 높여야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. Aurora MySQL의 경우 데이터베이스를 Amazon Aurora Serverless로 마이그레이션하십시오.

B. Aurora PostgreSQL의 경우 Amazon Aurora Serverless로 데이터베이스를 마이그레이션합니다.

C. 데이터베이스를 하나의 더 큰 MySQL 데이터베이스로 결합합니다. 대형 EC2 인스턴스에서 대형 데이터베이스를 실행합니다.

D. 데이터베이스 계층에 대한 EC2 자동 스케일링 그룹을 생성합니다. 기존 데이터베이스를 새 환경으로 마이그레이션합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

Aurora Serverless = 예측할 수 없는 간헐적 워크로드의 경우, 고객은 최소 Aurora 용량 단위(예: 1 CPU, 2GB RAM, 64 CPU, 122GB RAM)를 지정합니다. 또한 자동 복제, DB 스토리지의 자동 복구, DB 컴퓨팅의 Aurora Replica 자동 확장과 같은 RDS Aurora svc의 나머지 유용한 기능도 갖추고 있으며, AZ 또는 지역에 걸쳐 최대 15개의 활성 Aurora Replica를 지원합니다. "새로운 솔루션", "DB 컴퓨팅 확장 용이", "DB 속도, 확장성, 내구성(HA) 향상", "작은 운영 오버헤드"를 묻는 질문입니다. 서버리스 svc는 소프트웨어 패치 적용이나 업데이트와 같은 EC2 유지보수를 처리하는 것보다 더 완벽합니다.

1차 시도 : A<br>
2차 시도 : A<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 146 ⭕⭕

비즈니스에서 두 개의 앱을 AWS로 이전하려고 합니다. 두 앱 모두 동일한 파일에 액세스하여 엄청난 수의 파일을 동시에 처리합니다. 두 프로그램 모두 최소한의 지연으로 파일을 읽어야 합니다.

이 경우 솔루션 아키텍트가 제안하는 아키텍처는 무엇입니까?

A. 애플리케이션을 실행할 두 개의 AWS Lambda 기능을 구성합니다. 데이터를 저장할 인스턴스 저장소 볼륨을 사용하여 Amazon EC2 인스턴스를 생성합니다.

B. 애플리케이션을 실행할 두 AWS Lambda 기능을 구성합니다. 데이터를 저장할 Amazon EBS(Elastic Block Store) 볼륨을 사용하여 Amazon EC2 인스턴스를 생성합니다.

C. 두 애플리케이션을 동시에 실행하도록 최적화된 메모리 Amazon EC2 인스턴스 하나를 구성합니다. 프로비저닝된 IOPS가 있는 Amazon EBS(Amazon Elastic Block Store) 볼륨을 생성하여 데이터를 저장합니다.

D. 두 개의 Amazon EC2 인스턴스를 구성하여 두 응용 프로그램을 모두 실행합니다. 데이터를 저장할 범용 성능 모드와 버스트 처리량 모드를 사용하여 Amazon EFS(Amazon Elastic File System)를 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

EFS for concurrent access to files.

1차 시도 : D<br>
2차 시도 : D<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 147 ⭕❌

기업은 Kubernetes 클러스터를 사용하여 온프레미스 데이터 센터에서 컨테이너화된 애플리케이션을 운영합니다. 조직은 데이터를 MongoDB 데이터베이스에 저장합니다.
조직은 이러한 환경 중 일부를 AWS로 전환하기를 원하지만 현재 코드 또는 배포 방법을 수정할 수 없습니다. 비즈니스에는 운영 비용을 낮추는 솔루션이 필요합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. 컴퓨팅에는 Amazon EC2 작업자 노드와 Amazon ECS(Amazon Elastic Container Service)를 사용하고 데이터 스토리지에는 EC2의 MongoDB를 사용합니다.

B. 컴퓨팅에는 AWS Fargate와 Amazon ECS(Amazon Elastic Container Service)를 사용하고 데이터 스토리지에는 Amazon DynamoDB를 사용합니다.

C. 컴퓨팅에는 Amazon EC2 작업자 노드와 Amazon EKS(Amazon Elastic Kubernetes Service)를 사용하고 데이터 스토리지에는 Amazon DynamoDB를 사용합니다.

D. 컴퓨팅에는 AWS Fargate와 Amazon EKS(Amazon Elastic Kubernetes Service)를 사용하고 데이터 스토리지에는 Amazon DocumentDB(MongoDB 호환)를 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

A and B are wrong. "using a Kubernetes cluster" - favour EKS (C and D) over ECS (A and B)<br>
C is wrong. "lowers operating costs" - favour serverless (Fargate) over EC2.

1차 시도 : D 맞음<br>
2차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 148 ⭕⭕

비즈니스에 Amazon DynamoDB 데이터 스토리지를 활용하는 모바일 채팅 애플리케이션이 있습니다. 사용자는 새로운 메시지를 읽는 동안 가능한 한 짧은 지연을 원합니다. 솔루션 설계자의 목표는 가능한 최소한의 애플리케이션 수정으로 최적의 솔루션을 제공하는 것입니다.

솔루션 아키텍트가 선택해야 하는 기술은 무엇입니까?

A. 새 메시지 테이블에 대해 DAX(Amazon DynamoDB Accelerator)를 구성합니다. DAX 끝점을 사용하도록 코드를 업데이트합니다.

B. 늘어난 읽기 로드를 처리하기 위해 DynamoDB 읽기 복제본을 추가합니다. 읽기 복제본의 읽기 끝점을 가리키도록 응용프로그램을 업데이트합니다.

C. DynamoDB의 새 메시지 테이블에 대한 읽기 용량 단위 수를 두 배로 늘립니다. 기존 DynamoDB 끝점을 계속 사용합니다.

D. 애플리케이션 스택에 Amazon ElastiCache for Redis 캐시를 추가합니다. DynamoDB 대신 Redis 캐시 끝점을 가리키도록 애플리케이션을 업데이트합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

A가 틀림없어요. DAX에는 DB에 기록되는 모든 새 데이터가 캐시되는 Write-Through 모드가 있어 쓰기 후 다음 읽기가 캐시에서 읽힙니다. 스토리지 기반 캐싱 개념과 매우 유사합니다.

1차 시도 : A 맞음<br>
1차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 149 ⭕❌

기업은 Amazon Web Services를 활용하여 3계층 애플리케이션의 모든 구성 요소를 호스팅합니다. 조직은 환경 내부의 가능한 보안 취약성을 자동으로 식별하기를 원합니다. 조직은 발견을 추적하고 위반이 의심되는 경우 관리자에게 경고하기를 원합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. 의심스러 운 웹 트래픽을 평가하도록 AWS WAF를 설정합니다. AWS Lambda 함수를 생성하여 Amazon CloudWatch에 결과를 기록하고 관리자에게 e-메일 알림을 보냅니다.

B. 의심스러운 웹 트래픽을 평가하도록 AWS Shield를 설정합니다. AWS Lambda 함수를 생성하여 Amazon CloudWatch에 결과를 기록하고 관리자에게 e-메일 알림을 보냅니다.

C. Amazon CloudWatch에서 환경을 모니터링하고 결과를 생성하려면 Amazon Inspector를 배포하십시오. 메시지를 Amazon Simple Notification Service(Amazon SNS) 항목에 게시하여 관리자에게 이메일로 알리도록 Amazon EventBridge(Amazon CloudWatch Events) 규칙을 구성합니다.

D. Amazon CloudWatch에서 환경을 모니터링하고 결과를 생성하려면 Amazon GuardDuty를 배포합니다. 메시지를 Amazon Simple Notification Service(Amazon SNS) 항목에 게시하여 관리자에게 이메일로 알리도록 Amazon EventBridge(Amazon CloudWatch Events) 규칙을 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

A, B는 공격에 대한 방어 방법<br>
C의 Inspector는 EC2 전용

D의 GuardDuty는 지능형 위협 발견을 위한 것이며, 이 사용 사례에서 우리가 찾고 있는 것입니다.

1차 시도 : D 맞음<br>
2차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 150 ❌❌

Amazon RDS MySQL DB 인스턴스에서 회사의 프로덕션 애플리케이션은 OLTP(온라인 트랜잭션 처리) 트랜잭션을 처리합니다. 이 회사는 또한 동일한 데이터 액세스 권한을 가진 새로운 보고 도구(reporting tool)를 제공하고 있습니다. 보고 도구는 액세스 가능성이 높아야 하며 프로덕션 응용 프로그램의 성능에 부정적인 영향을 미치지 않아야 합니다.

이것은 어떻게 이루어지나요?

A. 프로덕션 RDS DB 인스턴스의 스냅샷을 매시간 생성합니다.

B. 프로덕션 RDS DB 인스턴스의 Multi-AZ RDS Read Replica를 생성합니다.

C. 프로덕션 RDS DB 인스턴스의 여러 RDS Read Replica를 작성합니다. 읽기 복제본을 자동 스케일링 그룹에 배치합니다.

D. 프로덕션 RDS DB 인스턴스의 Single-AZ RDS Read Replica를 생성합니다. replica에서 두 번째 Single-AZ RDS Read Replica를 만듭니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

RDS는 관리형 서비스이기 때문에 AWS에서 스케일링을 관리하므로 내가 Auto Scaling Group에 배치할 필요가 없다.

1차 시도 : C 틀림<br>
2차 시도 : C 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/15)