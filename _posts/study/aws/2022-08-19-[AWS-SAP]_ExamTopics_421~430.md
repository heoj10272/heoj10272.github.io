---
layout: post
title: "[AWS-SAP] ExamTopics 421~430"
subtitle: AWS
date: '2022-08-19 22:00:00 +0900'
category: study
tags: aws examtopics sap-c01
image:
  path: /assets/img/study_AWS/2022-08-19-[AWS-SAP]_ExamTopics_421~430/logo.png
---

SAP Examtopics 421~430번 문제를 풀어보자.<br>
1차 x/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

## Prob. 421 ⭕❌
---

A사는 규제되고 보안에 민감한 작업을 AWS로 마이그레이션할 계획입니다. 보안 팀은 AWS 모범 사례 및 업계에서 공인된 규정 준수 요구 사항을 준수하도록 하기 위한 프레임워크를 구축하고 있습니다. 팀의 경우 AWS Management Console이 리소스 프로비저닝의 주요 방법입니다.

솔루션 설계자는 비즈니스 요구사항을 충족하고 AWS 리소스의 구성을 정기적으로 평가, 감사 및 모니터링하기 위해 어떤 전략을 사용해야 합니까? (둘을 선택하십시오.)

A. AWS 구성 규칙을 사용하여 AWS 리소스에 대한 변경 사항을 정기적으로 감사하고 구성 규정 준수를 모니터링합니다. AWS Lambda를 사용하여 AWS Config 사용자 지정 규칙을 개발하여 테스트 기반 개발 접근 방식을 설정하고 필요한 컨트롤에 대한 구성 변경 평가를 추가로 자동화합니다.

B. Amazon CloudWatch Logs 에이전트를 사용하여 모든 AWS SDK 로그를 수집합니다. 뮤팅 API 호출과 일치하는 미리 정의된 필터 패턴 집합을 사용하여 로그 데이터를 검색합니다. 의도하지 않은 변경이 수행될 때 Amazon CloudWatch 알람을 사용하여 알림을 보냅니다. Amazon S3로 일괄 내보낸 다음 Amazon Glacier로 장기 보존 및 감사 기능을 사용하여 로그 데이터를 보관합니다.

C. AWS CloudTrail 이벤트를 사용하여 모든 AWS 계정의 관리 활동을 평가합니다. CloudTrail이 모든 계정과 사용 가능한 AWS 서비스에서 사용하도록 설정되어 있는지 확인하십시오. 추적 기능을 활성화하고, AWS KMS 키를 사용하여 CloudTrail 이벤트 로그 파일을 암호화하며, CloudWatch Logs를 통해 기록된 작업을 모니터링할 수 있습니다.

D. Amazon CloudWatch Events 거의 실시간 기능을 사용하여 시스템 이벤트 패턴을 모니터링하고 AWS Lambda 기능을 트리거하여 AWS 리소스의 승인되지 않은 변경 사항을 자동으로 되돌립니다. 또한 Amazon SNS 주제를 대상으로 하여 알림을 활성화하고 사고 대응 시간을 단축합니다.

E. CloudTrail을 Amazon SNS와 통합하여 승인되지 않은 API 활동을 자동으로 알립니다. CloudTrail이 모든 계정과 사용 가능한 AWS 서비스에서 사용하도록 설정되어 있는지 확인하십시오. 승인되지 않은 AWS 리소스의 변경 사항을 자동으로 되돌리는 람다 함수의 사용을 평가합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Use AWS Config rules to periodically audit changes to AWS resources and monitor the compliance of the configuration. Develop AWS Config custom rules using AWS Lambda to establish a test-driven development approach, and further automate the evaluation of configuration changes against the required controls.

B. Use Amazon CloudWatch Logs agent to collect all the AWS SDK logs. Search the log data using a pre-defined set of filter patterns that matches mutating API calls. Send notifications using Amazon CloudWatch alarms when unintended changes are performed. Archive log data by using a batch export to Amazon S3 and then Amazon Glacier for a long-term retention and auditability.

