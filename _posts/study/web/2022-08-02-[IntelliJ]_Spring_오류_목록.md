---
layout: post
title: "[IntelliJ] Spring 오류 목록"
subtitle: IntelliJ
date: '2022-8-2 03:00:00 +0900'
category: web
tags: intellij spring
image:
  path: /assets/img/study_Web/2022-08-02-[IntelliJ]_Spring_오류_목록/logo.png
---

IntelliJ에서의 Spring 오류 목록

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## 오류 목록

### lombok

```
Cause: class lombok.javac.apt.LombokProcessor 
(in unnamed module @0x45970520) cannot access class 
com.sun.tools.javac.processing.JavacProcessingEnvironment 
(in module jdk.compiler) because module jdk.compiler does not export
com.sun.tools.javac.processing to unnamed module @0x45970520
```

### 해결 방법

1\. 로컬 `cmd`에서 아래 명령어 실행 가능 여부 확인

```
java -version
javac -version
```

2\. `IntelliJ SDK`가 위 `java` 버전과 동일한지 확인

3\. `build.gradle`의 `dependency`에서 `lombok` 버전 명시

```
implementation('org.projectlombok:lombok')
annotationProcessor('org.projectlombok:lombok')
compileOnly('org.projectlombok:lombok')
```
위 코드를 다음과 같이 변경
```
implementation('org.projectlombok:lombok:1.18.24')
annotationProcessor('org.projectlombok:lombok:1.18.24')
compileOnly('org.projectlombok:lombok:1.18.24')
```
