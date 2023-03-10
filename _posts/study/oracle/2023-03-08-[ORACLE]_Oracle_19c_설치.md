---
layout: post
title: "[ORACLE] Oracle 19c 설치"
subtitle: Oracle
date: '2023-03-08 23:20:00 +0900'
category: study
tags: oracle
image:
  path: /assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/logo.png
---

윈도우에 Oracle 19c를 설치해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

# 1. Oracle 설치 파일 다운
---

[Oracle Database Software Downloads](https://www.oracle.com/kr/database/technologies/oracle-database-software-downloads.html)

위 링크로 들어가서 윈도우용 Oracle 설치 파일을 다운받자.

![1](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/1.png)

표시한 부분의 `ZIP` 파일을 다운받으면 된다.<br>
좀 오래 걸린다.<br>

설치가 다 되었으면, 압축을 풀어주자.

# 2. Oracle 설치
---

![2](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/2.png)

표시한 `setup.exe` 설치 파일을 **관리자 권한으로** 실행하자.<br>
권리자 권한으로 실행하지 않으면 설치 중간에 멈추는 현상이 발생한다(경험담).

![3](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/3.png)

[단일 인스턴스 데이터베이스 생성 및 구성(C)] 선택

![4](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/4.png)

[서버 클래스(S)] 선택

![5](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/5.png)

[표준 설치(T)] 선택

![6](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/6.png)

[가상 계정 사용(V)] 선택

![7](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/7.png)

[Oracle Base(S)] 에서 오라클을 설치할 경로를 선택한다.<br>
디폴트로 드라이브 루트 경로가 지정되어 있는데, 해당 경로에는 설치가 불가하므로 폴더를 하나 생성해서 지정해주자.

[비밀번호(P)] 에는 원하는 비밀번호를 입력한다.<br>
반드시 메모해 놓도록 하자.

![8](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/8.png)

이후 [다음] 을 누르면 위와 같은 경고문이 뜨는데, 무시하고 [예(Y)] 를 누르면 된다.

![9](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/9.png)

요약을 확인하고, [설치(I)] 를 클릭

![10](/assets/img/study_Oracle/2023-03-08-[ORACLE]_Oracle_19c_설치/10.png)

설치가 진행된다.<br>