C. Use AWS CloudTrail events to assess management activities of all AWS accounts. Ensure that CloudTrail is enabled in all accounts and available AWS services. Enable trails, encrypt CloudTrail event log files with an AWS KMS key, and monitor recorded activities with CloudWatch Logs.

D. Use the Amazon CloudWatch Events near-real-time capabilities to monitor system events patterns, and trigger AWS Lambda functions to automatically revert non-authorized changes in AWS resources. Also, target Amazon SNS topics to enable notifications and improve the response time of incident responses.

E. Use CloudTrail integration with Amazon SNS to automatically notify unauthorized API activities. Ensure that CloudTrail is enabled in all accounts and available AWS services. Evaluate the usage of Lambda functions to automatically revert non-authorized changes in AWS resources.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>


## Prob. 422 ⭕❌
---

기업은 고정 포트에서 TCP를 통해 액세스할 수 있는 새로운 서비스를 구축하고 있습니다. 솔루션 설계자는 서비스가 고가용성(HA)이며 가용성 영역 전체에서 중복되며 공개적으로 액세스할 수 있는 DNS 이름 my.service.com을 통해 연결할 수 있도록 보장해야 합니다. 다른 회사가 허용 목록에 주소를 추가하려면 서비스는 고정 주소 할당을 사용해야 합니다.

리소스가 단일 지역 내에서 여러 가용성 영역에 분산될 경우 이러한 기준을 충족할 수 있는 솔루션은 무엇입니까?

A. 각 인스턴스의 Elastic IP 주소를 사용하여 Amazon EC2 인스턴스를 생성합니다. NLB(네트워크 로드 밸런서)를 생성하고 정적 TCP 포트를 표시합니다. EC2 인스턴스를 NLB에 등록합니다. my.service.com이라는 새 네임 서버 레코드 집합을 만들고 레코드 집합에 EC2 인스턴스의 Elastic IP 주소를 할당합니다. EC2 인스턴스의 Elastic IP 주소를 다른 회사에 제공하여 허용 목록에 추가합니다.

B. 애플리케이션에 대한 서비스 정의 및 Amazon ECS 클러스터를 생성합니다. ECS 클러스터에 대한 공용 IP 주소를 생성하고 할당합니다. NLB(네트워크 로드 밸런서)를 생성하고 TCP 포트를 표시합니다. 대상 그룹을 만들고 ECS 클러스터 이름을 NLB에 할당합니다. my.service.com이라는 새 A 레코드 집합을 만들고 ECS 클러스터의 공용 IP 주소를 레코드 집합에 할당합니다. 허용 목록에 추가할 다른 회사에 ECS 클러스터의 공용 IP 주소를 제공합니다.

C. 서비스에 대한 Amazon EC2 인스턴스를 생성합니다. 각 가용성 영역에 대해 하나의 Elastic IP 주소를 생성합니다. NLB(네트워크 로드 밸런서)를 생성하고 할당된 TCP 포트를 표시합니다. 각 가용성 영역에 대한 NLB에 Elastic IP 주소를 할당합니다. 대상 그룹을 생성하고 EC2 인스턴스를 NLB에 등록합니다. my.service.com이라는 이름의 새 A(파일) 레코드 세트를 만들고 레코드 세트에 NLB DNS 이름을 할당합니다.

D. 애플리케이션의 서비스 정의 및 Amazon ECS 클러스터를 생성합니다. 클러스터의 각 호스트에 대해 공용 IP 주소를 생성하고 할당합니다. ALB(Application Load Balancer)를 생성하고 정적 TCP 포트를 표시합니다. 대상 그룹을 생성하고 ECS 서비스 정의 이름을 ALB에 할당합니다. 새 CNAME 레코드 집합을 만들고 공용 IP 주소를 레코드 집합에 연결합니다. 허용 목록에 추가할 다른 회사에 Amazon EC2 인스턴스의 Elastic IP 주소를 제공합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Create Amazon EC2 instances with an Elastic IP address for each instance. Create a Network Load Balancer (NLB) and expose the static TCP port. Register EC2 instances with the NLB. Create a new name server record set named my.service.com, and assign the Elastic IP addresses of the EC2 instances to the record set. Provide the Elastic IP addresses of the EC2 instances to the other companies to add to their allow lists.

