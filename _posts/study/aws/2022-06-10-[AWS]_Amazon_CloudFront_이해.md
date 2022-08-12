---
layout: post
title: "[AWS] Amazon CloudFront 이해"
subtitle: AWS
date: '2022-06-10 19:30:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/logo.png
---

AWS에서 제공하는 **Amazon CloudFront**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## 1. Amazon CloudFront 개요

아래는 AWS에서 소개하는 **Amazon CloudFront** 설명이다.

> **Amazon CloudFront**는 개발자 친화적 환경에서 짧은 지연 시간과 빠른 전송 속도로 데이터, 동영상, 애플리케이션 및 API를 전 세계 고객에게 안전하게 전송하는 고속 **콘텐츠 전송 네트워크(CDN)** 서비스입니다.

<br>
<hr/>

### 엣지 로케이션

![edge_location](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/edge_location.png){:.centered}

위 그림은 전세계의 AWS 엣지 로케이션의 위치를 나타낸다.

**엣지 로케이션**이란, 컨텐츠가 캐싱되고 유저에게 제공되는 지점이다.

<br>
<hr/>

### Content Delivery Network(CDN)

**Content Delivery Network(CDN)**란 다음과 같다.

* 웹페이지, 이미지, 동영상 등의 컨텐츠를 **본래 서버에서 받아와 캐싱**

* 해당 컨텐츠에 대한 요청이 들어오면 **캐싱해 둔 컨텐츠를 제공**

* 컨텐츠를 제공하는 서버와 실제 요청 지점 간의 지리적 거리가 매우 먼 경우, 혹은 통신 환경이 안좋은 경우 **요청지점 근처의 CDN을 통해 빠르게 컨텐츠 제공** 가능

* 서버로 요청이 필요 없기 때문에, 서버의 부하를 낮추는 효과가 있음

![CDN](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/CDN.png){:.centered}

위 그림은 **세계 각 지점(검정색)**에서 **우리나라에 위치한 서버(초록색)**로 데이터를 요청 할 때의 상황을 나타낸 것이다.

각 지점으로부터 우리나라까지의 위치가 굉장히 멀리 떨어져 있기 때문에, 필연적으로 속도가 느려진다.

![CDN_2](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/CDN_2.png){:.centered}

따라서 위 그림과 같이 각 지역별로 **엣지 로케이션(청록색)**을 둠으로서 서울에 위치한 서버로부터 각각 데이터를 받아와 전송해줄 수 있다.

<br>
<hr/>
<hr/>

## 2. Amazon CloudFront 동작 방식

Amazon CloudFront 동작 방식은 다음과 같다.

* 요청 받은 컨텐츠가 엣지 로케이션에 있다면, 바로 전달

* 요청 받은 컨텐츠가 엣지 로케이션에 없다면, 컨텐츠를 제공하는 근원에서 제공받아 전달

<br>
<hr/>
<hr/>

## 3. Amazon CloudFront 구성

* **Origin** : 실제 컨텐츠가 존재하는 근원(S3, EC2, ELB, Route53 등)
  + AWS 서비스(EC2, ELB, S3 등)
  + 온프레미스 서버

* **Distribution** : CloudFront의 CDN 구분 단위로 여러 엣지 로케이션으로 구성된 컨텐츠 제공 채널

* 주요 설정 및 용어
  + **TTL(Time To Live)** : 캐싱된 아이템이 살아 있는 시간 -> TTL 초 이후 캐싱에서 삭제
  + **파일 무효화(invalidate)** : TTL이 지나기 전에 강제로 캐시를 삭제하는 것
    - 주로 새로운 파일을 업데이트 한 후 TTL을 기다리지 못할 상황에 사용
    - 비용 발생
    - CloudFront API, 콘솔, Third-Party 툴 등을 사용 가능
  + **Cache Key**
    - 어떤 기준으로 컨텐츠를 캐싱할 것인지 결정
    - 기본적으로 URL
    - 이후 Header와 Cookie, 쿼리 스트링 등을 사용 가능
  + **정책(Policy)**
    - CloudFront가 동작하는 방법을 정의한 정책
    - 어떻게 캐싱을 할지, 어떤 내용을 Origin에 보낼지, 어떤 헤더를 허용할 지 등을 결정

<br>
<hr/>
<hr/>

## 4. Amazon CloudFront 기능

### I. CDN

