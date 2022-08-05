---
layout: post
title: "[Spring] @Annotation, Method 목록"
subtitle: Spring
date: '2022-8-2 03:00:00 +0900'
category: study
tags: web spring
image:
  path: /assets/img/study_Web/2022-08-05-[Spring]_@Annotation_목록/logo.png
---

Spring @Annotation, Method 목록

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

## @EnableJpaAuditing
---
```java
@EnableJpaAuditing // <--
@SpringBootApplication
public class Application {
    public static void main(String[] args){
        SpringApplication.run(Application.class, args);
    }
}
```

+ JPA `Auditing` 어노테이션들을 모두 활성화할 수 있게 해주는 활성화 어노테이션입니다.

# Entity
* * *

## @Entity
---

```java
@Entity // <--
public class Posts extends BaseTimeEntity {

}
```
+ 테이블과 링크될 클래스임을 나타냅니다.
+ 기본값으로 클래스의 카멜케이스 이름을 언더스코어 네이밍(_)으로 테이블 이름을 매칭합니다.
+ ex) `SalesManager.java` -> `sales_manager table`

## @id
---

```java
@Entity
public class Posts extends BaseTimeEntity {
    
    @Id // <--
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id; 

}
```

+ 해당 테이블의 `PK` 필드를 나타냅니다.

## @GeneratedValue
---

```java
@Entity
public class Posts extends BaseTimeEntity {
    
    @Id // <--
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id; 

}
```

+ `PK`의 생성 규칙을 나타냅니다.
+ 스프링 부트 2.0 에서는 `GenerationType.IDENTITY` 옵션을 추가해야만 `auto_increment`가 됩니다.

## @Column
---

```java
@Entity
public class Posts extends BaseTimeEntity {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id; 
    
    @Column(length = 500, nullable = false) // <--
    private String title;
    
    @Column(columnDefinition = "TEXT", nullable = false) // <--
    private String content;
    private String author;
}
```

+ 테이블의 `칼럼`을 나타내며 굳이 선언하지 않아도 해당 클래스의 필드는 모두 `칼럼`이 됩니다.
+ 사용하는 이유는, 기본값 외에 추가로 변경이 필요한 옵션이 있으면 사용합니다.
+ 문자열의 경우 `VARCHAR(255)`가 기본값인데, 사이즈를 `500`으로 늘리고 싶거나(ex: title), 타입을 `TEXT`로 변경하고 싶거나(ex: content)등의 경우에 사용합니다.


## @NoArgsConstructor
---

```java
@NoArgsConstructor
@Entity
public class Posts extends BaseTimeEntity {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id; 
    

    @Column(length = 500, nullable = false)
    private String title;
    
    @Column(columnDefinition = "TEXT", nullable = false)
    private String content;
    private String author;
}
```

+ 기본 생성자 자동 추가
+ `public Posts(){}`와 같은 효과

## @Getter
---

```java
@Getter
@NoArgsConstructor
@Entity
public class Posts extends BaseTimeEntity {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id; 
    

    @Column(length = 500, nullable = false)
    private String title;
    
    @Column(columnDefinition = "TEXT", nullable = false)
    private String content;
    private String author;
}
```

+ 클래스 내 모든 필드의 `Getter` 메소드를 자동생성

## @Builder
---

```java
@Getter
@NoArgsConstructor
@Entity
public class Posts extends BaseTimeEntity {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id; 
    

    @Column(length = 500, nullable = false)
    private String title;
    
    @Column(columnDefinition = "TEXT", nullable = false)
    private String content;
    private String author;

    @Builder
    public Posts(String title, String content, String author){
        this.title = title;
        this.content = content;
        this.author = author;
    }
}
```

+ 해당 클래스의 빌더 패턴 클래스를 생성
+ 생성자 상단에 선언 시 생성자에 포함된 필드만 빌더에 포함

## @MappedSuperclass
---
```java
@Getter
@MappedSuperclass // <-- 
@EntityListeners(AuditingEntityListener.class)
public class BaseTimeEntity {

    @CreatedDate
    private LocalDateTime createdDate;

    @LastModifiedDate
    private LocalDateTime modifiedDate;
}
```

