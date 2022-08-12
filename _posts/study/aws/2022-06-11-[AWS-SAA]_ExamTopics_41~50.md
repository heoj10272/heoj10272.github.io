---
layout: post
title: "[AWS-SAA] Examtopics 41~50"
subtitle: AWS
date: '2022-06-11 21:40:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-11-[AWS-SAA]_ExamTopics_41~50/logo.png
---

SAA Examtopics 41~50번 문제를 풀어보자.<br>
1차 2/10<br>
2차 5/10<br>
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 41 ⭕⭕

실험과 민첩성을 촉진하기 위해 비즈니스에서는 개발자가 현재 IAM 정책을 기존 IAM 역할에 연결할 수 있습니다. 반면 보안 운영 팀은 개발자가 현재 관리자 정책을 첨부하여 다른 보안 규칙을 우회할 수 있다고 우려하고 있습니다.

솔루션 설계자는 이 문제를 처리할 때 어떤 접근 방식을 사용해야 합니까?

A. 개발자가 새 정책을 만들 때마다 알림을 보내는 Amazon SNS 항목을 만듭니다.

B. 서비스 제어 정책을 사용하여 조직 단위의 모든 계정에서 IAM 활동을 비활성화합니다.

C. 개발자가 정책을 첨부하지 못하도록 하고 모든 IAM 작업을 보안 운영 팀에 할당합니다.

D. 개발자 IAM 역할에 관리자 정책 연결을 명시적으로 거부하는 IAM 권한 경계를 설정합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Permission boundaries are for this use case. Be aware that you can assign boundaries only to users and roles, not groups

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 42 ❌⭕

새로 형성된 회사는 3계층 웹 애플리케이션을 개발했습니다. 프런트 엔드는 완전히 정적 정보로 구성됩니다. 마이크로서비스는 애플리케이션 계층을 형성합니다. 사용자 데이터는 최소한의 지연으로 액세스할 수 있는 JSON 문서 형식으로 보관됩니다. 회사는 첫 해에 월별 트래픽 급증과 함께 최소한의 정규 트래픽을 예상합니다. 스타트업 팀의 운영 간접비는 최소한으로 유지되어야 합니다.

솔루션 설계자는 이를 달성하기 위한 수단으로 무엇을 제안해야 합니까?

A. 프런트 엔드를 저장하고 서비스하려면 Amazon S3 정적 웹 사이트 호스팅을 사용하십시오. 애플리케이션 계층에 AWS Elastic Beanstalk를 사용합니다. Amazon DynamoDB를 사용하여 사용자 데이터를 저장합니다.

B. Amazon S3 정적 웹 사이트 호스팅을 사용하여 프런트 엔드를 저장하고 제공합니다. 애플리케이션 계층에 Amazon Elastic Kubernetes Service(Amazon EKS)를 사용합니다. Amazon DynamoDB를 사용하여 사용자 데이터를 저장합니다.

C. Amazon S3 정적 웹 사이트 호스팅을 사용하여 프런트 엔드를 저장하고 제공합니다. 애플리케이션 계층에 Amazon API Gateway 및 AWS Lambda 함수를 사용합니다. Amazon DynamoDB를 사용하여 사용자 데이터를 저장합니다.

D. Amazon S3 정적 웹 사이트 호스팅을 사용하여 프런트 엔드를 저장하고 제공합니다. 애플리케이션 계층에 Amazon API Gateway 및 AWS Lambda 함수를 사용합니다. 읽기 복제본과 함께 Amazon RDS를 사용하여 사용자 데이터를 저장합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

JSON 문서와 같은 비구조화된 데이터는 RDS에 저장할 수 없다.

minimal operational overhead expenditures => lambda & API gateway instead of Beanstalk or EKS<br>
API Gateway + Lambda is best for "Microservices"

1차 시도 : B 틀림<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 43 ❓❓

