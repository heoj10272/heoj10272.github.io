---
layout: post
title: "[AWS] SAP-C02 ExamTopics 1~10"
subtitle: AWS
date: '2023-03-14 23:00:00 +0900'
category: study
tags: aws sap-c02
image:
  path: /assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/logo.png
---

SAP-C02 기출 1~10번 문제를 풀어보자.<br>
1차 5/10<br>

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>


## Prob. 1 ⭕⭕⭕
---

기업은 하이브리드 DNS 솔루션을 설계해야 합니다. 이 솔루션은 VPC에 저장된 리소스에 대해 cloud.example.com 도메인에 대해 Amazon Route 53 프라이빗 호스팅 영역을 사용합니다.<br>
회사의 DNS 확인 요구 사항은 다음과 같습니다:<br>
온프레미스 시스템은 cloud.example.com를 해결하고 연결할 수 있어야 합니다.<br>
모든 VPC가 cloud.example.com을 해결할 수 있어야 합니다.<br>
사내 회사 네트워크와 AWS Transit Gateway 간에 AWS Direct Connect 연결이 이미 있습니다.<br>
최고의 성능으로 이러한 요구사항을 충족하려면 어떤 아키텍처를 사용해야 합니까?

A. 프라이빗 호스팅 영역을 모든 VPC에 연결합니다. 공유 서비스 VPC에 Route 53 인바운드 해결사를 만듭니다. 모든 VPC를 Transit Gateway에 연결하고 인바운드 해결사를 가리키는 cloud.example.com의 사내 DNS 서버에 전달 규칙을 생성합니다.

B. 프라이빗 호스트 영역을 모든 VPC에 연결합니다. 공유 서비스 VPC에 Amazon EC2 조건부 전달자를 배포합니다. 모든 VPC를 Transit Gateway에 연결하고 조건부 전달자를 가리키는 cloud.example.com의 사내 DNS 서버에 전달 규칙을 생성합니다.

C. 프라이빗 호스트 영역을 공유 서비스 VPC에 연결합니다. 공유 서비스 VPC에서 Route 53 아웃바운드 해결사를 생성합니다. 모든 VPC를 Transit Gateway에 연결하고 아웃바운드 해결사를 가리키는 cloud.example.com의 사내 DNS 서버에 전달 규칙을 생성합니다.

D. 프라이빗 호스트 영역을 공유 서비스 VPC에 연결합니다. 공유 서비스 VPC에 Route 53 인바운드 해결사를 만듭니다. 공유 서비스 VPC를 Transit Gateway에 연결하고 인바운드 해결사를 가리키는 cloud.example.com의 온프레미스 DNS 서버에 전달 규칙을 생성합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company needs to architect a hybrid DNS solution. This solution will use an Amazon Route 53 private hosted zone for the domain cloud.example.com for the resources stored within VPCs.<br>
The company has the following DNS resolution requirements:<br>
On-premises systems should be able to resolve and connect to cloud.example.com.<br>
All VPCs should be able to resolve cloud.example.com.<br>
There is already an AWS Direct Connect connection between the on-premises corporate network and AWS Transit Gateway.<br>
Which architecture should the company use to meet these requirements with the HIGHEST performance?

A. Associate the private hosted zone to all the VPCs. Create a Route 53 inbound resolver in the shared services VPC. Attach all VPCs to the transit gateway and create forwarding rules in the on-premises DNS server for cloud.example.com that point to the inbound resolver.

B. Associate the private hosted zone to all the VPCs. Deploy an Amazon EC2 conditional forwarder in the shared services VPC. Attach all VPCs to the transit gateway and create forwarding rules in the on-premises DNS server for cloud.example.com that point to the conditional forwarder.

C. Associate the private hosted zone to the shared services VPC. Create a Route 53 outbound resolver in the shared services VPC. Attach all VPCs to the transit gateway and create forwarding rules in the on-premises DNS server for cloud.example.com that point to the outbound resolver.

D. Associate the private hosted zone to the shared services VPC. Create a Route 53 inbound resolver in the shared services VPC. Attach the shared services VPC to the transit gateway and create forwarding rules in the on-premises DNS server for cloud.example.com that point to the inbound resolver.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

A : 정답

B : `EC2 conditional fowarder`는 최고의 성능을 만족시키지 못한다.

C : 모든 VPC가 프라이빗 호스트 영역에 연결되어야 하므로 틀렸다.

D : 모든 VPC가 프라이빗 호스트 영역에 연결되어야 하므로 틀렸다.

1차 시도 : A <br>
2차 시도 : A <br>
3차 시도 : A <br>
</div>
</details>

<br>

## Prob. 2 ❌⭕⭕
---
A사는 REST 기반 API를 통해 여러 고객에게 날씨 데이터를 제공하고 있습니다. 이 API는 Amazon API Gateway에서 호스팅하며 각 API 작업에 대해 서로 다른 AWS 람다 기능과 통합됩니다. 이 회사는 DNS에 Amazon Route 53을 사용하고 weather.example.com의 리소스 레코드를 만들었습니다. 이 회사는 API에 대한 데이터를 Amazon DynamoDB 테이블에 저장합니다. 이 회사는 API가 다른 AWS 리전으로 페일오버할 수 있는 솔루션이 필요합니다.<br>
이러한 요구사항을 충족하는 솔루션은 무엇입니까?

A. 새 리전에 새 람다 기능 세트를 배포합니다. 두 리전의 람다 함수가 있는 에지에 최적화된 API 끝점을 대상으로 사용하도록 API Gateway API를 업데이트합니다. DynamoDB 테이블을 글로벌 테이블로 변환합니다.

