# Web Browser
- chrome
- safari
- edge
- whale
- firefox

# Web Server

Web Server (단순 웹서버)
- Apache HTTP 서버
- Nginx
- IIS

WebBrowser (HTTP Client) <--HTTP 요청, HTTP 응답--> Web Server (HTTP Server) -> WebResource (정적 자원)

WebResource (정적 자원, "실행되지 않는" 자원)
- HTML
- CSS
- JavaScript
- Images

# Web Application Server, WAS

Web Server + Application Server (웹 어플리케이션 서버, WAS)
- 무료
	- 웹 컨테이너
		- Tomcat
		- Resin
		- Jetty
- 유료
	- Java EE 서버
		- WebLogic
		- WebSphere
		- JBoss (유/무료)
		- JEUS

WebBrowser (HTTP Client) <--HTTP 요청, HTTP 응답--> Web Application Server -> 실행 -> App.

App. (동적 자원, "실행되는" 자원)
- JavaApp.
- PHP
- Perl
- Go
- JavaScript
- ASP
- Python

Tomcat / Resin -> JavaApp.
NodeJS -> JavaScript App.
ASP.NET -> VBScript or C# App

# Java Web App. 과 JAVA EE 기술 명세

JavaEE 기술 명세에 따라
- WAS에서 App. 실행
- WAS 제작
- Java App. 제작 (웹 개발자, 나)

# Java EE (Enterprise Edition, 기업용)
- 기업용 App. 제작기술 모음
- 멀티유저, 공유자원관리, 분산컴퓨팅, 접근보안 등

대표 기술
- **Servlet/JSP/JSTL/EL (해당 내용에 집중!)**
	- **웹 어플리케이션 제작 기술**
- EJB (한 물 간 기술)
	- 분산 컴포넌트 제작 기술
- Web Service
	- 웹 기반 분산 컴포넌트 제작 기술
- Authentication & Deployment
	- 관리 및 보안 기술

# Java EE 기술 명세와 각 항목의 버전
|           | Servlet | JSP | EL  | EJB |
| --------- | ------- | --- | --- | --- |
| Java EE 5 | 2.5     | 2.1 |     | 3.0 |
| Java EE 6 | 3.0     | 2.2 | 2.2 | 3.1 |
| Java EE 7 | 3.1     | 2.3 | 3.0 | 3.2 |
| Java EE 8 | 4.0     | 2.3 | 3.0 | 3.2 |

# Java EE 기술 명세와 구현 서버
|           | Web Logic                | Web Sphere | JEUS     | Tomcat |
| --------- | ------------------------ | ---------- | -------- | ------ |
| Java EE 5 | 10.3                     | 6.1, 7.0   | 6.0      | 6.0    |
| Java EE 6 | 11g(10.3.6), 12c(12.1.x) | 7.0, 8.0   | 7.0      | 7.0    |
| Java EE 7 | 12c(12.1.3), 12c(12.2.x) | 8.5, 9.0   | 8.0      | 8.0    |
| Java EE 8 | 12c(12.2.1), 14c(14.1.x) | 9.0.x      | 8.1, 8.2 | 8.5    |
-> JavaApplication을 개발할 때 고객사의 서버 버전을 확인하고, 그에 맞춰서 Java EE 버전을 선택 후 어플리케이션을 작성해야 함

# Java EE 구현 서버와 서블릿 컨테이너

Java EE 구현 서버 구조
- Web 컨테이너
	- Servlet
	- JSP
	- EL
	- JSTL
	- ...
- EJB 컨테이너
	- EJB
	- ...
- +a

Java EE 구현 서버 종류
- 유료
	- Web Logic
	- WebSphere
	- JBoss(유/무)
	- JEUS
- 무료
	- Geronemo
	- GlassFish

Web 컨테이너 종류
- 무료
	- Tomcat
	- Jetty
	- Undertow
- 유료
	- Resin

Tomcat, Jetty를 설치하면 JSB 컨테이너는 사용할 수 없다