* **CDN** : 컨텐츠를 최적화하여 보다 빠르게 유저에게 제공
  + **정적/동적 컨텐츠 모두 최적화**
  + **정적(Static) 컨텐츠** : 서버를 거치지 않고 클라이언트에서 직접 보여주는 내용
    - 이미지
    - CSS
    - 기타 서버가 필요 없는 내용들
  + **동적(Dynamic) 컨텐츠** : 서버 계산, DB조회 등이 필요한 내용
    - 로그인
    - 게시판

보통의 다른 CDN에서는 동적 컨텐츠는 캐싱을 잘 못시키는데, CloudFront에서는 동적 컨텐츠 또한 지원한다.

![Dynamic_Static](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/Dynamic_Static.png){:.centered}

일반적인 CloudFront의 처리 패턴은 위 그림과 같다.<br>
동적 컨텐츠는 동적 컨텐츠를 제공하는 Origin으로, 정적 컨텐츠는 정적 컨텐츠를 제공하는 오리진으로 **경로 패턴을 분기 처리** 한다.

각 컨텐츠별 최적화 방식은 다음과 같다.

* **정적 컨텐츠** : 캐싱으로 접근 속도 최적화

* **동적 컨텐츠** : 네트워크 최적화, 연결 유지, Gzip 압축 등을 사용
  + DNS Lookup, TCP Connection, Time to First Byte 등을 최적화

<br>
<hr/>

### II. HTTPS 지원

  * **HTTPS 지원**
    + Origin에서 HTTPS를 지원하지 않더라도 HTTPS 통신을 지원할 수 있도록 구성 가능

일반적으로 웹 브라우저를 통해서 웹서버에 접근하면 HTTP만을 지원한다.

![alert](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/alert.png){: width="60%" height="60%"}{:.centered}

이 경우 위와 같이 `주의 요함`이 뜨게 된다.

하지만 CloudFront를 사용하면 HTTPS를 Origin에서 지원하지 않더라도 지원하게끔 만들 수 있다.<br>
그 과정은 다음과 같다.

![https](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/https.png){:.centered}

웹서버(EC2)와 CloudFront간의 통신은 HTTP 통신이지만, 사용자와 CloudFront 사이의 통신은 **AWS Certificate Manager(ACM)**를 통해서 HTTPS 통신으로 만든다.

<br>
<hr/>

### III. 지리적 제한

  * **지리적 제한** : 특정 지역의 컨텐츠 접근을 제한 가능

  다른 나라에서의 저작권이나 계약에 의해 해당 지역에서 서비스를 지원할 수 없을 경우, 접근을 제한할 수 있다.

<br>
<hr/>

### IV. 다른 서비스와 연계

  * **다른 서비스와 연계**
    + AWS WAF(보안 서비스), Lambda@Edge 등과 연동 가능

#### Lambda@edge

  * Lambda를 사용

  * 사용 사례
    + 예 : 한국에서 요청이 올 경우 한국 웹 서버, 미국에서 올 경우 미국 웹 서버로 분산
    + 커스텀 에러 페이지
    + Cookie를 검사해 다른 페이지로 리다이렉팅 -> A/B 테스팅
    + CloudFront에서 Origin에 도착 이전에 인증 등

  과정은 다음과 같다.

  ![Lambda_edge](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/Lambda_edge.png){:.centered}
  
  Lambda@edge는 위와 같이 **4가지 case**가 있다.

  사용자로부터 CloudFront에 도착하기 전(**Viewer Request**), <br>
  CloudFront에서 웹서버(Origin)로 요청을 보내기 전(**Origin Request**),<br>
  웹서버에서 CloudFront로 응답을 보내기 전(**Origin Response**), <br>
  마지막으로 CloudFront에서 사용자에게 응답을 보내기 전(**Viewer Response**)

  각 단계에서 Lambda를 실행해서 전달 내용을 변경, 로깅, 분석 등을 할 수 있다.

#### CloudFront Function

  * Lambda@edge 1/6의 비용으로 경량 javascript 실행
  
  * 사용 사례 : 캐싱, 헤더 조작 등

<br>
<hr>

### V. 리포팅

  * **주요 CloudFront 이용 지표 확인 가능**
    + 캐시 상태
    + 가장 많이 요청 받은 컨텐츠
    + Top Referrer
      - 어디서 들어와서 해당 웹 애플리케이션을 보고 있는지

  다음은 위 요소들의 화면이다.

![total_requests](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/total_requests.png){:.centered}

Total requests
{:.figcaption}

<br>

![top_referrers](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/top_referrers.png){:.centered}

Top referrers
{:.figcaption}

<br>

![which_device](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/which_device.png){:.centered}

어떤 디바이스로 요청했는지도 알 수 있다.
{:.figcaption}

