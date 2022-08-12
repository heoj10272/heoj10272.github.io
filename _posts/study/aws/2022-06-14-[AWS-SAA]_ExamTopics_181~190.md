---
layout: post
title: "[AWS-SAA] Examtopics 181~190"
subtitle: AWS
date: '2022-06-14 1:50:00 +0900'
category: study
tags: aws examtopics saa-c02
image:
  path: /assets/img/study_AWS/2022-06-14-[AWS-SAA]_ExamTopics_181~190/logo.png
---

SAA Examtopics 181~190번 문제를 풀어보자.<br>
1차 6/10<br>
2차 8/10<br>
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## Prob. 181 ❌⭕

이제 온프레미스에서 웹 애플리케이션을 호스팅하는 회사는 AWS로 마이그레이션하고 최신 버전의 프로그램을 시작할 준비가 되었습니다. 조직은 URL query string에 따라 AWS 또는 온프레미스 호스팅 애플리케이션으로 요청을 라우팅해야 합니다. 온프레미스 애플리케이션은 인터넷을 통해 액세스할 수 없으며 Amazon VPC와 회사 데이터 센터 간에 VPN 연결이 형성됩니다. 회사는 ALB(Application Load Balancer)를 사용하여 이 애플리케이션을 배포할 계획입니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. Use two ALBs: one for on-premises and one for the AWS resource. Add hosts to each target group of each ALB. Route with Amazon Route 53 based on the URL query string.

B. Use two ALBs: one for on-premises and one for the AWS resource. Add hosts to the target group of each ALB. Create a software router on an EC2 instance based on the URL query string.

C. Use one ALB with two target groups: one for the AWS resource and one for on premises. Add hosts to each target group of the ALB. Configure listener rules based on the URL query string.

D. Use one ALB with two AWS Auto Scaling groups: one for the AWS resource and one for on premises. Add hosts to each Auto Scaling group. Route with Amazon Route 53 based on the URL query string.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

ALB에는 경로를 기준으로 대상을 지정할 수 있는 여러 대상 그룹이 있을 수 있습니다.<br>
또한 IP 대상 그룹 유형은 사내 서버 주소를 가질 수 있습니다.

A- I don't find Anything about routing with query string in Route53<br>
B - Create an EC2 its not an option.<br>
C - You can use listeners to routing with query string and have only one LB is better in management.<br>
D - Auto-scaling group for on-premises don't make sense for me<br>

1차 시도 : A 틀림<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 182 ❌⭕

등록된 상위 ​​도메인에서 회사는 다양한 비즈니스 라인을 위한 많은 웹사이트를 호스팅합니다. 하위 도메인에 따르면 이러한 웹 사이트를 방문하는 모든 사람은 적절한 백엔드 Amazon EC2 인스턴스로 연결됩니다. 정적 웹 페이지, 그림 및 PHP 및 JavaScript와 같은 서버 측 프로그래밍은 모두 웹 사이트에서 호스팅됩니다.
특정 웹사이트는 비즈니스 시작 후 처음 2시간 동안 트래픽이 급증한 후 나머지 시간 동안 지속적으로 사용됩니다. 솔루션 설계자는 비용 효율적이면서도 특정 트래픽 패턴에 자동으로 용량을 조정하는 시스템을 구축해야 합니다.

이러한 요구 사항에 적합한 AWS 서비스 또는 기능 조합은 무엇입니까? (2개를 선택하세요.)

A. AWS Batch

B. Network Load Balancer

C. Application Load Balancer

D. Amazon EC2 Auto Scaling

E. Amazon S3 website hosting

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, D

해설 : 

"웹 사이트는 정적 웹 페이지, 이미지 및 PHP와 같은 서버측 스크립트를 호스팅합니다. JavaScript입니다."<br>
E. (잘못됨). Amazon S3는 서버 측 스크립팅을 지원하지 않습니다.<br>
A. (유효하지 않습니다)<br>
B. (잘못됨)NLB는 4계층에서 실행되며 애플리케이션의 가용성을 보장할 수 없습니다.<br>
네트워크 로드 밸런서는 가용성을 확인할 때 애플리케이션 A와 애플리케이션 B를 구분하지 않지만(실제로 포트가 다르지 않으면 구분할 수 없음) 애플리케이션 로드 밸런서는 사용 가능한 애플리케이션 계층 데이터를 검사하여 두 애플리케이션 사이를 구분합니다. <br>
이러한 차이는 네트워크 로드 밸런서가 충돌했거나 오프라인 상태인 애플리케이션에 요청을 전송하게 될 수 있지만 애플리케이션 로드 밸런서는 이와 같은 실수를 하지 않는다는 것을 의미합니다