Amazon Elastic Container Service(Amazon ECS) 컨테이너 인스턴스는 ALB(Application Load Balancer) 뒤에 전자 상거래 웹 사이트의 웹 애플리케이션을 설치하는 데 사용됩니다. 사용량이 많은 순간에는 웹 사이트 속도가 느려지고 가용성이 감소합니다. 솔루션 설계자는 Amazon CloudWatch 경보를 활용하여 가용성 문제가 발생할 때 알림을 받고 리소스를 확장할 수 있습니다. 비즈니스 경영진은 이러한 상황에 자동으로 대응하는 시스템을 원합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. ALB에 시간 초과가 있을 때 ECS 서비스를 확장하도록 AWS 자동 스케일링을 설정합니다. CPU 또는 메모리 예약이 너무 많을 경우 ECS 클러스터를 확장하도록 AWS 자동 스케일링을 설정합니다.

B. AWS 자동 스케일링을 설정하여 ALB CPU 사용률이 너무 높을 경우 ECS 서비스를 스케일아웃합니다. CPU 또는 메모리 예약이 너무 많을 때 ECS 클러스터를 확장하도록 AWS 자동 스케일링을 설정합니다.

C. 서비스의 CPU 활용도가 너무 높을 경우 ECS 서비스를 확장하도록 AWS 자동 스케일링을 설정합니다. CPU 또는 메모리 예약이 너무 많을 경우 ECS 클러스터를 확장하도록 AWS 자동 스케일링을 설정합니다.

D. AWS 자동 스케일링을 설정하여 ALB 대상 그룹의 CPU 사용률이 너무 높을 경우 ECS 서비스를 스케일아웃합니다. CPU 또는 메모리 예약이 너무 많을 경우 ECS 클러스터를 확장하도록 AWS 자동 스케일링을 설정합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : Discussion 참고 / 답 C나 D인데 C가 유력하긴 하다.

해설 : 

모르겠다.<br>
Discussion 참고

1차 시도 : C 맞았는데 모름
2차 시도 : D 틀림 모르겠음
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 44 ❌❌

기업은 Site-to-Site VPN 연결을 사용하여 온프레미스에서 AWS 클라우드 서비스에 안전하게 액세스할 수 있도록 합니다. Amazon EC2 인스턴스에 대한 VPN 연결을 통한 트래픽 증가로 인해 사용자가 VPN 연결 속도가 느려지고 있습니다.
어떤 접근 방식이 VPN 처리량을 증가시킬까요?

A. 동일한 네트워크에 대해 여러 고객 게이트웨이를 구현하여 처리량을 확장합니다.

B. 동일한 비용의 다중 경로 라우팅이 있는 중계(Transit) 게이트웨이를 사용하고 VPN 터널을 추가합니다.

C. 등가 비용 다중 경로 라우팅 및 다중 채널로 가상 사설 게이트웨이를 구성합니다.

D. VPN 구성의 터널 수를 늘려 기본 제한을 초과하여 처리량을 확장합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

AWS Transit Gateway를 사용하면 여러 VPC 간의 연결을 간소화할 수 있으며 단일 VPN 연결로 AWS Transit Gateway에 연결된 모든 VPC에 연결할 수도 있다.<br>
또한 AWS Transit Gateway를 사용하면 여러 VPN 터널에서 ECMP(등비용 다중 경로) 라우팅 지원을 통해 IPsec VPN 처리량을 확장할 수 있다. <br>
단일 VPN 터널의 최대 처리량은 여전히 1.25Gbps이다. <br>
ECMP 사용 중계 게이트웨이에 대한 VPN 터널을 여러 개 설정하면 기본 제한인 1.25Gbps 이상으로 확장할 수 있습니다.

1차 시도 : A 틀림<br>
2차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 45 ⭕❓

Amazon EC2 Linux 인스턴스에서 비즈니스는 웹 사이트를 호스팅합니다. 몇 가지 예가 오작동하고 있습니다. 문제 해결은 실패한 인스턴스에 스왑 공간이 부족함을 나타냅니다. 운영 팀의 리더는 이를 위한 모니터링 솔루션이 필요합니다.

솔루션 설계자는 어떤 권장 사항을 제시해야 합니까?

A. Amazon CloudWatch SwapUsage 메트릭 차원을 구성합니다. CloudWatch의 EC2 메트릭에서 SwapUsage 차원을 모니터링합니다.

B. EC2 메타데이터를 사용하여 정보를 수집한 다음 Amazon CloudWatch 사용자 지정 메트릭에 게시합니다. CloudWatch에서 SwapUsage 메트릭을 모니터링합니다.

