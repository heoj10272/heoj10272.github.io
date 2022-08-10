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

# Auth
* * *

## @EnableWebSecurity
---

```java

@RequiredArgsConstructor
@EnableWebSecurity // <--
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    private final CustomOAuth2UserService customOAuth2UserService;

    @Override
    protected void configure(HttpSecurity http) throws Exception {

    }
}
```

+ `Spring Security` 설정들을 활성화시켜 줍니다.

## http
---
```java
@RequiredArgsConstructor
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    private final CustomOAuth2UserService customOAuth2UserService;

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
                .csrf().disable()
                .headers().frameOptions().disable()
                .and()
                .authorizeRequests()
                .antMatchers("/", "/css/**", "/images/**", "/js/**", "/h2-console/**", "/profile").permitAll()
                .antMatchers("/api/v1/**").hasRole(Role.USER.name())
                .anyRequest().authenticated()
                .and()
                .logout()
                .logoutSuccessUrl("/")
                .and()
                .oauth2Login()
                .userInfoEndpoint()
                .userService(customOAuth2UserService);
    }
}
```

### csrf().disable().headers().frameOptions().disable()

```java
.csrf().disable().headers().frameOptions().disable()
```

+ `h2-console` 화면을 사용하기 위해 해당 옵션들을 `disabled` 합니다.

### authorizeRequests

```java
.authorizeRequests()
```

+ `URL`별 권한 관리를 설정하는 옵션의 시작점입니다.
+ `authorizeRequests`가 선언되어야만 `antMatchers` 옵션을 사용할 수 있습니다.

### andMatchers

```java
.antMatchers("/", "/css/**", "/images/**", "/js/**", "/h2-console/**", "/profile").permitAll()
.antMatchers("/api/v1/**").hasRole(Role.USER.name())
```

+ 권한 관리 대상을 지정하는 옵션입니다.
+ `URL`, `HTTP 메소드`별로 관리가 가능합니다.
+ `"/"`등 지정된 `URL`들은 `permitAll()` 옵션을 통해 전체 열람 권한을 주었습니다.
+ `"api/v1/**"` 주소를 가진 API는 `USER` 권한을 가진 사람만 가능하도록 했습니다.

### anyRequest

```java
.anyRequest().authenticated()
```

+ 설정된 값들 이외 나머지 `URL`들을 나타냅니다.
+ 여기서는 `authenticated()`을 추가하여 나머지 `URL`들은 모두 인증된 사용자들에게만 허용하게 합니다.
+ 인증된 사용자 즉, 로그인한 사용자들을 이야기합니다.

### logout().logoutSuccessUrl("/")

```java
.logout()
.logoutSuccessUrl("/")
```

+ 로그아웃 기능에 대한 여러 설정의 진입점입니다.
+ 로그아웃 성공 시 `/` 주소로 이동합니다.

### oauth2Login

```java
.oauth2Login()
```

+ `OAuth 2` 로그인 기능에 대한 여러 설정의 진입점입니다.

### userInfoEndpoint()

```java
.userInfoEndpoint()
```

+ `OAuth 2` 로그인 성공 이후 사용자 정보를 가져올 때의 설정들을 담당합니다.

### userService

```java
.userService(customOAuth2UserService);
```

+ 소셜 로그인 성공 시 후속 조치를 진행할 `UserService` 인터페이스의 구현체를 등록합니다.
+ 리소스 서버(즉, 소셜 서비스들)에서 사용자 정보를 가져온 상태에서 추가로 진행하고자 하는 기능을 명시할 수 있습니다.