1차 시도 : C, E 틀림<br>
2차 시도 : C, D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 183 ⭕⭕

웹 애플리케이션으로서 한 기업이 새로운 비디오 게임을 구축했습니다. 애플리케이션은 VPC의 MySQL용 Amazon RDS를 사용하여 3계층 설계로 배포됩니다. 여러 플레이어가 데이터베이스 계층을 통해 온라인에서 동시에 경쟁합니다. 게임 제작자는 거의 실시간으로 상위 10개 점수판을 표시하고 플레이어가 기존 점수를 유지하면서 게임을 일시 중지했다가 다시 시작할 수 있기를 원합니다.

이러한 기준이 충족되도록 솔루션 설계자는 어떤 조치를 취해야 합니까?

A. Memcached 클러스터용 Amazon ElastiCache를 설정하여 웹 응용 프로그램이 표시할 점수를 캐시합니다.

B. 표시할 웹 응용 프로그램의 점수를 계산하고 캐시하도록 Amazon ElastiCache for Redis 클러스터를 설정합니다.

C. 웹 응용 프로그램 앞에 Amazon CloudFront 배포를 배치하여 응용 프로그램 섹션의 스코어보드를 캐시합니다.

D. MySQL용 Amazon RDS에 읽기 복제본을 만들어 쿼리를 실행하여 스코어보드를 계산하고 웹 응용 프로그램에 읽기 트래픽을 제공합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Redis용 ElastiCache는 확장 가능하고 안전한 완전관리형 서비스로서, 웹, 모바일 앱, 게임, 광고 기술 및 IoT와 같은 고성능 사용 사례에 지원하는 데 매우 적합한 서비스

1차 시도 : B 맞음<br>
2차 시도 : B 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 184 ⭕⭕

기업에서 온프레미스 NAS(Network Attached Storage)를 Amazon Web Services(AWS)로 마이그레이션하려고 합니다. 회사는 VPC 내부의 모든 Linux 인스턴스에서 데이터에 액세스할 수 있도록 하고 데이터 저장소에 대한 변경 사항이 이를 사용하는 모든 인스턴스에서 즉시 동기화되도록 보장하고자 합니다. 대량의 데이터는 드물게 보는 반면 특정 파일은 많은 사람들이 동시에 읽습니다.

이 기준을 충족하고 가장 비용 효율적인 옵션은 무엇입니까?

A. 데이터가 포함된 Amazon EBS(Amazon Elastic Block Store) 스냅샷을 생성합니다. VPC 내의 사용자와 공유합니다.

B. 적절한 일수가 지나면 데이터를 S3 Standard-Infrequent Access(S3 Standard-IA)로 전환하도록 수명 주기 정책이 설정된 Amazon S3 버킷을 생성합니다.

C. VPC 내에 Amazon EFS(Elastic File System) 파일 시스템을 생성합니다. 처리량 모드를 프로비저닝됨으로 설정하고 동시 사용을 지원하는 데 필요한 IOPS 양으로 설정합니다.

D. VPC 내에 Amazon EFS(Elastic File System) 파일 시스템을 생성합니다. 적절한 일수가 경과한 후 데이터를 EFS IA(Recurrent Access)로 전환하도록 라이프사이클 정책을 설정합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

Concurrency = EFS


1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 185 ❌❌

수년 동안 비즈니스는 Amazon RDS 인스턴스에 분석 데이터를 저장해 왔습니다. 이 회사는 소비자가 이 데이터에 액세스할 수 있도록 하는 API를 개발하기 위해 솔루션 설계자를 고용했습니다. 이 프로그램은 유휴 기간이 있을 것으로 예상되지만 몇 초 안에 트래픽이 급증할 수 있습니다.