뿐만 아니라 **어떤 OS**, **어떤 나라**에서 접속했는지도 알 수 있다.

이러한 리포트들은 모두 **Origin에 전달**할 수 있다.<br>
아래 **뷰어 정보 확인** 항목 참조.

<br>
<hr/>
<hr/>

## 5. Amazon CloudFront 정책

* 총 3가지 정책 설정 가능
  + **Cache Control** : 캐싱 방법 및 압축
    - TTL 및 Cache Key 정책
    - CloudFront가 어떻게 캐싱을 할 지를 결정
  + **Origin Request** : Origin으로 어떤 내용을 보낼 것인가
    - Origin에 쿠키, 헤더, 쿼리스트링 중 어떤 것을 보낼 것인가
  + **뷰어에게 보낼 HTTP header**
    - CloudFront가 뷰어(사용자)에게 응답과 같이 실어 보낼 HTTP Header

### CloudFront의 뷰어 정보 확인

  * CloudFront에서 뷰어의 정보를 헤더에 더해 Origin에 전송
  
  * **확인 가능한 뷰어의 정보**
    + **디바이스 타입** : Android/IOS/SmartTV/Tablet/Desktop
    + **IP Address**
    + **Country**/**도시**/**위도, 경도**/**타임존** 등

  이를 토대로 사용자에게 보여줄 컨텐츠를 분기할 수 있다.<br>
  뷰어의 정보 중 Country가 미국이라면, 영어로 된 컨텐츠를 보여주고, 한국이라면 한글로 된 컨텐츠를 보여주는게 가능하다.

<br>
<hr/>
<hr/>

## 6. Amazon CloudFront 보안

### I. Signed URL

* **Signed URL** : 어플리케이션에서 CloudFront의 컨텐츠에 접근 할 수 있는 URL을 제공하여 컨텐츠 제공을 제어하는 방법
  + URL에는 시작시간, 종료시간, IP파일명, URL의 유효기간 등의 정보를 담을 수 있음
  + **이 URL 접근 이외의 접근을 막고 허용된 유저에게만 URL을 전달하여 컨텐츠 제공을 제어 가능**
  + **단 하나의 파일** 또는 **컨텐츠**에 대한 허용만 가능
  + **S3 Signed URL**과 비슷한 방식

<br>
<hr/>

### II. Signed Cookie

* **Signed Cookie** : **다수의 컨텐츠**의 제공 방식을 제어하고 싶을 때 사용
  + Signed URL과 마찬가지로 **여러 제약 사항 설정 가능**
  + **다수의 파일** 및 **스트리밍** 접근 허용 가능
  + 예 : 로그인 했을 때 해당 사용자에게 허락된 컨텐츠들을 제공
  + 예 : 프리미엄 유저만 볼 수 있는 강의 동영상 등

<br>
<hr/>

### III. Origin Access Identity(OAI)

* **Origin Access Identity(OAI)**
  + **S3의 컨텐츠**를 CloudFront를 사용해서만 볼 수 있도록 제한하는 방법
    - S3의 컨텐츠는 정적이기 떄문에 CloudFront를 자주 사용함
  + CLoudFront만 권한을 가지고 S3에 접근하고 나머지 접근권한은 막음
  + S3 Bucket Policy로 CloudFront의 접근을 허용해야 사용 가능

<br>
<hr/>

### IV. Field Level Encryption

* **Field Level Encryption**
  + **CloudFront로부터 Origin 사이의 통신을 암호화**
  + 최대 10개의 필드까지
  + 공개 키 방식으로 암호화 -> CloudFront에 공개 키를 제공 후 Origin에서 Private Key로 해독

  과정은 다음 그림과 같다.

  ![Field_Level_Encryption](/assets/img/study_AWS/2022-06-10-[AWS]_Amazon_CloudFront_이해/Field_Level_Encryption.png){:.centered}

  유저가 CloudFront에 요청을 보낸다.<br>
  그러면 CloudFront에서 웹서버(EC2)로 요청을 보낸다.<br>
  이 과정에서 생각보다 많은 과정을 거치게 된다.<br>
  때문에 CLoudFront에 Public Key를 제공하여 암호화 하도록 시킨다.<br>
  암호화된 요청(필드)은 웹서버(EC2)에서 Private Key를 통해 해독된다.

  이러한 과정에 꺼려진다면 웹서버에 HTTPS 통신을 사용하도록 구현하면 되나, 과정에 까다로울 수 있다.

<br>
<hr/>
<hr/>
<br>

  * Ref
    - [Youtube](https://youtu.be/6C9284C-zP4)