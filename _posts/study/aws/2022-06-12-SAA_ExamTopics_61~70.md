---
layout: post
title: SAA Examtopics 61~70
subtitle: AWS
date: '2022-06-12 20:30:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-12-SAA_ExamTopics_61~70/logo.png
---

SAA Examtopics 61~70번 문제를 풀어보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 61

Amazon EC2에서 기업은 Amazon RDS 데이터베이스에 의해 백업되는 매우 안전한 애플리케이션을 운영하고 있습니다. 모든 개인 식별 정보(PII)는 규정 준수 표준을 준수하기 위해 저장 시 암호화되어야 합니다.

최소한의 인프라 변경으로 이러한 요구 사항을 달성하기 위해 솔루션 설계자는 어떤 솔루션을 제안해야 합니까?

A. AWS 인증서 관리자를 배포하여 인증서를 생성합니다. 인증서를 사용하여 데이터베이스 볼륨을 암호화합니다.

B. AWS 클라우드를 구축합니다.HSM을 사용하여 암호화 키를 생성하고 CMK(고객 마스터 키)를 사용하여 데이터베이스 볼륨을 암호화합니다.

C. AWS KMS CMK(키 관리 서비스 고객 마스터 키)를 사용하여 SSL 암호화를 구성하여 데이터베이스 볼륨을 암호화합니다.

D. AWS KMS(키 관리 서비스) 키를 사용하여 Amazon EBS(Amazon Elastic Block Store) 암호화 및 Amazon RDS 암호화를 구성하여 인스턴스 및 데이터베이스 볼륨을 암호화합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

D-it covers both EC2 and RDS database.<br>

A and C are rules out because question says 'at rest'.<br>
Certificates /SSL are for encryption in transit.

B does not fulfill 'Minimum' Infrastrucure changes, it also does not talk about the EC2 volume.

1차 시도 : C
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 62

솔루션 설계자가 설정한 IAM 정책은 다음과 같습니다.

  ![prob_62](/assets/img/study_AWS/2022-06-12-SAA_ExamTopics_61~70/prob_62.png)

정책에서 허용할 액션은 무엇입니까?

A. AWS 람다 기능은 모든 네트워크에서 삭제할 수 있습니다.

B. AWS 람다 함수는 모든 네트워크에서 만들 수 있습니다.

C. AWS 람다 기능은 100.220.0.0/20 네트워크에서 삭제할 수 있습니다.

D. 220.100.16.0/20 네트워크에서 AWS 람다 기능을 삭제할 수 있습니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

쉬운 문제.

1차 시도 : C
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 63

Amazon Aurora에서 기업은 데이터베이스를 운영하고 있습니다. 매일 밤 데이터베이스는 비활성화됩니다. 사용자 트래픽이 이른 시간에 급증하면 데이터베이스에서 많은 양의 읽기를 수행하는 애플리케이션이 성능 문제에 직면하게 됩니다. 이러한 피크 시간 동안 데이터베이스에서 읽을 때 프로그램에서 시간 초과 문제가 발생합니다. 전담 운영 인력이 없기 때문에 조직은 성능 문제를 해결하기 위한 자동화된 솔루션이 필요합니다.

데이터베이스가 증가하는 읽기 로드에 자동으로 조정되도록 솔루션 설계자가 취해야 하는 활동은 무엇입니까? (2개를 선택하세요.)

A. 데이터베이스를 Aurora Serverless로 마이그레이션합니다.

B. Aurora 데이터베이스의 인스턴스 크기를 늘립니다.

C. Aurora 복제본으로 Aurora 오토 스케일링을 구성합니다.

D. 데이터베이스를 Aurora Multi-Master 클러스터로 마이그레이션합니다.

E. MySQL Multi-AZ 배포를 위해 데이터베이스를 Amazon RDS로 마이그레이션합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C

해설 : 

A and C

- The problem here is to AUTOMATICALLY SCALE READS during traffic surges

A. Migrate the database to Aurora Serverless.<br>
Correct.<br>
 https://aws.amazon.com/rds/aurora/serverless/

B. Increase the instance size of the Aurora database.<br>
Wrong. <br>
The excess capacity will be unutilized during off-peak periods

C. Configure Aurora Auto Scaling with Aurora Replicas.<br>
Correct.<br>
 https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Integrating.AutoScaling.html

