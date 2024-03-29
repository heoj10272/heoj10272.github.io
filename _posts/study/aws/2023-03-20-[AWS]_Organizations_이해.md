---
layout: post
title: "[AWS] Organizations 이해"
subtitle: AWS
date: '2023-03-20 21:30:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2023-03-20-[AWS]_Organizations_이해/logo.png
---

AWS **Organizations**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>

# 1. Organizations 개요
---

> **AWS Organizations**는 생성한 여러 AWS 계정을 조직에 통합하고, 중앙에서 관리할 수 있게 해주는 계정 관리 서비스입니다. AWS Organizations의 계정 관리 및 통합 결제 기능을 활용하면 기업의 에산, 보안 및 규정 준수 요구 사항을 보다 잘 충족할 수 있습니다. 조직의 관리자로서 조직에서 계정을 생성하고 기존 계정을 조직에 초대할 수 있습니다.

즉, AWS의 계정을 조직 단위로 관리할 수 있게 해주는 서비스라고 할 수 있다.

<br>

# 2. 구성 요소
---

![1](/assets/img/study_AWS/2023-03-20-[AWS]_Organizations_이해/1.png)

## I. Organization(조직)
---

가장 큰 단위로 AWS의 계정들을 단일 개체로서 통합 관리할 수 있도록 한다.<br>
`AWS Organizations Console` 로 조직 내 모든 계정을 중앙에서 확인 및 관리할 수 있다.

조직은 `Management Account(관리 계정)` 하나와 0개 이상의 `Member Account(멤버 계정)` 을 갖는다.<br>
즉, 관리 계정은 필수적이다.

조직의 제일 위에는 `Root` , 아래로는 `Organization Unit(OU)` 가 있는 트리 계층 구조로 계정을 조직할 수 있다.<br>
각 계정은 루트에 바로 위치하거나, 계층 구조 내의 OU 중 하나에 배치할 수 있다.

조직은 사용자가 설정하는 `feature set(기능 모음)` 으로 결정되는 다양한 기능을 가질 수 있다.

## II. Root(루트)
---

조직의 모든 계정에 대한 상위 컨테이너이다.

정책을 루트에 적용하면, 해당 정책은 조직의 모든 OU와 계정에 적용된다.

참고로, 루트는 하나만 존재할 수 있다(you can have only one root).<br>
조직을 생성하면, AWS Organizations가 자동으로 생성해준다.

## III. Organizational unit(OU)
---

루트에 속하는 계정들을 감싸는 컨테이너이다.<br>

OU는 다른 OU를 포함할 수 있다.<br>
때문에 사용자는 위쪽에는 루트가, 아래쪽에는 OU 브랜치가, 맨 끝에는 리프에 해당하는 계정이 있는 upside-down 형태의 트리 구조를 만들 수 있다.

정책을 계층 구조 내의 노드 하나에 연결하면, 정책은 아래쪽으로 내려오면서 모든 브랜치(OU)와 리프(계정)에 적용된다.

각 OU는 상위 OU를 하나만 가질 수 있으며, 현재 하나의 계정은 한 개의 OU에만 속할 수 있다.

## IV. Account(계정)
---

Oragnizations의 계정은 말 그대로의 AWS 리소스를 포함하는 표준 계정이자 자격 증명이다.

참고로, 여기서 말하는 계정은 `사용자 계정` 이 아니다.<br>
`AWS Account(계정)` 과 `사용자 계정` 은 엄연히 다른 것으로, 사용자 계정은 `IAM` 으로 만들어지는 자격 증명을 뜻한다.<br>
따라서 하나의 AWS 계정은 많은 사용자 계정과 역할을 포함하는 큰 개념이다.

앞서 말했듯이 조직에는 두 가지 유형의 계정이 있다.
하나는 `관리 계정` , 또 하나는 `멤버 계정` 이다.

* 관리 계정
    + 관리 계정은 조직을 만들 때 사용하는 계정이다
    + 조직의 관리 계정에서 수행할 수 있는 사항은 다음과 같다
        - 조직내에 계정 생성
        - 기존의 다른 계정을 조직에 초대
        - 조직에서 계정 제거
        - 초대 관리
        - 조직 내 개체(루트, OU 또는 계정)에 정책 적용
        - 지원되는 AWS 서비스들을 통합하여 조직 내 모든 계정에 서비스들을 효과적으로 제공
    + 관리 계정은 `payer account` 로서 멤버 계정에서 발생한 모든 요금을 지불해야 한다.
    + **조직의 관리 계정은 변경될 수 없다(중요)**.