## CustomOAuth2UserService
---
```java
@RequiredArgsConstructor
@Service
public class CustomOAuth2UserService implements OAuth2UserService<OAuth2UserRequest, OAuth2User> {
    private final UserRepository userRepository;
    private final HttpSession httpSession;

    @Override
    public OAuth2User loadUser(OAuth2UserRequest userRequest) throws OAuth2AuthenticationException {
        OAuth2UserService delegate = new DefaultOAuth2UserService();
        OAuth2User oAuth2User = delegate.loadUser(userRequest);

        String registrationId = userRequest.getClientRegistration().getRegistrationId();
        String userNameAttributeName = userRequest.getClientRegistration().getProviderDetails()
                .getUserInfoEndpoint().getUserNameAttributeName();

        OAuthAttributes attributes = OAuthAttributes.of(registrationId, userNameAttributeName, oAuth2User.getAttributes());

        User user = saveOrUpdate(attributes);

        httpSession.setAttribute("user", new SessionUser(user));

        return new DefaultOAuth2User(
                Collections.singleton(new SimpleGrantedAuthority(user.getRoleKey())),
                attributes.getAttributes(),
                attributes.getNameAttributeKey());
    }


    private User saveOrUpdate(OAuthAttributes attributes) {
        User user = userRepository.findByEmail(attributes.getEmail())
                .map(entity -> entity.update(attributes.getName(), attributes.getPicture()))
                .orElse(attributes.toEntity());

        return userRepository.save(user);
    }
}
```
### registrationId

```java
String registrationId = userRequest.getClientRegistration().getRegistrationId();
```

+ 현재 로그인 진행 중인 서비스를 구분하는 코드입니다.
+ 지금은 `구글`만 사용하는 불필요한 값이지만, 이후 `네이버` 로그인 연동 시에 `네이버` 로그인인지, `구글` 로그인인지 구분하기 위해 사용합니다.

### userNameAttributeName

```java
String userNameAttributeName = userRequest.getClientRegistration().getProviderDetails()
                .getUserInfoEndpoint().getUserNameAttributeName();
```

+ `OAuth2` 로그인 진행 시 키가 되는 필드값을 이야기합니다. `Primary Key`와 같은 의미입니다.
+ `구글`의 경우 기본적으로 코드를 지원하지만, `네이버` `카카오` 등은 기본 지원하지 않습니다. `구글`의 경우 기본 코드는 `"sub"`입니다.
+ 이후 `네이버` 로그인과 `구글` 로그인을 동시 지원할 때 사용됩니다.

### OAuthAttributes
```java
OAuthAttributes attributes = OAuthAttributes.of(registrationId, userNameAttributeName, oAuth2User.getAttributes());
```

+ `OAuth2UserService`를 통해 가져온 `OAuth2user`의 `attribute`를 담을 클래스입니다.
+ 이후 `네이버` 등 다른 소셜 로그인도 이 클래스를 사용합니다.

### SessionUser

```java
httpSession.setAttribute("user", new SessionUser(user));
```

+ 세션에 사용자 정보를 저장하기 위한 `Dto` 클래스입니다.
+ 왜 `User` 클래스를 쓰지 않고 새로 만들어서 쓰는지 뒤이어서 상세하게 설명하겠습니다.

## @Target(ElementType.PARAMETER)
---
```java
@Target(ElementType.PARAMETER) // <--
@Retention(RetentionPolicy.RUNTIME)
public @interface LoginUser {

}
```

+ 이 어노테이션이 생성될 수 있는 위치를 지정합니다.
+ `PARAMETER`로 지정했으니 메소드의 파라미터로 선언된 객체에서만 사용할 수 있습니다.
+ 이 외에도 클래스 선언문에 쓸 수 있는 `TYPE` 등이 있습니다.

## @interface
---
```java
@Target(ElementType.PARAMETER)
@Retention(RetentionPolicy.RUNTIME)
public @interface LoginUser { // <--

}
```

+ 이 파일을 어노테이션 클래스로 지정합니다.
+ `LoginUser`라는 이름을 가진 어노테이션이 생성되었다고 보면 됩니다.