B. 새 API Gateway API 및 람다 기능을 다른 지역에 배포합니다. Route 53 DNS 레코드를 다중값 응답으로 변경합니다. 두 API Gateway API를 모두 응답에 추가합니다. 대상 상태 모니터링을 사용합니다. DynamoDB 테이블을 글로벌 테이블로 변환합니다.

C. 새 API Gateway API 및 람다 기능을 다른 지역에 배포합니다. Route 53 DNS 레코드를 페일오버 레코드로 변경합니다. 대상 상태 모니터링을 사용합니다. DynamoDB 테이블을 글로벌 테이블로 변환합니다.

D. 새 영역에 새 API Gateway API를 배포합니다. 람다 기능을 전역 기능으로 변경합니다. Route 53 DNS 레코드를 다중값 응답으로 변경합니다. 두 API Gateway API를 모두 응답에 추가합니다. 대상 상태 모니터링을 사용합니다. DynamoDB 테이블을 글로벌 테이블로 변환합니다.

<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company is providing weather data over a REST-based API to several customers. The API is hosted by Amazon API Gateway and is integrated with different AWS Lambda functions for each API operation. The company uses Amazon Route 53 for DNS and has created a resource record of weather.example.com. The company stores data for the API in Amazon DynamoDB tables. The company needs a solution that will give the API the ability to fail over to a different AWS Region.<br>
Which solution will meet these requirements?

A. Deploy a new set of Lambda functions in a new Region. Update the API Gateway API to use an edge-optimized API endpoint with Lambda functions from both Regions as targets. Convert the DynamoDB tables to global tables.

B. Deploy a new API Gateway API and Lambda functions in another Region. Change the Route 53 DNS record to a multivalue answer. Add both API Gateway APIs to the answer. Enable target health monitoring. Convert the DynamoDB tables to global tables.

C. Deploy a new API Gateway API and Lambda functions in another Region. Change the Route 53 DNS record to a failover record. Enable target health monitoring. Convert the DynamoDB tables to global tables.

D. Deploy a new API Gateway API in a new Region. Change the Lambda functions to global functions. Change the Route 53 DNS record to a multivalue answer. Add both API Gateway APIs to the answer. Enable target health monitoring. Convert the DynamoDB tables to global tables.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

This solution involves deploying a new API Gateway API and Lambda functions in another region. <br>
The company should also convert the DynamoDB tables to global tables to enable cross-region replication of the data. <br>
Then, the company should change the Route 53 DNS record to a failover record and enable target health monitoring to automatically route traffic to the new region in the event of a failure or outage in the primary region.

1차 시도 : B <br>
2차 시도 : C <br>
3차 시도 : C <br>
</div>
</details>

<br>


## Prob. 3 ❓⭕⭕
---
A사는 운영이라는 단일 OU와 함께 AWS 조직을 사용하여 여러 계정을 관리합니다. 모든 계정은 운영 OU의 구성원입니다. 관리자는 조직 루트에서 거부 목록 SCP를 사용하여 제한된 서비스에 대한 액세스를 관리합니다.<br>
그 회사는 최근에 새로운 사업부를 인수했고 새로운 사업부의 기존 AWS 계정을 조직에 초대했습니다. 새 사업부의 관리자는 회사 정책에 맞게 기존 AWS Config 규칙을 업데이트할 수 없다는 것을 알게 되었습니다.<br>
관리자가 추가적인 장기 유지보수 없이 변경을 수행하고 현재 정책을 계속 적용할 수 있는 옵션은 무엇입니까?

A. AWS Config에 대한 액세스를 제한하는 조직의 루트 SCP를 제거합니다. 회사의 표준 AWS 구성 규칙에 대한 AWS 서비스 카탈로그 제품을 생성하고 새 계정을 포함하여 조직 전체에 배포합니다.

B. 새 계정에 대해 Onboarding이라는 임시 OU를 생성합니다. SCP를 Onboarding OU에 적용하여 AWS 구성 작업을 허용합니다. AWS 구성 조정이 완료되면 새 계정을 운영 OU로 이동합니다.

C. 조직의 루트 SCP를 거부 목록 SCP에서 변환하여 목록 SCP가 필요한 서비스만 허용하도록 합니다. 새 계정의 주체에 대해서만 AWS 구성 작업을 허용하는 SCP를 조직의 루트에 임시로 적용합니다.

D. 새 계정에 대해 Onboarding이라는 임시 OU를 생성합니다. SCP를 Onboarding OU에 적용하여 AWS 구성 작업을 허용합니다. 조직의 루트 SCP를 운영 OU로 이동합니다. AWS 구성 조정이 완료되면 새 계정을 운영 OU로 이동합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company uses AWS Organizations with a single OU named Production to manage multiple accounts. All accounts are members of the Production OU. Administrators use deny list SCPs in the root of the organization to manage access to restricted services.<br>
The company recently acquired a new business unit and invited the new unit’s existing AWS account to the organization. Once onboarded, the administrators of the new business unit discovered that they are not able to update existing AWS Config rules to meet the company’s policies.<br>
Which option will allow administrators to make changes and continue to enforce the current policies without introducing additional long-term maintenance?

A. Remove the organization’s root SCPs that limit access to AWS Config. Create AWS Service Catalog products for the company’s standard AWS Config rules and deploy them throughout the organization, including the new account.

B. Create a temporary OU named Onboarding for the new account. Apply an SCP to the Onboarding OU to allow AWS Config actions. Move the new account to the Production OU when adjustments to AWS Config are complete.

C. Convert the organization’s root SCPs from deny list SCPs to allow list SCPs to allow the required services only. Temporarily apply an SCP to the organization’s root that allows AWS Config actions for principals only in the new account.

D. Create a temporary OU named Onboarding for the new account. Apply an SCP to the Onboarding OU to allow AWS Config actions. Move the organization’s root SCP to the Production OU. Move the new account to the Production OU when adjustments to AWS Config are complete.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : D

