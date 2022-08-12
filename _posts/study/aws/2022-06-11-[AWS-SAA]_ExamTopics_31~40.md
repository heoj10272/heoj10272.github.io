---
layout: post
title: "[AWS-SAA] Examtopics 31~40"
subtitle: AWS
date: '2022-06-11 21:30:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-11-[AWS-SAA]_ExamTopics_31~40/logo.png
---

SAA Examtopics 31~40번 문제를 풀어보자.<br>
1차 7/10<br>
2차 8/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 31 ⭕⭕

현재 회사의 레거시 애플리케이션은 단일 인스턴스가 있는 암호화되지 않은 Amazon RDS MySQL 데이터베이스에 의존합니다. 
이 데이터베이스의 모든 현재 및 새 데이터는 새로운 규정 준수 표준을 준수하도록 암호화되어야 합니다.

이것은 어떻게 달성될 수 있습니까?

A. 서버 측 암호화가 설정된 Amazon S3 버킷을 생성합니다. 모든 데이터를 Amazon S3로 이동합니다. RDS 인스턴스를 삭제합니다.

B. 암호화가 활성화된 상태에서 RDS Multi-AZ 모드를 활성화합니다. 대기 인스턴스에 대한 페일오버를 수행하여 원래 인스턴스를 삭제합니다.

C. RDS 인스턴스의 스냅샷을 만듭니다. 스냅샷의 암호화된 복사본을 생성합니다. 암호화된 스냅샷에서 RDS 인스턴스를 복원합니다.

D. 암호화가 활성화된 RDS 읽기 복제본을 작성합니다. 읽기 복제본을 마스터로 승격하고 응용프로그램을 새 마스터로 전환합니다. 이전 RDS 인스턴스를 삭제합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

다이렉트로 진행중인 RDS를 암호화 시키는 방법은 없다.<br>
스냅샷을 베이스로 새로 데이터베이스를 만들때만 암호화가 가능하다.<br>
파일 시스템을 암호화 하는 것이다.<br>
평문으로 삽입 후 데이터 전체가 암호화된다.

1차 시도 : C 맞음<br>
1차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 32 ❌⭕

마케팅 회사는 Amazon S3 버킷을 사용하여 통계 연구를 위한 CSV 데이터를 저장합니다. 
Amazon EC2 인스턴스에서 실행되는 애플리케이션이 S3 버킷에 저장된 CSV 데이터를 올바르게 처리하려면 권한이 필요합니다.

EC2 인스턴스의 S3 버킷에 대한 가장 안전한 액세스를 제공하는 단계는 무엇입니까?

A. S3 버킷에 리소스 기반 정책을 연결합니다.

B. S3 버킷에 대한 특정 권한이 있는 응용 프로그램에 대한 IAM 사용자를 생성합니다.

C. 최소 권한 권한(least privilege permissions)이 있는 IAM 역할을 EC2 인스턴스 프로파일에 연결합니다.

D. 인스턴스의 응용 프로그램이 API 호출에 사용할 수 있도록 EC2 인스턴스에 AWS 자격 증명을 직접 저장합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

IAM 역할을 할당하는 것이 가장 낫다.<br>
다른 옵션들은 CLI등을 통해 내부에 Access Key를 남기게 된다.

1차 시도 : D 틀림<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 33 ⭕⭕

Amazon Linux EC2 인스턴스 클러스터에서 기업은 애플리케이션을 실행합니다. 
조직은 규정 준수를 위해 모든 애플리케이션 로그 파일을 7년 동안 저장해야 합니다.
로그 파일은 모든 파일에 대한 동시 액세스가 필요한 보고 프로그램에 의해 평가됩니다.

비용 효율성 측면에서 이러한 기준을 가장 잘 충족하는 스토리지 시스템은 무엇입니까?

A. Amazon Elastic Block Store (Amazon EBS)

B. Amazon Elastic File System (Amazon EFS)

C. Amazon EC2 instance store

D. Amazon S3

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D, (or B?)

