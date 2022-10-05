---
layout: post
title: "[AWS-SAA] Examtopics 11~20"
subtitle: AWS
date: '2022-06-11 21:10:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-11-[AWS-SAA]_ExamTopics_11~20/logo.png
---

SAA Examtopics 11~20번 문제를 풀어보자.<br>
1차 6/10<br>
2차 6/10<br>
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 11 ❓⭕

Amazon EC2 인스턴스에서 기업은 일시적인 트랜잭션 데이터를 생성하는 애플리케이션을 개발하고 있습니다. 
애플리케이션에는 조정 가능하고 일관된 IOPS를 제공할 수 있는 데이터 스토리지에 대한 액세스가 필요합니다.
솔루션 설계자는 어떤 권장 사항을 제시해야 합니까?

A. 처리량 최적화 HDD(st1) 루트 볼륨과 콜드 HDD(sc1) 데이터 볼륨을 사용하여 EC2 인스턴스를 프로비저닝합니다.

B. 루트 및 데이터 볼륨으로 사용할 처리량 최적화 HDD(st1) 볼륨을 사용하여 EC2 인스턴스를 프로비저닝합니다.

C. 범용 SSD(gp2) 루트 볼륨 및 프로비저닝된 IOPS SSD(io1) 데이터 볼륨을 사용하여 EC2 인스턴스를 프로비저닝합니다.

D. 범용 SSD(gp2) 루트 볼륨을 사용하여 EC2 인스턴스를 프로비저닝합니다. 데이터를 Amazon S3 버킷에 저장하도록 애플리케이션을 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

잘 모르겠음.<br>
Discussion 참조.

C is my answer: Only gp3, io1, or io2 Volumes have configurable IOPS.<br>
[링크](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes.html)

1차 시도 : 모름<br>
2차 시도 : 맞음<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 12 ❌❌

새로운 워크로드를 구현하기 전에 솔루션 설계자는 회사의 현재 IAM 규칙을 검토하고 업데이트해야 합니다. 솔루션 설계자가 작성한 정책은 다음과 같습니다:

![prob_12](/assets/img/study_AWS/2022-06-11-[AWS-SAA]_ExamTopics_11~20/prob_12.png)

그 정책의 순효과는 무엇입니까?

A. 사용자는 s3을 제외한 모든 작업을 수행할 수 있습니다.MFA(Multi-factor Authentication)가 활성화된 경우 PutObject를 입력합니다.

B. 사용자는 s3을 제외한 모든 작업이 허용됩니다.MFA(Multi-factor Authentication)가 활성화되지 않은 경우 PutObject를 입력합니다.

C. 사용자는 s3을 제외한 모든 작업이 거부됩니다.MFA(Multi-factor Authentication)가 활성화된 경우 PutObject를 입력합니다.

D. 사용자는 s3을 제외한 모든 작업이 거부됩니다.MFA(Multi-factor Authentication)가 활성화되지 않은 경우 PutObject를 입력합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

사용자는 s3을 제외한 모든 작업이 거부됩니다.<br>
MFA(Multi-factor Authentication)가 활성화되지 않은 경우 PutObject를 입력합니다.<br>

"Effect": "Deny"<br>
\* = All resources<br>
"NotAction": "S3:PutObject" = Except S3:PutObject<br>
"Condition": "aws:MultiFactorAuthPresent": "false" = If MFA is not enabled

1차 시도 : A<br>
2차 시도 : 틀림<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 13 ❌❓

실시간 처리를 허용하려면 웹 애플리케이션이 Amazon S3에 주문 데이터를 유지해야 합니다.
솔루션 설계자는 확장 가능하고 내결함성이 있는 아키텍처를 설계해야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까? (2개를 선택하세요.)

A. 주문 이벤트를 Amazon DynamoDB 테이블에 기록합니다. DynamoDB Streams를 사용하여 페이로드를 구문 분석하고 Amazon S3에 데이터를 쓰는 AWS Lambda 함수를 트리거합니다.

B. 주문 이벤트를 Amazon Simple Queue Service(Amazon SQS) 대기열에 기록합니다. 대기열을 사용하여 페이로드를 파싱하고 Amazon S3에 데이터를 쓰는 AWSLambda 함수를 트리거합니다.

C. 아마존 심플 알림 서비스(Amazon SNS) 항목에 주문 이벤트를 작성합니다. SNS 항목을 사용하여 페이로드를 구문 분석하고 데이터를 Amazon S3에 쓰는 AWS Lambda 함수를 트리거합니다.

D. 주문 이벤트를 Amazon Simple Queue Service(Amazon SQS) 대기열에 기록합니다. Amazon EventBridge(Amazon CloudWatch Events) 규칙을 사용하여 페이로드를 구문 분석하고 데이터를 Amazon S3에 쓰는 AWS Lambda 함수를 트리거합니다.