## supportsParameter()
---
```java
@RequiredArgsConstructor
@Component
public class LoginUserArgumentResolver implements HandlerMethodArgumentResolver {

    private final HttpSession httpSession;

    @Override
    public boolean supportsParameter(MethodParameter parameter) { // <--
        boolean isLoginUserAnnotation = parameter.getParameterAnnotation(LoginUser.class) != null;
        boolean isUserClass = SessionUser.class.equals(parameter.getParameterType());
        return isLoginUserAnnotation && isUserClass;
    }

    @Override
    public Object resolveArgument(MethodParameter parameter, ModelAndViewContainer mavContainer, NativeWebRequest webRequest, WebDataBinderFactory binderFactory) throws Exception {
        return httpSession.getAttribute("user");
    }
}
```

+ 컨트롤러 메서드의 특정 파라미터를 지원하는지 판단합니다.
+ 여기서는 파라미터에 `@LoginUser` 어노테이션이 붙어 있고, 파라미터 클래스 타입이 `SessionUser.class`인 경우 `true`를 반환합니다.

## resolveArgument()
---
```java
@RequiredArgsConstructor
@Component
public class LoginUserArgumentResolver implements HandlerMethodArgumentResolver {

    private final HttpSession httpSession;

    @Override
    public boolean supportsParameter(MethodParameter parameter) { 
        boolean isLoginUserAnnotation = parameter.getParameterAnnotation(LoginUser.class) != null;
        boolean isUserClass = SessionUser.class.equals(parameter.getParameterType());
        return isLoginUserAnnotation && isUserClass;
    }

    @Override
    public Object resolveArgument(MethodParameter parameter, ModelAndViewContainer mavContainer, NativeWebRequest webRequest, WebDataBinderFactory binderFactory) throws Exception { // <--
        return httpSession.getAttribute("user");
    }
}
```
+ 파라미터에 전달할 객체를 생성합니다.
+ 여기서는 세션에서 객체를 가져옵니다.

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

## @Enumerated(EnumType.STRING)
---
```java
@Getter
@NoArgsConstructor
@Entity
public class User extends BaseTimeEntity {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String name;

    @Column(nullable = false)
    private String email;

    @Column
    private String picture;

    @Enumerated(EnumType.STRING)
    @Column(nullable = false)
    private Role role;

    @Builder
    public User(String name, String email, String picture, Role role) {
        this.name = name;
        this.email = email;
        this.picture = picture;
        this.role = role;
    }

    public User update(String name, String picture) {
        this.name = name;
        this.picture = picture;

        return this;
    }

    public String getRoleKey() {
        return this.role.getKey();
    }
}
```

+ JPA로 데이터베이스를 저장할 때 `Enum` 값을 어떤 형태로 저장할지를 결정합니다.
+ 기본적으로는 `int`로 된 숫자가 지정됩니다.
+ 숫자로 지정되면 데이터베이스로 확인할 떄 그 값이 무슨 코드를 의미하는지 알 수가 없습니다.
+ 그래서 `문자열(EnumType.STRING)`로 저장될 수 있도록 선언합니다.

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

## findByEmail
---
```java
public interface UserRepository extends JpaRepository<User, Long> {

    Optional<User> findByEmail(String email); // <--
}
```

+ 소셜 로그인으로 반환되는 값 중 `email`을 통해 이미 생성된 사용자인지 처음 가입하는 사용자인지 판단하기 위한 메소드입니다.

# Repository Test
* * *

# Service
* * *

## postsRepository.delete(posts)
---

```java
@Transactional
    public void delete (Long id) {
        Posts posts = postsRepository.findById(id)
                .orElseThrow(() -> new IllegalArgumentException("해당 사용자가 없습니다. id=" + id));

        postsRepository.delete(posts);
    }
```

+ `JpaRepository`에서 이미 `delete` 메소드를 지원하고 있으니 이를 활용합니다.
+ 엔티티를 파라미터로 삭제할 수도 있고, `deleteById` 메소드를 이용하면 `id`로 삭제할 수도 있습니다.
+ 존재하는 `Posts`인지 확인을 위하 엔티티 조회 후 그대로 삭제합니다.


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