건축가는 어떤 옵션을 추천해야 합니까?

A. Set up an Amazon API Gateway and use Amazon ECS.

B. Set up an Amazon API Gateway and use AWS Elastic Beanstalk.

C. Set up an Amazon API Gateway and use AWS Lambda functions.

D. Set up an Amazon API Gateway and use Amazon EC2 with Auto Scaling.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

여기서 핵심은 "애플리케이션에서 비활동 기간이 발생할 것으로 예상됩니다."입니다.<br>
Lambda는 사용량에 따라 과금되며 스케일아웃이 가능합니다.<br>
A. 모든 리소스 ECS 제공에 대한 비용을 지불합니다.<br>
B. 당신은 EBS 제공에 대한 모든 자원을 지불할 것입니다.<br>
C. 정답입니다<br>
D. 비활성 기간 동안 Ec2 인스턴스에 대한 비용을 지불해야 합니다.

람다는 수평으로 확장되므로 요청이 버스트될 경우 처리할 수 있습니다. 게다가 비용 효과도 높습니다.

1차 시도 : A 틀림<br>
2차 시도 : A 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 186 ⭕⭕

모바일 게임 스타트업은 Amazon EC2 인스턴스를 사용하여 애플리케이션 서버를 호스팅합니다. 15분마다 서버는 플레이어로부터 업데이트를 받습니다. 모바일 게임은 마지막 업데이트 이후 게임의 진행 상황을 포함하는 JSON 객체를 생성하고 이를 Application Load Balancer에 전달합니다. 모바일 게임을 플레이하면 게임 업데이트가 손실됩니다. 이 회사는 오래된 장치가 업데이트를 받을 수 있는 오래 지속되는 방법을 개발할 계획입니다.

솔루션 설계자는 시스템 디커플링을 위해 무엇을 제안해야 합니까?

A. Amazon Kinesis Data Streams를 사용하여 데이터를 캡처하고 JSON 개체를 Amazon S3에 저장합니다.

B. Amazon Kinesis Data Firehose를 사용하여 데이터를 캡처하고 JSON 개체를 Amazon S3에 저장합니다.

C. Amazon SQS(Simple Queue Service) FIFO 대기열을 사용하여 데이터를 캡처하고 EC2 인스턴스를 사용하여 대기열에 있는 메시지를 처리합니다.

D. Amazon SNS(Amazon Simple Notification Service)를 사용하여 데이터와 EC2 인스턴스를 캡처하여 애플리케이션 로드 밸런서로 전송된 메시지를 처리합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

데이터가 손실되지 않도록 한다는 점과 디커플링이라는 키워드를 봤을 때 답은 C. SQS이다.

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 187 ⭕⭕

회사의 IT 지출에 대한 최근 검토는 백업 비용 절감의 중요성을 보여줍니다. 조직의 CIO는 물리적 백업 테이프를 단계적으로 폐지하여 온프레미스 백업 아키텍처를 단순화하고 비용을 절감하기를 원합니다. 사내 백업 시스템 및 절차에 대한 회사의 현재 투자는 보호되어야 합니다.

솔루션 설계자는 어떤 권장 사항을 제시해야 합니까?

A. NFS 인터페이스를 사용하여 백업 애플리케이션과 연결하도록 AWS Storage Gateway를 설정합니다.

B. NFS 인터페이스를 사용하여 백업 애플리케이션과 연결하는 Amazon EFS(Elastic File System) 파일 시스템을 설정합니다.

C. iSCSI 인터페이스를 사용하여 백업 애플리케이션과 연결하는 Amazon EFS(Elastic File System) 파일 시스템을 설정합니다.

D. iSCSI VTL(가상 테이프 라이브러리) 인터페이스를 사용하여 백업 애플리케이션과 연결하도록 AWS 스토리지 게이트웨이를 설정합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 :

VTL을 사용하여 물리적 백업 테이프를 백업할 수 있다.

1차 시도 : D 맞음<br>
2차 시도 : D 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 188 ❓⭕

