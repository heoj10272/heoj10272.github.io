---
layout: post
title: "[ORACLE] Oracle 19c 삭제"
subtitle: Oracle
date: '2023-03-12 22:20:00 +0900'
category: study
tags: oracle
image:
  path: /assets/img/study_Oracle/2023-03-12-[ORACLE]_Oracle_19c_삭제/logo.png
---

윈도우에 설치한 Oracle 19c를 삭제해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<hr/>

Oracle 19c를 설치할 때 `setup` 파일을 관리자 권한으로 실행하지 않았다가 한 번 ...<br>
경로를 잘못 설정해서 다시 한 번 삭제를 하게 되었다.<br>

`deinstall.xml` 파일이 있기는 하지만, 나의 경우는 잘 실행되지 않아 수동으로 삭제하는 방법을 기록하기로 했다.

# 1. Oracle 관련 서비스 중지
---

![1](/assets/img/study_Oracle/2023-03-12-[ORACLE]_Oracle_19c_삭제/1.png)

먼저 `[서비스]`를 윈도우에서 검색하여 실행해준다.

![2](/assets/img/study_Oracle/2023-03-12-[ORACLE]_Oracle_19c_삭제/2.png)

이후 Oracle로 시작하는 모든 서비스를 `우클릭` - `[중지(O)]` 를 클릭하여 중지한다.<br>
금방 되는것도 있고, 약간 시간이 걸리는 것도 있다.

# 2. Oracle 관련 레지스트리 삭제
---

![3](/assets/img/study_Oracle/2023-03-12-[ORACLE]_Oracle_19c_삭제/3.png)

`[Win]` + `R` 또는 윈도우 검색에 `regedit` 을 입력하여 레지스트리 편집기를 실행한다.

![4](/assets/img/study_Oracle/2023-03-12-[ORACLE]_Oracle_19c_삭제/4.png)

`HKEY_LOCAL_MACHINE/SOFTWARE/ORACLE` 폴더 삭제

![5](/assets/img/study_Oracle/2023-03-12-[ORACLE]_Oracle_19c_삭제/5.png)

`HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services` 경로 내의 모든 Oracle 관련 폴더 삭제

추가로, 다음의 경로 내에 있는 Oracle 관련 폴더도 있으면 삭제한다.<br>

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node`
2. `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services`
3. `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\Services`
4. `HKEY_CLASSES_ROOT`
나는 한 번 지웠어서 그런지 보이지 않는다...

# 3. 재부팅
---

레지스트리까지 다 지웠으면, 재부팅을 한다.

# 4. Oracle 관련 파일 삭제
---

아래 경로를 하나씩 뒤져보면서 해당되는 파일들을 모두 삭제한다.

1. `C:\Oracle` 또는 Oracle을 설치한 드라이브의 `Oracle` 폴더
2. `C:\Program Files\Oracle`
3. `C:\Program Files (x86)\Oracle`
4. `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\` 폴더 내의 Oracle 관련 폴더
5. `C:\Users` 폴더 내의 Oracle 관련 폴더

이후 `C:\Temp` 폴더까지 비워준다.

이제 삭제가 완료되었다.

# Ref
---
  - [Oracle-Base](https://oracle-base.com/articles/misc/manual-oracle-uninstall)
