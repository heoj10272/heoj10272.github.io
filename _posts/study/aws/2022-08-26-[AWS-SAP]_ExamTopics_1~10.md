---
layout: post
title: "[AWS-SAP] ExamTopics 1~10"
subtitle: AWS
date: '2022-08-26 1:00:00 +0900'
category: study
tags: aws examtopics sap-c01
image:
  path: /assets/img/study_AWS/2022-08-26-[AWS-SAP]_ExamTopics_1~10/logo.png
---

SAP Examtopics 1~10번 문제를 풀어보자.<br>
1차 5/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 1 ⭕
---
회사 정책에서는 유휴 상태의 중요한 데이터를 암호화해야 합니다. EC2 인스턴스에 연결된 EBS 데이터 볼륨에 데이터를 저장하는 동안 데이터를 보호할 수 있는 옵션을 고려하고 있습니다.

다음 중 미사용 데이터를 암호화할 수 있는 옵션은 무엇입니까? (3개를 선택하십시오.)

A. 타사 볼륨 암호화 도구를 구현합니다.

B. 서버에서 실행 중인 모든 서비스에 대해 SSL/TLS를 구현합니다.

C. EBS에 저장하기 전에 응용프로그램 내부의 데이터를 암호화합니다.

D. 파일 시스템 수준에서 기본 데이터 암호화 드라이버를 사용하여 데이터를 암호화합니다.

E. EBS 볼륨이 기본적으로 암호화되어 있으므로 아무 작업도 수행하지 마십시오.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Your company policies require encryption of sensitive data at rest. You are considering the possible options for protecting data while storing it at rest on an EBS data volume, attached to an EC2 instance.

Which of these options would allow you to encrypt your data at rest? (Choose three.)

A. Implement third party volume encryption tools

B. Implement SSL/TLS for all services running on the server

C. Encrypt data inside your applications before storing it on EBS

D. Encrypt data using native data encryption drivers at the file system level

E. Do nothing as EBS volumes are encrypted by default
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, C, D

해설 : 

B : SSL/TLS는 유휴(rest)가 아닌 실행중?(transit)상태의 데이터 암호화에 사용된다.