* 멤버 계정
    + 멤버 계정은 조직의 나머지 모든 계정들이다
    + 하나의 계정은 하나의 조직에만 속할 수 있다
    + 멤버 계정에 정책을 적용하면 해당 계정에만 정책이 적용된다


# 3. 기능
---

## I. Invitation(초대)
---

말 그대로 다른 계정에 조직에 대한 가입을 요청하는 과정이다.

초대는 조직의 `관리 계정`에서만 발행할 수 있다.<br>
초대는 계정 ID 또는 초대된 계정과 연결된 이메일 주소로 전달된다.<br>

초대받은 계정이 초대를 수락하면, 해당 계정은 조직의 `멤버 계정`이 된다.<br>

만약 조직이 모든 멤버를 대상으로 `통합 결제(consolidated billing)` 지원에서 `모든 기능(all features)` 지원으로 바뀌는 일을 승인하게 될 경우, 모든 멤버 계정에 초대가 가게 된다.

초대는 계정 사이에 `핸드셰이크(Handshake)` 를 함으로서 이루어지며, `AWS Organizations Console` 에서는 보이지 않을 수 있으나 `AWS CLI` 또는 `AWS Organizations API` 를 사용할 때는 반드시 핸드셰이크로 직접 작업해야 한다.

## II. HandShake(핸드셰이크)
---

두 대상간에 정보를 교환하는 다양한 단계로 구성된 과정이다.

AWS Organizations에서 핸드셰이크가 주로 사용되는 경우는 위 `초대` 를 위한 기본 작업을 구현할 때이다.<br>
핸드셰이크 메세지는 핸드셰이크 개시자와 받는 사람간에 전달되고 응답되며, 현재 상태가 어떠한지를 알 수 있게 해준다.<br>
또한 위에서 말했듯 핸드셰이크는 조직이 `통합 결제` 에서 `모든 기능` 을 지원하도록 변경될 때도 사용되며, `콘솔`을 사용할 떄는 아니지만 `CLI`나 `API` 를 사용할 때는 직접 핸드셰이크를 사용해야 한다.

## III. Available feature sets(사용 가능한 기능 세트)
---

기능 세트에는 두 가지가 있다.

* all features(모든 기능)
    + AWS Organizations가 사용할 수 있는 기본 기능 세트이다
    + 통합 결제의 모든 기능과 조직 내 계정에 대한 더 많은 제어를 제공하는 고급 기능을 함께 제공한다
        - 예를 들어 모든 기능을 활성화 하면 조직의 관리 계정은 멤버 계정이 하는 일을 완전히 제어할 수 있다
        - 관리 계정은 `SCP` 를 적용하여 계정의 `사용자(루트 사용자 포함)`와 `Role` 이 액세스할 수 있는 서비스와 작업을 제한할 수 있다
        - 관리 계정이 멤버 계정을 조직에서 나가지 못하도록 할 수도 있다
        - 지원되는 AWS 서비스들을 통합하여 조직의 모든 계정에 기능을 제공할 수 있도록 할 수 있다
    + 모든 기능을 활성화한 상태로 조직을 만드는 것도 되고, 통합 결제 기능만 제공하는 조직에서 모든 기능을 제공하도록 바꿀 수도 있다
        - 상술했듯 이 경우 기존에 초대된 모든 멤버 계정이 다시 한 번 초대를 승인하여 수락하여야 한다

* consolidated billing(통합 결제)
    + 이 기능 세트는 공유 결제 기능은 제공하지만 추가적인 고급 기능은 제공하지 않는다
        - 예를 들어 AWS 서비스들을 통합하여 모든 계정에 적용하거나, 정책을 사용하여 다른 계정의 사용자 및 역할이 수행할 수 있는 작업을 제한할 수 없다.

## IV. SCP(서비스 제어 정책)
---

SCP를 적용하면 대상의 계정 내 사용자, 역할이 사용할 수 있는 서비스와 작업을 지정할 수 있다.