## @WithMockUser(roles="USER")
---
```java
@Test
@WithMockUser(roles="USER") // <--
    public void Posts_등록된다() throws Exception{
}
```
+ 인증된 모의(가짜) 사용자를 만들어서 사용합니다.
+ `roles`에 권한을 추가할 수 있습니다.
+ 즉, 이 어노테이션으로 인해 `ROLE_USER` 권한을 가진 사용자가 API를 요청하는 것과 동일한 효과를 가지게 됩니다.

## @Before
---
```java
@Before
    public void setup(){
        mvc = MockMvcBuilders
                .webAppContextSetup(context)
                .apply(springSecurity())
                .build();
    }
```
+ 매번 테스트가 시작되기 전에 `MockMvc` 인스턴스를 생성합니다.

## mvc.perform
---
```java
mvc.perform(post(url)
                .contentType(MediaType.APPLICATION_JSON_UTF8)
                .content(new ObjectMapper().writeValueAsString(requestDto)))
                .andExpect(status().isOk());
```
+ 생성된 `MockMvc`를 통해 API를 테스트합니다.
+ 본문(Body) 영역은 문자열로 표현하기 위해 `ObjectMapper`를 통해 문자열 `JSON`으로 변환합니다.

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

## OAuthAttributes
---

```java
@Getter
public class OAuthAttributes {
    private Map<String, Object> attributes;
    private String nameAttributeKey;
    private String name;
    private String email;
    private String picture;

    @Builder
    public OAuthAttributes(Map<String, Object> attributes, String nameAttributeKey, String name, String email, String picture) {
        this.attributes = attributes;
        this.nameAttributeKey = nameAttributeKey;
        this.name = name;
        this.email = email;
        this.picture = picture;
    }

    public static OAuthAttributes of(String registrationId, String userNameAttributeName, Map<String, Object> attributes) {

        return ofGoogle(userNameAttributeName, attributes);
    }

    private static OAuthAttributes ofGoogle(String userNameAttributeName, Map<String, Object> attributes) {
        return OAuthAttributes.builder()
                .name((String) attributes.get("name"))
                .email((String) attributes.get("email"))
                .picture((String) attributes.get("picture"))
                .attributes(attributes)
                .nameAttributeKey(userNameAttributeName)
                .build();
    }

    public User toEntity() {
        return User.builder()
                .name(name)
                .email(email)
                .picture(picture)
                .role(Role.GUEST)
                .build();
    }
}
```
### of()

```java
public static OAuthAttributes of(String registrationId, String userNameAttributeName, Map<String, Object> attributes) {

        return ofGoogle(userNameAttributeName, attributes);
    }
```

+ `OAuth2User`에서 반환하는 사용자 정보는 `Map`이기 때문에 값 하나하나를 변환해야만 합니다.

### toEntity()

```java
public User toEntity() {
    return User.builder()
            .name(name)
            .email(email)
            .picture(picture)
            .role(Role.GUEST)
            .build();
}
```

+ `User` 엔티티를 생성합니다.
+ `OAuthAttributes`에서 엔티티를 생성하는 시점은 처음 가입할 때입니다.
+ 가입할 때의 기본 권한을 `GUEST`로 주기 위해서 `role` 빌더값에는 `Role.GUEST`를 사용합니다.
+ `OAuthAttributes` 클래스 생성이 끝났으면 패키지에 `SessionUser` 클래스를 생성합니다.

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
{%raw%}{{>layout/header}}{%endraw%}
{%raw%}{{>layout/footer}}{%endraw%}
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

## {%raw%}{{#posts}}{%endraw%}
---

```java
{%raw%}{{>layout/header}}{%endraw%}

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
            {%raw%}{{#posts}}{%endraw%} // <--
                <tr>
                    <!-- List에서 뽑아낸 객체의 필드를 사용함 -->
                    <td>{%raw%}{{id}}{%endraw%}</td>
                    <td>{%raw%}{{title}}{%endraw%}</td>
                    <td>{%raw%}{{author}}{%endraw%}</td>
                    <td>{%raw%}{{modifiedDate}}{%endraw%}</td>
                </tr>
            {%raw%}{{/posts}}{%endraw%}
            </tbody>
        </table>
    </div>
{%raw%}{{>layout/footer}}{%endraw%}
```