Java EE 5,6 = SunMicrosystems
Java EE 7,8,끝 = Oracle (SpringBoot 2.7.x, Tomcat 9.x)
Jakarta EE 8,9 = Eclipse (SpringBoot 3.x, Tomcat 10.x)

Java EE 8 버전을 복제하여 패키지 이름을 javax에서 jakarta로 변경해 Jakarta 8 제작

# Java Web Application 개발 환경
pdf 캡

# Java Web Application 운영 환경
pdf 캡

# Tomcat Server

CATALINA_HOME/
ㅏ bin/ <- 서버 실행과 관련된 파일
ㅏ conf/ <- 서버 설정 파일 
ㅏ lib/ <- 서버 라이브러리 파일
ㅏ logs/ <- 서버 실행 로그 파일
ㅏ temp/ <- 서버가 실행 중에 생성하는 파일을 두는 폴더
ㅏ webapps/ <- 웹 어플리케이션 폴더를 두는 폴더
ㅏ work/ <- JSP를 Servlet 자바소스로 변환한 파일을 두는 폴더

서버 시작 
	-> startup.bat (윈도우)
	-> startup.sh (맥, 리눅스)

서버 종료
	-> shutdown.bat (윈도우)
	-> shutdown.sh (맥, 리눅스)

# Embedded Tomcat 서버 실행

new Tomcat()
- port = 8888
- baseDir = temp
- URIEncoding = UTF-8
- 웹 어플리케이션 경로 = / (root)
	- 정적 파일 경로 = src/main/webapp/ {.html, .css, .js, .git...}
	- 서블릿 클래스 경로 = build/classes/java/main {.class, .properties, .xml 등}

- 웹 자원 주소 = http://localhost:8888
	1. 정적 파일 경로에서 /index.html을 찾는다.
	2. 동적 파일 경로에서 /index.html로 경로가 설정된 서블릿을 찾는다.

# 웹 경로와 파일 경로

http://localhost:8888/a/b/index.html
= src/main/webapp/a/b/index.html

# 웹 어플리케이션 프로젝트와 배포

1. .war 파일 배포 (Web ARchive file, war, 웹 묶음 파일)
	- 프로젝트 빌드 -> app.war 파일 생성 (build)
	- app.war 파일을 Tomcat 서버에 배포 (deploy)
	-                 ㅏ webapps/
	- 과거의 방식이며, 번거로움

2. 프로젝트 + 톰캣서버 배포
	- 프로젝트 빌드 -> app.jar 파일 생성
	- app.jar 파일 내용
		- app 클래스 (동적 자원)
		- 정적 자원
		- 톰캣 임베디드 라이브러리
	- Spring Boot의 방식

# Maven 빌드 도구 표준 웹 프로젝트 구조

프로젝트/
	src/
		main/
			java/
			resources/
			webapp/
				.html, .css, .js, .gif 등 정적 자원
				WEB-INF/
					web.xml <- 배치 설정 파일 (Deployment Descriptor File; DDFile)
					classes/ <- .class, .properties, .xml  
					lib/ <- .jar
					.xml, .properties 등 설정 파일

# 웹 프로젝트 배치

## 1. 직접 서버에 배치

### 웹 프로젝트 작성
웹 프로젝트
	src/
		main/
			java/
			resources/
			webapp/ -> 복사 to .war (html, css, js 파일 등)
### 빌드 후 war 파일 생성 (gradle build)
.war
/
	WEB-INF/
		classes/ (웹 프로젝트 java, resources 폴더 복사됨)
		lib/ <- 의존 라이브러리

### 배치 (직접 파일 복사)
Tomcat 서버
	webapps/
		app.war

## 2. Eclipse 자동 배치 <- 웹 어플리케이션을 개발하는 동안 사용하는 배치 방법

### 웹 프로젝트 작성
웹 프로젝트
	src/
		main/
			java/
			resources/
			webapp/

