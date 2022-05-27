---
layout: post
title: Windows에서 EC2 인스턴스 접속 (PuTTY)
subtitle: AWS
date: '2022-05-27 21:00:00 +0900'
category: study
tags: aws
image:
  path: /assets/img/study_AWS/aws_logo.png
---

Linux는 SSH를 가지고 있지만 Windows는 SSH를 가지고 있지 않기 때문에, SSH의 역할을 해주는 프로그램이 필요하다.

즉, Windows에서 Linux로 원격 접속을 하기 위해서는 별도의 프로그램이 필요하다.<br>
이번에는 PuTTY를 사용해서 `EC2` 인스턴스에 접속한다.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

## ppk 파일 만들기

PuTTY를 실행하기 전에, PuTTYgen을 실행한다.<br>
이전에 키 페어를 생성할 때 pem파일이 아닌 pkk파일을 생성했다면 이 과정은 건너뛰어도 된다.

![1](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/1.png)

PuTTYgen 기본 초기화면이다.<br>
`Load` 버튼을 눌러 이전 EC2 인스턴스를 생성할 때 만들었던 키 페어 파일(pem)을 가져오자.

![2](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/2.png)

`Load`버튼을 눌러 pem 파일이 있는 경로를 들어가면 처음에는 파일이 보이지 않는다.<br>
오른쪽 하단에서 파일 유형을 [All Files(*.*)]로 바꾸면 보인다.

![3](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/3.png)

알림창이 뜨면 성공이다.<br>
`확인` 버튼을 누르고 `Save private key` 버튼을 누르고 `예` 버튼을 눌러 생성되는 pkk파일을 저장한다.<br>
저장 장소는 pem파일과 마찬가지로 안전한 곳에 보관하자.

<hr/>

## PuTTY로 인스턴스 접속

이제 PuTTY를 실행한다.

![4](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/4.png)

![5](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/5.png)

인스턴스-인스턴스 ID를 클릭하면 요약 정보를 볼 수 있다.
{:.figcaption}

`Host Name(or IP address)` 항목에는 AWS 인스턴스의 `퍼블릭 IPv4 주소` 또는 `퍼블릭 IPv4 DNS`를 붙여넣기 하면 된다.

![6](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/6.png)

다음은 Category에서 `Connection` — `SSH` — `Auth`의 Private key file for authentication 항목의 `Borwse…` 버튼을 눌러 이전에 저장한 pkk파일을 불러온다.

![7](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/7.png)

다음으로 같은 `Connection`의 `Data`를 누르고 `Login details` — `Auto-login username`에 자신이 선택한 인스턴스의 AMI에 맞는 username을 기입한다.

> 각 AMI별 default user name
> * For Amazon Linux 2 or the Amazon Linux AMI, the user name is `ec2-user`.
> * For a CentOS AMI, the user name is `centos` or `ec2-user`.
> * For a Debian AMI, the user name is `admin`.
> * For a Fedora AMI, the user name is `fedora` or `ec2-user`.
> * For a RHEL AMI, the user name is `ec2-user` or `root`.
> * For a SUSE AMI, the user name is `ec2-user` or `root`.
> * For an Ubuntu AMI, the user name is `ubuntu`.
> * For an Oracle AMI, the user name is `ec2-user`.
> * For a Bitnami AMI, the user name is `bitnami`.
> * Otherwise, check with the AMI provider.

위는 AWS에서 안내하는 AMI별 default username이다.<br>
나는 Amazon Linux를 사용하고 있으므로 ec2-user를 입력한다.<br>
이렇게 username을 등록해 놓으면 일일이 username을 입력해 로그인을 하지 않아도 되므로 편하다.

![8](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/8.png)

이제 다시 `Session` Category로 돌아와 원하는 이름으로 `Save`를 눌러 Session을 저장해놓자.<br>
이러면 다시 PuTTY를 켜도 `Load`를 누르면 설정사항이 불러와진다.

이제 `Open` 버튼을 눌러 접속해보자.<br>
경고창이 뜨면 `Accept` 버튼을 누르면 된다.

<hr/>

## 결과

![9](/assets/img/study_AWS/[AWS]_Windows에서_EC2_인스턴스_접속_(PuTTY)/9.png)

이렇게 뜨면 성공이다.

<hr/>

다음은 RDS 인스턴스를 생성하는 방법을 소개한다.