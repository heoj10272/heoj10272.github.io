---
layout: post
title: "[Ansible] Ansible 설치"
subtitle: AWS
date: '2022-11-23 18:00:00 +0900'
category: study
tags: ansible
image:
  path: /assets/img/study_Ansible/2022-11-23-[Ansible]_Ansible_설치/logo.png
---

`Ansible` 을 설치해보자.<br>
`VirtualBox` 에 설치한다.
<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>

# 1. Ansible 설치
---

우선 `제어 노드(iac-control1)` 에 접근할 것이다.<br>
`제어 노드` 는 `iac-control1` , `관리 노드` 는 `iac-node1` 이다.<br>

아래 명령어로 `iac-control1` 에 접속한다.<br>
이전의 [Ansible 실습 환경 설정](https://heoj10272.github.io/study/Ansible-_Ansible_%EC%8B%A4%EC%8A%B5_%ED%99%98%EA%B2%BD_%EC%84%A4%EC%A0%95.html)의 과정을 거쳤다면, 이미 접속해 있을텐데, 경로를 잊었다면 아니라면 아래 경로로 이동한 뒤 명령어를 치면 된다.<br>

* 경로 : `C:\windows\system32\vagrant\iac`

```shell
vagrant ssh iac-control1
```

![1](/assets/img/study_Ansible/2022-11-23-[Ansible]_Ansible_설치/1.png)

기본적으로 `Ansible` 이 설치는 되어 있을텐데, 너무 옛날 버전이라 새로 설치해야한다.
<br>
아래 명령어로 현재 `Ansible` 의 정보를 확인 가능하다.<br>
참고로 알아두자.<br>

```shell
apt info ansible
```

아무튼 접속되었으면 아래 명령어를 실행하자.<br>

* 설치 가능한 패키지 리스트 최신화
```shell
sudo apt update
```

* `software-properties-common` 패키지 설치
```shell
sudo apt install software-properties-common
```

* `ppa(personal package archive)` 저장소 추가
```shell
sudo add-apt-repository --yes -update ppa:ansible/ansible
```
공식 `Ansible` 저장소 `ansible/ansible` 를 추가하였다.

* `Ansible` 설치
```shell
sudo apt install ansible
```

* 설치 확인
```shell
ansible --version
```

![2](/assets/img/study_Ansible/2022-11-23-[Ansible]_Ansible_설치/2.png)

설치가 잘 되었다.<br>

이제 네트워크 환경을 한 번 확인해보자.<br>

```shell
ip a s
```