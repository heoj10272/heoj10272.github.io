---
layout: post
title: "[AWS] Amazon Cognito 이해"
subtitle: AWS
date: '2022-06-07 13:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-07-[AWS]_Amazon_Cognito_이해/logo.png
---

AWS에서 제공하는 **Amazon Cognito**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

## 1. Amazon Cognito 개요

아래는 AWS에서의 **Amazon Cognito**에 대한 설명이다.

> **Amazon Cognito**는 **웹 및 모바일 앱에 대한 인증**, **권한 부여** 및 **사용자 관리**를 제공합니다. <br>
> 사용자는 사용자 이름과 암호를 사용하여 직접 로그인하거나 Facebook, Amazon, Google 또는 Apple 같은 타사를 통해 로그인할 수 있습니다.

즉 **Amazon Cognito**는 권한 부여, 사용자 관리 뿐만 아니라 **내부**, **외부**에서 웹 및 모바일 앱에 **액세스** 할 수 있도록 해주는 서비스이다.

<hr/>

## 2. Amazon Cognito 구성 요소

**Amazon Cognito**의 두 가지 주요 구성 요소는 **사용자 풀**과 **자격 증명 풀**이다. 

**사용자 풀**은 앱 사용자의 가입 및 로그인 옵션을 제공하는 사용자 디렉터리이다.<br>
**자격 증명 풀**은 사용자에게 기타 AWS 서비스에 액세스할 수 있는 권한을 부여한다.

이 둘은 **별도**로 또는 **함께** 사용할 수 있다.

함께 사용할 경우 아래 시나리오 다이어그램을 따른다.

  ![Scenario_Diagram](/assets/img/study_AWS/2022-06-07-[AWS]_Amazon_Cognito_이해/Scenario_Diagram.png)

위 시나리오의 목표는 **사용자 인증 이후 다른 AWS 서비스에 대한 사용자 액세스 권한을 부여하는 것**이다.

1. 첫 번째 단계에서 **앱 사용자는 사용자 풀을 통해 로그인하여 인증 성공 이후 풀 토큰을 받는다**.
2. 다음으로 **앱은 자격 증명 풀을 통해 사용자 풀 토큰을 AWS 자격 증명으로 교환한다**.
3. 마지막으로 앱 사용자는 **AWS 자격 증명을 사용하여 Amazon S3, Dynamo DB 등 다른 AWS 서비스에 액세스할 수 있다**.

<hr/>

## 3. Amazon Cognito 기능

### I. 사용자 풀

**사용자 풀**은 Amazon Cognito의 **사용자 디렉터리**이다. <br>
사용자 풀에서 사용자는 Amazon Cognito를 통해, 또는 서드 파티 자격 증명 공급자(IdP)를 통해 페더레이션하여 **웹 또는 모바일 앱에 로그인할 수 있다**. <br>
사용자가 직접 또는 타사를 통해 로그인하는지 여부와 무관하게 **사용자 풀의 모든 멤버는 디렉터리 프로필을 보유**하며, **SDK를 통해 액세스할 수 있다**.

아래는 **사용자 풀 제공 사항**이다.

* **가입 및 로그인 서비스**

* 사용자 로그인을 위한 **내장 사용자 지정 웹 UI**

* Facebook, Google, Login with Amazon 및 Sign in with Apple을 통한 **소셜 로그인** 및 **사용자 풀의 SAML** 및 **OIDC 자격 증명 공급자를 통한 로그인**

* **사용자 디렉터리 관리** 및 **사용자 프로필**

* **멀티 팩터 인증(MFA)**, **이상 있는 자격 증명 확인**, **계정 탈취 보호**, **전화 및 이메일 확인**과 같은 보안 기능

* **AWS Lanbda 트리거**를 통한 **사용자 지정 워크플로우** 및 **사용자 마이그레이션**

### II. 자격 증명 풀

**자격 증명 풀**로 사용자는 **임시 AWS 자격 증명을 얻어 Amazon S3, DynamoDB 등의 다른 AWS 서비스에 액세스할 수 있다**. 
**자격 증명 풀**은 **익명 게스트 사용자**는 물론 **자격 증명에 대한 사용자 인증**에 사용할 수 있는 **다음 자격 증명 공급자를 지원한다**.

* **Amazon Cognito user pools**

* **Facebook**, **Google**, **Login with Amazon** 및 **Sign in with Apple**을 통한 **소셜 로그인**

* **OpenID Connect(OIDC) 공급자**

* **SAML 자격 증명 공급자**

* **개발자 인증 자격 증명**

사용자 프로필 정보를 저장하려면 자격 증명 풀이 사용자 풀에 **통합**되어야 한다.

<hr/>

* Ref
  - [AWS Amazon Cognito Userguide](https://docs.aws.amazon.com/ko_kr/cognito/latest/developerguide/what-is-amazon-cognito.html)