E : Amazon EBS volume은 디폴트로 암호화되지 않는다. [관련 링크](https://aws.amazon.com/premiumsupport/knowledge-center/ebs-automatic-encryption/)
```
새로운 Amazon EBS 볼륨은 기본적으로 암호화되지 않습니다. 하지만 Amazon Elastic Compute Cloud(Amazon EC2) 콘솔은 지정된 리전에서 생성된 모든 새로운 Amazon EBS 볼륨 및 스냅샷 사본에 대해 기본적으로 암호화를 활성화하는 설정이 있습니다.
```

1차 시도 : A, C, D 맞음 <br>
</div>
</details>

<br>

## Prob. 2 ❌
---
A customer is deploying an SSL enabled web application to AWS and would like to implement a separation of roles between the EC2 service administrators that are entitled to login to instances as well as making API calls and the security officers who will maintain and have exclusive access to the application's X.509 certificate that contains the private key.

A. 보안 담당자가 소유하고 웹 서버의 EC2 역할만 액세스할 수 있는 S3 버킷에 인증서를 업로드합니다.

B. 클라우드에서 부팅할 때 보안 담당자가 관리하는 CloudHSM 으로부터 인증서를 검색하도록 웹 서버를 구성합니다.

C. 인증서에 대한 액세스를 기관 보안 책임자로만 제한하도록 웹 서버에 대한 시스템 권한을 구성합니다.

D. 보안 관리자만 인증서 저장소에 액세스할 수 있도록 권한을 부여하는 IAM 정책을 구성하고 ELB에서 SSL을 종료합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A customer is deploying an SSL enabled web application to AWS and would like to implement a separation of roles between the EC2 service administrators that are entitled to login to instances as well as making API calls and the security officers who will maintain and have exclusive access to the application's X.509 certificate that contains the private key.

A. Upload the certificate on an S3 bucket owned by the security officers and accessible only by EC2 Role of the web servers.

B. Configure the web servers to retrieve the certificate upon boot from an CloudHSM is managed by the security officers.

C. Configure system permissions on the web servers to restrict access to the certificate only to the authority security officers

D. Configure IAM policies authorizing access to the certificate store only to the security officers and terminate SSL on an ELB.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

CloudHSM 은 인증서의 private key를 보관할 수 있지만, 인증서를 보관할수는 없다고 한다.<br>
또한 X.509는 SSL 웹 인증서로, KMS나 CloudHSM 암호화 키가 아니다.

1차 시도 : A 틀림<br>
</div>
</details>

<br>


## Prob. 3 ⭕
---
귀하는 최근에 도시의 거리 소음과 대기 질을 측정하기 위해 센서를 만드는 신생 회사에 입사했습니다. 이 회사는 3개월 동안 각 센서가 1분마다 1KB의 센서 데이터를 AWS에서 호스팅되는 백엔드에 업로드하는 약 100개의 센서를 시범 구현했습니다.
파일럿 기간 동안 데이터베이스에서 피크 또는 10 IOPS를 측정했으며, 데이터베이스에 매달 평균 3GB의 센서 데이터를 저장했습니다.
현재 배포는 EC2 인스턴스와 Postgre를 사용하는 로드 밸런싱된 자동 스케일링 수집 계층으로 구성됩니다.500GB 표준 스토리지가 포함된 SQL RDS 데이터베이스입니다.
파일럿은 성공한 것으로 간주되며 귀사의 CEO는 관심을 끌거나 일부 잠재적 투자자를 확보했습니다. 비즈니스 계획에는 백엔드에서 지원해야 하는 100,000개 이상의 센서를 배포해야 합니다. 또한 센서 데이터를 최소 2년 동안 저장해야 매년 비교할 수 있습니다.
개선되었습니다.
자금을 확보하려면 플랫폼이 이러한 요구 사항을 충족하고 추가 확장을 위한 여지를 남겨야 합니다.

어떤 설정이 요구 사항을 충족합니까?

A. 수집 계층에 SQS 대기열을 추가하여 RDS 인스턴스에 대한 쓰기를 버퍼링합니다.

B. DynamoDB 테이블로 데이터를 수집하고 이전 데이터를 Redshift 클러스터로 이동합니다.

C. RDS 인스턴스를 96TB의 스토리지가 있는 6노드 Redshift 클러스터로 교체합니다.

D. 현재 아키텍처를 유지하되 RDS 스토리지를 3TB 및 10K 프로비저닝 IOPS로 업그레이드하십시오.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You have recently joined a startup company building sensors to measure street noise and air quality in urban areas. The company has been running a pilot deployment of around 100 sensors for 3 months each sensor uploads 1KB of sensor data every minute to a backend hosted on AWS.
During the pilot, you measured a peak or 10 IOPS on the database, and you stored an average of 3GB of sensor data per month in the database.
The current deployment consists of a load-balanced auto scaled Ingestion layer using EC2 instances and a PostgreSQL RDS database with 500GB standard storage.
The pilot is considered a success and your CEO has managed to get the attention or some potential investors. The business plan requires a deployment of at least 100K sensors which needs to be supported by the backend. You also need to store sensor data for at least two years to be able to compare year over year
Improvements.
To secure funding, you have to make sure that the platform meets these requirements and leaves room for further scaling.

Which setup win meet the requirements?

A. Add an SQS queue to the ingestion layer to buffer writes to the RDS instance

B. Ingest data into a DynamoDB table and move old data to a Redshift cluster

C. Replace the RDS instance with a 6 node Redshift cluster with 96TB of storage

D. Keep the current architecture but upgrade RDS storage to 3TB and 10K provisioned IOPS
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

For 100 devices, we need 10 IOPS and 3G per months<br>
So for 100K devices, we need 10K IOPS and 3T per month (or 3T x 24 = 72T per 2 years).<br>
B is correct as we need quick IO process, scalable, no storage limit to handle data then store it to RedShift.<br>
C. RedShift from beginning seem not correct, Redshift is Datawarehouse and can't process quick data, it's used to store data. Furthermore, 96T is fixed and we can't do scalable

100 디바이스일 때 : 10 IOPS, 3G 데이터 저장 발생<br>
100,000 디바이스일 때 : 10,000 IOPS, 3T 데이터 저장 발생

B. 빠른 IO, 확장성, 사실상 무한정의 스토리지 용량이 필요하므로 DynamoDB와 Redshift를 활용하는것이 좋아보인다.

C가 안되는 이유는, Redshift는 데이터 보관소이지 데이터를 빠르게 처리할수는 없다. 또한 96T의 고정된 데이터 용량을 사용하므로 확장성이 없다.

1차 시도 : B 맞음<br>
</div>
</details>

<br>

## Prob. 4 ❓
---
한 웹 회사에서 배포된 VPC에 침입 탐지 및 방지 시스템을 구현하려고 합니다. 이 플랫폼에는 VPC 내부에서 실행되는 수천 개의 인스턴스로 확장할 수 있는 기능이 있어야 합니다.

이러한 목표를 달성하기 위해 솔루션을 어떻게 설계해야 합니까?

A. 모니터링 소프트웨어와 ENI(Elastic Network Interface)가 비규칙(Promiscuous) 모드 패킷 스니핑으로 설정된 인스턴스를 구성하여 VPC 전체의 트래픽을 확인합니다.

B. 두 번째 VPC를 생성하고 기본 애플리케이션 VPC에서 확장 가능한 가상화된 IDS/IPS 플랫폼이 있는 두 번째 VPC를 통해 모든 트래픽을 라우팅합니다.

C. 호스트 기반 'route' 명령을 사용하여 VPC에서 실행 중인 서버를 구성하여 모든 트래픽을 플랫폼을 통해 확장 가능한 가상화된 IDS/IPS로 전송합니다.

D. 모든 네트워크 트래픽을 수집하고 해당 트래픽을 검사를 위해 IDS/IPS 플랫폼으로 보내는 에이전트로 각 호스트를 구성합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A web company is looking to implement an intrusion detection and prevention system into their deployed VPC. This platform should have the ability to scale to thousands of instances running inside of the VPC.
How should they architect their solution to achieve these goals?

A. Configure an instance with monitoring software and the elastic network interface (ENI) set to promiscuous mode packet sniffing to see an traffic across the VPC.

B. Create a second VPC and route all traffic from the primary application VPC through the second VPC where the scalable virtualized IDS/IPS platform resides.

C. Configure servers running in the VPC using the host-based 'route' commands to send all traffic through the platform to a scalable virtualized IDS/IPS.

D. Configure each host with an agent that collects all network traffic and sends that traffic to the IDS/IPS platform for inspection.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

The key line of the question is - "thousands of instances running in the VPC" .

Option C does not confirm that the incoming traffic is passed through the IDS/IPS before reaching the host, which is one of the primary feature/requirement of any IDS/IPS. The traffic will need to pass through the IDS so that any vulnerability could be assessed. Moreover in Option C, you can not expect to manage thousands and thousands of Servers through host based routing.

Option A is invalid as promiscuous mode is not supported in AWS.

Option D does not meet the IPS requirement and moreover although it can perform IDS activities but again it is not a scalable solution.

SO, OPTION B is the correct ANSWER.

`IDS/IPS`가 뭘까?<br>
[링크 참조](https://run-it.tistory.com/47)

IDS(Intrusion Detection System: 침입 탐지 시스템)은 외부에서 내부로 들어오는 패킷이 정상인지 아닌지를 탐지하는 네트워크계의 CCTV 같은 솔루션이다. (여기서 차단 기능이 더해지면 IPS)

그렇기 때문에 IDS/IPS는 일반적으로 내부 네트워크로 들어오는 모든 패킷을 탐지할 수 있는 경로에 설치된다.

개념을 알고 보니 IDS/IPS 전용 문제같다.<br>
A의 promiscuous 모드는 아예 AWS에서 지원이 안된다고 하니 기억하자.<br>
C의 경우 호스트에 도달하기 전에 트래픽이 IDS/IPS 단계를 거쳐야하는데, 호스트 기반 'route' 명령은 이를 위반하나보다. 또한 호스트 기반 라우팅은 수천 대의 서버를 관리할 수 없다고 한다.<br>
D의 경우 네트워크 트래픽을 수집하는게 IDS/IPS의 조건을 위배하는 것 같다. <br>

1차 시도 : 모름 <br>
</div>
</details>

<br>

## Prob. 5 ⭕
---
A사는 Amazon Simple Storage Service(S3)에 데이터를 저장하고 있습니다. 회사의 보안 정책에 따라 데이터는 유휴 상태에서 암호화되어야 합니다.

다음 중 이를 달성할 수 있는 방법은 무엇입니까? (3개를 선택하십시오.)

A. AWS 키 관리 서비스 관리 키와 함께 Amazon S3 서버 측 암호화를 사용합니다.

B. 고객이 제공한 키와 함께 Amazon S3 서버 측 암호화를 사용합니다.

C. EC2 키 쌍과 함께 Amazon S3 서버 측 암호화를 사용합니다.

D. Amazon S3 버킷 정책을 사용하여 유휴 데이터에 대한 액세스를 제한합니다.

E. 자체 마스터 키를 사용하여 Amazon S3로 수집하기 전에 클라이언트 측의 데이터를 암호화합니다.

F. SSL을 사용하여 Amazon S3로 전송하는 동안 데이터를 암호화합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company is storing data on Amazon Simple Storage Service (S3). The company's security policy mandates that data is encrypted at rest.

Which of the following methods can achieve this? (Choose three.)

A. Use Amazon S3 server-side encryption with AWS Key Management Service managed keys.

B. Use Amazon S3 server-side encryption with customer-provided keys.

C. Use Amazon S3 server-side encryption with EC2 key pair.

D. Use Amazon S3 bucket policies to restrict access to the data at rest.

E. Encrypt the data on the client-side before ingesting to Amazon S3 using their own master key.

F. Use SSL to encrypt the data while in transit to Amazon S3.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, B, E

해설 : 

쉬운 문제였다.<br>
각 문항들이 데이터 암호화를 어떻게 하는지에 대한 메뉴얼 같다...

1차 시도 : A, B, E 맞음<br>
</div>
</details>

<br>

## Prob. 6 ❌
---
당신의 회사는 많은 양의 항공 이미지 데이터를 S3에 업로드했습니다. 과거에는 사내 환경에서 전용 서버 그룹을 사용하여 이 데이터를 처리하고 Rabbit MQ - 오픈 소스 메시징 시스템을 사용하여 서버로 작업 정보를 가져왔습니다. 데이터가 처리되면 테이프로 이동하여 오프사이트로 배송됩니다. 매니저는 현재 설계를 유지하고 AWS 아카이브 스토리지 및 메시징 서비스를 활용하여 비용을 최소화하라고 말했습니다.

어떤 것이 올바른가요?

A. 작업 메시지 전달에 SQS를 사용하여 Cloud Watch 경보를 사용하여 EC2 작업자 인스턴스를 유휴 상태로 종료합니다. 데이터가 처리되면 S3 개체의 스토리지 클래스를 Reduced Redundancy Storage로 변경합니다.

B. 스폿 인스턴스를 사용하여 SQS에서 메시지를 처리하는 대기열 크기에 따라 자동 확장 작업자를 설정합니다. 데이터가 처리되면 S3 개체의 스토리지 클래스를 Reduced Redundancy Storage로 변경합니다.

C. 스폿 인스턴스를 사용하여 SQS에서 메시지를 처리하는 대기열 크기에 따라 자동 확장 작업자를 설정합니다. 데이터가 처리되면 S3 개체의 저장 클래스를 Glacier로 변경합니다.

D. SNS를 사용하여 작업 메시지를 전달합니다. Cloud Watch 알람을 사용하여 스폿 작업자 인스턴스가 유휴 상태가 될 때 종료합니다. 데이터가 처리되면 S3 개체의 저장 클래스를 Glacier로 변경합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Your firm has uploaded a large amount of aerial image data to S3. In the past, in your on-premises environment, you used a dedicated group of servers to oaten process this data and used Rabbit MQ - An open source messaging system to get job information to the servers. Once processed the data would go to tape and be shipped offsite. Your manager told you to stay with the current design, and leverage AWS archival storage and messaging services to minimize cost.

Which is correct?

A. Use SQS for passing job messages use Cloud Watch alarms to terminate EC2 worker instances when they become idle. Once data is processed, change the storage class of the S3 objects to Reduced Redundancy Storage.

B. Setup Auto-Scaled workers triggered by queue depth that use spot instances to process messages in SQS. Once data is processed, change the storage class of the S3 objects to Reduced Redundancy Storage.

C. Setup Auto-Scaled workers triggered by queue depth that use spot instances to process messages in SQS. Once data is processed, change the storage class of the S3 objects to Glacier.

D. Use SNS to pass job messages use Cloud Watch alarms to terminate spot worker instances when they become idle. Once data is processed, change the storage class of the S3 object to Glacier.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

애초에 큐의 depth에 따라 트리거 된다는게 이해가 되지 않는다.<br>
많이 쌓이면 확장한다는 뜻인가?<br>
Reduced Redundancy Storage도 모르겠다.<br>
메시징 서비스라는 말에 SNS가 혹했는데, SQS도 메시징 서비스라는 것을 잊지 말자.

[링크](https://heoj10272.github.io/study/AWS-_Amazon_S3_%EC%9D%B4%ED%95%B4.html#i-%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80-%ED%81%B4%EB%9E%98%EC%8A%A4-%EC%9C%A0%ED%98%95)
에 Reduced Redundancy 항목을 추가했다.<br>
중요하지 않은 데이터를 저장하는 스토리지 클래스라는 것만 알면 될 것 같다.<br>
공식에서 권장하지 않는 클래스인 만큼, 답으로 고를 일은 없을 것이다.

1차 시도 : D 틀림<br>
</div>
</details>

<br>

## Prob. 7 ⭕
---
당신은 매우 큰 전자 상거래 사이트의 전반적인 보안 태세를 강화하기 위해 고용되었습니다. VPC에서 잘 설계된 다중 계층 애플리케이션을 실행하고 있으며, S3에서 직접 제공되는 정적 자산으로 웹 및 애플리케이션 계층 앞에서 ELB를 사용합니다. 동적인 데이터에 RDS와 DynamoDB를 함께 사용한 다음 EMR을 통한 추가 처리를 위해 매일 밤 S3에 아카이빙합니다. 그들은 의심스러운 로그 항목을 발견했고 누군가가 무단 액세스를 시도하고 있다고 의심하기 때문에 우려하고 있습니다.

다음 중 이러한 종류의 공격에 대한 비용 효과적이고 확장 가능한 완화를 제공하는 접근 방식은 무엇입니까?

A. DirectConnect 파트너 위치에서 공간을 임대하고 VPC에 대한 1G DirectConnect 연결을 설정한 후 해당 공간에 인터넷 연결을 설정하고 하드웨어 웹 애플리케이션 방화벽(WAF)에서 트래픽을 필터링할 것을 권장합니다. 그런 다음 트래픽을 DirectConnect 연결을 통해 VPC에서 실행 중인 애플리케이션에 전달합니다.

B. 이전에 식별된 적대적 소스 IP를 명시적 INBOUND DENY NACL로 웹 계층 서브넷에 추가합니다.

C. 호스트 기반 WAF를 실행하는 EC2 인스턴스의 자동 확장 그룹 및 새 ELB를 생성하여 WAF 계층을 추가합니다. 그들은 새로운 WAF 계층 ELB로 해결하기 위해 Route 53을 리디렉션할 것입니다. WAF 계층은 트래픽을 현재 웹 계층에 전달합니다. 웹 계층 Security Group은 WAF 계층 Security Group의 트래픽만 허용하도록 업데이트됩니다.

D. 웹 계층 ELB에서 TLS 1.2를 제외한 모든 항목을 제거하고 고급 프로토콜 필터링을 실행하십시오. 이렇게 하면 ELB 자체가 WAF 기능을 수행할 수 있습니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You've been hired to enhance the overall security posture for a very large e-commerce site. They have a well architected multi-tier application running in a VPC that uses ELBs in front of both the web and the app tier with static assets served directly from S3. They are using a combination of RDS and DynamoDB for their dynamic data and then archiving nightly into S3 for further processing with EMR. They are concerned because they found questionable log entries and suspect someone is attempting to gain unauthorized access.

Which approach provides a cost effective scalable mitigation to this kind of attack?

A. Recommend that they lease space at a DirectConnect partner location and establish a 1G DirectConnect connection to their VPC they would then establish Internet connectivity into their space, filter the traffic in hardware Web Application Firewall (WAF). And then pass the traffic through the DirectConnect connection into their application running in their VPC.

B. Add previously identified hostile source IPs as an explicit INBOUND DENY NACL to the web tier subnet.

C. Add a WAF tier by creating a new ELB and an AutoScaling group of EC2 Instances running a host-based WAF. They would redirect Route 53 to resolve to the new WAF tier ELB. The WAF tier would their pass the traffic to the current web tier The web tier Security Groups would be updated to only allow traffic from the WAF tier Security Group

D. Remove all but TLS 1.2 from the web tier ELB and enable Advanced Protocol Filtering. This will enable the ELB itself to perform WAF functionality.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

보안 문제는 웬만하면 WAF가 들어가는게 맞는 듯 하다.

1차 시도 : C 맞음<br>
</div>
</details>

<br>

## Prob. 8 ⭕
---
귀사는 가족들의 반려동물의 건강한 생활습관을 증진시키기 위해 생체 정보를 수집하는 차세대 반려동물 목걸이를 개발하고 있습니다. 각 목걸이는 2초마다 30kb의 JSON 형식의 생체 데이터를 수집 플랫폼으로 밀어넣고, 수집 플랫폼은 웹 포털을 통해 애완동물 주인과 수의사에게 건강 트렌드 정보를 처리하고 분석합니다. 경영진은 다음 요구 사항이 충족되도록 컬렉션 플랫폼을 설계해야 합니다.<br>
✑ 인바운드 생체 인식 데이터의 실시간 분석 기능을 제공합니다.<br>
✑ 생체 인식 데이터의 처리가 매우 내구성이 있는지 확인합니다. 신축성 있고 평행합니다.<br>
✑ 분석 처리 결과는 데이터 마이닝을 위해 지속되어야 합니다.

다음 중 수집 플랫폼의 초기 요구 사항을 충족하는 아키텍처는 무엇입니까?

A. S3를 사용하여 인바운드 센서 데이터를 수집하여 일일 예약 데이터 파이프라인을 사용하여 S3에서 데이터를 분석하고 결과를 Redshift Cluster에 저장합니다.

B. Amazon Kinesis를 사용하여 인바운드 센서 데이터를 수집하고 Kinesis 클라이언트를 사용하여 데이터를 분석한 후 EMR을 사용하여 결과를 Redshift 클러스터에 저장합니다.

C. SQS를 사용하여 인바운드 센서 데이터를 수집하여 Amazon Kinesis를 통해 SQS에서 데이터를 분석하고 결과를 Microsoft SQL Server RDS 인스턴스에 저장합니다.

D. EMR을 사용하여 인바운드 센서 데이터를 수집하고, Amazon Kinesis를 통해 EUR의 데이터를 분석하고, 결과를 DynamoDB에 저장합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Your company is in the process of developing a next generation pet collar that collects biometric information to assist families with promoting healthy lifestyles for their pets. Each collar will push 30kb of biometric data in JSON format every 2 seconds to a collection platform that will process and analyze the data providing health trending information back to the pet owners and veterinarians via a web portal. Management has tasked you to architect the collection platform ensuring the following requirements are met.<br>
✑ Provide the ability for real-time analytics of the inbound biometric data<br>
✑ Ensure processing of the biometric data is highly durable. Elastic and parallel<br>
✑ The results of the analytic processing should be persisted for data mining

Which architecture outlined below win meet the initial requirements for the collection platform?

A. Utilize S3 to collect the inbound sensor data analyze the data from S3 with a daily scheduled Data Pipeline and save the results to a Redshift Cluster.

B. Utilize Amazon Kinesis to collect the inbound sensor data, analyze the data with Kinesis clients and save the results to a Redshift cluster using EMR.

C. Utilize SQS to collect the inbound sensor data analyze the data from SQS with Amazon Kinesis and save the results to a Microsoft SQL Server RDS instance.

D. Utilize EMR to collect the inbound sensor data, analyze the data from EUR with Amazon Kinesis and save me results to DynamoDB.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

Real-time -> Kinesis<br>
Elastic and parallel -> Kinesis Shard<br>
Data mining -> Redshift

실시간 서비스이므로 Kinesis를 골랐고, B와 D중 망설이다 분석이라는 키워드 때문에 Redshift를 골랐다.<br>
샤딩으로 수평 확장이 가능한가 보다.<br>

그런데 EMR과 EUR이 무엇일까?

1차 시도 : B 맞음<br>
</div>
</details>

<br>

## Prob. 9 ❓
---
VPC의 인터넷 연결을 설계하고 있습니다. 웹 서버를 인터넷에서 사용할 수 있어야 합니다.
애플리케이션에 고가용성 아키텍처가 있어야 합니다.

어떤 대안을 고려해야 합니까? (두 개를 선택하십시오.)

A. VPC에서 NAT 인스턴스를 구성합니다. NAT 인스턴스를 통해 기본 경로를 생성하고 이를 모든 서브넷과 연결합니다. NAT 인스턴스 공용 IP 주소를 가리키는 DNS A 레코드를 구성합니다.

B. CloudFront 배포를 구성하고 웹 서버의 개인 IP 주소를 가리키도록 오리진을 구성합니다. CloudFront 배포판에 Route53 CNAME 레코드를 구성합니다.

C. 모든 웹 서버를 ELB 뒤에 배치합니다. ELB DNS 이름을 가리키도록 Route53 CNAME를 구성합니다.

D. 모든 웹 서버에 EIP를 할당합니다. 상태 점검 및 DNS 페일오버를 사용하여 모든 EIP를 포함하는 Route53 레코드 세트를 구성합니다.

E. EIP를 사용하여 ELB를 구성합니다. 모든 웹 서버를 ELB 뒤에 배치합니다. EIP를 가리키는 Route53A 레코드를 구성합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
You are designing Internet connectivity for your VPC. The Web servers must be available on the Internet.
The application must have a highly available architecture.

Which alternatives should you consider? (Choose two.)

A. Configure a NAT instance in your VPC. Create a default route via the NAT instance and associate it with all subnets. Configure a DNS A record that points to the NAT instance public IP address.

B. Configure a CloudFront distribution and configure the origin to point to the private IP addresses of your Web servers. Configure a Route53 CNAME record to your CloudFront distribution.

C. Place all your web servers behind ELB. Configure a Route53 CNAME to point to the ELB DNS name.

D. Assign EIPs to all web servers. Configure a Route53 record set with all EIPs, with health checks and DNS failover.

E. Configure ELB with an EIP. Place all your Web servers behind ELB. Configure a Route53 A record that points to the EIP.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, E

해설 : 

A. Configure a NAT instance in your VPC. Create a default route via the NAT instance and associate it with all subnets. Configure a DNS A record that points to the NAT instance public IP address. - DOEST NO TMAKE SENSE. NAT IS FOR OUTGOING NOT INCOMING.<br>
B. Configure a CloudFront distribution and configure the origin to point to the private IP addresses of your Web servers. Configure a Route53 CNAME record to your CloudFront distribution. ORIGIN CAN NOT BE PRIVATE IP.<br>
C. Place all your web servers behind ELB. Configure a Route53 CNAME to point to the ELB DNS name. POSSIBLE ANSWER<br>
D. Assign EIPs to all web servers. Configure a Route53 record set with all EIPs, with health checks and DNS failover. WHAT? NON SENSE.<br>
E. Configure ELB with an EIP. Place all your Web servers behind ELB. Configure a Route53 A record that points to the EIP. WILL WORK.

A. NAT은 VPC에서 인터넷을 사용할 수 있도록 하는거지 인터넷에서 VPC를 접속할 수 있도록 해주지는 못한다.<br>
B. CloudFront의 Origin은 Private IP가 될 수 없다. 또한 Route53의 CNAME이 아닌 ALIAS를 사용해야 한다?<br>
D. 아예 말이 안되는 듯 하다.

E가 정답인 이유는 ALB는 EIP를 가지지 못하지만, NLB는 가질 수 있다고 한다.
1차 시도 : D, E <br>
</div>
</details>

<br>

## Prob. 10 ❌
---
귀사의 팀에는 개발, 테스트 및 프로덕션 환경에 배포해야 하는 Tomcat 기반 Java 애플리케이션이 있습니다. 어느 정도 조사한 결과, Elastic Beanstalk는 관리 용이성으로 인해 개발자 툴 및 RDS와 긴밀하게 통합되어 있기 때문에 사용하기로 결정했습니다. 귀사의 QA 팀장은 매일 밤 검증된 프로덕션 데이터 세트를 귀사의 환경으로 롤업해야 한다고 지적합니다. 마찬가지로 조직의 다른 소프트웨어 팀도 VPC의 EC2 인스턴스를 통해 동일한 복원된 데이터에 액세스하려고 합니다.

위의 요구 사항을 충족하는 지속성 및 보안을 위한 최적의 설정은 다음과 같습니다.

A. Elastic Beanstalk 정의의 일부로 RDS 인스턴스를 생성하고 애플리케이션 서브넷의 호스트에서 RDS 인스턴스에 액세스할 수 있도록 해당 Security Group을 변경합니다.

B. RDS 인스턴스를 별도로 생성하고 해당 IP 주소를 코드의 애플리케이션의 DB 연결 문자열에 추가합니다. 보안 그룹을 변경하여 VPC의 IP 주소 블록 내의 호스트에서 RDS 인스턴스에 액세스할 수 있도록 합니다.

C. RDS 인스턴스를 별도로 생성하고 해당 DNS 이름을 앱의 DB 연결 문자열에 환경 변수로 전달합니다. 클라이언트 시스템에 대한 Security Group을 생성하고 DB 트래픽에 대한 유효한 소스로 RDS 인스턴스 자체의 Security Group에 추가합니다.

D. RDS 인스턴스를 별도로 생성하고 해당 DNS 이름을 환경 변수로 DB 연결 문자열에 전달합니다. 애플리케이션 서브넷의 호스트에서 해당 인스턴스에 액세스할 수 있도록 Security Group을 변경합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
Your team has a tomcat-based Java application you need to deploy into development, test and production environments. After some research, you opt to use Elastic Beanstalk due to its tight integration with your developer tools and RDS due to its ease of management. Your QA team lead points out that you need to roll a sanitized set of production data into your environment on a nightly basis. Similarly, other software teams in your org want access to that same restored data via their EC2 instances in your VPC.

The optimal setup for persistence and security that meets the above requirements would be the following.

A. Create your RDS instance as part of your Elastic Beanstalk definition and alter its security group to allow access to it from hosts in your application subnets.

B. Create your RDS instance separately and add its IP address to your application's DB connection strings in your code Alter its security group to allow access to it from hosts within your VPC's IP address block.

C. Create your RDS instance separately and pass its DNS name to your app's DB connection string as an environment variable. Create a security group for client machines and add it as a valid source for DB traffic to the security group of the RDS instance itself.

D. Create your RDS instance separately and pass its DNS name to your's DB connection string as an environment variable Alter its security group to allow access to It from hosts in your application subnets.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

It can't be A because the scenario specifically requires persistence. <br>
According to [docs](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.managing.db.html) "A database instance that is part of your environment is tied to the lifecycle of your environment. If you terminate the environment, the database instance is terminated as well. An integrated database instance also cannot be removed from your environment once added."<br>
It can't be B because we never have access to the IP address of any RDS instance.<br>
C & D are very similar except that the scenario requirements specifically state that optimal security should be applied.<br>
It can't be D because RDS is opened to all "hosts in your application subnets" where C only opens RDS to specific client machines in a specific security group.<br>
C is the correct answer.

지속성을 위해서 Beanstalk를 정의할 때는 RDS는 제외하도록 하자.

1차 시도 : B <br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional/view/)