해설 : 

An SCP at a lower level can't add a permission after it is blocked by an SCP at a higher level. SCPs can only filter; they never add permissions.<br>
SO you need to create a new OU for the new account assign an SCP, and move the root SCP to Production OU. Then move the new account to production OU when AWS config is done.

Not A: too much overhead and maintenance.<br>
Not B: SCP at Root will still deny Config to the temporary OU.<br>
Not C: Too much overhead to create allow list.

Please note Question Constraint: Which option will allow administrators to make changes and continue to enforce the current policies without introducing additional long-term maintenance?<br>
Strategies for using SCPs<br>
You can configure the service control policies (SCPs) in your organization to work as either of the following:<br>
A deny list – actions are allowed by default, and you specify what services and actions are prohibited<br>
An allow list – actions are prohibited by default, and you specify what services and actions are allowed.

즉 SCP는 필터의 역할, 즉 제한하거나 열어주거나만 할 수 있지 상위 레벨에서의 접근 제한에 대한 허가는 할 수 없다.<br>
문제에서는 새 유닛(비지니스)가 들어왔지만, 해당 유닛의 관리자는 AWS Config를 업데이트 할 수 없는 상황이다.<br>
A의 경우는 기존에 존재하는 SCP를 제거하는 것이기 때문에, 너무 많은 수고가 들게 된다.<br>
B의 경우는 아직 루트 SCP가 건재하기 때문에, 새로운 onboarding OU에 SCP로 허가하더라도 막힐 것이다.<br>
C의 경우는 deny list로 사용하던걸 allow list로 바꾸면 하나하나 다시 지정해줘야 하므로 너무 많은 수고가 들게 된다.<br>
D의 경우, B와 비슷하지만 루트 SCP가 Production OU로 넘어가기 때문에 onboarding OU로의 효력을 잃게 되므로, onboarding OU는 AWS Config의 업데이트가 가능하게 된다.


1차 시도 : 모름 <br>
2차 시도 : D <br>
3차 시도 : D <br>
</div>
</details>

<br>

## Prob. 4 ⭕⭕⭕
---
A사는 사내 데이터 센터에서 2계층 웹 기반 애플리케이션을 실행하고 있습니다. 응용 프로그램 계층은 상태 저장 응용 프로그램을 실행하는 단일 서버로 구성됩니다. 애플리케이션이 Postgre에 연결됩니다별도의 서버에서 실행 중인 SQL 데이터베이스입니다. 애플리케이션의 사용자 기반이 크게 증가할 것으로 예상되어 회사는 애플리케이션과 데이터베이스를 AWS로 마이그레이션하고 있습니다. 솔루션은 Amazon Aurora Postgre를 사용합니다SQL, Amazon EC2 자동 스케일링 및 Elastic Load Balancing이 있습니다.<br>
애플리케이션 및 데이터베이스 계층을 확장할 수 있는 일관된 사용자 환경을 제공하는 솔루션은 무엇입니까?

A. Aurora 복제본에 대해 Aurora 자동 스케일링을 활성화합니다. 최소 미결 요청 라우팅 알고리즘과 스틱 세션을 사용하도록 설정된 네트워크 로드 밸런서를 사용합니다.

B. Aurora 작성자에 대해 Aurora 자동 스케일링을 활성화합니다. 라운드 로빈 라우팅 알고리즘과 스틱 세션을 사용하도록 설정된 상태에서 애플리케이션 로드 밸런서를 사용합니다.

C. Aurora 복제본에 대해 Aurora 자동 스케일링을 사용합니다. 라운드 로빈 라우팅 및 스틱 세션을 사용하도록 설정된 상태에서 애플리케이션 로드 밸런서를 사용합니다.

D. Aurora 작성자에 대해 Aurora Scaling을 활성화합니다. 최소 미결 요청 라우팅 알고리즘과 스틱 세션을 사용하도록 설정된 네트워크 로드 밸런서를 사용합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company is running a two-tier web-based application in an on-premises data center. The application layer consists of a single server running a stateful application. The application connects to a PostgreSQL database running on a separate server. The application’s user base is expected to grow significantly, so the company is migrating the application and database to AWS. The solution will use Amazon Aurora PostgreSQL, Amazon EC2 Auto Scaling, and Elastic Load Balancing.<br>
Which solution will provide a consistent user experience that will allow the application and database tiers to scale?

A. Enable Aurora Auto Scaling for Aurora Replicas. Use a Network Load Balancer with the least outstanding requests routing algorithm and sticky sessions enabled.

B. Enable Aurora Auto Scaling for Aurora writers. Use an Application Load Balancer with the round robin routing algorithm and sticky sessions enabled.

C. Enable Aurora Auto Scaling for Aurora Replicas. Use an Application Load Balancer with the round robin routing and sticky sessions enabled.

D. Enable Aurora Scaling for Aurora writers. Use a Network Load Balancer with the least outstanding requests routing algorithm and sticky sessions enabled.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C

해설 : 

- Aurora writers is a distractor.
- Single master mode only has read replica - with Aurora replicas.
- Multi master mode, not in the options
- NLB does not support round robin and least outstanding algorithm

로드밸런싱 알고리즘에는 `Round Robin` 방식과 `Least Outstanding` 방식이 있다.<br>
라운드 로빈은 EC2 인스턴스에 요청을 순서대로 할당하는 방식이고, Least Outstanding은 라운드 로빈의 개선판 느낌으로 부하가 가장 적은 인스턴스에 요청을 할당한다.

1차 시도 : C <br>
2차 시도 : C <br>
3차 시도 : C <br>
</div>
</details>

<br>

