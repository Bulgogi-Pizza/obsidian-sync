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