C. 인스턴스에 Amazon CloudWatch 에이전트를 설치합니다. 설정된 예약에 따라 적절한 스크립트를 실행합니다. CloudWatch에서 스왑 활용률 메트릭 모니터링

D. EC2 콘솔에서 상세 모니터링을 활성화합니다. Amazon CloudWatch 스왑 사용률 사용자 지정 메트릭을 생성합니다. CloudWatch에서 스왑 활용률 메트릭 모니터링

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

Cloudwatch agent for swap, memory utilization monitoring. Default cant. Must be custom.

D option does not provide SwapUtilization , it s only available thru agent (option C)

1차 시도 : C 맞음<br>
2차 시도 : D 모르겠음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 46 ❌⭕

AWS는 기업에서 OLTP(온라인 트랜잭션 처리) 부담을 수행하는 데 사용됩니다. 이 워크로드는 암호화되지 않은 Amazon RDS 데이터베이스 인스턴스를 사용하여 다중 AZ 환경에 배포됩니다. 이 인스턴스의 데이터베이스는 매일 백업됩니다.

데이터베이스와 스냅샷이 지속적으로 암호화되도록 솔루션 설계자는 앞으로 무엇을 해야 합니까?

A. 최신 DB 스냅샷 복사본을 암호화합니다. 암호화된 스냅샷을 복원하여 기존 DB 인스턴스를 바꿉니다.

B. 암호화된 새 Amazon EBS(Amazon Elastic Block Store) 볼륨을 생성하고 여기에 스냅샷을 복사합니다. DB 인스턴스에서 암호화를 사용합니다.

C. 스냅샷을 복사하고 AWS KMS(키 관리 서비스)를 사용하여 암호화를 사용하도록 설정합니다. 암호화된 스냅샷을 기존 DB 인스턴스에 복원합니다.

D. AWS KMS(키 관리 서비스) 관리 키(SSE-KMS)를 사용하여 서버 측 암호화를 사용하여 암호화된 Amazon S3 버킷에 스냅샷을 복사합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

You can't restore from a DB snapshot to an existing DB instance; a new DB instance is created when you restore.

1차 시도 : C 틀림<br>
2차 시도 : A 맞음<br>
</div>
</details>


<br>
<hr/>
<hr/>

## Prob. 47 ❌⭕

기업은 다양한 Amazon EC2 인스턴스를 통해 소비자로부터 데이터를 수집하는 애플리케이션을 운영합니다. 처리 후 데이터는 장기 저장을 위해 Amazon S3에 업로드됩니다. 애플리케이션 연구에 따르면 EC2 인스턴스가 장기간 비활성 상태인 것으로 나타났습니다. 솔루션 설계자는 비용을 최소화하면서 사용량을 최대화하는 시스템을 제공해야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. 온디맨드 인스턴스가 있는 오토 스케일링 그룹에서 Amazon EC2를 사용합니다.

B. 온디맨드 인스턴스와 함께 Amazon Lightsail을 사용하도록 애플리케이션을 구축합니다.

C. 작업이 없을 때 EC2 인스턴스를 자동으로 중지하는 Amazon CloudWatch cron 작업을 생성합니다.

D. Amazon SQS(Amazon Simple Queue Service) 및 AWS Lambda와 함께 이벤트 중심 설계를 사용하도록 응용 프로그램을 다시 설계하십시오.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A or D

해설 : 

D가 일반적인 답이지만, 재설계는 꺼려진다면 A가 답일 수 있다.<br>
또한 사용량을 최대화해야 하므로 람다 D가 아니라 A가 답이라는 사람이 있다.<br>
둘 다 맞다 치겠다.

1차 시도 : C 틀림<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 48 ❌❓

기업은 많은 독립적인 Amazon Web Services 계정에서 통합된 다중 계정 설계로 마이그레이션하려고 합니다. 조직은 사업부를 위해 많은 수의 새 AWS 계정을 생성할 계획입니다. 조직은 이러한 AWS 계정에 대한 액세스를 인증하기 위해 단일 회사 디렉터리 서비스를 사용해야 합니다.

이러한 요구 사항을 충족하기 위해 솔루션 설계자는 어떤 단계를 옹호해야 합니까? (2개를 선택하세요.)