## Prob. 5 ⭕❌⭕
---
회사는 사내에서 호스팅하는 응용프로그램에서 메타데이터를 수집하기 위해 서비스를 사용합니다. TV 및 인터넷 라디오와 같은 소비자 장치가 애플리케이션에 액세스합니다. 대부분의 오래된 장치는 특정 HTTP 헤더를 지원하지 않으며 이러한 헤더가 응답에 있으면 오류가 발생합니다. 회사는 지원되지 않는 헤더를 이전 장치로 전송된 응답에서 제거하도록 사내 로드 밸런서를 구성했습니다. 이 헤더는 사용자 에이전트 헤더로 식별됩니다.<br>
이 회사는 서비스를 AWS로 마이그레이션하고 서버리스 기술을 채택하며 이전 장치를 지원하는 기능을 유지하기를 원합니다. 이 회사는 이미 애플리케이션을 일련의 AWS 람다 기능으로 마이그레이션했습니다.<br>
이러한 요구사항을 충족하는 솔루션은 무엇입니까?

A. 메타데이터 서비스에 대한 Amazon CloudFront 배포를 생성합니다. ALB(애플리케이션 로드 밸런서)를 생성합니다. 요청을 ALB로 전달하도록 CloudFront 배포를 구성합니다. 각 요청 유형에 대해 올바른 람다 기능을 호출하도록 ALB를 구성합니다. CloudFront 함수를 생성하여 사용자-에이전트 헤더 값을 기준으로 문제가 있는 헤더를 제거합니다.

B. 메타데이터 서비스에 대한 Amazon API Gateway REST API를 생성합니다. 각 요청 유형에 대해 올바른 람다 함수를 호출하도록 API Gateway를 구성합니다. 사용자-에이전트 헤더 값을 기준으로 문제가 있는 헤더를 제거하도록 기본 게이트웨이 응답을 수정합니다.

C. 메타데이터 서비스에 대한 Amazon API Gateway HTTP API를 생성합니다. 각 요청 유형에 대해 올바른 람다 함수를 호출하도록 API Gateway를 구성합니다. 사용자 에이전트 값을 기준으로 문제가 있는 헤더를 제거하는 응답 매핑 템플릿을 만듭니다. 응답 데이터 매핑을 HTTP API와 연결합니다.

D. 메타데이터 서비스에 대한 Amazon CloudFront 배포를 생성합니다. ALB(애플리케이션 로드 밸런서)를 생성합니다. 요청을 ALB로 전달하도록 CloudFront 배포를 구성합니다. 각 요청 유형에 대해 올바른 람다 기능을 호출하도록 ALB를 구성합니다. User-Agent 헤더 값을 기반으로 뷰어 요청에 응답하여 문제가 있는 헤더를 제거하는 Lambda@Edge 함수를 만듭니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company uses a service to collect metadata from applications that the company hosts on premises. Consumer devices such as TVs and internet radios access the applications. Many older devices do not support certain HTTP headers and exhibit errors when these headers are present in responses. The company has configured an on-premises load balancer to remove the unsupported headers from responses sent to older devices, which the company identified by the User-Agent headers.<br>
The company wants to migrate the service to AWS, adopt serverless technologies, and retain the ability to support the older devices. The company has already migrated the applications into a set of AWS Lambda functions.<br>
Which solution will meet these requirements?

A. Create an Amazon CloudFront distribution for the metadata service. Create an Application Load Balancer (ALB). Configure the CloudFront distribution to forward requests to the ALB. Configure the ALB to invoke the correct Lambda function for each type of request. Create a CloudFront function to remove the problematic headers based on the value of the User-Agent header.

B. Create an Amazon API Gateway REST API for the metadata service. Configure API Gateway to invoke the correct Lambda function for each type of request. Modify the default gateway responses to remove the problematic headers based on the value of the User-Agent header.

C. Create an Amazon API Gateway HTTP API for the metadata service. Configure API Gateway to invoke the correct Lambda function for each type of request. Create a response mapping template to remove the problematic headers based on the value of the User-Agent. Associate the response data mapping with the HTTP API.

D. Create an Amazon CloudFront distribution for the metadata service. Create an Application Load Balancer (ALB). Configure the CloudFront distribution to forward requests to the ALB. Configure the ALB to invoke the correct Lambda function for each type of request. Create a Lambda@Edge function that will remove the problematic headers in response to viewer requests based on the value of the User-Agent header.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A

해설 : 

A, D 중 답에 대한 의견이 분분하나, CloudFront의 주된 기능으로서의 역할을 봤을 때 A가 더 적절해보인다.

1차 시도 : A <br>
2차 시도 : D <br>
3차 시도 : A <br>
</div>
</details>

<br>

## Prob. 6 ❌⭕⭕
---
소매업체는 비즈니스 파트너인 다른 회사에 일련의 데이터 파일을 제공해야 합니다. 이 파일들은 소매 회사에 속한 A 계정의 Amazon S3 버킷에 저장됩니다. 비즈니스 파트너 회사는 IAM 사용자 중 한 명인 User_DataProcessor가 자신의 AWS 계정(계정 B)에서 파일에 액세스하기를 원합니다.<br>
User_DataProcessor가 S3 버킷에 성공적으로 액세스할 수 있도록 하기 위해 기업이 취해야 할 단계의 조합은 무엇입니까? (두 가지를 선택하십시오.)

A. 계정 A에서 S3 버킷에 대한 CORS(교차 오리진 리소스 공유) 기능을 설정합니다.

B. 계정 A에서 S3 버킷 정책을 다음과 같이 설정하십시오:<br>
![1](/assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/1.png)

C. 계정 A에서 S3 버킷 정책을 다음과 같이 설정하십시오:<br>
![2](/assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/2.png)