E. 아마존 심플 알림 서비스(Amazon SNS) 항목에 주문 이벤트를 작성합니다. Amazon EventBridge(Amazon CloudWatch Events) 규칙을 사용하여 페이로드를 구문 분석하고 데이터를 Amazon S3에 쓰는 AWS Lambda 함수를 트리거합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : Discussion 대환장 A, B가 제일 많긴 하다

해설 : 

Discussion 참조

1차 시도 : A, D<br>
2차 시도 : B, ?<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 14 ⭕❌

us-east-1 지역의 비즈니스에서 사진 호스팅 서비스를 제공합니다. 많은 국가의 사용자가 프로그램을 사용하여 이미지를 업로드하고 탐색할 수 있습니다. 일부 사진은 몇 달 동안 조회수가 높은 반면 다른 사진은 일주일 미만 동안 조회수가 적습니다. 이 프로그램은 최대 20MB 크기의 사진 업로드를 지원합니다. 서비스는 사진 정보를 기반으로 각 사용자에게 어떤 사진을 보여줄지 결정합니다.

적합한 사용자에게 가장 비용 효율적인 액세스를 제공하는 옵션은 무엇입니까?

A. 사진을 Amazon DynamoDB에 저장합니다. 자주 보는 항목을 캐시하려면 DAX(DynamoDB Accelerator)를 켜십시오.

B. 사진을 Amazon S3 Intelligent-Tiering 스토리지 클래스에 저장합니다. 사진 메타데이터와 S3 위치를 DynamoDB에 저장합니다.

C. 사진을 Amazon S3 Standard 스토리지 클래스에 저장합니다. 30일 이상 지난 사진을 S3 Standard-Infrequent Access(S3 Standard-IA) 스토리지 클래스로 이동하기 위해 S3 라이프사이클 정책을 설정합니다. 메타데이터를 추적하려면 개체 태그를 사용하십시오.

D. 사진을 Amazon S3 Glacier 스토리지 클래스에 저장합니다. 30일이 지난 사진을 S3 Glacier Deep Archive 스토리지 클래스로 이동하기 위한 S3 Lifecycle 정책을 설정합니다. 사진 메타데이터와 해당 S3 위치를 Amazon Elastic Search Service(Amazon ES)에 저장합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

그냥 B라고 함.

1차 시도 : B 맞음<br>
2차 시도 : A 틀림<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 15 ⭕⭕

한 비즈니스에서 Amazon S3 버킷에 정적 사진을 저장할 웹 사이트를 만들고 있습니다. 회사의 목표는 모든 향후 요청에 대한 대기 시간과 비용을 줄이는 것입니다.

솔루션 설계자는 서비스 구성을 어떻게 제안해야 합니까?

A. Amazon S3 앞에 NAT 서버를 구축합니다.

B. Amazon S3 앞에 Amazon CloudFront를 배포합니다.

C. Amazon S3 앞에 네트워크 로드 밸런서를 배포합니다.

D. 웹 사이트의 용량을 자동으로 조정하도록 자동 배율을 구성합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Cloudfront + S3 = Static Website

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 16 ❌❌

전자 상거래 웹 사이트의 데이터베이스 계층의 경우 회사는 처리량이 제공되는 Amazon DynamoDB를 사용합니다. 플래시 판매 기간 동안 데이터베이스가 트랜잭션 볼륨을 관리할 수 없을 때 클라이언트는 지연 기간에 직면할 수 있습니다. 결과적으로 비즈니스는 거래를 잃게 됩니다. 데이터베이스는 정규 시간 동안 정상적으로 작동합니다.

어떤 접근 방식이 회사의 성과 문제를 해결합니까?

A. 플래시 영업 중에 DynamoDB를 온디맨드 모드로 전환합니다.

B. 빠른 메모리 성능을 위해 DynamoDB Accelerator를 구현합니다.

C. Amazon Kinesis를 사용하여 트랜잭션을 DynamoDB로 대기열에 넣습니다.

D. 트랜잭션을 DynamoDB로 대기열에 넣으려면 Amazon SQS(Amazon Simple Queue Service)를 사용하십시오.


<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A(91%) or B(9%)

해설 : 

Discussion에서의 한 유저는 B. DAX의 경우 Read에만 영향을 주며, 트랜잭션 볼륨을 관리할 수 없는 이유로 capacity를 꼽았다. 그렇기 때문에 답이 A. 라고 주장한다.

하지만 다른 유저는 DAX는 Read 뿐만 아니라 Write(Put)에도 영향을 주며, DynamoDB는 capacity가 부족할 경우 자동으로 확장할 수 있기 때문에 답이 B. 라고 주장한다.

1차 시도 : B 틀림<br>
2차 시도 : D 틀림<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 17 ⭕⭕

중요한 미디어 회사는 AWS를 사용하여 웹 애플리케이션을 호스팅합니다. 회사는 전 세계 소비자에게 신뢰할 수 있는 액세스를 제공하기 위해 비밀 미디어 파일 캐싱을 시작할 계획입니다. Amazon S3 버킷은 자료를 저장하는 데 사용됩니다. 조직은 요청의 출처에 관계없이 신속하게 자재를 공급해야 합니다.
어떤 솔루션이 이러한 기준을 충족할까요?