+ JPA `Entity` 클래스들이 `BaseTimeEntity`을 상속할 경우 필드들(`createdDate`, `modifiedDate`)도 칼럼으로 인식하도록 합니다.

## @EntityListeners(AuditingEntityListener.class)
---
```java
@Getter
@MappedSuperclass 
@EntityListeners(AuditingEntityListener.class) // <-- 
public class BaseTimeEntity {

    @CreatedDate
    private LocalDateTime createdDate;

    @LastModifiedDate
    private LocalDateTime modifiedDate;
}
```

+ `BaseTimeEntity` 클래스에 `Auditing` 기능을 포함시킵니다.

## @CreatedDate
---
```java
@Getter
@MappedSuperclass 
@EntityListeners(AuditingEntityListener.class) 
public class BaseTimeEntity {

    @CreatedDate // <-- 
    private LocalDateTime createdDate;

    @LastModifiedDate
    private LocalDateTime modifiedDate;
}
```

+ `Entity`가 생성되어 저장될 때 시간이 저장됩니다.

## @LastModifiedDate
---
```java
@Getter
@MappedSuperclass 
@EntityListeners(AuditingEntityListener.class) 
public class BaseTimeEntity {

    @CreatedDate 
    private LocalDateTime createdDate;

    @LastModifiedDate // <-- 
    private LocalDateTime modifiedDate;
}
```

+ 조회한 `Entity`의 값을 변경할 때 시간이 자동 저장됩니다.


# Repository
* * *

## @Query
---

```java
public interface PostsRepository extends JpaRepository<Posts, Long> {

    @Query("SELECT p FROM Posts p ORDER BY p.id DESC") // <--
    List<Posts> findAllDesc();
}
```

+  `SpringDataJpa`에서 제공하지 않는 메소드는 위처럼 쿼리로 작성해도 된다.

# Repository Test
* * *

## @SpringBootTest
---

```java
@RunWith(SpringRunner.class)
@SpringBootTest
public class PostsRepositoryTest {

}
```

+ 별다른 설정 없이 `@SpringBootTest`를 사용할 경우 `H2` 데이터베이스를 자동으로 실행해 줍니다.


## @After
---

```java
@RunWith(SpringRunner.class)
@SpringBootTest
public class PostsRepositoryTest {

    @Autowired
    PostsRepository postsRepository;

    @After // <--
    public void cleanup(){
        postsRepository.deleteAll();
    }
}
```

+ `Junit`에서 단위 테스트가 끝날 때마다 수행되는 메소드를 지정
+ 보통은 배포 전 전체 테스트를 수행할 때 테스트간 데이터 침범을 막기 위해 사용합니다.
+ 여러 테스트가 동시에 수행되면 테스트용 데이터베이스인 `H2`에 데이터가 그대로 남아 있어 다음 테스트 실행 시 테스트가 실패할 수 있습니다.

## @postsRepository
---

```java
@RunWith(SpringRunner.class)
@SpringBootTest
public class PostsRepositoryTest {

    @Autowired
    PostsRepository postsRepository;

    @After
    public void cleanup(){
        postsRepository.deleteAll();
    }

    @Test
    public void 게시글저장_불러오기(){

        //given
        String title = "테스트 게시글";
        String content = "테스트 본문";

        postsRepository.save(Posts.builder() // <--
                .title(title)
                .content(content)
                .author("heoj10272@gmail.com")
                .build());

        //when
        List<Posts> postsList = postsRepository.findAll(); // <--

        // then
        Posts posts = postsList.get(0);
        assertThat(posts.getTitle()).isEqualTo(title);
        assertThat(posts.getContent()).isEqualTo(content);
    }
}
```

### save

```java
postsRepository.save(Posts.builder()
                .title(title)
                .content(content)
                .author("heoj10272@gmail.com")
                .build());
```

+ 테이블 `posts`에 `insert/update` 쿼리를 실행합니다.
+ `id` 값이 있다면 `update`가, 없다면 `insert` 쿼리가 실행됩니다.

### findAll

```java
List<Posts> postsList = postsRepository.findAll();
```

+ 테이블 `posts`에 있는 모든 데이터를 조회해오는 메소드입니다.

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