B. Create an Amazon ECS cluster and a service definition for the application. Create and assign public IP addresses for the ECS cluster. Create a Network Load Balancer (NLB) and expose the TCP port. Create a target group and assign the ECS cluster name to the NLB. Create a new A record set named my.service.com, and assign the public IP addresses of the ECS cluster to the record set. Provide the public IP addresses of the ECS cluster to the other companies to add to their allow lists.

C. Create Amazon EC2 instances for the service. Create one Elastic IP address for each Availability Zone. Create a Network Load Balancer (NLB) and expose the assigned TCP port. Assign the Elastic IP addresses to the NLB for each Availability Zone. Create a target group and register the EC2 instances with the NLB. Create a new A (alias) record set named my.service.com, and assign the NLB DNS name to the record set.

D. Create an Amazon ECS cluster and a service definition for the application. Create and assign public IP address for each host in the cluster. Create an Application Load Balancer (ALB) and expose the static TCP port. Create a target group and assign the ECS service definition name to the ALB. Create a new CNAME record set and associate the public IP addresses to the record set. Provide the Elastic IP addresses of the Amazon EC2 instances to the other companies to add to their allow lists.
</div>
</details>


<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>


## Prob. 423 ⭕❌
---

기업은 모든 Amazon Web Services 계정에 대해 중앙 집중식 로깅 인프라를 구축해야 합니다. 아키텍처는 모든 AWS CloudTrail 및 VPC Flow 로그에 대해 거의 실시간에 가까운 데이터 분석을 제공해야 합니다. 조직은 Amazon Elastic Search Service(Amazon ES)를 사용하여 로깅 계정의 로그를 분석할 계획입니다.

A. 각 AWS 계정의 CloudTrail 및 VPC Flow Logs를 구성하여 로깅 계정의 중앙 집중식 Amazon S3 버킷으로 데이터를 전송합니다. 및 AWS Lambda 함수를 생성하여 로깅 계정의 S3 버킷에서 Amazon ES로 데이터를 로드합니다.

B. Amazon CloudWatch 계정의 로그 그룹으로 데이터를 보내도록 CloudTrail 및 VPC Flow Logs를 구성합니다. 각 AWS 계정에서 CloudWatch 구독 필터를 구성하여 로깅 계정의 Amazon Kinesis Data Firehouse에 데이터를 전송합니다. Kinesis Data Firehouse에서 로깅 계정의 Amazon ES로 데이터를 로드합니다.

C. CloudTrail 및 VPC Flow Logs를 구성하여 각 AWS 계정의 별도의 Amazon S3 버킷으로 데이터를 전송합니다. S3 이벤트로 트리거된 AWS Lambda 함수를 생성하여 데이터를 중앙 로깅 버킷에 복사합니다. 다른 Lambda 함수를 생성하여 로깅 계정의 S3 버킷에서 Amazon ES로 데이터를 로드합니다.

D. 각 AWS 계정의 Amazon CloudWatch Logs에 있는 로그 그룹으로 데이터를 보내도록 CloudTrail 및 VPC Flow Logs를 구성합니다. 각 AWS 계정에 AWS Lambda 함수를 생성하여 로그 그룹에 가입하고 데이터를 로깅 계정의 Amazon S3 버킷으로 스트리밍합니다. 다른 Lambda 함수를 생성하여 로깅 계정의 S3 버킷에서 Amazon ES로 데이터를 로드합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Configure CloudTrail and VPC Flow Logs in each AWS account to send data to a centralized Amazon S3 bucket in the logging account. Create and AWS Lambda function to load data from the S3 bucket to Amazon ES in the logging account.