A. AWS DataSync를 사용하여 S3 버킷을 웹 응용 프로그램에 연결합니다.

B. AWS Global Accelerator를 배포하여 S3 버킷을 웹 응용 프로그램에 연결합니다.

C. Amazon CloudFront를 배포하여 S3 버킷을 CloudFront 에지 서버에 연결합니다.

D. S3 버킷을 웹 응용 프로그램에 연결하려면 Amazon Simple Queue Service(Amazon SQS)를 사용하십시오.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

A. Data Sync는 온프레미스에서 AWS로 데이터를 옮길 때 사용된다.
B. Global Accelerator는 캐싱이 아닌 network latency를 낮추는데 사용된다.
D. SQS는 문제와 상관이 없는 솔루션이다.

C. CloudFront는 [OAI](https://heoj10272.github.io/study/Amazon-CloudFront-%EC%9D%B4%ED%95%B4.html#iii-origin-access-identityoai)로 `비밀 캐싱`에 도움이 된다.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 18 ⭕⭕

AWS 클라우드에는 웹 애플리케이션이 배포됩니다. 웹 및 데이터베이스 계층으로 구성된 2계층 설계입니다. 웹 서버에서 XSS(교차 사이트 스크립팅) 공격이 가능합니다.

솔루션 설계자가 취약점을 해결하기 위해 취해야 하는 최선의 조치는 무엇입니까?

A. 클래식 로드 밸런서를 생성합니다. 로드 밸런서 뒤에 웹 계층을 배치하고 AWS WAF를 활성화합니다.

B. 네트워크 로드 밸런서를 생성합니다. 로드 밸런서 뒤에 웹 계층을 배치하고 AWS WAF를 활성화합니다.

C. 애플리케이션 로드 밸런서를 생성합니다. 로드 밸런서 뒤에 웹 계층을 배치하고 AWS WAF를 활성화합니다.

D. 애플리케이션 로드 밸런서를 생성합니다. 로드 밸런서 뒤에 웹 계층을 놓고 AWS Shield Standard를 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

AWS WAF는 CLB가 아닌 ALB(애플리케이션 로드 밸런서)와 통합되어 사용된다.

ALB + WAF = Protection from XSS, DDOS => Shield

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 19 ⭕⭕

웹사이트에서 기업은 검색 가능한 물건을 보관합니다. 데이터는 Amazon RDS for MySQL 데이터베이스의 천만 개 이상의 행이 있는 테이블에 저장됩니다. 데이터베이스는 2TB 범용 SSD(gp2) 어레이에 저장됩니다. 매일 회사 웹 사이트는 이 데이터에 대한 수백만 건의 변경 사항을 수신합니다. 조직은 특정 작업에 10초 이상이 소요된다는 사실을 발견하고 병목 현상이 데이터베이스 스토리지 성능이라는 결론을 내렸습니다.

성능 요구 사항을 충족하는 옵션은 무엇입니까?

A. 스토리지 유형을 Provisioned IOPS SSD(io1)로 변경합니다.

B. 인스턴스를 메모리에 최적화된 인스턴스 클래스로 변경합니다.

C. 인스턴스를 버스트 가능한 성능 DB 인스턴스 클래스로 변경합니다.

D. MySQL 기본 비동기 복제로 Multi-AZ RDS 읽기 복제본을 사용합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

데이터 I/O에 따른 스토리지 성능 개선이 필요하므로, A. Provisioned IOPS SSD 솔루션의 이상적인 상황이다.

1차 시도 : A 맞음 <br>
2차 시도 : A 맞음 <br>

</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 20 ⭕⭕

기업은 Amazon S3를 사용하여 민감한 데이터를 저장할 준비가 되어 있습니다. 규정 준수를 위해 데이터를 암호화해야 합니다. 암호화 키 사용에 대한 감사가 필요합니다. 매년 키를 교체해야 합니다.

어떤 솔루션이 이러한 매개변수를 충족하며 운영 효율성 측면에서 가장 최적입니까?

A. 고객이 제공한 키를 사용한 서버 측 암호화(SSE-C)

B. Amazon S3 관리 키를 사용한 서버 측 암호화(SSE-S3)

C. AWS KMS(SSE-KMS) 고객 마스터 키(CMK)를 통한 서버 측 암호화(수동 회전 포함)

D. 자동 회전을 통한 AWS KMS(SSE-KMS) 고객 마스터 키(CMK)를 통한 서버 측 암호화

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

고객이 관리하는 CMK에 대해 자동 키 순환을 활성화하면 AWS KMS는 CMK에 대한 새로운 암호화 자료를 매년 생성한다.

암호화 키에 대한 감사와 키 순환 모두 AWS-KMS에서만 가능하다.
자세한건 KMS에 대해서 알아보도록 하자.

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>

</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/2)