### Eclipse 임시 배치 폴더
이클립스 워크스페이스 /.metadata/.plugins/org.eclipse.wst.server.core/
	tmp0/
		conf/ <- tocmat서버/conf/ 폴더를 복사해온다
		logs/ <- 실행 기록 파일
		temp/ <- 실행 중 생성하는 파일을 두는 곳
		webapps/ <- 사용안함
		work/ <- JSP 변환 파일 두는 곳
		wtpwebapps/ <- 웹 프로젝트 배포 폴더
			웹 프로젝트/
				WEB-INF
					classes/
					lib/
				정적 자원

## 3. 웹 프로젝트 + WAS 배치 <- SpringBoot 방식

### 웹 프로젝트 작성
웹 프로젝트
	src/
		main/
			java/
			resources/
			webapp/

### + WAS Library

### build
.jar 파일 생성

# 웹 컴포넌트 - 리스너 (옵저버 패턴)

# 웹 컴포넌트 - 필터 (Chain of Responsibility, GoF의 디자인 패턴)

<\<interface>>
filter
\--------------
init()



# 웹 컴포넌트 - 서블릿 (Command, GoF의 디자인 패턴)

<\<interface>>
Servlet  <- 클라이언트 요청이 들어오면 실행
\-------------
init()
service()
destroy()
getSurvletInfo()
getServletConfig()

# HTTP의 GET요청과 POST요청

## GET
- URL로 데이터 전달

## POST
- URL

# payload
- 유료하중 = 옮기는 짐에서 실제 수송료를 부과하는 짐
- 화물 + 수송장치
- 수송비는 화물의 중량에 대해서만 계산을 한다
- 서버에 보내고 싶은 데이터 = payload

---
# 서블릿

## Servlet
- Java 웹 애플리케이션의 기본적인 동작 단위
- 클라이언트 요청을 처리하고 응답을 생성하는 Java 클래스
- 순수 Java 코드로 작성되며, HTML을 동적으로 생성할 수 있음

### 예제
```java
import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.PrintWriter;

@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
	protected void doGet(HttpServletRequest request, HttpServletResponse response) 
			throws ServlerException, IOException {
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		out.println("<h1>Hello, Servlet!</h1>");
	}
}
```

### 실행 방법
1. 서블릿을 작성한 후 컴파일하고, WEB-INF/web.xml 파일에 서블릿 매핑을 설정하거나, 위 예제처럼 @WebServlet 어노테이션을 사용해 URL 매핑
2. Tomcat 같은 서블릿 컨테이너 필요, Tomcat 설치 후, 빌드, war파일 생성, 배치 혹은 Tomcat-embed로 자동 빌드, 생성 및 배치
3. Tomcat 실행 후 브라우저에서 URL:port/context경로로 접근

---
# 상위 레벨의 서블릿 표현 기술들

- 서블릿의 복잡성을 줄이고, 웹 페이지의 표현을 더 간결하고 효율적으로 만드는 데 기여하는 도구들
## JSP (Java Server Page)
### 개념
- 서블릿을 쉽게 만들기 위한 상위 레벨의 템플릿 기술
- JSP 파일 실행 시 서블릿으로 변환(컴파일)
- 서블릿처럼 동작하지만, HTML 기반이므로 웹 페이지 작성이 더 직관적

### 특징
- HTML과 Java 코드를 혼합하여 사용할 수 있음
- 서블릿 기반이기 때문에 Java 웹 애플리케이션에서 사용됨
- <%= %> 같은 스크립트릿을 이용해 직접적으로 Java 코드 삽입 가능

### 문제점
- JSP에서 Java 코드를 많이 작성하게 되면, 코드의 가독성이 떨어지고 유지보수가 어려워질수 있음
- 비즈니스 로직을 JSP에 작성하는 것은 지양하고, 표현과 로직을 분리하기 위해 EL과 JSTL이 도입됨

### 예제
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
	<head>
		<title>Hello JSP</title>
	</head>
	<body>
		<h1>Hello, JSP!</h1>
		<p>현재 시간: <%= new java.util.Date() %></p>
	</body>