SCP는 `IAM 권한 정책(IAM permissions)`과 비슷하나, 특정 허가를 부여하지 않는다.<br>
대신, SCP는 조직, OU, 계정에 대한 최대 권한을 지정한다.<br>
무슨 말인가 하면, SCP는 필터로서 역할을 거르기만 할 수 있고, 상위 계층에 적용된 SCP를 하위 계층에 적용된 SCP가 거스를 수 없다.<br>
즉, 상위 계층에서 허가하지 않는 작업을 하위 계층에서 허가하여 사용할 수 없다는 뜻이다.


## V. Allow lists(허용 목록) vs deny lists(거부 목록)
---

중요한 개념이니 꼭 숙지하자.<br>
허용 목록과 거부 목록은 SCP에 추가 적용하여 계정에 사용 가능한 권한을 필터링 할 수 있다.

* Allow lists(허용 목록)
    + 허용되는 액세스를 명시적으로 지정한다
        - 즉, 다른 모든 액세스는 묵시적으로 모두 차단된다
    + 기본적으로 AWS Organizaitons는 `FullAWSAccess` 라는 AWS 관리형 정책을 모든 루트, OU, 계정에 적용시킨다
        - 따라서 모든 계정은 처음부터 모든 서비스와 작업에 접근할 수 있다.
        - 때문에 허용 목록을 지정하려면, 허용 목록을 정리한 SCP로 `FullAWSAccess` 를 **교체**한다(중요)
            - 해당 SCP는 IAM 보다 상위로 적용되기 때문에, 이렇게 하면 IAM 정책이 모든 작업을 허용한다 하더라도 SCP가 허용하는 리소스에만 접근할 수 있다
    + SCP는 허가를 부여하지 않음에 명심
        - 필터링만 하기 때문에 하위 계층에서 SCP로 허용 목록을 작성하더라도 상위 계층에서 차단한 리소스에는 접근할 수 없다

* Deny lists(거부 목록)
    + 허용되지 않는 액세스를 명시적으로 지정한다
        - 즉, 다른 모든 액세스는 묵시적으로 모두 허용된다
    + 상술했듯 `FullAWSAccess` 가 기본으로 적용되므로, 거부 목록을 적용할 때는 `FullAWSAccess` 를 SCP로 교체할 필요 없이 그대로 두고 거부할 목록만을 정리한 SCP를 추가로 연결하면 된다
        - IAM 정책보다 상위에 존재하기 때문에 거부 목록에 오른 리소스는 IAM 정책으로 허용한다 해도 접근할 수 없다

## VI. AI services opt-out policy(인공지능 서비스 옵트아웃 정책)
---

조직의 모든 계정에서 AWS AI 서비스에 대한 옵트아웃 설정을 표준화 하는데 동무을 주는 정책 유형이다.

특정 AWS AI 서비스는 Amazon AI 서비스 및 기술의 개발과 지속적인 개선을 위해 해당 서비스에서 처리한 고객 컨텐츠를 저장하고 사용할 수 있다.<br>
AWS 고객은 AI 서비스 옵트아웃 정책을 사용하여 서비스 개선을 위해 자신의 콘텐츠가 저장, 사용되지 않도록 옵트아웃 할 수 있다.

## VII. Backup policy(백업 정책)
---

조직의 모든 계정에서 리소스에 대한 백업 전략을 표준화하고 구현하는데 도움을 주는 정책 유형이다.

백업 정책을 사용하면 리소스에 대한 백업 계획을 구성하고 배포할 수 있다.

## VIII. Tag policy(태그 정책)
---

조직의 모든 계정에서 리소스 전반의 태그를 표준화 하는데 도움을 주는 정책 유형이다.

태그 정책을 사용하면 특정 리소스에 대한 태그 지정 규칙을 지정할 수 있다.

태그는 사용자 또는 AWS 리소스에 적용되는 커스텀 속성 레이블이다.
각 태그는 두 가지로 구성된다.

* Tag key(태그 키)
    + 예) `CostCenter` , `Environment`, `Project`
    + 대소문자 구별, 최대 128자

* Tag value(태그 값)
    + 예) `111122223333` , `Production`
    + 선택적으로 기입할 수 있으며, 생략할 경우 빈 문자열로 취급되지만 `Null` 로 설정할 수는 없다
    + 대소문자 구별, 최대 256자


* Ref
  - [AWS Docs](https://docs.aws.amazon.com/ko_kr/organizations/latest/userguide/orgs_getting-started_concepts.html)
