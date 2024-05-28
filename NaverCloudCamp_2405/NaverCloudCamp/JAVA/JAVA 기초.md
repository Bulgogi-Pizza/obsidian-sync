- S/W

사용자 <-(입출력)-> 컴퓨터 with "[CPU, RAM, HDD]" <<< H/W and "[명령어 + 데이터]" <<< S/W

SW

- 시스템 S/W (H/W 제어) ex) OS(운영체제), 드라이버, 임베디드
- 응용 S/W MS-Word, Photoshop, LOL 등

응용 S/W

- stand alone S/W (외부 S/W의 도움 없이 실행) ex) MS-Word, Photoshop, Excel, PPT 등
- Client/Server S/W (외부 S/W와 통신 필요) ex) LOL, OneDrive, 카카오톡 등

Client/Server S/W

- 설치형 S/W ex) LOL, 카카오톡
- 비설치형 S/W ex) gmail, 네이버 메일, Youtube 등 Web Browser를 통해 실행 -> Web Application

UNIX / LINUX
iOS - UNIX 기반
Android - LINUX 기반

Web Application

- Web Browser로 실행 ↔ Web Server ↔ (실행, HTML) 우리가 만들 것 = “App.” (JAVA로 작성)
    - HTML
    - CSS
    - JavaScript
    - Images

### Web Application과 기술

Web Server (Tomcat 제품 사용) --실행-> Web App --데이터 저장-> DBMS (MySQL 제품 사용)

- Java + Servlet/JSP + Spring F/W + Tomcat
- Jquery + Bootstrap + React +
	- HTML
	- Css
	- JavaScript + jQuery
- SQL
- XML
- Properties
- 개발 보조도구 
	- Gradle 빌드 도구
	- Docker
	- git
	- Jenkins

### Application 개발 및 실행 절차

**명령문** --변환-> **실행할 수 있는 코드** --실행-> **OS**


명령문
- 컴퓨터가 해야 할 일을 명시
- = Computer Program

## CPU, 기계어, OS 

Windows OS -> Intel CPU
Linux OS -> Intel CPU
Mac OS -> Inter CPU (과거)

삼성 -> 한국인
LG -> 한국인
SK -> 한국인

같은 CPU를 사용하지만 같은 기계어 파일을 다른 OS에서 사용하지 못하는 이유는?
- 같은 이력서를 다른 회사에 제출하지 못하는 이유는? "양식이 다르기 떄문"
- 같은 논리로 OS 마다 실행파일 양식이 다르다
- Windows : PE (Portable Executable)
- Linux : ELF (Executable and Linkable Format)
- MaxOS : Mach-O (Mach Object)
- Android : APK (Android Package)

Windows OS -> Intel CPU
Windows OS -> ARM CPU

같은 OS를 사용하지만 같은 기계어 파일을 다른 OS에서 사용하지 못하는 이유는?
- CPU별 기계어가 다르기 때문

### 객체지향 언어의 등장

- C언어의 몸집이 커지고, 코드를 좀 더 조직적이고 체계적으로 관리하기 위해 Classification(분류, Class) 기능을 탑재한 C++을 만듦.
- 당연히 C보다는 속도가 느림 하지만 그 관리의 용이성이 있음

> [!question] 질문
> C보다 C++이 더 느리다고 하셨고, 전에 언어가 결국 기계어로 바뀌면 속도는 같다고 하셨는데 어디서 차이가 나는건지?

### JavaScript

- 자바 문법을 빌려와서 자바보다는 가벼운 문법을 붙임
- JavaScript Engine 사용 (Interpreter)
- chrome에는 V8 JS Engine이 내장되어 있음
- chrome에는 HTML 렌더링 엔진으로 Blink가 내장되어 있음
- Blink는 Webkit을 개선해서 만든 HTML 렌더링 엔진임
- Webkit 엔진은 Safari 브라우저에 내장되어 있었음, 그걸 가져가서 Blink를 만든 것
- Webkit 엔진은 리눅스의 K Browser 에서 가져옴
- JavaScript를 데스크톱에서 만들기 위한 노력
- V8 엔진을 오픈소스로 공개함 그것을 데스크톱에서 바로 쓸 수 있도록 기능을 추가하여 만듦 -> Node.js
- Node.js 로 \*.js 파일 오픈 가능
- 인터프리터 -> 기계어 번역 후 CPU로 돌리는 것 (컴파일)이 아닌 소스코드를 바로 사용
- 자바 = 인터프리터 방식과 컴파일 방식이 섞인 하이브리드 방식