D. 계정 B에서 User_DataProcessor의 사용 권한을 다음과 같이 설정하십시오:<br>
![3](/assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/3.png)

E. 계정 B에서 User_DataProcessor의 사용 권한을 다음과 같이 설정하십시오:<br>
![4](/assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/4.png)
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A retail company needs to provide a series of data files to another company, which is its business partner. These files are saved in an Amazon S3 bucket under Account A, which belongs to the retail company. The business partner company wants one of its IAM users, User_DataProcessor, to access the files from its own AWS account (Account B).<br>
Which combination of steps must the companies take so that User_DataProcessor can access the S3 bucket successfully? (Choose two.)

A. Turn on the cross-origin resource sharing (CORS) feature for the S3 bucket in Account A.

B. In Account A, set the S3 bucket policy to the following:<br>
![1_1](/assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/1.png)

C. In Account A, set the S3 bucket policy to the following:<br>
![2_1](/assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/2.png)

D. In Account B, set the permissions of User_DataProcessor to the following:<br>
![3_1](/assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/3.png)

E. In Account B, set the permissions of User_DataProcessor to the following:<br>
![4_1](/assets/img/study_AWS/2023-03-14-[AWS]_SAP-C02_ExamTopics_1~10/4.png)
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : C, D

해설 : 

열어주는 쪽에서 `principal`로 다른 계정이 접근 가능하도록 열어줘야 하고<br>
접근하는 쪽에서 접근할 `resource`, `action`, `effect` 를 설정해야 한다.

참고로, `CORS` 는 다른 도메인으로부터 웹 브라우저가 리소스에 접근하려 할 때 설정하는 것이다.

1차 시도 : C, E <br>
2차 시도 : C, D <br>
3차 시도 : C, D <br>
</div>
</details>

<br>

## Prob. 7 ❌❌
---
A사는 Amazon EC2 인스턴스에서 전통적인 웹 애플리케이션을 실행하고 있습니다. 회사는 응용 프로그램을 컨테이너에서 실행되는 마이크로 서비스로 리팩터링해야 합니다. 애플리케이션의 별도 버전은 프로덕션 환경과 테스트 환경의 두 가지로 구분됩니다. 응용 프로그램의 로드는 가변적이지만 최소 로드와 최대 로드가 알려져 있습니다. 솔루션 설계자는 운영 복잡성을 최소화하는 서버리스 아키텍처로 업데이트된 애플리케이션을 설계해야 합니다.<br>
이러한 요구사항을 가장 경제적으로 충족하는 솔루션은 무엇입니까?

A. 컨테이너 이미지를 AWS Lambda as functions에 업로드합니다. 예상 피크 부하를 처리하기 위해 관련 람다 함수에 대한 동시성 한계를 구성합니다. Amazon API Gateway 내에서 두 개의 개별 Lambda 통합을 구성합니다. 하나는 프로덕션용이고 다른 하나는 테스트용입니다.

B. 컨테이너 이미지를 Amazon Elastic Container Registry(Amazon ECR)에 업로드합니다. Fargate 시작 유형을 사용하여 두 개의 자동 확장 Amazon ECS(Elastic Container Service) 클러스터를 구성하여 예상 로드를 처리합니다. ECR 이미지에서 작업을 배포합니다. 트래픽을 ECS 클러스터로 유도하도록 두 개의 개별 애플리케이션 로드 밸런서를 구성합니다.

C. 컨테이너 이미지를 Amazon Elastic Container Registry(Amazon ECR)에 업로드합니다. Fargate 시작 유형을 사용하여 두 개의 자동 확장 Amazon EKS(Elastic Kubernetes Service) 클러스터를 구성하여 예상 로드를 처리합니다. ECR 이미지에서 작업을 배포합니다. 트래픽을 EKS 클러스터로 전달하도록 두 개의 개별 애플리케이션 로드 밸런서를 구성합니다.

D. 컨테이너 이미지를 AWS Elastic Beanstalk에 업로드합니다. Elastic Beanstalk에서 프로덕션 및 테스트를 위한 별도의 환경 및 배포를 생성합니다. 트래픽을 Elastic Beanstalk 배포로 유도하도록 두 개의 개별 애플리케이션 로드 밸런서를 구성합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company is running a traditional web application on Amazon EC2 instances. The company needs to refactor the application as microservices that run on containers. Separate versions of the application exist in two distinct environments: production and testing. Load for the application is variable, but the minimum load and the maximum load are known. A solutions architect needs to design the updated application with a serverless architecture that minimizes operational complexity.<br>
Which solution will meet these requirements MOST cost-effectively?

A. Upload the container images to AWS Lambda as functions. Configure a concurrency limit for the associated Lambda functions to handle the expected peak load. Configure two separate Lambda integrations within Amazon API Gateway: one for production and one for testing.

B. Upload the container images to Amazon Elastic Container Registry (Amazon ECR). Configure two auto scaled Amazon Elastic Container Service (Amazon ECS) clusters with the Fargate launch type to handle the expected load. Deploy tasks from the ECR images. Configure two separate Application Load Balancers to direct traffic to the ECS clusters.

C. Upload the container images to Amazon Elastic Container Registry (Amazon ECR). Configure two auto scaled Amazon Elastic Kubernetes Service (Amazon EKS) clusters with the Fargate launch type to handle the expected load. Deploy tasks from the ECR images. Configure two separate Application Load Balancers to direct traffic to the EKS clusters.

D. Upload the container images to AWS Elastic Beanstalk. In Elastic Beanstalk, create separate environments and deployments for production and testing. Configure two separate Application Load Balancers to direct traffic to the Elastic Beanstalk deployments.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

A와 B 왔다갔다 하는듯.