B. Configure CloudTrail and VPC Flow Logs to send data to a log group in Amazon CloudWatch account. Configure a CloudWatch subscription filter in each AWS account to send data to Amazon Kinesis Data Firehouse in the logging account. Load data from Kinesis Data Firehouse into Amazon ES in the logging account.

C. Configure CloudTrail and VPC Flow Logs to send data to a separate Amazon S3 bucket in each AWS account. Create an AWS Lambda function triggered by S3 events to copy the data to a centralized logging bucket. Create another Lambda function to load data from the S3 bucket to Amazon ES in the logging account.

D. Configure CloudTrail and VPC Flow Logs to send data to a log group in Amazon CloudWatch Logs in each AWS account. Create AWS Lambda functions in each AWS accounts to subscribe to the log groups and stream the data to an Amazon S3 bucket in the logging account. Create another Lambda function to load data from the S3 bucket to Amazon ES in the logging account.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>


## Prob. 424 ⭕❌
---

솔루션 설계자는 기업의 Amazon EC2 인스턴스 및 Amazon EBS(Amazon Elastic Block Store) 볼륨을 평가하여 기업이 리소스를 얼마나 효과적으로 사용하고 있는지 확인해야 합니다. 조직은 수많은 대용량 메모리 Amazon EC2 인스턴스를 사용하여 액티브/패시브 설정에서 데이터베이스 클러스터를 호스팅합니다. 조직은 데이터베이스에 액세스하는 앱에서 이러한 EC2 인스턴스를 사용하는 방식에 대한 패턴을 탐지하지 못했습니다.
솔루션 설계자는 환경을 분석하고 결과에 따라 적절한 조치를 취해야 합니다.

다음 중 비용 효율성 측면에서 이러한 기준에 가장 적합한 옵션은 무엇입니까?

A. AWS Systems Manager OpsCenter를 사용하여 대시보드를 생성합니다. EC2 인스턴스 및 해당 EBS 볼륨과 연결된 Amazon CloudWatch 메트릭에 대한 시각화를 구성합니다. 대시보드를 정기적으로 검토하고 사용 패턴을 식별합니다. 메트릭의 피크를 기준으로 EC2 인스턴스의 크기를 조정합니다.

B. Amazon CloudWatch에서 EC2 인스턴스와 해당 EBS 볼륨에 대한 상세 모니터링을 설정합니다. 메트릭을 기반으로 하는 대시보드를 만들고 검토합니다. 사용 패턴을 식별합니다. 메트릭의 피크를 기준으로 EC2 인스턴스의 크기를 조정합니다.

C. 각 EC2 인스턴스에 Amazon CloudWatch 에이전트를 설치합니다. AWS Compute Optimizer를 켜고 12시간 이상 실행되도록 합니다. Compute Optimizer의 권장 사항을 검토하고 지시에 따라 EC2 인스턴스의 크기를 조정합니다.

D. AWS 엔터프라이즈 지원 플랜에 가입합니다. AWS Trusted Advisor를 설정합니다. 12시간 기다리세요. Trusted Advisor의 권장 사항을 검토하고 지시에 따라 EC2 인스턴스의 크기를 조정합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Create a dashboard by using AWS Systems Manager OpsCenter. Configure visualizations for Amazon CloudWatch metrics that are associated with the EC2 instances and their EBS volumes. Review the dashboard periodically, and identify usage patterns. Rightsize the EC2 instances based on the peaks in the metrics.

B. Turn on Amazon CloudWatch detailed monitoring for the EC2 instances and their EBS volumes. Create and review a dashboard that is based on the metrics. Identify usage patterns. Rightsize the EC2 instances based on the peaks in the metrics.

C. Install the Amazon CloudWatch agent on each of the EC2 instances. Turn on AWS Compute Optimizer, and let it run for at least 12 hours. Review the recommendations from Compute Optimizer, and rightsize the EC2 instances as directed.