+ `posts`라는 `List`를 순회합니다.
+ `java`의 `for문`과 동일하게 생각하면 됩니다.

## {%raw%}{{변수명}}{%endraw%}
---
```java
{%raw%}{{>layout/header}}{%endraw%}

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
            {%raw%}{{#posts}}{%endraw%}
                <tr>
                    <!-- List에서 뽑아낸 객체의 필드를 사용함 -->
                    <td>{%raw%}{{id}}{%endraw%}</td> // <--
                    <td>{%raw%}{{title}}{%endraw%}</td> // <--
                    <td>{%raw%}{{author}}{%endraw%}</td> // <--
                    <td>{%raw%}{{modifiedDate}}{%endraw%}</td> // <--
                </tr>
            {%raw%}{{/posts}}{%endraw%}
            </tbody>
        </table>
    </div>
{%raw%}{{>layout/footer}}{%endraw%}
```
+ List에서 뽑아낸 객체의 필드를 사용합니다.

## {%raw%}{{post.id}}{%endraw%}
---

```java
{%raw%}{{>layout/header}}{%endraw%}
<h1>게시글 수정</h1>

<div class="col-md-12">
    <div class="col-md-4">
        <form>
            <div class="form-group">
                <label for="title">글 번호</label>
                <input type="text" class="form-control" id="id" value="{{post.id}}" readonly> // <--
            </div>
            <div class="form-group">
                <label for="title">제목</label>
                <input type="text" class="form-control" id="title" value="{{post.title}}"> // <--
            </div>
            <div class="form-group">
                <label for="author"> 작성자 </label>
                <input type="text" class="form-control" id="author" value="{{post.author}}" readonly> // <--
            </div>
            <div class="form-group">
                <label for="content"> 내용 </label>
                <textarea class="form-control" id="content">{%raw%}{{post.content}}{%endraw%}</textarea>
            </div>
        </form>
        <a href="/" role="button" class="btn btn-secondary">취소</a>
        <button type="button" class="btn btn-primary" id="btn-update">수정 완료</button>
        <button type="button" class="btn btn-danger" id="btn-delete">삭제</button>
    </div>
</div>
{%raw%}{{>layout/footer}}{%endraw%}
```

+ 머스테치는 객체의 필드 접근 시 점(Dot)으로 구분합니다.
+ 즉, `Post` 클래스의 `id`에 대한 접근은 `post.id`로 사용할 수 있습니다.

### readOnly

```java
<input type="text" class="form-control" id="id" value="{{post.id}}" readonly>
<input type="text" class="form-control" id="author" value="{{post.author}}" readonly>
```

+ `Input` 태그에 읽기 가능만 허용하는 속성입니다.
+ `id`와 `author`는 수정할 수 없도록 읽기만 허용하도록 추가합니다.

## $('#btn-update').on('click')
---
```java
var main = {
    init : function () {
        var _this = this;
        $('#btn-save').on('click', function () { // <--
            _this.save();
        });
        $('#btn-update').on('click', function () { // <--
            _this.update();
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
            window.location.href = '/';
        }).fail(function (error) {
            alert(JSON.stringify(error));
        });
    },
    update : function () {
        var data = {
            title: $('#title').val(),
            content: $('#content').val()
        };

        var id = $('#id').val();

        $.ajax({
            type: 'PUT',
            url: '/api/v1/posts/'+id,
            dataType: 'json',
            contentType:'application/json; charset=utf-8',
            data: JSON.stringify(data)
        }).done(function() {
            alert('글이 수정되었습니다.');
            window.location.href = '/';
        }).fail(function (error) {
            alert(JSON.stringify(error));
        });
    }
};
main.init();
```