해설 : 

EFS도 동시 접속이 가능하다.
EFS는 EC2에 S3를 빠르게 붙이려고 하는 형태?
EC2를 벗어나면 쓸 수 없다?

EFS는 Concurrency를 지원한다.

S2는 Write Concurrency를 지원하지 않지만, 지금 상황은 Read이므로 D가 답이라는 말이 있다.

또한 S3는 비용효율적 측면에서 아주 싸다.

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 34 ⭕⭕

Amazon EC2 인스턴스 집합에서 기업은 교육 사이트를 제공합니다. 
이 회사는 웹에서 수백 개의 교육 비디오를 포함하는 새로운 과정이 일주일 안에 제공되면 엄청난 인기를 얻을 것으로 예측합니다.

솔루션 설계자는 예측된 서버 로드를 최소로 유지하기 위해 무엇을 해야 합니까?

A. Redis용 Amazon ElastiCache에 비디오를 저장합니다. ElastiCache API를 사용하여 웹 서버를 업데이트하여 비디오를 제공합니다.

B. 비디오를 Amazon EFS(Amazon Elastic File System)에 저장합니다. EFS 볼륨을 마운트할 웹 서버의 사용자 데이터 스크립트를 만듭니다.

C. 비디오를 Amazon S3 버킷에 저장합니다. 해당 S3 버킷의 OAI(Origin Access ID)를 사용하여 Amazon CloudFront 배포를 생성합니다. OAI에 대한 Amazon S3 액세스를 제한합니다.

D. 비디오를 Amazon S3 버킷에 저장합니다. AWS 스토리지 게이트웨이 파일 게이트웨이를 생성하여 S3 버킷에 액세스합니다. 파일 게이트웨이를 마운트할 웹 서버의 사용자 데이터 스크립트를 생성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

이러한 형태의 경우 대부분 S3와 CloudFront조합이 권고된다.

A. Redis에는 인메모리데이터에 비디오를 저장하는데에 적합하지 않다.
B. EFS로 서버 로드를 줄일 수 없다. EFS가 생각보다 빠르지 않다? EBS보다 느리다?
D. 온프레미스에 대한 솔루션이다.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 35 ⭕⭕

기업은 3계층 웹 애플리케이션을 온프레미스에서 AWS 클라우드로 전환하기로 선택합니다. 
새 데이터베이스는 저장 용량을 동적으로 확장하고 테이블 조인을 수행할 수 있어야 합니다.

이 기준을 충족하는 AWS 서비스는 무엇입니까?

A. Amazon Aurora

B. Amazon RDS for SqlServer

C. Amazon DynamoDB Streams

D. Amazon DynamoDB on-demand

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

C, D의 DynamoDB는 테이블 조인이 불가능하다.<br>
RDS scaling is not dynamic. It is manual.<br>
RDS는 Unscalable, Aurora는 Scalable?<br>
참고 : RDS, Aurora 둘 다 디스크에 한정해서 축소 불가, 확장 가능?<br>
Aurora가 엄청 비싸긴 비싸다고 함

1차 시도 : A 맞음<br>
2차 시도 : A 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 36 ❌❓

Amazon EC2 인스턴스 집합에서 기업은 프로덕션 애플리케이션을 실행합니다. 
이 프로그램은 Amazon SQS 대기열에서 데이터를 가져와 동시에 메시지를 처리합니다. 
메시지 볼륨은 가변적이며 트래픽이 자주 중단됩니다. 
이 프로그램은 중단 없이 지속적으로 메시지를 처리해야 합니다.

비용 효율성 측면에서 이러한 기준에 가장 적합한 옵션은 무엇입니까?

A. 필요한 최대 용량을 처리하려면 스팟 인스턴스를 단독으로 사용하십시오.

B. 예약 인스턴스를 단독으로 사용하여 필요한 최대 용량을 처리합니다.

C. 기본 용량으로 예약 인스턴스를 사용하고 추가 용량을 처리하려면 스팟 인스턴스를 사용합니다.

