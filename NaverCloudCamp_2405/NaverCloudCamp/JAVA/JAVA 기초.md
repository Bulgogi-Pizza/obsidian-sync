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