D. Sign up for the AWS Enterprise Support plan. Turn on AWS Trusted Advisor. Wait 12 hours. Review the recommendations from Trusted Advisor, and rightsize the EC2 instances as directed.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>


## Prob. 425 ⭕❌
---

사내에서 기업은 대용량 미디어 공유 프로그램을 운영합니다. 현재 수백만 개의 비디오 클립을 포함하여 400테라바이트 이상의 데이터를 저장합니다. 조직은 애플리케이션의 안정성을 높이고 비용을 절감하기 위해 이 애플리케이션을 AWS로 이전하고 있습니다.
Solutions Architecture 팀은 필름을 Amazon S3 버킷에 저장하고 Amazon CloudFront를 사용하는 고객에게 배포할 계획입니다. 조직은 최소 다운타임으로 10일 이내에 이 애플리케이션을 AWS로 전환해야 합니다. 현재 이 회사는 인터넷에 1Gbps로 연결되어 있으며 사용 가능한 용량의 30%를 차지하고 있습니다.

다음 중 조직이 모든 요구사항을 준수하면서 워크로드를 AWS로 전환할 수 있는 옵션은 무엇입니까?

A. Amazon S3 클라이언트에서 다중 부분 업로드를 사용하여 인터넷을 통해 데이터를 Amazon S3 버킷에 병렬 업로드합니다. 조절 기능을 사용하여 Amazon S3 클라이언트가 사용 가능한 인터넷 용량의 30% 이상을 사용하지 않도록 합니다.

B. 1PB 용량의 AWS Snowmobile을 데이터 센터에 전달하도록 요청합니다. 데이터를 Snowmobile에 로드한 후 다시 전송하여 AWS가 해당 데이터를 Amazon S3 버킷에 다운로드하도록 합니다. 마이그레이션이 실행 중인 동안 생성된 새 데이터를 동기화합니다.

C. Amazon S3 클라이언트를 사용하여 인터넷을 통해 데이터 센터의 데이터를 Amazon S3 버킷으로 전송합니다. 조절 기능을 사용하여 Amazon S3 클라이언트가 사용 가능한 인터넷 용량의 30% 이상을 사용하지 않도록 합니다.

D. 여러 AWS Snowball 장치를 데이터 센터에 전달하도록 요청합니다. 데이터를 이러한 장치에 동시에 로드하고 다시 보냅니다. AWS가 해당 데이터를 Amazon S3 버킷에 다운로드하도록 합니다. 마이그레이션이 실행 중인 동안 생성된 새 데이터를 동기화합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Use a multi-part upload in Amazon S3 client to parallel-upload the data to the Amazon S3 bucket over the Internet. Use the throttling feature to ensure that the Amazon S3 client does not use more than 30 percent of available Internet capacity.

B. Request an AWS Snowmobile with 1 PB capacity to be delivered to the data center. Load the data into Snowmobile and send it back to have AWS download that data to the Amazon S3 bucket. Sync the new data that was generated while migration was in flight.

C. Use an Amazon S3 client to transfer data from the data center to the Amazon S3 bucket over the Internet. Use the throttling feature to ensure the Amazon S3 client does not use more than 30 percent of available Internet capacity.

D. Request multiple AWS Snowball devices to be delivered to the data center. Load the data concurrently into these devices and send it back. Have AWS download that data to the Amazon S3 bucket. Sync the new data that was generated while migration was in flight.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>


## Prob. 426 ⭕❌
---

AWS에서 기업은 접근성이 높은 새로운 웹 애플리케이션을 개발하고 있습니다. 애플리케이션은 AWS 애플리케이션 서버와 사내에 저장된 백엔드 REST API 간에 지속적이고 신뢰할 수 있는 통신이 필요합니다. AWS와 사내 간의 백엔드 연결은 AWS Direct Connect 연결을 사용하여 개인 가상 인터페이스를 통해 처리됩니다. Amazon Route 53은 백엔드 REST API의 IP 주소를 확인하기 위해 애플리케이션의 개인 DNS 레코드를 처리하는 데 사용됩니다.