## Model
---
```java
@RequiredArgsConstructor
@Controller
public class indexController {

    private final PostsService postsService;
    
    @GetMapping("/")
    public String index(Model model){ // <--
        model.addAttribute("posts", postsService.findAllDesc());
        return "index";
    }

    @GetMapping("/posts/save")
    public String postsSave() {
        return "posts-save";
    }
}
```
+ 서버 템플릿 엔진에서 사용할 수 있는 객체를 저장할 수 있습니다.
+ 여기서는 `postsService.findAllDesc()`로 가져온 결과를 `posts`로 `index.mustache`에 전달합니다.

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

## @RequestParam
---

```java
@RestController
public class HelloController {

    @GetMapping("/hello/dto")
    public HelloResponseDto helloDto(@RequestParam("name") String name, @RequestParam("amount") int amount) { // <--
        return new HelloResponseDto(name, amount);
    }
}
```

+ 외부에서 API로 넘긴 파라미터를 가져오는 어노테이션입니다.
+ 여기서는 외부에서 `name (@RequestParam("name"))`이란 이름으로 넘긴 파라미터를 메소드 파라미터 `name(String name)`을 저장하게 됩니다.

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

    @Test
    public void helloDto가_리턴된다() throws Exception{
        String name = "hello";
        int amount = 1000;

        mvc.perform(
                get("/hello/dto")
                        .param("name",name) 
                        .param("amount",String.valueOf(amount))) 
                .andExpect(status().isOk())
                .andExpect(jsonPath("$.name", is(name)))
                .andExpect(jsonPath("$.amount", is(amount)));
    }
}

```

+ 웹 API를 테스트할 때 사용합니다.
+ 스프링 MVC 테스트의 시작점입니다.
+ 이 클래스를 통해 HTTP `GET`, `POST` 등에 대한 API 테스트를 할 수 있습니다.

### perform

```java
mvc.perform(get("/hello"))
```

+ `MockMvc`를 통해 `/hello` 주소로 HTTP `GET` 요청을 합니다.
+ 체이닝이 지원되어 아래와 같이 여러 검증 기능을 이어서 선언할 수 있습니다.

### andExpect

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

+ `mvc.perform`의 결과를 검증합니다.
+ 응답 본문의 내용을 검증합니다.
+ `Controller`에서 `"hello"`를 리턴하기 때문에 이 값이 맞는지 검증합니다.

### param

```java
.param("name",name) 
.param("amount",String.valueOf(amount))
```

+ API 테스트할 때 사용될 요청 파라미터를 설정합니다.
+ 단, 값은 `String`만 허용됩니다.
+ 그래서 숫자/날짜 등의 데이터도 등록할 때는 문자열로 변경해야만 합니다.

### jsonPath

```java
.andExpect(jsonPath("$.name", is(name)))
.andExpect(jsonPath("$.amount", is(amount)));
```

+ `JSON` 응답값을 필드별로 검증할 수 있는 메소드입니다.
+ `$`를 기준으로 필드명을 명시합니다.
+ 여기서는 `name`과 `amount`를 검증하니 `$.name`, `$.amount`로 검증합니다.

# DTO
* * *

## @Getter
---

```java
@Getter // <--
@RequiredArgsConstructor
public class HelloResponseDto {
    
    private final String name;
    private final int amount;
}
```

+ 선언된 모든 필드의 get 메소드를 생성해 줍니다.

## @ReqiredArgsConstructor
---

```java
@Getter
@RequiredArgsConstructor // <--
public class HelloResponseDto {
    
    private final String name;
    private final int amount;
}

```

+ 선언된 모든 `final` 필드가 포함된 생성자를 생성해 줍니다.
+ `final`이 없는 필드는 생성자에 포함되지 않습니다.

# DTO Test
* * *

## assertThat
---

```java
public class HelloResponseDtoTest {

