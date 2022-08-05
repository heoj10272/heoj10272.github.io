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


# Controller
* * *

## @RestController
---

```java
@RestController
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

    @GetMapping("/hello")
    public String hello(){
        return "hello";
    }
}
```
+ HTTP Method인 `Get`의 요청을 받을 수 있는 API를 만들어 줍니다.
+ 예전에는 `@RequestMapping(method = RequestMethod.GET)`으로 사용되었습니다.
+ 이제 이 프로젝트는 `/hello`로 요청이 오면 문자열 `hello`를 반환하는 기능을 가지게 되었습니다.