백엔드 API에 대한 보안 연결을 설정할 가능성이 가장 높은 아키텍처는 무엇입니까?

A. 백엔드 REST API에 대해 최소 두 개의 백엔드 엔드포인트를 구현하고 Route 53 상태 검사를 사용하여 각 백엔드 엔드포인트의 가용성을 모니터링하고 DNS 레벨 페일오버를 수행합니다.

B. 다른 네트워크 통신사의 두 번째 Direct Connect 연결을 설치하고 첫 번째 Direct Connect 연결과 동일한 가상 개인 게이트웨이에 연결합니다.

C. 동일한 네트워크 통신 사업자의 동일한 Direct Connect 연결에 대해 두 번째 교차 연결을 설치하고 두 연결을 모두 동일한 전용 가상 인터페이스의 동일한 LAG(링크 집계 그룹)에 가입합니다.

D. 내부 데이터 센터에서 AWS로 공용 인터넷을 통해 라우팅된 IPSec VPN 연결을 생성하여 Direct Connect 연결과 동일한 가상 개인 게이트웨이에 연결합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Implement at least two backend endpoints for the backend REST API, and use Route 53 health checks to monitor the availability of each backend endpoint and perform DNS-level failover.

B. Install a second Direct Connect connection from a different network carrier and attach it to the same virtual private gateway as the first Direct Connect connection.

C. Install a second cross connect for the same Direct Connect connection from the same network carrier, and join both connections to the same link aggregation group (LAG) on the same private virtual interface.

D. Create an IPSec VPN connection routed over the public internet from the on-premises data center to AWS and attach it to the same virtual private gateway as the Direct Connect connection.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>


## Prob. 427 ⭕❌
---

기업은 Amazon CloudFront 배포를 통해 애플리케이션 로드 밸런서 뒤에서 작동하는 웹 애플리케이션의 정적 및 동적 콘텐츠를 모두 배포하고 있습니다. 동적 콘텐츠의 경우 웹 응용 프로그램은 사용자 권한 부여 및 세션 모니터링이 필요합니다. CloudFront 배포는 HTTP 화이트리스트 헤더 Authorization, Host 및 User-Agent와 세션 쿠키를 오리진으로 전달하는 단일 캐시 동작으로 설정됩니다. 다른 모든 캐시 동작 매개 변수는 그대로 유지됩니다.
유효한 ACM 인증서가 해당 CNAME과 함께 배포 설정을 통해 CloudFront 배포에 배포됩니다. 또한 ACM 인증서가 애플리케이션 로드 밸런서의 HTTPS 수신기에 적용됩니다. CloudFront의 오리진 프로토콜 정책이 HTTPS만 사용하도록 구성되었습니다. 캐시 통계 보고서에 따르면 이 배포는 누락률이 매우 높습니다.

CloudFront와 애플리케이션 로드 밸런서 간의 SSL/TLS 핸드셰이크를 위태롭게 하지 않으면서 이 배포의 캐시 적중률을 높이기 위해 솔루션 설계자가 할 수 있는 일은 무엇입니까?

A. 정적 및 동적 콘텐츠에 대한 두 가지 캐시 동작을 만듭니다. 두 캐시 동작의 화이트리스트 헤더 섹션에서 사용자-에이전트 및 호스트 HTTP 헤더를 제거합니다. 정적 콘텐츠에 대해 구성된 캐시 동작에 대해 화이트리스트 쿠키 섹션에서 세션 쿠키를 제거하고 화이트리스트 헤더 섹션에서 권한 부여 HTTP 헤더를 제거합니다.

B. 캐시 동작의 화이트리스트 헤더 섹션에서 사용자-에이전트 및 권한 부여 HTTP 헤더를 제거합니다. 그런 다음 미리 지정된 쿠키를 인증에 사용하도록 캐시 동작을 업데이트합니다.

