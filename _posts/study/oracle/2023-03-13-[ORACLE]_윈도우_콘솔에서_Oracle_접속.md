---
layout: post
title: "[ORACLE] 윈도우 콘솔에서 Oracle 접속"
subtitle: Oracle
date: '2023-03-13 23:30:00 +0900'
category: study
tags: oracle
image:
  path: /assets/img/study_Oracle/2023-03-13-[ORACLE]_윈도우_콘솔에서_Oracle_접속/logo.png
---

윈도우 콘솔로 Oracle에 접속해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

# Windows 콘솔에서 오라클 접속
---

1. [Oracle 환경 변수 확인](https://heoj10272.github.io/study/ORACLE-_%ED%99%98%EA%B2%BD_%EB%B3%80%EC%88%98_%ED%99%95%EC%9D%B8.html) 글에서처럼 환경 변수가 기본값으로 세팅되어 있을 경우

    ```
    sqlplus / as sysdba
    ```

2. `system` 계정으로 접속

    ```
    sqlplus system/[자신이 지정한 PW]
    ```

    나의 경우는 다음과 같다.

    ```
    sqlplus system/password
    ```