D. 기본 용량에는 예약 인스턴스를 사용하고 추가 용량을 처리하려면 온디맨드 인스턴스를 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C or D // 답 C인듯

해설 : 

데이터는 SQS에 쌓이고 있기 때문에, 데이터가 날아갈 일은 없다?

1차 시도 : D 틀림<br>
2차 시도 : 모름<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 37 ⭕❌

한 스타트업이 자동차에 설치된 사물인터넷(IoT) 센서에서 데이터를 수집하는 애플리케이션을 개발했습니다.
Amazon Kinesis Data Firehose를 통해 데이터가 Amazon S3로 전송되고 저장됩니다. 
매년 데이터는 수십억 개의 S3 객체를 생성합니다. 
매일 아침 비즈니스는 이전 30일 동안의 데이터를 사용하여 일련의 기계 학습(ML) 모델을 재교육합니다.
회사는 1년에 4번, 이전 12개월의 데이터를 사용하여 다른 기계 학습 모델을 분석하고 교육합니다. 
데이터는 최대 1년 동안 최소한의 지연으로 액세스할 수 있어야 합니다. 
데이터는 1년 후에 아카이브를 위해 보존해야 합니다.

비용 효율성 측면에서 이러한 기준을 가장 잘 충족하는 스토리지 시스템은 무엇입니까?

A. S3 Intelligent-Tiering 스토리지 클래스를 사용합니다. 1년 후 개체를 S3 Glacier Deep Archive로 전환하기 위한 S3 Lifecycle 정책을 만듭니다.

B. S3 Intelligent-Tiering 스토리지 클래스를 사용합니다. 1년 후 개체를 자동으로 S3 Glacier Deep Archive로 이동하도록 S3 Intelligent-Tiering을 구성합니다.

C. S3 Standard-Infrequent Access(S3 Standard-IA) 스토리지 클래스를 사용합니다. 1년 후 개체를 S3 Glacier Deep Archive로 전환하기 위한 S3 Lifecycle 정책을 만듭니다.

D. S3 Standard 스토리지 클래스를 사용합니다. 30일 후 개체를 S3 Standard-Infrequent Access(S3 Standard-IA)로 전환하고 1년 후에는 S3 Glacier Deep Archive로 전환하기 위한 S3 라이프사이클 정책을 생성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D (B가 답이라는 말이 있음) // 답 B가 유력 // 다시 보니 D인듯

해설 : 

    S3 Intelligent-Tiering is the ideal storage class for data with UNKNOWN, CHANGING, or UNPREDICTABLE access patterns, independent of object size or retention period.

위 내용을 이유로 B는 답이 아니라는 말이 있음.
하지만 한 유저는 Intelligent-Tiering이 ML/AI 서비스를 위한 스토리지 클래스이기 때문에 B 일 수도 있다고 말함.

A와 B는 무슨 차이인가?

1차 시도 : D 맞음<br>
2차 시도 : 틀림 <br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 38 ⭕⭕

비즈니스에는 Amazon S3에 데이터 스토리지가 필요합니다. 
규정 준수 요구 사항은 개체가 수정될 때 원래 상태를 유지해야 한다고 규정합니다. 
또한 5년 이상 된 데이터는 감사 목적으로 보관해야 합니다.

솔루션 아키텍트가 가장 노력하기 위해 추천해야 하는 것은 무엇입니까?

A. 거버넌스 모드에서 개체 수준 버전 지정 및 S3 개체 잠금 사용

B. 규정 준수 모드에서 개체 수준 버전 지정 및 S3 개체 잠금 사용

C. 개체 수준 버전 지정을 사용합니다. 5년 이상된 데이터를 S3 Glacier Deep Archive로 이동하기 위한 라이프사이클 정책 지원

D. 개체 수준 버전 지정을 사용합니다. 5년 이상 된 데이터를 S3 Standard-Infrequent Access(S3 Standard-IA)로 이동하기 위한 라이프사이클 정책 사용

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C (B라는 말이 있음)

