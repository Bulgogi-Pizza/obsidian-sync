# IoC 컨테이너

- Inversion Of Control 컨테이너
- = bean container
- = DI(dependency injection) 컨테이너

## IoC
- 제어의 역전
	- Dependency Injection
	- Event Listener

각 객체가 의존하는 객체를 자동으로 주입해 줌
-> "의존 객체 주입(dependency injection; DI)"

## Spring IoC 컨테이너

- spring.io 사이트에서 제공하는 프레임워크

### ApplicationContext 인터페이스

- 스프링 IoC 컨테이너의 사용 규칙을 정의한 인터페이스
- 모든 스프링 IoC 컨테이너는 이 규칙에 따라 정의되어 있음

### Application Context 구현체(implements, 인터페이스를 구현한 클래스 또는 그 클래스의 인스턴스)의 종류

1. XML 파일에서 설정 정보를 읽어들이는 IoC 컨테이너
	- ClassPathXmlApplicationContext
		- 설정 파일을 자바 CLASSPATH 경로에서 찾음
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.springframework.org/schema/beans
https://www.springframework.org/schema/beans/spring-beans.xsd">

<!-- 여기에 Spring Framework의 설정 정보를 기술한다. -->

</beans>
<!-- :a -> alias, 없다면 기본 네임스페이스에 소속된 태그라는 뜻 -->
<a:beans xmlns:a="http://www.springframework.org/schema/beans" >

	<a:bean>
	</a:bean>

</a:beans>
```
xmlns = xml name space, alias없이 선언됨, 기본 네임스페이스에 소속된 태그라는 뜻 (네임스페이스들은 하나의 default 태그를 가질 수 있음)
xmlms:xsi = xsi 라는 alias 내에서 소속됨
xsi:schemaLocation = 
	- FileSystemXmlApplicationContext
		- 설정 파일을 OS 경로에서 찾음.

2. 자바 클래스 파일의 애노테이션에서 설정 정보를 읽어들이는 IoC 컨테이너
	- AnnotationConfigApplicationContext
		- 설정 정보를 자바 클래스에서 찾음
```java
package study.spring.ioc.ex01.e;
  
import org.springframework.context.annotation.Bean;
import study.spring.ioc.ex01.Car;
  
// 클래스 선언부에 애노테이션으로 스프링 설정에 관한 정보를 지정할 수 있다.
public class AppConfig {
  
	// 객체 생성
	// 꼭 Bean을 써야 자동으로 Bean에 등록해줌
	@Bean
	public Car c1() {
		return new Car();
	}
}
```

```xml
<bean id="c1" class="com.eomcs.spring.ioc.ex01.Car"/>
<!-- fully-qulifiedname = FQName = QName
패키지명을 포함한 클래스 명 -->
```

```java
Car obj = new Car();
beanContainer.put("c1", obj);
```

위 두개의 코드는 같은 작업을 수행시킴

org.springframework.context.annotation.internalConfigurationAnnotationProcessor = org.springframework.context.annotation.ConfigurationClassPostProcessor
- @Configuration으로 정의된 클래스를 분석
- @Bean 등록

org.springframework.context.annotation.internalAutowiredAnnotationProcessor = org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor
- @Value 처리
- @Autowired 처리

org.springframework.context.annotation.internalCommonAnnotationProcessor = org.springframework.context.annotation.CommonAnnotationBeanPostProcessor
- Java EE의 공통 어노테이션(@PostConstruct, @PreDestroy, @Resource)을 처리

org.springframework.context.event.internalEventListenerFactory = org.springframework.context.event.DefaultEventListenerFactory



















```java
package hello.hello_spring.controller;  
  
import org.springframework.stereotype.Controller;  
import org.springframework.ui.Model;  
import org.springframework.web.bind.annotation.GetMapping;  
  
@Controller  // Web Application에서 첫 번째 진입점
public class HelloController {  
  
  @GetMapping("hello")  
  public String hello(Model model) {  
    model.addAttribute("data", "hello!");  
    return "hello";  
  }  
}
```

@Controller
- Web Applicaion에서 첫 번째 진입점

@GetMapping(URL)
- Web App.에서 URL에 접속하면 해당 Annotation에 접근함
- Get

Model
- Model View Controller 에서의 Model

templates/hello.html
```HTML
<!DOCTYPE HTML>  
<html xmlns:th="http://www.thymeleaf.org">  
<head>  
  <title>Hello</title>  
  <meta content="text/html; charset=UTF-8" http-equiv="Content-Type"/>  
</head>  
<body>  
<p th:text="'안녕하세요. ' + ${data}">안녕하세요. 손님</p>  
</body>  
</html>
```

th
- thymeleaf의 th

```HTML
<html xmlns:th="http://www.thymeleaf.org"> 
```
- thymeleaf 문법을 사용할 수 있게 해줌

```HTML
<p th:text="'안녕하세요. ' + ${data}">안녕하세요. 손님</p>
```
- ${data}에 model.addAttribute("data", "hello!"); 에서 지정해줬듯, "data"에 "hello!"가 치환되어서 들어감


# 빌드와 실행

콘솔로 이동
1. `./gradlew build
2. `cd build/libs
3. `java -jar hello-spring-0.0.1-SNAPSHOT.jar
4. 실행 확인
# MVC와 템플릿엔진
Model View Controller
서버에서 만들어준 뒤에 클라이언트에게 보내주는 방식

