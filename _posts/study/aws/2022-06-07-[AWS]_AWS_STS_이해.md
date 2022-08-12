---
layout: post
title: "[AWS] AWS STS 이해"
subtitle: AWS
date: '2022-06-07 13:15:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-06-07-[AWS]_AWS_STS_이해/logo.png
---

AWS에서 제공하는 **AWS STS**를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

## 1. AWS STS 개요

**AWS Security Token Service(AWS STS)**를 사용하면 AWS 리소스에 대한 액세스를 제어할 수 있는 **임시 보안 자격 증명**을 생성하여 신뢰받는 사용자에게 제공할 수 있다. 

**임시 보안 자격 증명**은 다음과 같은 차이점을 제외하고는 IAM 사용자가 사용할 수 있는 **장기 액세스 키 자격 증명**과 거의 동일한 효력을 지닌다.

1. **임시 보안 자격 증명**은 그 이름이 암시하듯 **단기적**이다. <br>
  이 자격 증명은 **몇 분에서 몇 시간까지 지속되도록 구성할 수 있다**. <br>
  자격 증명이 **만료**된 후 AWS는 더는 그 자격 증명을 인식하지 못하거나 그 자격 증명을 사용한 API 요청으로부터 이루어지는 **어떤 종류의 액세스도 허용하지 않는다**.

2. **임시 보안 자격 증명**은 사용자와 함께 저장되지 않지만 **동적으로 생성되어 요청시 사용자에게 제공**된다. <br>
  임시 보안 자격 증명이 **만료**되었을 때(심지어는 만료 전이라도) 사용자는 **새 자격 증명을 요청할 수 있다**. <br>
  단, 자격 증명을 요청하는 해당 사용자에게 그렇게 할 수 있는 **권한**이 있어야 한다.

이러한 차이점은 다음과 같은 임시 자격 증명 사용의 **이점**을 발생시킬 수 있다.

* 애플리케이션으로 **장기 AWS 보안 자격 증명을 배포 또는 포함할 필요가 없다**.

* 사용자에 대한 **AWS 자격 증명을 정의하지 않고도 AWS 리소스에 대한 액세스 권한을 사용자에게 제공할 수 있다**. 
  + 임시 자격 증명은 **역할 및 ID 페더레이션을 위한 기초**이다.

* 임시 보안 자격 증명은 **수명이 제한**되어 있어서, 더 이상 필요하지 않을 때 **교체하거나 명시적으로 취소할 필요가 없다**. 

<hr/>

* Ref
  - [AWS ID Credentials Temp Userguide](https://docs.aws.amazon.com/ko_kr/IAM/latest/UserGuide/id_credentials_temp.html)


</span>
