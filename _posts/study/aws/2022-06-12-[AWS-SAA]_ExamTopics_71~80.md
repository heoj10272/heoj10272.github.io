---
layout: post
title: "[AWS-SAA] Examtopics 71~80"
subtitle: AWS
date: '2023-12-12 20:30:01 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-12-[AWS-SAA]_ExamTopics_71~80/logo.png
---

SAA Examtopics 71~80번 문제를 풀어보자.<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 71

기업의 데이터 계층은 PostgreSQL 전용 Amazon RDS를 기반으로 합니다. 조직은 데이터베이스 비밀번호 순환(password rotation)을 채택해야 합니다. 

다음 중 운영 오버헤드가 가장 적은 이 기준을 충족하는 옵션은 무엇입니까?

A. Store the password in AWS Secrets Manager. Enable automatic rotation on the secret.

B. Store the password in AWS Systems Manager Parameter Store. Enable automatic rotation on the parameter.

C. Store the password in AWS Systems Manager Parameter Store. Write an AWS Lambda function that rotates the password.

D. Store the password in AWS Key Management Service (AWS KMS). Enable automatic rotation on the customer master key (CMK).

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

## Prob. 72

기업은 TCP 기반 애플리케이션을 회사의 가상 사설 클라우드(VPC)로 이전하려고 합니다. 이 프로그램은 회사 데이터 센터에 있는 물리적 장치를 통해 지원되지 않는 TCP 포트를 통해 대중에게 제공됩니다. 이 공용 엔드포인트의 대기 시간은 3밀리초 미만이며 초당 최대 3백만 개의 요청을 처리할 수 있습니다. 조직이 동일한 수준의 성능으로 작동하려면 AWS의 새로운 퍼블릭 엔드포인트가 필요합니다.

이 요구 사항을 충족하려면 어떤 솔루션 아키텍처 접근 방식을 권장해야 합니까?

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

## Prob. 73

동일한 AWS 계정 내에서 회사는 us-west-2 리전에 두 개의 VPC를 가지고 있습니다. 비즈니스는 이러한 **VPC 간의 네트워크 통신을 허용**해야 합니다. 매월 약 500GB의 데이터가 VPC 간에 전송됩니다.

이러한 VPC를 연결하는 데 가장 비용 효율적인 접근 방식은 무엇입니까?

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

## Prob. 74

비즈니스의 프로덕션 워크로드는 6개의 Aurora 복제본으로 구성된 Amazon Aurora MySQL DB 클러스터에서 호스팅됩니다. 회사는 세 개의 Aurora 복제본 간에 부서 중 하나의 거의 실시간 보고 요청 배포를 자동화하고자 합니다. 이 세 개의 복사본은 계산 및 메모리 측면에서 나머지 DB 클러스터와 다르게 구성됩니다.

어떤 솔루션이 이러한 기준을 충족합니까?

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

## Prob. 75

기업의 온프레미스 데이터 센터가 스토리지 한도에 도달했습니다. 조직은 대역폭 비용을 가능한 한 낮게 유지하면서 스토리지 시스템을 AWS로 전환하기를 원합니다. 솔루션은 빠르고 비용 없는 데이터 검색을 가능하게 해야 합니다. 

이러한 조건은 어떻게 충족되어야 합니까?

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

## Prob. 76

인수한 지 한 달 이내에 새로 인수한 회사는 AWS에 자체 인프라를 구축하고 다양한 앱을 클라우드로 이전해야 합니다. 각 애플리케이션에는 약 50TB의 데이터 전송이 필요합니다. 이전 후 이 회사와 모회사는 데이터 센터와 앱 간의 처리량이 일정한 보안 네트워크 연결이 필요합니다. 솔루션 설계자는 데이터 전송이 한 번만 발생하고 네트워크 연결이 유지되도록 보장해야 합니다.

어떤 솔루션이 이러한 기준을 충족할까요?

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

## Prob. 77

솔루션 설계자는 인터넷 기반 타사 웹 서비스에서 2분마다 데이터를 검색하는 솔루션을 만들어야 합니다. 각 데이터 검색은 Python 스크립트를 사용하여 100밀리초 미만으로 수행됩니다. 검색 결과는 센서 데이터를 포함하여 크기가 1KB 미만인 JSON 객체입니다. 솔루션 설계자는 JSON 개체와 날짜를 모두 유지해야 합니다.

이러한 요구 사항을 충족하는 데 가장 **비용 효율적인** 접근 방식은 무엇입니까?

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

## Prob. 78

비즈니스에는 현재 파일 공유 서비스가 없습니다. 새 프로젝트에는 온-프레미스 데스크톱 컴퓨터용 디스크로 탑재할 수 있는 파일 저장소가 필요합니다. 사용자가 저장소에 액세스하려면 먼저 파일 서버가 Active Directory 도메인에 대해 사용자를 인증해야 합니다.

Active Directory 사용자가 워크스테이션에 드라이브로 스토리지를 배포할 수 있는 서비스는 무엇입니까?

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

## Prob. 79

온프레미스 애플리케이션을 보유한 기업은 애플리케이션의 유연성과 가용성을 높이기 위해 AWS로 전환하고 있습니다. 현재 설계에서는 Microsoft SQL Server 데이터베이스를 많이 사용합니다. 회사는 다른 데이터베이스 솔루션을 조사하고 필요한 경우 데이터베이스 엔진을 마이그레이션하려고 합니다.
개발 팀은 테스트 데이터베이스를 만들기 위해 4시간마다 프로덕션 데이터베이스의 전체 복사본을 만듭니다. 이 기간 동안 사용자는 지연이 발생합니다.

솔루션 설계자는 대체 데이터베이스로 어떤 데이터베이스를 제안해야 합니까?

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

## Prob. 80

Amazon EC2 인스턴스에서 기업은 애플리케이션을 실행합니다. 웹 페이지에 대한 트래픽 양은 업무 시간 동안 크게 증가했다가 감소합니다.
Amazon EC2 인스턴스의 CPU 사용량은 애플리케이션의 최종 사용자 수요를 측정하는 좋은 방법입니다. 조직은 Auto Scaling 그룹에 대해 2개의 EC2 인스턴스의 최소 그룹 크기와 10개의 EC2 인스턴스의 최대 그룹 크기를 지정했습니다.
회사에서는 Auto Scaling 그룹의 기존 스케일링 정책이 잘못된 것은 아닐까 걱정하고 있습니다. 조직은 과도한 EC2 인스턴스 프로비저닝 및 불필요한 요금 지불을 방지해야 합니다.

솔루션 설계자는 이러한 요구 사항을 충족하기 위해 어떤 권장 사항을 제시해야 합니까?
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
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/33)