A. 모든 기능이 설정된 상태에서 AWS 조직에 새 조직을 만듭니다. 조직에서 새 AWS 계정을 생성합니다.

B. Amazon Cognito ID 풀을 설정합니다. Amazon Cognito 인증을 허용하도록 AWS Single Sign-On을 구성합니다.

C. AWS 계정을 관리하도록 SCP(서비스 제어 정책)를 구성합니다. AWS 디렉토리 서비스에 AWS Single Sign-On을 추가합니다.

D. AWS 조직에 새 조직을 만듭니다. AWS 디렉터리 서비스를 직접 사용하도록 조직의 인증 메커니즘을 구성합니다.

E. 조직에 AWS SSO(Single Sign-On)를 설정합니다. AWS SSO를 구성하고 회사의 회사 디렉토리 서비스와 통합합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, E

해설 : 

[링크1](https://docs.aws.amazon.com/singlesignon/latest/userguide/manage-your-identity-source-ad.html)

[링크2](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)

Discussion 참고

1차 시도 : B, C<br>
2차 시도 : 모르겠음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 49 ❌❓

솔루션 설계자는 완료하는 데 최대 2시간이 소요되는 일일 데이터 처리 작업을 개발하고 있습니다. 작업이 중지되면 처음부터 다시 시작해야 합니다.

솔루션 설계자가 이 문제를 해결하는 가장 비용 효율적인 방법은 무엇입니까?

A. cron 작업에 의해 트리거된 Amazon EC2 예약된 인스턴스에서 로컬로 실행되는 스크립트를 생성합니다.

B. Amazon EventBridge(Amazon CloudWatch Events) 예약 이벤트로 트리거된 AWS Lambda 함수를 생성합니다.

C. Amazon EventBridge(Amazon CloudWatch Events) 스케줄링된 이벤트로 트리거된 Amazon ECS(Amazon Elastic Container Service) Fargate 작업을 사용합니다.

D. Amazon EventBridge(Amazon CloudWatch Events) 스케줄링된 이벤트로 트리거된 Amazon EC2에서 실행되는 Amazon Elastic Container Service(Amazon ECS) 작업을 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

A is wrong; "EC2 Reserved Instance" not cost effective compared to serverless<br>
B is wrong; Lambda runs for 15 minutes max<br>
D is wrong; "running on Amazon EC2" not cost effective<br>
C is correct; Fargate is serverless & cost effective comparted to other options.<br>

1차 시도 : D 틀림<br>
2ck 시도 : 모름<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 50 ❌⭕

비즈니스에서 AWS를 사용하여 설문 조사 웹 사이트를 호스팅하려고 합니다. 회사는 많은 양의 트래픽을 예상했습니다. 이 트래픽의 결과로 데이터베이스는 비동기식으로 업데이트됩니다. 조직은 AWS에 보관된 데이터베이스에 대한 쓰기 누락을 방지하기를 원합니다. (The organization want to avoid dropping writes to the database housed on AWS.)
이러한 데이터베이스 요청을 처리하려면 비즈니스 애플리케이션을 어떻게 작성해야 합니까?

A. Amazon Simple Notification Service(Amazon SNS) 항목에 게시하도록 응용 프로그램을 구성합니다. SNS 항목에 데이터베이스를 등록합니다.

B. Amazon Simple Notification Service(Amazon SNS) 항목에 가입하도록 응용 프로그램을 구성합니다. 데이터베이스 업데이트를 SNS 항목에 게시합니다.

C. 데이터베이스에 데이터를 쓸 리소스가 있을 때까지 데이터베이스 연결을 대기하려면 Amazon SQS(Simple Queue Service) FIFO 대기열을 사용합니다.

D. 쓰기를 캡처하고 데이터베이스에 쓸 때마다 대기열을 배출하려면 Amazon SQS(Simple Queue Service) FIFO 대기열을 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Amazon SQS is used for capturing data asynchronously.<br>
SNS is not correct because there is no resilient once SNS pushes messages out .

Why is it D and not C? Because if the consumer consumes connections that doesn't make sense.

1차 시도 : C 틀림<br>
2차 시도 : D 맞음 근데 C랑 D 차이 잘 모르곘음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/5)