기업은 내부 웹 기반 응용 프로그램을 유지 관리합니다. 애플리케이션은 Application Load Balancer를 통해 라우팅되는 Amazon EC2 인스턴스에 배포됩니다. 인스턴스는 Amazon EC2 Auto Scaling 그룹을 통해 여러 가용 영역에 분산됩니다. 업무 시간 동안 Auto Scaling 그룹은 최대 20개의 인스턴스로 확장한 다음 하룻밤 사이에 2개의 인스턴스로 축소합니다. 직원들은 프로그램이 하루를 시작하기에는 매우 느리지만 오전 중반까지는 잘 수행된다고 말합니다.

비용을 낮게 유지하면서 직원의 우려를 수용하기 위해 규모를 어떻게 변경할 수 있습니까?

A. 사무실이 문을 열기 직전에 원하는 용량을 20으로 설정하는 예약된 작업을 실행합니다.

B. 낮은 CPU 임계값에서 트리거되는 단계적 스케일링 동작을 구현하고 냉각 기간을 줄입니다.

C. 더 낮은 CPU 임계값에서 트리거된 목표 추적 동작을 구현하고 냉각 시간을 줄입니다.

D. 사무실이 문을 열기 직전에 최소 및 최대 용량을 20으로 설정하는 예약된 작업을 구현합니다.

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : Discussion 참조 / C

해설 : 
타켓 트랙킹이 가장 좋은 방안일 것.

1차 시도 : A 틀림<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 189 ⭕❌

기업은 모든 이메일을 7년 동안 외부에 저장 및 보존해야 하는 규제 의무를 준수해야 합니다. 관리자가 온프레미스에서 압축된 이메일 파일을 준비했으며 관리형 서비스를 통해 데이터를 AWS 스토리지로 전송하기를 원합니다.

솔루션 아키텍트가 추천해야 하는 관리형 서비스는 무엇입니까?"

A. Amazon Elastic File System (Amazon EFS)

B. Amazon S3 Glacier

C. AWS Backup

D. AWS Storage Gateway

<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

question asks about the transfer service and NOT the storage service , AWS Storage gateway is the only one transfer service in options.

AWS Backup은 온프레미스 서버를 백업할 수 없다.<br>
Storage gateway를 사용해야 한다.

1차 시도 : D 맞음<br>
2차 시도 : B 틀림<br>
</div>
</details>

<br>
<hr/>
<hr/>

## Prob. 190 ⭕⭕

기업은 Elastic Load Balancer를 통해 여러 가용 영역에 분산된 Amazon EC2 인스턴스에서 웹 사이트를 호스팅합니다. 인스턴스는 EC2 Auto Scaling 그룹의 일부로 관리됩니다. 웹 사이트는 Amazon Elastic Block Store(Amazon EBS) 볼륨을 통해 다운로드할 수 있는 제품 설명서를 저장합니다. 조직에서 종종 제품 정보를 변경하므로 Auto Scaling 그룹에서 생성한 새 인스턴스에는 오래된 데이터가 있는 경우가 많습니다. 새 인스턴스에서 모든 변경 사항을 수신하는 데 최대 30분이 소요될 수 있습니다. 또한 변경 사항에는 업무 시간 동안 EBS 볼륨 크기 조정이 포함됩니다.
회사는 제품 설명서가 지속적으로 최신 상태이고 아키텍처가 증가하는 고객 요구에 빠르게 적응할 수 있도록 보장하기를 원합니다.
솔루션 설계자는 기업이 애플리케이션 코드나 웹사이트를 업그레이드하지 않고도 이러한 목표를 충족해야 합니다.

솔루션 설계자는 이 목표를 달성하기 위해 어떤 조치를 취해야 합니까?

A. Store the product manuals in an EBS volume. Mount that volume to the EC2 instances.

B. Store the product manuals in an Amazon S3 bucket. Redirect the downloads to this bucket.

C. Store the product manuals in an Amazon Elastic File System (Amazon EFS) volume. Mount that volume to the EC2 instances.

D. Store the product manuals in an Amazon S3 Standard-Infrequent Access (S3 Standard-IA) bucket. Redirect the downloads to this bucket.


<br>
<hr/>
<br>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

constantly current - always EFS

1차 시도 : C 맞음<br>
2차 시도 : C 맞음<br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c02/view/19)