이 옵션은 ECS 클러스터에 대한 Fargate 시작 유형을 활용하여 서버리스 아키텍처를 사용해야 하는 요구 사항을 충족합니다. 이 유형을 사용하면 예상 부하에 따라 컨테이너를 자동으로 확장할 수 있습니다. 또한 각 환경에 대해 별도의 ECS 클러스터 및 애플리케이션 로드 밸런싱 장치를 구성하여 운영 및 테스트를 위한 별도의 배포를 허용합니다. 또한 이 옵션은 컨테이너 오케스트레이션 및 확장에 ECS 및 Fargate를 활용하여 운영 복잡성을 최소화합니다.

1차 시도 : C <br>
2차 시도 : A <br>
</div>
</details>

<br>

## Prob. 8 ⭕⭕
---
A사는 ALB(Application Load Balancer) 뒤에 있는 일련의 Amazon EC2 인스턴스에서 실행되는 다중 계층 웹 애플리케이션을 보유하고 있습니다. 인스턴스가 자동 스케일링 그룹에 있습니다. ALB 및 자동 스케일링 그룹은 백업 AWS 영역에서 복제됩니다. 자동 스케일링 그룹의 최소값과 최대값은 0으로 설정됩니다. Amazon RDS Multi-AZ DB 인스턴스는 애플리케이션의 데이터를 저장합니다. DB 인스턴스에 백업 영역에 읽기 복제본이 있습니다. 애플리케이션은 Amazon Route 53 레코드를 사용하여 최종 사용자에게 끝점을 제공합니다.<br>
이 회사는 애플리케이션에서 백업 영역으로 자동으로 페일오버할 수 있는 기능을 제공하여 RTO를 15분 이내로 줄여야 합니다. 이 회사는 액티브-액티브 전략을 위한 충분한 예산을 가지고 있지 않습니다.<br>
솔루션 설계자는 이러한 요구사항을 충족하기 위해 무엇을 권장해야 합니까?

A. 두 ALB 간의 트래픽을 로드 밸런싱하는 지연 시간 기반 라우팅 정책으로 응용 프로그램의 Route 53 레코드를 재구성합니다. 백업 영역에 AWS 람다 기능을 생성하여 읽기 복제본을 승격하고 자동 스케일링 그룹 값을 수정합니다. 기본 영역의 ALB에 대한 HTTP Code_Target_5XX_Count 메트릭을 기반으로 Amazon CloudWatch 경보를 생성합니다. Lambda 기능을 호출하도록 CloudWatch 알람을 구성합니다.

B. 백업 영역에서 AWS 람다 기능을 생성하여 읽기 복제본을 승격하고 자동 스케일링 그룹 값을 수정합니다. 웹 애플리케이션을 모니터링하고 상태 점검 상태가 비정상일 때 Amazon Simple Notification Service(Amazon SNS) 알림을 람다 기능으로 전송하는 상태 점검으로 Route 53을 구성합니다. 상태 점검 실패 시 백업 영역의 ALB로 트래픽을 라우팅하는 페일오버 정책으로 응용 프로그램의 Route 53 레코드를 업데이트합니다.

C. 백업 영역의 자동 스케일링 그룹이 기본 영역의 자동 스케일링 그룹과 동일한 값을 갖도록 구성합니다. 두 ALB 간의 트래픽을 로드 밸런싱하는 지연 시간 기반 라우팅 정책을 사용하여 응용 프로그램의 Route 53 레코드를 재구성합니다. 읽은 복제본을 제거합니다. 읽기 복제본을 독립 실행형 RDS DB 인스턴스로 바꿉니다. 스냅샷과 Amazon S3를 사용하여 RDS DB 인스턴스 간에 교차 영역 복제를 구성합니다.

D. AWS Global Accelerator에서 두 ALB를 동일한 가중치 대상으로 엔드포인트를 구성합니다. 백업 영역에 AWS 람다 기능을 생성하여 읽기 복제본을 승격하고 자동 스케일링 그룹 값을 수정합니다. 기본 영역의 ALB에 대한 HTTP Code_Target_5XX_Count 메트릭을 기반으로 Amazon CloudWatch 경보를 생성합니다. Lambda 기능을 호출하도록 CloudWatch 알람을 구성합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company has a multi-tier web application that runs on a fleet of Amazon EC2 instances behind an Application Load Balancer (ALB). The instances are in an Auto Scaling group. The ALB and the Auto Scaling group are replicated in a backup AWS Region. The minimum value and the maximum value for the Auto Scaling group are set to zero. An Amazon RDS Multi-AZ DB instance stores the application’s data. The DB instance has a read replica in the backup Region. The application presents an endpoint to end users by using an Amazon Route 53 record.<br>
The company needs to reduce its RTO to less than 15 minutes by giving the application the ability to automatically fail over to the backup Region. The company does not have a large enough budget for an active-active strategy.
What should a solutions architect recommend to meet these requirements?

A. Reconfigure the application’s Route 53 record with a latency-based routing policy that load balances traffic between the two ALBs. Create an AWS Lambda function in the backup Region to promote the read replica and modify the Auto Scaling group values. Create an Amazon CloudWatch alarm that is based on the HTTPCode_Target_5XX_Count metric for the ALB in the primary Region. Configure the CloudWatch alarm to invoke the Lambda function.

B. Create an AWS Lambda function in the backup Region to promote the read replica and modify the Auto Scaling group values. Configure Route 53 with a health check that monitors the web application and sends an Amazon Simple Notification Service (Amazon SNS) notification to the Lambda function when the health check status is unhealthy. Update the application’s Route 53 record with a failover policy that routes traffic to the ALB in the backup Region when a health check failure occurs.

