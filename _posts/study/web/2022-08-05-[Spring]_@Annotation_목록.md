---
layout: post
title: "[Spring] @Annotation 목록"
subtitle: Spring
date: '2022-8-2 03:00:00 +0900'
category: study
tags: web spring
image:
  path: /assets/img/study_Web/2022-08-02-[IntelliJ]_Spring_오류_목록/logo.png
---

IntelliJ에서의 Spring 오류 목록

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

# Application
* * *

## @SpringBootApplication
---

```java
@SpringBootApplication // <--
public class Application {
    public static void main(String[] args){
        SpringApplication.run(Application.class, args);
    }
}
```

+ `@SpringBootApplication`으로 인해 스프링 부트의 자동 설정, 스프링 Bean 읽기와 생성을 모두 자동으로 설정됩니다.
+ 특히나 **`@SpringBootApplication`이 있는 위치부터 설정을 읽어**가기 때문에 이 클래스는 항상 **프로젝트의 최상단에 위치**해야만 합니다.

```java
SpringApplication.run(Application.class, args);
```

+ `main` 메소드에서 실행하는 `SpringApplication.run`으로 인해 `내장 WAS(Web Application Server)`를 실행합니다.
+ `내장 WAS`란 별도로 외부에 WAS를 두지 않고 애플리케이션을 실행할 때 내부에서 `WAS`를 실행하는 것을 이야기합니다.
+ 이렇게 되면 항상 서버에서 `톰캣`을 설치할 필요가 없게 되고, 스프링 부트로 만들어진 `Jar 파일(실행 가능한 Java 패키징 파일)`로 실행하면 됩니다.

# Controller
* * *

## @RestController
---

```java
@RestController // <--
public class HelloController {

}
```

+ 컨트롤러를 `JSON`을 반환하는 컨트롤러로 만들어 줍니다.
+ 예전에는 `@ResponseBody`를 각 메소드마다 선언했던 것을 한번에 사용할 수 있게 해준다고 생각하면 됩니다.

## @GetMapping
---
```java
@RestController
public class HelloController {

    @GetMapping("/hello") // <--
    public String hello(){
        return "hello";
    }
}
```

+ HTTP Method인 `Get`의 요청을 받을 수 있는 API를 만들어 줍니다.
+ 예전에는 `@RequestMapping(method = RequestMethod.GET)`으로 사용되었습니다.
+ 이제 이 프로젝트는 `/hello`로 요청이 오면 문자열 `hello`를 반환하는 기능을 가지게 되었습니다.

# Controller Test
* * *

## @RunWith(SpringRunner.class)
---

```java
@RunWith(SpringRunner.class) // <--
public class HelloControllerTest {
    
}
```

+ 테스트를 진행할 때 `JUnit`에 내장된 실행자 외에 다른 실행자를 실행시킵니다.
+ 여기서는 `SpringRunner`라는 실행자를 사용합니다.
+ 즉, 스프링 부트 테스트와 `JUnit` 사이에 연결자 역할을 합니다.

## @WebMvcTest
---

```java
@RunWith(SpringRunner.class)
@WebMvcTest(controllers = HelloController.class) // <--
public class HelloControllerTest {
    
}

```

+ 여러 스프링 테스트 어노테이션 중, Web(Spring MVC)에 집중할 수 있는 어노테이션입니다.
+ 선언할 경우 `@Controller`, `@ControllerAdvice` 등을 사용할 수 **있습니다**.
+ 단, `@Service`, `@Component`, `@Repository` 등은 사용할 수 **없습니다**.
+ 여기서는 컨트롤러만 사용하기 때문에 선언합니다.

## @Autowired
---

```java
@RunWith(SpringRunner.class)
@WebMvcTest(controllers = HelloController.class)
public class HelloControllerTest {

    @Autowired // <--
    private MockMvc mvc;
}

```

+ 스프링이 관리하는 빈(Bean)을 주입 받습니다.

## MockMvc
---

```java
@RunWith(SpringRunner.class)
@WebMvcTest(controllers = HelloController.class)
public class HelloControllerTest {

    @Autowired
    private MockMvc mvc; // <--

    @Test
    public void hello가_리턴된다() throws Exception{

        String hello = "hello";
        mvc.perform(get("/hello"))
        .andExpect(status().isOk())
        .andExpect(content().string(hello));
    }
}

```

+ 웹 API를 테스트할 때 사용합니다.
+ 스프링 MVC 테스트의 시작점입니다.
+ 이 클래스를 통해 HTTP `GET`, `POST` 등에 대한 API 테스트를 할 수 있습니다.

```java
mvc.perform(get("/hello"))
```

+ `MockMvc`를 통해 `/hello` 주소로 HTTP `GET` 요청을 합니다.
+ 체이닝이 지원되어 아래와 같이 여러 검증 기능을 이어서 선언할 수 있습니다.

```java
.andExpect(status().isOk())
```

+ `mvc.perform`의 결과를 검증합니다.
+ HTTP `Header`의 `Status`를 검증합니다.
+ 우리가 흔히 알고 있는 `200`, `404`, `500` 등의 상태를 검증합니다.
+ 여기선 `OK` 즉, `200`인지 아닌지를 검증합니다.

```java
.andExpect(content().string(hello))
```

+ mvc.perform의 결과를 검증합니다.
+ 응답 본문의 내용을 검증합니다.
+ Controller에서 "hello"를 리턴하기 때문에 이 값이 맞는지 검증합니다.