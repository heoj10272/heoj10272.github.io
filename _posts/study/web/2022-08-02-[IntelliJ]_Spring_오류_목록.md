---
layout: post
title: "[IntelliJ] Spring 오류 목록"
subtitle: IntelliJ
date: '2022-8-2 03:00:00 +0900'
category: study
tags: web intellij spring
image:
  path: /assets/img/study_Web/2022-08-02-[IntelliJ]_Spring_오류_목록/logo.png
---

IntelliJ에서의 Spring 오류 목록

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}


# 🎯 오류 목록
* * *

## 📌 lombok
---

```
Cause: class lombok.javac.apt.LombokProcessor 
(in unnamed module @0x45970520) cannot access class 
com.sun.tools.javac.processing.JavacProcessingEnvironment 
(in module jdk.compiler) because module jdk.compiler does not export
com.sun.tools.javac.processing to unnamed module @0x45970520
```

### ✔ 해결 방법
---

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



## 📌 Test Results 내부 빨간 경고 출력
---

```
8월 02, 2022 8:03:42 오후 org.junit.platform.launcher.core.EngineDiscoveryOrchestrator lambda$logTestDescriptorExclusionReasons$7
INFO: 0 containers and 1 tests were Method or class mismatch
```

### ✔ 해결 방법
---

테스트 메소드 중 일부만 실행하였을 때 발생한다.<br>
모든 메소드를 테스트시 출력되지 않으므로 그냥 넘어가도 괜찮다.



## 📌 Test 오류 : No tests found for given includes
---

```
No tests found for given includes: .....
```

### ✔ 해결 방법
---

`Settings` - `Build, Execution, Deployment` - `Build Tools` - `Gradle`<br>
`Gradle projects` - `Build and run`<br>
`Run test using:` 을 `Gradle`에서 `intelliJ IDEA`로 바꾼 후 적용



## 📌 h2 console에서 POSTS 테이블이 보이지 않음
---

### ✔ 해결 방법
---

`application.properties`에 다음 문구 추가

```
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL57Dialect
spring.jpa.properties.hibernate.dialect.storage_engine=innodb
spring.datasource.hikari.jdbc-url=jdbc:h2:mem:testdb;MODE=MYSQL
spring.datasource.hikari.username=sa
spring.h2.console.enabled=true
```


## 📌 구글 로그인시 로그인한 사용자의 이름이 아닌 로컬 컴퓨터 로그인 이름이 출력되는 경우
---

### ✔ 해결 방법
---

`userName`이라는 이름을 윈도우 환경변수에서 사용하고 있기 때문에 충돌이 난 것으로 예상됨.

`IndexController`, `index.mustache`에서 변수명을 `userName` → `loginUserName` 으로 바꿔주면 해결