C. Configure the Auto Scaling group in the backup Region to have the same values as the Auto Scaling group in the primary Region. Reconfigure the application’s Route 53 record with a latency-based routing policy that load balances traffic between the two ALBs. Remove the read replica. Replace the read replica with a standalone RDS DB instance. Configure Cross-Region Replication between the RDS DB instances by using snapshots and Amazon S3.

D. Configure an endpoint in AWS Global Accelerator with the two ALBs as equal weighted targets. Create an AWS Lambda function in the backup Region to promote the read replica and modify the Auto Scaling group values. Create an Amazon CloudWatch alarm that is based on the HTTPCode_Target_5XX_Count metric for the ALB in the primary Region. Configure the CloudWatch alarm to invoke the Lambda function.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : B

해설 : 

B는 RTO를 15분 이내로 줄이고 액티브-액티브 전략을 위한 큰 예산이 없다는 회사의 요구 사항을 충족하기 때문에 맞습니다.

이 솔루션에서는 백업 영역에 AWS 람다 기능을 생성하여 읽기 복제본을 승격하고 자동 스케일링 그룹 값을 수정합니다. Route 53은 웹 애플리케이션을 모니터링하고 상태 점검 상태가 비정상일 때 Amazon SNS 알림을 람다 기능으로 전송하는 상태 점검으로 구성됩니다. 또한 Route 53 레코드는 상태 점검 실패 시 백업 영역의 ALB로 트래픽을 라우팅하는 페일오버 정책으로 업데이트됩니다. 이렇게 하면 기본 영역이 중단되면 페일오버 정책이 트리거되고 트래픽이 백업 영역으로 이동되므로 복구 시간이 빠릅니다.

1차 시도 : B <br>
2차 시도 : B <br>
</div>
</details>

<br>

## Prob. 9 ⭕
---
한 회사에서 중요한 애플리케이션을 단일 Amazon EC2 인스턴스에 호스팅하고 있습니다. 애플리케이션은 메모리 내 데이터스토어에 Amazon ElastiCache for Redis 단일 노드 클러스터를 사용합니다. 애플리케이션은 관계형 데이터베이스에 Amazon RDS for Maria DB 인스턴스를 사용합니다. 애플리케이션이 작동하려면 인프라의 각 부분이 정상이고 활성 상태여야 합니다.<br>
솔루션 설계자는 최소한의 다운타임으로 인프라가 장애로부터 자동으로 복구될 수 있도록 애플리케이션 아키텍처를 개선해야 합니다.<br>
다음 중 이러한 요구 사항을 충족하는 단계의 조합은 무엇입니까? (세 개를 선택하십시오.)

A. Elastic Load Balancer를 사용하여 여러 EC2 인스턴스에 트래픽을 분산합니다. EC2 인스턴스가 최소 용량이 두 인스턴스인 자동 스케일링 그룹에 속하는지 확인합니다.

B. Elastic Load Balancer를 사용하여 여러 EC2 인스턴스에 트래픽을 분산합니다. EC2 인스턴스가 무제한 모드로 구성되어 있는지 확인합니다.

C. 동일한 가용성 영역에 읽기 복제본을 작성하도록 DB 인스턴스를 수정합니다. 읽기 복제본을 장애 시나리오의 기본 DB 인스턴스로 승격합니다.

D. DB 인스턴스를 수정하여 두 개의 가용성 영역에 걸쳐 확장되는 Multi-AZ 배포를 만듭니다.

E. Redis용 ElastiCache 클러스터에 대한 복제 그룹을 생성합니다. 인스턴스의 최소 용량이 두 개인 자동 스케일링 그룹을 사용하도록 클러스터를 구성합니다.

F. Redis용 ElastiCache 클러스터에 대한 복제 그룹을 만듭니다. 클러스터에서 Multi-AZ를 사용하도록 설정합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A company is hosting a critical application on a single Amazon EC2 instance. The application uses an Amazon ElastiCache for Redis single-node cluster for an in-memory data store. The application uses an Amazon RDS for MariaDB DB instance for a relational database. For the application to function, each piece of the infrastructure must be healthy and must be in an active state.<br>
A solutions architect needs to improve the application's architecture so that the infrastructure can automatically recover from failure with the least possible downtime.<br>
Which combination of steps will meet these requirements? (Choose three.)

A. Use an Elastic Load Balancer to distribute traffic across multiple EC2 instances. Ensure that the EC2 instances are part of an Auto Scaling group that has a minimum capacity of two instances.

B. Use an Elastic Load Balancer to distribute traffic across multiple EC2 instances. Ensure that the EC2 instances are configured in unlimited mode.

C. Modify the DB instance to create a read replica in the same Availability Zone. Promote the read replica to be the primary DB instance in failure scenarios.

D. Modify the DB instance to create a Multi-AZ deployment that extends across two Availability Zones.

E. Create a replication group for the ElastiCache for Redis cluster. Configure the cluster to use an Auto Scaling group that has a minimum capacity of two instances.

F. Create a replication group for the ElastiCache for Redis cluster. Enable Multi-AZ on the cluster.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, D, F

해설 : 

A. ELB(Elastic Load Balancer)를 사용하여 여러 EC2 인스턴스에 트래픽을 분산하면 인스턴스 중 하나를 사용할 수 없게 되는 경우에도 애플리케이션을 사용할 수 있습니다. 인스턴스를 최소 용량이 두 개인 자동 스케일링 그룹의 일부로 구성하면 트래픽을 처리할 정상적인 인스턴스가 항상 하나 이상 있는지 확인할 수 있습니다.

D. DB 인스턴스를 수정하여 두 개의 가용성 영역에 걸쳐 확장되는 Multi-AZ 배포를 작성하면 장애가 발생한 경우에도 데이터베이스를 사용할 수 있습니다. 장애가 발생하면 트래픽이 자동으로 보조 가용성 영역으로 이동하여 다운타임이 줄어듭니다.