    @Test
    public void 롬복_기능_테스트(){
        //given
        String name = "test";
        int amount = 1000;

        //when
        HelloResponseDto dto = new HelloResponseDto(name, amount);

        //then
        assertThat(dto.getName()).isEqualTo(name); // <--
        assertThat(dto.getAmount()).isEqualTo(amount); // <--
    }
}
```

+ `assertj`라는 테스트 검증 라이브러리의 검증 메소드입니다.
+ 검증하고 싶은 대상을 메소드 인자로 받습니다.
+ 메소드 체이닝이 지원되어 `isEqualTo`와 같이 메소드를 이어서 사용할 수 있습니다.

```java
assertThat(dto.getName()).isEqualTo(name);
```

+ `assertj`의 동등 비교 메소드입니다.
+ `assertThat`에 있는 값과 `isEqualTo`의 값을 비교해서 같을 때만 성공입니다.

# Mustache
* * *

## layout/header, layout/footer
---
```java
{{>layout/header}}
{{>layout/footer}}
```

+ `{{> }}`는 현재 `머스테치 파일(index.mustache)`을 기준으로 다른 파일을 가져옵니다.

## window.location.href
---
```java
var main = {
    init : function () {
        var _this = this;
        $('#btn-save').on('click', function () {
            _this.save();
        });
    },
    save : function () {
        var data = {
            title: $('#title').val(),
            author: $('#author').val(),
            content: $('#content').val()
        };

        $.ajax({
            type: 'POST',
            url: '/api/v1/posts',
            dataType: 'json',
            contentType:'application/json; charset=utf-8',
            data: JSON.stringify(data)
        }).done(function() {
            alert('글이 등록되었습니다.');
            window.location.href = '/'; // <--
        }).fail(function (error) {
            alert(JSON.stringify(error));
        });
    }
};
main.init();
```

+ 글 등록이 성공하면 메인페이지(/)로 이동합니다.

## {{#posts}}
---

```java
{{>layout/header}}

    <h1>스프링 부트로 시작하는 웹 서비스 Ver. 2</h1>
    <div class="col-md-12">
        <div class="row">
            <div class="col-md-6">
                <a href="/posts/save" role="button"
                   class="btn btn-primary">글 등록</a>
            </div>
        </div>
        <br>
        <!-- 목록 출력 영역 -->
        <table class="table table-horizontal table-bordered">
            <thead class="thead-strong">
            <tr>
                <th>게시글번호</th>
                <th>제목</th>
                <th>작성자</th>
                <th>최종수정일</th>
            </tr>
            </thead>
            <tbody id="tbody">
            <!-- posts라는 List를 순회함 -->
            <!-- Java의 for문과 동일하게 생각하면 됨 -->
            {{#posts}} // <--
                <tr>
                    <!-- List에서 뽑아낸 객체의 필드를 사용함 -->
                    <td>{{id}}</td>
                    <td>{{title}}</td>
                    <td>{{author}}</td>
                    <td>{{modifiedDate}}</td>
                </tr>
            {{/posts}}
            </tbody>
        </table>
    </div>
{{>layout/footer}}
```

+ `posts`라는 `List`를 순회합니다.
+ `java`의 `for문`과 동일하게 생각하면 됩니다.

## {{변수명}}
---
```java
{{>layout/header}}

    <h1>스프링 부트로 시작하는 웹 서비스 Ver. 2</h1>
    <div class="col-md-12">
        <div class="row">
            <div class="col-md-6">
                <a href="/posts/save" role="button"
                   class="btn btn-primary">글 등록</a>
            </div>
        </div>
        <br>
        <!-- 목록 출력 영역 -->
        <table class="table table-horizontal table-bordered">
            <thead class="thead-strong">
            <tr>
                <th>게시글번호</th>
                <th>제목</th>
                <th>작성자</th>
                <th>최종수정일</th>
            </tr>
            </thead>
            <tbody id="tbody">
            <!-- posts라는 List를 순회함 -->
            <!-- Java의 for문과 동일하게 생각하면 됨 -->
            {{#posts}}
                <tr>
                    <!-- List에서 뽑아낸 객체의 필드를 사용함 -->
                    <td>{{id}}</td> // <--
                    <td>{{title}}</td> // <--
                    <td>{{author}}</td> // <--
                    <td>{{modifiedDate}}</td> // <--
                </tr>
            {{/posts}}
            </tbody>
        </table>
    </div>
{{>layout/footer}}
```
+ List에서 뽑아낸 객체의 필드를 사용합니다.