### Hybrid 방식

- Compile 방식과 Interprete 방식이 섞임
- \*.java --compile-> \*.class (가상의 기계어, 기계어와 유사, 중간 언어) {Bytecode} => P-code
- Bytecode Interpreter (JVM, Java Virtual Machine)를 사용해서 \*.class 파일을 로드

### Hybrid 방식을 취한 이유

- 컴파일 방식의 단점
	- 각 OS마다 기계어를 달리 만들어야(Compile) 함
- 인터프리터 방식의 단점
	- 실행할 때 마다 소스 파일 필요 (소스 파일이 공개됨)
	- 실행할 때마다 문법 검사 -> 실행 속도가 느림
	- 해당 문장을 실행하기 전까지는 문법 오류 체크가 안됨
>[!question] 질문
>결국 JVM도 OS 별로 개발을 해야 하지 않나요?
>C언어도 Write Once, Run Anywhere!이 적용되지 않나요?
- Hybrid 방식의 이점
	- \*.class파일은 기계어와 흡사하기 때문에 source를 실행하는 것 보다 실행속도가 빠름
	- .java --compile-> .class로 한 번만 컴파일 하면 여러 OS에서 실행할 수 있음

### Java 컴파일과 실행

- Hello.java 를 window, linux, macos용 컴파일러에서 컴파일해도 결국 나오는 Hello.class (Bytecode, P-Code)는 같음
- 5명의 팀이 일한다고 쳤을 때, window를 쓰든 linux를 쓰든 같은 코드로 코딩 가능

### Java 도구

- JDK (Java Development Kit)
	- JRE (Java Runtime Environment)
		- JVM
		- 실행 시 사용할 도구
	- 개발 관련 도구
		- 컴파일러
		- 디버거
		- 프로파일러
		- 문서 생성기

- JDK를 설치하면 JRE가 자동으로 포함됨, 그 내부의 JVM 역시 포함됨

- 제품 분류
	- Java SE (Standard Edition)
		- JRE (Desktop 기능 제외)
		- Server JRE
		- ==**JDK**==
	- Java EE (Enterprise Edition)
		- **==Web Application Development Kit==**
		- 분산 ADK
		- Resource Management Kit
		- Web Service Development Kit
		- etc.
		- +
		- ==**Server for testing**==
	- <del>Java ME (Micro Edition) (폭망)</del>
		- 대안 기술이 많다 (Android Things, SmartThings 등)
		- Embedded Application Development Kit

### Enterprise 용 App. 실행 요건

1. 다중 사용자가 이용
	- Web App. 제작 도구
		- Servlet
		- JSP
		- JSTL
		- EL
		- <del>JSF 폭망</del> JavaScript 도구가 활성화됐기 때문

사용자1 -> WebBrowser --요청-> Web Server --실행-> App
사용자2 -> WebBrowser --요청-> Web Server ...

App - Web Server가 실행할 수 있는 App. 개발 도구 제공

2. App의 분산 배치 -> 분산 컴포넌트 제작 도구
	- X 다중 사용자 -> 서버 (회계, 인사, 결재, 주문) 
	- O 다중 사용자 -> 회계서버, 인사서버, 결재서버, 주문서버
	
	- 서버를 하나로 묶어 둘 것이 아니라 각 서버를 나눠두면 하나의 서버가 다운 되어도 문제가 커지지 않음
	- 다만 각 서버간 통신을 해야 하는 경우가 생기기 때문에 한 시스템에서 다른 시스템의 코드를 실행해야함 -> 코드를 작성할 때 다른 컴퓨터에서 사용할 수 있게 만들어야 함 -> 분산 컴포넌트 제작 기술 (Distribution Component)
	- 분산 컴포넌트 제작 기술
		- EJB
		- WebService
		- REST API