F. Redis용 ElastiCache 클러스터에 대한 복제 그룹을 만들고 Multi-AZ를 활성화하면 장애가 발생한 경우에도 메모리 내 데이터 저장소를 사용할 수 있습니다. 이렇게 하면 트래픽이 자동으로 보조 가용성 영역으로 이동하여 다운타임을 줄일 수 있습니다.

1차 시도 : A, D, F <br>
</div>
</details>

<br>

## Prob. 10 ❌
---
한 소매 회사가 AWS에서 전자 상거래 애플리케이션을 운영하고 있습니다. 애플리케이션은 ALB(Application Load Balancer) 뒤에 있는 Amazon EC2 인스턴스에서 실행됩니다. 이 회사에서는 Amazon RDS DB 인스턴스를 데이터베이스 백엔드로 사용합니다. Amazon CloudFront는 ALB를 가리키는 하나의 오리진으로 구성됩니다. 정적 콘텐츠가 캐시됩니다. 아마존 53번 도로는 모든 공공 구역을 유치하는 데 사용됩니다.<br>
응용 프로그램을 업데이트한 후 ALB가 502 상태 코드(불량 게이트웨이) 오류를 반환하는 경우가 있습니다. 근본 원인은 ALB로 반환되는 잘못된 형식의 HTTP 헤더입니다. 솔루션 설계자가 오류가 발생한 직후 웹 페이지를 다시 로드하면 웹 페이지가 성공적으로 반환됩니다.
회사에서 문제를 해결하는 동안 솔루션 설계자는 방문자에게 표준 ALB 오류 페이지 대신 사용자 정의 오류 페이지를 제공해야 합니다.<br>
최소한의 운영 오버헤드로 이 요구사항을 충족하는 단계의 조합은 무엇입니까? (두 개를 선택하십시오.)

A. Amazon S3 버킷을 생성합니다. 정적 웹 페이지를 호스트하도록 S3 버킷을 구성합니다. 사용자 지정 오류 페이지를 Amazon S3에 업로드합니다.

B. ALB 상태가 응답 Target을 확인하는 경우 Amazon CloudWatch 경보를 생성하여 AWS Lambda 함수를 호출합니다.실패한 상태 검사가 0보다 큽니다. 공용으로 액세스할 수 있는 웹 서버를 가리키도록 ALB에서 전달 규칙을 수정하도록 람다 기능을 구성합니다.

C. 상태 점검을 추가하여 기존 Amazon Route 53 레코드를 수정합니다. 상태 검사가 실패할 경우 예비 대상을 구성합니다. 공개적으로 액세스할 수 있는 웹 페이지를 가리키도록 DNS 레코드를 수정합니다.

D. ALB 상태 점검 응답 Elb인 경우 Amazon CloudWatch 경보를 생성하여 AWS 람다 함수를 호출합니다.내부 오류가 0보다 큽니다. ALB에서 전달 규칙이 액세스 가능한 공용 웹 서버를 가리키도록 람다 기능을 구성합니다.

E. CloudFront 사용자 정의 오류 페이지를 구성하여 사용자 정의 오류 응답을 추가합니다. 공개적으로 액세스할 수 있는 웹 페이지를 가리키도록 DNS 레코드를 수정합니다.
<details>
<summary>원문 보기</summary>
<div markdown="1">
<br>
A retail company is operating its ecommerce application on AWS. The application runs on Amazon EC2 instances behind an Application Load Balancer (ALB). The company uses an Amazon RDS DB instance as the database backend. Amazon CloudFront is configured with one origin that points to the ALB. Static content is cached. Amazon Route 53 is used to host all public zones.<br>
After an update of the application, the ALB occasionally returns a 502 status code (Bad Gateway) error. The root cause is malformed HTTP headers that are returned to the ALB. The webpage returns successfully when a solutions architect reloads the webpage immediately after the error occurs.<br>
While the company is working on the problem, the solutions architect needs to provide a custom error page instead of the standard ALB error page to visitors.<br>
Which combination of steps will meet this requirement with the LEAST amount of operational overhead? (Choose two.)

A. Create an Amazon S3 bucket. Configure the S3 bucket to host a static webpage. Upload the custom error pages to Amazon S3.

B. Create an Amazon CloudWatch alarm to invoke an AWS Lambda function if the ALB health check response Target.FailedHealthChecks is greater than 0. Configure the Lambda function to modify the forwarding rule at the ALB to point to a publicly accessible web server.

C. Modify the existing Amazon Route 53 records by adding health checks. Configure a fallback target if the health check fails. Modify DNS records to point to a publicly accessible webpage.

D. Create an Amazon CloudWatch alarm to invoke an AWS Lambda function if the ALB health check response Elb.InternalError is greater than 0. Configure the Lambda function to modify the forwarding rule at the ALB to point to a public accessible web server.

E. Add a custom error response by configuring a CloudFront custom error page. Modify DNS records to point to a publicly accessible web page.
</div>
</details>

<details>
<summary>정답 및 해설 보기</summary>
<div markdown="1">
<br>
Answer : A, E

해설 : 

옵션 A를 사용하면 S3 버킷에서 호스팅할 수 있는 사용자 정의 오류 페이지를 생성할 수 있습니다. 옵션 E는 오류 페이지를 호스팅하는 S3 버킷을 가리킬 수 있는 CloudFront의 사용자 지정 오류 응답을 구성하는 방법을 제공합니다. 따라서 방문자는 애플리케이션 인프라를 수정하지 않고도 사용자 지정 오류 페이지를 볼 수 있습니다.

1차 시도 : B, E <br>
</div>
</details>

<br>
<hr/>
<hr/>
<br>

* Ref
  - [ExamTopics](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-professional-sap-c02/view/1/)