C. 화이트리스트 헤더 섹션에서 Host HTTP 헤더를 제거하고 기본 캐시 동작에 대해 화이트리스트 쿠키 섹션에서 세션 쿠키를 제거합니다. 자동 개체 압축을 사용하도록 설정하고 사용자 권한 부여에 Lambda@Edge 뷰어 요청 이벤트를 사용합니다.

D. 정적 및 동적 콘텐츠에 대한 두 가지 캐시 동작을 만듭니다. 두 캐시 동작의 화이트리스트 헤더 섹션에서 사용자 에이전트 HTTP 헤더를 제거합니다. 정적 콘텐츠에 대해 구성된 캐시 동작에 대해 화이트리스트 쿠키 섹션에서 세션 쿠키를 제거하고 화이트리스트 헤더 섹션에서 권한 부여 HTTP 헤더를 제거합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Create two cache behaviors for static and dynamic content. Remove the User-Agent and Host HTTP headers from the whitelist headers section on both of the cache behaviors. Remove the session cookie from the whitelist cookies section and the Authorization HTTP header from the whitelist headers section for cache behavior configured for static content.

B. Remove the User-Agent and Authorization HTTP headers from the whitelist headers section of the cache behavior. Then update the cache behavior to use presigned cookies for authorization.

C. Remove the Host HTTP header from the whitelist headers section and remove the session cookie from the whitelist cookies section for the default cache behavior. Enable automatic object compression and use Lambda@Edge viewer request events for user authorization.

D. Create two cache behaviors for static and dynamic content. Remove the User-Agent HTTP header from the whitelist headers section on both of the cache behaviors. Remove the session cookie from the whitelist cookies section and the Authorization HTTP header from the whitelist headers section for cache behavior configured for static content.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>

## Prob. 428 ⭕❌
---

한 온라인 소매업체는 사내 데이터 센터의 단일 서버에서 상태 저장 웹 애플리케이션과 MySQL 데이터베이스를 실행합니다. 회사는 추가적인 마케팅 캠페인 및 판촉 활동을 통해 소비자 기반을 확대하고자 합니다. 이 회사는 아키텍처의 안정성을 높이기 위해 준비 과정에서 애플리케이션과 데이터베이스를 AWS로 전환할 계획입니다.

가장 신뢰할 수 있는 옵션은 무엇입니까?

A. 데이터베이스를 Amazon RDS MySQL Multi-AZDB 인스턴스로 마이그레이션합니다. Amazon Neptune의 Application Load Balancer Store 세션 뒤에 있는 Amazon EC2 인스턴스의 자동 스케일링 그룹에 애플리케이션을 배포합니다.

B. 데이터베이스를 Amazon Aurora MySQL로 마이그레이션합니다. 애플리케이션 로드 밸런서 뒤에 있는 Amazon EC2 인스턴스의 자동 확장 그룹에 애플리케이션을 배포합니다. 세션을 Amazon ElastiCache for Redis 복제 그룹에 저장합니다.

C. 데이터베이스를 Amazon DocumentDB로 마이그레이션합니다(MongoDB 호환). 네트워크 로드 밸런서 뒤에 있는 Amazon EC2 인스턴스의 자동 확장 그룹에 애플리케이션을 배포합니다. 아마존 키네시스 데이터 파이어호스에 세션을 저장합니다.

D. 데이터베이스를 Amazon RDS MariaDB Multi-AZDB 인스턴스로 마이그레이션합니다. 애플리케이션 로드 밸런서 뒤에 있는 Amazon EC2 인스턴스의 자동 확장 그룹에 애플리케이션을 배포합니다. Memcached용 Amazon ElastiCache에 세션을 저장합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Migrate the database to an Amazon RDS MySQL Multi-AZ DB instance. Deploy the application in an Auto Scaling group on Amazon EC2 instances behind an Application Load Balancer Store sessions in Amazon Neptune.

B. Migrate the database to Amazon Aurora MySQL. Deploy the application in an Auto Scaling group on Amazon EC2 instances behind an Application Load Balancer. Store sessions in an Amazon ElastiCache for Redis replication group.