</html>
```

### 실행 방법

1. JSP 파일을 프로젝트 내의 적절한 디렉토리 (/webapp)에 저장
2. Tomcat 같은 서블릿 컨테이너에서 애플리케이션 배포
3. 브라우저에서 URL:port/jsp경로로 접근하면 JSP 페이지 실행됨

---
## EL (Expression Language)

### 개념
- JSP의 기능을 보완하는 기술
- JSP 코드의 복잡성을 줄이고 가독성과 유지보수성을 높이기 위해 등장
- JSP에서 간결하게 데이터를 표현하고, Java 객체에 접근하는 방법을 제공하는 표현 언어
- JSP에서 Java 코드를 직접 작성하지 않아도, JavaBean 객체나 Map 등의 속성 값을 쉽게 참조 가능

### 특징
- 객체의 프로퍼티, 배열, List, Map 등에 쉽게 접근 가능
- 값 출력 외에도 조건문(empty, boolean) 등을 간결하게 표현 가능
- ${} 문법을 사용하여 표현
```jsp
<p>사용자 이름: ${user.name}</p>
```

### 장점
- 가독성 향상
	- EL을 사용하면 Java 코드를 JSP에 직접 작성할 필요가 없어 코드가 훨씬 간결해짐
- 유지보수 용이성
	- 로직과 프레젠테이션이 분리되어 유지보수가 쉬워짐

### 예제
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
	<head>
		<title>User Page</title>
	</head>
	<body>
		<%
			request.setAttribute("userName", "John Doe");
		%>
		<h1>Welcome, ${userName}!</h1>
	</body>
</html>
```

### 실행 방법

1. EL은 JSP 파일에서 자동으로 동작하므로 별도의 설정이 필요 없음
2. 위 JSP 파일을 Tomcat에서 배포한 후 브라우저에서 실행하면, EL을 통해 userName 속성을 표시

---
## JSTL (JavaServer Pages Standard Tag Library)

### 구성요소
- JSTL 1.2 API
	- JSTL 기본 클래스와 인터페이스 제공 -> JDBC API와 같은 역할
- JSTL 구현체
	- JSTL API 규격에 맞춰 인터페이스 구현 -> JDBC Driver와 같은 역할

### 개념
- JSP의 기능을 보완하는 기술
- JSP 코드의 복잡성을 줄이고 가독성과 유지보수성을 높이기 위해 등장
- JSP에서 로직을 태그로 처리하여 반복, 조건, 데이터 포맷팅 등을 쉽게 구현하는 라이브러리

### 특징
- 여러 기능을 제공하는 다양한 태그 라이브러리로 구성
	- 조건 태그
		- <c:if>
		- <c:choose>
		- <c:when>
		- <c:otherwise>
	- 반복 태그
		- <c:forEach>
		- <c:forTokens>
	- 값 설정/추출
		- <c:set>
		- <c:out>
	- 포맷팅 태그
	- XML 처리 태그
	- 등

```jsp
<c:if test="${user.age > 20}">
	<p>성인입니다.</p>
</c:if>
```

### 예제
```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
	<head>
		<title>Items</title>
	</head>
	<body>
		<%
			String[] items = {"Item 1", "Item 2", "Item 3"};
			request.setAttribute("itemList", items);
		%>
		<ul>
			<c:forEach var="item" items="${itemsList}">
				<li>${item}</li>
			</c:forEach>
		</ul>
	</body>
</html>
```

### 실행 방법

1. JSTL을 사용하려면 JSTL 라이브러리를 프로젝트에 추가해야 함 (의존성 추가)
2. JSTL 태그 라이브러리를 JSP 파일에 추가하고, Tomcat에 배포 후 브라우저에서 실행