D. Migrate the database to an Aurora multi-master cluster.<br>
Wrong. <br>
This helps to scale WRITES, not reads - https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-multi-master.html

E. Migrate the database to an Amazon RDS for MySQL Multi-AZ deployment.<br>
Wrong. <br>
This is for availability and disaster recovery, NOT read scaling. <br>
The standby instance is NOT used to serve reads or writes. <br>
Active-passive failover is adopted.<br>
 https://aws.amazon.com/rds/features/multi-az/

1차 시도 : B, C
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 64

Amazon EC2 인스턴스 기반 애플리케이션은 Amazon DynamoDB 데이터베이스에 대한 액세스 권한이 필요합니다. EC2 인스턴스와 DynamoDB 테이블은 모두 동일한 AWS 계정으로 관리됩니다. 권한은 솔루션 설계자가 구성해야 합니다.

DynamoDB 테이블에 대한 EC2 인스턴스 최소 권한 액세스를 제공하는 접근 방식은 무엇입니까?

A. DynamoDB 테이블에 대한 액세스를 허용하는 적절한 정책을 사용하여 IAM 역할을 만듭니다. 인스턴스 프로파일을 생성하여 이 IAM 역할을 EC2 인스턴스에 할당합니다.

B. DynamoDB 테이블에 대한 액세스를 허용하는 적절한 정책을 사용하여 IAM 역할을 만듭니다. EC2 인스턴스를 신뢰 관계 정책 문서에 추가하여 역할을 수행할 수 있도록 합니다.

C. DynamoDB 테이블에 대한 액세스를 허용하는 적절한 정책을 사용하여 IAM 사용자를 만듭니다. 자격 증명을 Amazon S3 버킷에 저장하고 애플리케이션 코드 내에서 직접 읽습니다.

D. DynamoDB 테이블에 대한 액세스를 허용하는 적절한 정책을 사용하여 IAM 사용자를 만듭니다. 응용 프로그램이 IAM 자격 증명을 로컬 스토리지에 안전하게 저장하고 이를 사용하여 DynamoDB를 호출하는지 확인합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

A is correct<br>
Roles are designed to be “assumed” by other principals which do define “who am I?”, such as users, Amazon services, and EC2 instances.<br>
An instance profile, on the other hand, defines “who am I?” Just like an IAM user represents a person, an instance profile represents EC2 instances. <br>The only permissions an EC2 instance profile has is the power to assume a role.<br>
So the EC2 instance runs under the EC2 instance profile, defining “who” the instance is. It then “assumes” the IAM role, which ultimately gives it any real power.<br>
https://medium.com/devops-dudes/the-difference-between-an-aws-role-and-an-instance-profile-ae81abd700d#:~:text=Roles%20are%20designed%20to%20be,instance%20profile%20represents%20EC2%20instances.

1차 시도 : A
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 65

비즈니스는 Amazon EC2 인스턴스를 사용하여 API 기반 인벤토리 보고 애플리케이션을 운영합니다. 이 프로그램은 Amazon DynamoDB 데이터베이스를 사용하여 데이터를 저장합니다. 기업의 물류 센터는 API와 통신하는 온프레미스 배송 애플리케이션을 사용하여 배송 라벨을 생성하기 전에 인벤토리를 업데이트합니다. 매일 조직은 애플리케이션 중단으로 인해 트랜잭션이 누락되는 것을 목격했습니다.

솔루션 설계자는 애플리케이션의 탄력성을 높이기 위해 무엇을 제안해야 합니까?

A. 로컬 데이터베이스에 쓰도록 발송 응용 프로그램을 수정합니다.

B. AWS Lambda를 사용하여 서버 없이 실행되도록 애플리케이션 API를 수정합니다.

C. EC2 인벤토리 애플리케이션 API를 호출하도록 Amazon API Gateway를 구성합니다.

D. Amazon Simple Queue Service(Amazon SQS)를 사용하여 인벤토리 업데이트를 보내도록 응용 프로그램을 수정합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : Discussion 참조

해설 : 

1차 시도 : D
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 66

거대한

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 

1차 시도 : 
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 67

거대한

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 

1차 시도 : 
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 68

거대한

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 

1차 시도 : 
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 69

거대한

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 

1차 시도 : 
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 70

거대한

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 

1차 시도 : 
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/7)