C. Migrate the database to Amazon DocumentDB (with MongoDB compatibility). Deploy the application in an Auto Scaling group on Amazon EC2 instances behind a Network Load Balancer. Store sessions in Amazon Kinesis Data Firehose.

D. Migrate the database to an Amazon RDS MariaDB Multi-AZ DB instance. Deploy the application in an Auto Scaling group on Amazon EC2 instances behind an Application Load Balancer. Store sessions in Amazon ElastiCache for Memcached.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>

## Prob. 429 ⭕❌
---

사용자가 IP 10.10.10.1/32에서 발송되지 않은 요청을 거부하도록 IAM 정책을 구성했습니다. 다른 규정은 모든 요청은 오후 5시에서 7시 사이에 이루어져야 한다는 것입니다.

사용자가 IP 55.109.10.12/32에서 액세스를 요청하면 오후 6시에 어떻게 됩니까?

A. 액세스가 거부됩니다.

B. 시간 또는 IP를 기준으로 정책을 설정할 수 없습니다.

C. IAM이 정책 충돌에 대해 오류를 발생시킵니다.

D. 액세스를 허용합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. It will deny access

B. It is not possible to set a policy based on the time or IP

C. IAM will throw an error for policy conflict

D. It will allow access
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>


## Prob. 430 ⭕❌
---

비즈니스는 애플리케이션 로드 밸런서 뒤에 있는 자동 확장 그룹의 여러 Amazon EC2 인스턴스에 분산되어 있는 애플리케이션을 운영합니다. 모든 응용 프로그램 액세스 시도는 보안 팀이 검사할 수 있도록 해야 합니다. 클라이언트의 IP 주소, 연결 종류 및 사용자 에이전트가 모두 제공되어야 합니다.

어떤 솔루션이 이러한 기준을 충족합니까?

A. EC2 상세 모니터링을 사용하도록 설정하고 네트워크 로그를 포함합니다. 모든 로그를 Amazon Kinesis Data Firehose를 통해 보안 팀이 분석에 사용하는 Amazon ES(Elastic Search Service) 클러스터로 보냅니다.

B. 모든 EC2 인스턴스 네트워크 인터페이스에 대해 VPC 흐름 로그를 사용하도록 설정합니다. VPC 흐름 로그를 Amazon S3 버킷에 게시합니다. 보안 팀이 Amazon Athena를 사용하여 로그를 쿼리하고 분석하도록 합니다.

C. 애플리케이션 로드 밸런서에 대한 액세스 로그를 사용하도록 설정하고 로그를 Amazon S3 버킷에 게시합니다. 보안 팀이 Amazon Athena를 사용하여 로그를 쿼리하고 분석하도록 합니다.

D. 트래픽 미러링을 사용하도록 설정하고 모든 EC2 인스턴스 네트워크 인터페이스를 소스로 지정합니다. 보안팀이 분석에 사용하는 Amazon Elastic Search Service(Amazon ES) 클러스터로 모든 트래픽 정보를 Amazon Kinesis Data Firehose를 통해 전송합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A. Enable EC2 detailed monitoring, and include network logs. Send all logs through Amazon Kinesis Data Firehose to an Amazon Elasticsearch Service (Amazon ES) cluster that the security team uses for analysis.

B. Enable VPC Flow Logs for all EC2 instance network interfaces. Publish VPC Flow Logs to an Amazon S3 bucket. Have the security team use Amazon Athena to query and analyze the logs.

C. Enable access logs for the Application Load Balancer, and publish the logs to an Amazon S3 bucket. Have the security team use Amazon Athena to query and analyze the logs.

D. Enable Traffic Mirroring and specify all EC2 instance network interfaces as the source. Send all traffic information through Amazon Kinesis Data Firehose to an Amazon Elasticsearch Service (Amazon ES) cluster that the security team uses for analysis.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : 

해설 : 


1차 시도 :  <br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional/view/43/)