브라우저의 URL -> @GetMapping(URL) -> return String
String -> templates/String.html 파일로 연결
String.html 파일 렌더링 후 웹 브라우저에 전송

```java
@Controller
public class HelloController {
    @GetMapping("hello-mvc")
	public String helloMvc(@RequestParam("name") String name, Model model) {         model.addAttribute("name", name);
	return "hello-template";
    } }
```

### GoF의 Facade(퍼사드)패턴이 적용된 것

\<\<Front Controller>>
DispatcherServlet
- 클라이언트 요청을 접수
	- 요청을 처할 페이지 컨트롤러에 전달
	- 뷰컴포넌트 실행
	- 요청처리와 관련된 객체를 IoC컨테이너를 이용해 관리

\<\<Page Controller>>
Controller
- 요청 처리 담당
	- 클라이언트가 보낸 데이터를 가공
	- 적절한 서비스 컴포넌트 실행
	- 결과 데이터를 뷰 컴포넌트가 쓸 수 있도록 가공

ViewResolver
- 뷰 이름으로 뷰 컴포넌트를 찾는다
	- 뷰 컴포넌트 리턴

View
- 클라이언트에게 보낼 콘텐츠를 생성

### -> Page Controller 동작

1. Call -> \<\<PageController>> Controller
	1. 요청 데이터 가공
2. Call -> Service
	1. 업무로직 수행
	2. 트랜잭션 제어
	3. 결과데이터 조립
3. Call -> DAO
	1. DBMS로부터 데이터 조회
	2. 데이터 변경
4. SQL -> DBMS
5. return -> DAO
6. 생성 -> Domain
	1. 클라이언트가 콘텐츠를 만들 때 사용할 데이터
7. return -> Service
8. 조립 -> Domain
9. return -> Service
10. return -> Controller
11. 도메인 객체 보관 -> Model
	1. 도메인 객체 보관
	2. 결과를 사용할 데이터 가공 및 보관
		1. 뷰 컴포넌트가 사용하기 좋게 데이터를 가공
12. view name

### -> View Component 동작

-> 요청
1. DispatcherServlet
2. call -> Controller
3. 보관 -> Model 
4. view name return -> DispatcherServlet
5. Model 객체에 보관된 데이터를 옮긴다 -> ServletRequest
6. View 컴포넌트 요청 -> ViewResolver
7. **return -> View**
8. **DispatcherServlet -> 실행 -> View**
9. **View -> 사용 -> ServletRequest**
10. **View -> 컨텐츠 생성 -> View**
<- 응답


### DispatcherServlet 설정

DispatcherServlet -> 생성 -> XmlWebApplicationContext
- DispatcherServlet은 자체적으로 XmlWebApplicationContext를 가지고 있음
- 파라미터를 사용해 IoC컨테이너의 설정 파일을 지정해야 함
- 초기화 파라미터명 : contextConfigLocation
- 초기화 파라미터값 : 예) /WEB-INF/app-servlet.xml
- 설정하고 싶지 않다면 init-value를 비우기

XmlWebApplicationContext
- 페이지 컨트롤러 객체 보관
- 웹 관련 객체 보관
- IoC컨테이너 생성 시 설정 파일 참조 (app-servlet.xml)

app-servlet.xml
- IoC 컨테이너 설정파일
# Spring 웹 개발에서 API

정적 방식에서 뷰를 찾아서 정적 컨텐츠를 보내주는 방식
vs
API라는 방식으로 데이터를 바로 내리는 방식

```java
@Controller
public class HelloController {
    @GetMapping("hello-string")
    @ResponseBody //html의 바디에 바로 쏴버림
	public String helloString(@RequestParam("name") String name) { return "hello " + name;
    }
}
```
html의 바디 부분에 hello + name을 직접 쏴버림

Spring
	객체를 받아서 바로 반환하면 JSON 방식으로 뿌리는 것이 default
	예전 레거시 코드의 경우 XML로 받기도 하는데 그건 예전임

# @ResponseBody 사용 원리

웹 브라우저에서 URL로 연결
-> Spring @GetMapping(URL)로 연결
-> @ResponseBody 발견 시 HTML의 body 에 바로 데이터를 던져야 겠구나 함
-> HttpMEssageConverter라는 친구가 반응함
	- StringConverter or JsonConverter(객체의 경우)
-> 객체 반환 시 JSON형태, String은 그대로 String로 HTML의 body에 전송

# 비즈니스 요구사항 정리

데이터 : 회원 ID, 이름
기능 : 회원 등록, 조회

### 일반적인 웹 애플리케이션 계층 구조

컨트롤러
- 웹MVC의 컨트롤러 역할
서비스
- 핵심 비즈니스 로직 구현
리포지토리
- 데이터베이스에 접근, 도메인 객체를 DB에 저장하고 관리
도메인
- 비즈니스 도메인 객체, 예) 회원, 주문, 쿠폰 등등 주로 데이터베이스에 저장하고 관리됨

# 회원 리포지토리 테스트 케이스 작성

기존
1. 자바의 main 메서드 통해서 실행
2. 웹앱의 컨트롤러로 해당 기능을 실행

-> 준비와 실행이 너무 오래걸림
-> 반복 실행이 어려움
-> 여러 테스트를 한번에 실행하기 어려움

해결
JUnit이라는 프레임워크로 테스트 실행

@Test
-> 테스트 작성

@AfterEach
-> 각 테스트가 끝난 후 실행 (초기화 등의 행위)