해설 : 

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 39 ❓⭕

여러 Amazon EC2 인스턴스는 애플리케이션을 호스팅하는 데 사용됩니다. 
이 프로그램은 Amazon SQS 대기열에서 메시지를 읽고 Amazon RDS 데이터베이스에 쓴 다음 대기열에서 제거합니다. 
RDS 테이블에 중복 항목이 포함되는 경우가 있습니다. 
SQS 대기열에 중복 메시지가 없습니다.

솔루션 설계자는 메시지가 한 번만 처리되도록 어떻게 보장할 수 있습니까?

A. CreateQueue API 호출을 사용하여 새 큐를 만듭니다.

B. AddPermission API 호출을 사용하여 적절한 권한을 추가하십시오.

C. ReceiveMessage API 호출을 사용하여 적절한 대기 시간을 설정합니다.

D. ChangeMessageVisibility API 호출을 사용하여 가시성 시간 초과를 늘립니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

표시 시간 제한은 Amazon SQS가 메시지를 반환할 때 시작됩니다. 이 시간 동안 소비자는 메시지를 처리하고 삭제합니다. 그러나 메시지를 삭제하기 전에 소비자가 실패하고 표시 시간 제한이 만료되기 전에 시스템에서 해당 메시지에 대한 메시지 삭제 작업을 호출하지 않으면 메시지가 다른 소비자에게 표시되고 메시지가 다시 수신됩니다. 메시지를 한 번만 수신해야 하는 경우, 사용자는 가시성 제한 시간 내에 메시지를 삭제해야 합니다.

1차 시도 : 모름<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 40 ⭕⭕

한 기업이 리테일 웹사이트의 전 세계 출시를 발표했습니다. 웹사이트는 Elastic Load Balancer를 통해 라우팅되는 수많은 Amazon EC2 인스턴스에서 호스팅됩니다. 인스턴스는 Auto Scaling 그룹의 여러 가용 영역에 분산됩니다. 회사는 고객이 웹사이트를 보는 장치에 따라 맞춤형 자료를 제공하기를 원합니다.

이러한 요구 사항을 충족하기 위해 솔루션 설계자는 어떤 단계를 함께 수행해야 합니까? (2개를 선택하세요.)

A. 여러 버전의 콘텐츠를 캐시하도록 Amazon CloudFront를 구성합니다.

B. 트래픽을 다른 인스턴스로 전달하도록 네트워크 로드 밸런서에서 호스트 헤더를 구성합니다.

C. User-Agent 헤더를 기반으로 특정 개체를 사용자에게 전송하도록 Lambda@Edge 기능을 구성합니다.

D. AWS Global Accelerator를 구성합니다. 요청을 NLB(네트워크 로드 밸런서)로 전달합니다. 서로 다른 EC2 인스턴스에 대한 호스트 기반 라우팅을 설정하도록 NLB를 구성합니다.

E. AWS Global Accelerator를 구성합니다. 요청을 NLB(네트워크 로드 밸런서)로 전달합니다. 서로 다른 EC2 인스턴스에 대한 경로 기반 라우팅을 설정하도록 NLB를 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

해설 : 

A. <br>
CloudFront는 요청 헤더 기반의 콘텐츠 캐싱이 가능하다.<br>
이렇게 하면 사용자가 사용하는 디바이스, 최종 사용자의 위치, 최종 사용자가 사용하는 언어 및 다양한 조건에 따라 서로 다른 버전의 콘텐츠를 제공할 수 있다.

C. <br>
Lambda@Edge기능을 사용하면 요청을 제출한 디바이스에 대한 정보가 포함된 User-Agent 헤더를 기반으로 사용자에게 다른 객체를 전송한다.<br>
예를 들어 디바이스별로 사용자에게 서로 다른 해상도로 이미지를 보낼 수 있다.

1차 시도 : A, C 맞음<br>
2차 시도 : A, C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/4)