+ `btn-update`란 `id`를 가진 HTML 엘리먼트에 `click` 이벤트가 발생할 때 `update function`을 실행하도록 이벤트를 등록합니다.

## ajax
---
```java
var main = {
    init : function () {
        var _this = this;
        $('#btn-save').on('click', function () {
            _this.save();
        });
        $('#btn-update').on('click', function () { 
            _this.update();
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
            window.location.href = '/';
        }).fail(function (error) {
            alert(JSON.stringify(error));
        });
    },
    update : function () {
        var data = {
            title: $('#title').val(),
            content: $('#content').val()
        };

        var id = $('#id').val();

        $.ajax({
            type: 'PUT', // <--
            url: '/api/v1/posts/'+id, // <--
            dataType: 'json',
            contentType:'application/json; charset=utf-8',
            data: JSON.stringify(data)
        }).done(function() {
            alert('글이 수정되었습니다.');
            window.location.href = '/';
        }).fail(function (error) {
            alert(JSON.stringify(error));
        });
    }
};
main.init();
```
### type:'PUT'

```java
type: 'PUT'
```

+ 여러 `HTTP Method` 중 `PUT` 메소드를 선택합니다.
+ `PostsApiController`에 있는 API에서 이미 `@PutMapping`으로 선언했기 때문에 `PUT`을 사용해야 합니다. 
+ 참고로 이는 `REST` 규약에 맞게 설정된 것입니다.
+ `REST`에서 `CRUD`는 다음과 같이 `HTTP Method`에 매핑됩니다.
    - 생성(Create) - `POST`
    - 읽기(Read) - `GET`
    - 수정(Update) - `PUT`
    - 삭제(Delete) - `DELETE`

### url: '/api/v1/posts/'+id

```java
url: '/api/v1/posts/'+id
```
+ 어느 게시글을 수정할지 `URL Path`로 구분하기 위해 `Path`에 `id`를 추가합니다.

## {%raw%}{{#userName}}{%endraw%}
---
```java
{%raw%}{{#userName}}{%endraw%}
    Logged in as: <span id="user">{%raw%}{{userName}}{%endraw%}</span>
    <a href="/logout" class="btn btn-info active" role="button">Logout</a>
{%raw%}{{/userName}}{%endraw%}
```
+ 머스테치는 다른 언어와 같은 `if문(if userName != null 등)`을 제공하지 않습니다.
+ `true/false` 여부만을 판단할 뿐입니다.
+ 그래서 머스테치에서는 항상 최종값을 넘겨줘야 합니다. 
+ 여기서도 역시 `userName`이 있다면 `userName`을 노출시키도록 구성했습니다.

### a href="/logout"

```java
<a href="/logout" class="btn btn-info active" role="button">Logout</a>
```

+ 스프링 시큐리티에서 기본적으로 제공하는 로그아웃 `URL`입니다.
+ 즉, 개발자가 별도로 저 `URL`에 해당하는 컨트롤러를 만들 필요가 없습니다.
+ `SecurityConfig` 클래스에서 `URL`을 변경할 순 있지만 기본 `URL`을 사용해도 충분하니 여기서는 그대로 사용합니다.

## {%raw%}{{^userName}}{%endraw%}
---
```java
{%raw%}{{^userName}}{%endraw%}
    <a href="/oauth2/authorization/google" class="btn btn-success active" role="button">Google Login</a>
{%raw%}{{/userName}}{%endraw%}
```
+ 머스테치에서 해당 값이 존재하지 않는 경우에는 `^`을 사용합니다.
+ 여기서는 `userName`이 없다면 로그인 버튼을 노출시키도록 구성했습니다.

### a href="/oauth2/authorization/google"
```java
<a href="/oauth2/authorization/google" class="btn btn-success active" role="button">Google Login</a>
```
+ 스프링 시큐리티에서 기본적으로 제공하는 로그인 `URL`입니다.
+ 로그아웃 `URL`과 마찬가지로 개발자가 별도의 컨트롤러를 생성할 필요가 없습니다.