---
## 주요 차이점 요약
| 개념      | JSP                  | EL              | JSTL                      |
| ------- | -------------------- | --------------- | ------------------------- |
| **역할**  | HTML과 Java 코드를 함께 작성 | 간단한 값 표현과 객체 참조 | 조건, 반복 등 로직을 태그로 구현       |
| **문법**  | `<%= %>`, `<% %>`    | `${}`           | `<c:if>`, `<c:forEach>` 등 |
| **가독성** | Java 코드가 많아질수록 떨어짐   | 간결하고 직관적        | 태그를 사용해 코드 가독성 향상         |
| **용도**  | 동적 웹 페이지 생성          | 값 표현 및 객체 접근    | 로직 구현 및 반복, 조건 처리         |
# 실무에서의 서블릿, JSP, EL, JSTL

- 현대 웹 애플리케이션 개발에서는 서블릿, JSP, EL, JSTL 보다 더 효율적이고 생산성이 높은 프레임워크와 기술들이 주로 사용됨

## 이유 1. 프레임워크의 대두

- Spring MVC, Spring Boot와 같은 현대적 웹 프레임워크는 서블릿, JSP, EL, JSTL을 사용하던 과거 방식에서 더 나아가 추상화된 구조와 편리한 기능을 제공
- Spring Framework를 사용하면 서블릿이나 JSP를 직접 작성할 필요 없이, 컨트롤러, 서비스, 리포지토리 계층으로 비즈니스 로직과 프레젠테이션을 더 체계적으로 분리 가능
- Thymeleaf, Freemarker 같은 템플릿 엔진이 JSP의 자리를 대신하며, 더 나은 개발 경험을 제공
- 특히 Thymeleaf는 HTML 파일을 직접 사용할 수 있어 웹 디자이너와의 협업에도 유리

## 이유 2. 프론트엔드와 백엔드의 분리

- SPA (Single Page Application) 아키텍처가 인기를 끌면서, React, Angular, Vue.js 같은 프론트엔드 프레임워크를 사용하여 클라이언트 측에서 대부분의 UI 상태 관리를 처리하고, 백엔드는 REST API 또는 GraphQL을 통해 데이터만 전달하는 방식이 일반적임
- 백엔드에서는 서블릿과 JSP 대신 API 서버를 구축하여 데이터를 주고받는 방식 선호

## 이유 3. JSP의 한계
- JSP는 유지보수와 확장성 측면에서 한계를 가지고 있음
- Java 코드를 HTML과 섞어서 사용하면 코드가 복잡해지고 가독성이 떨어짐
- 이런 문제를 해결하기 위해, 비즈니스 로직과 UI 로직을 명확히 분리한 MVC 패턴이 사용되며, JSP는 점차 대체되고 있음
- 또한 JSTP이나 EL로 어느 정도 개선할 수는 있지만, 여전히 현대적인 웹 개발의 요구 사항을 충족시키기엔 부족한 점이 많음

<hr>

# 페이지 컨트롤러 자동 생성하기

이전 방식
```java
new AuthController(userService)
```

개선
```java
@Controller
class AuthController{
 -
 -
 -
}
```
ContextLoaderListener에서 @Controller 애노테이션이 붙은 클래스를 찾아 인스턴스를 자동 생성

# 애노테이션 Annotation
```java
//어디에 붙일건지!
@Target(value = ElementType.TYPE)
// 보존 정책 (언제까지 유지할지?)
@Retention(value = RetentionPolicy.RUNTIME)
public @interface Controller {
	String value() default "";
}
```


# 객체 자동 생성 기능을 재사용 할 수 있게 별도의 클래스로 분리

ContextLoaderListener
- 프론트 컨트롤러를 위한 객체 준비
- 페이지 컨트롤러 자동 생성
	- 분리 -> ApplicationContext
	- -> 객체를 자동 생성하는 일을 함


# IOC (Inversion Of Control)
- 제어의 흐름을 역행

예
1) Dependency Injection (의존성 주입)
2) Event Handler (이벤트 처리)

Application Context
- 객체를 자동 생성하는 일을 함
	- "bean container"
- 객체의 의존객체를 자동 주입하는 역할을 함
	- "DI (dependency injection) container"
	- -> "IOC container"