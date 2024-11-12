# S/W의 개념과 종류

사용자 <-(입출력)-> 컴퓨터 with "[CPU, RAM, HDD]" <<< H/W and "[명령어 + 데이터]" <<< S/W

### SW 

- 시스템 S/W (H/W 제어) ex) OS(운영체제), 드라이버, 임베디드
- 응용 S/W MS-Word, Photoshop, LOL 등

### 응용 S/W 

- stand alone S/W (외부 S/W의 도움 없이 실행) ex) MS-Word, Photoshop, Excel, PPT 등
- Client/Server S/W (외부 S/W와 통신 필요) ex) LOL, OneDrive, 카카오톡 등

### Client/Server S/W 

- 설치형 S/W ex) LOL, 카카오톡
- 비설치형 S/W ex) gmail, 네이버 메일, Youtube 등 Web Browser를 통해 실행 -> Web Application

>[!info] Info
>UNIX / LINUX
iOS - UNIX 기반
Android - LINUX 기반

### Web Application

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

### CPU, 기계어, OS 

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

>[!info] 답변
>컴파일러 최적화와 기계어 최적화 차이, 그리고 메소드 방식과 절차형 방식의 차이

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

### Java Formatting
- font : D2Coding
- format setting : "https://raw.githubusercontent.com/google/styleguide/gh-pages/eclipse-java-google-style.xml"

$ javac -encoding UTF-8 Hello.java
-encoding ~~~ 소스 코드가 어떤 규칙에 따라 작성됐는지 알려줌
* jdk 17은 자동으로 지정이 안돼서 오류가 뜨고, 21 버전은 자동으로 지정됨

$ javac -d 폴더 Hello.java
-d 폴더 -> 컴파일 결과 파일을 둘 폴더를 지정

$ java -(classpath or cp) 경로 Hello
-classpath 경로 -> 클래스 파일이 있는 위치를 알려줌

$ javac -target 17 Hello.java
	-> Hello.class가 17버전 이상에서 실행 가능 JVM21 ok, JVM 17 ok, JVM 11 fail

### 윈도우에서 컴파일 할 때 문자집합 오류가 발생하는 이유

Windows는 "MS949" 규칙에 따라 텍스트를 읽고 쓰는데, VSCode에서 저장하면 UTF-8 형식으로 문자를 저장하기 때문, 그래서 Windows에서 컴파일 할 때에는 "MS949" 규칙에 따라 저장되었을 것이라 착각하고 오류가 생김

### 개발 관리

App.1 --

App.2

### Git 저장소와 프로젝트 폴더

1. Case 1
	저장소/
	ㅣ
	ㅏ 프로젝트 A
	ㅏ 프로젝트 B

버전은 저장소 단위로 관리되기 때문에 프로젝트 단위로 관리할 경우 좋지 않은 방식

2. Case 2
	저장소/
	ㅣ
	ㅏ 메인 프로젝트 A
	ㅏ 서브 프로젝트 1
	ㅏ 서브 프로젝트 2
	.
	.
	.

그래서 이렇게 저장하는 경우가 있고 대부분은 Case 3 를 따름

3. Case 3
	저장소 (프로젝트 A)/
	ㅣ
	ㅏ src
	ㅏ bin

	저장소 (프로젝트 B)/
	ㅣ
	ㅏ src
	ㅏ bin

### Build
<quote>소스파일을 Application으로 제작하는 과정</quote>

1. Compile
2. Link
3. Test
4. Packaging
5. Deploy

컴파일 -> API 문서 생성

빌드 도구
-> 빌드를 관리하는 도구
- Ant 
- Maven 
- Gradle

### Build Tool and JDK
- source file --javac, javadoc--> 
- compile -> \*.class, API --단위테스트-> 
- Test 결과 문서

	- build tool -> javac, javadoc

Ant -> build.xml
Maven -> pom.xml
Gradle -> build.gradle

프로젝트 폴더 내에 pom.xml, build.gradle 둘 다 있다? -> Maven Gradle 둘 다 사용

Maven 표준 프로젝트 디렉토리로 구성하기

$gradle init

build script file
Domain-Specific Language (DSL) (특정 영역에 사용되는 언어)
- Groovy (we use it)
- Kotlin

### Gradle Project 디렉토리 구조
myapp/ <-- root project 디렉토리
ㅣ
ㅏ app/ <-- main project 디렉토리
ㅣ    ㅏ src/
ㅣ    ㅏ build.gradle <-- main project의 빌드 명세서
ㅣ
ㅏ gradle/ <-- gradle이 설치 안된 경우 자동으로 설치해주는 도구
ㅣ    ㅏ wrapper/
ㅣ    ㅏ libs.versions.toml <-- 의존 라이브러리 버전 정보
ㅣ
ㅏ gradlew (linux, unix)  --> ㅣGradle이 로컬 컴퓨터에 설치 안 된 경우 사용
ㅏ gradle.bat (window)  --> ㅣ할 수 있는 도구, 자동으로 설치하여 실행한다
ㅏ settings.gradle <-- Gradle 메인 설정
ㅏ .gitignore <-- GIT ignore 파일
ㅏ .gitattributers <-- GIT 보조 설정 파일

gradle clean : build 내용 삭제
gradle build : gradle 빌드하기

javac -d bin Hello.java

ㅏ Hello.java
ㅏ bin/
ㅣ  ㅏ Hello.class

java -classpath(or -cp) bin Hello

real : .java --> .class --> Bytecode Player --> OS
mean : Java --> Bytecode --> JVM --> OS

>[!todo] 독학
>하버드 CS50 ~ 강의 듣기

### 프로그래밍 언어의 발전 과정

1. 명령문
~~
~~
~~
~~
~~
~~
~~

코드를 관리하기 쉽게 묶는다

2. Function
f(){
~~
~~
~~
}
f(){
~~
~~
~~
}
f(){
~~
~~
~~
}

Function을 관리하기 쉽게 묶는다

3. Class
Class A{
	f(){
	
	}
	f(){
	
	}
}
Class B{
	f(){
	
	}
	f(){
	
	}
}

클래스를 관리하기 쉽게 분류

4. package
ㅏ a/
ㅣ  ㅏ A
ㅣ  ㅏ B
ㅣ
ㅏ c/
ㅣ  ㅏ D
ㅣ  ㅏ E

5. module

A\[package A, package B]
C\[package C, package D]

### 소스파일과 클래스블록, 클래스 파일의 관계

C - Source file n개 컴파일 --링크-> 1개의 목적파일
Java - Source file n개 컴파일 ----> n개의 클래스 파일

>[!question] 질문
>왜 classes는 java -> main, src는 main -> java??

test.java 파일 밑에
class A
class B
class C
선언 후 컴파일하면
A.class B.class C.class 파일이 생성됨
-> 1개의 파일, N개의 class -> N개의 class 파일

test2.java 파일 밑에
public class X
class B

### entry point : main() 메서드

Test3.java
 class Test3{}

-> Test3.class 생성
-> java Test3
-> 오류! bcz) Java의 Entry point인 main() method는 public static void main(String[] Var){} 로 선언되어야 하기 때문!

### Application argument

$ java -classpath --- Test5 aaa bbb ccc
-> JVM --생성-> "aaa" "bbb" "ccc" (String[] 스트링 배열)

main(String[] args){  <- args에 "aaa","bbb","ccc"가 전달 됨
	args[0] -> "aaa"
	args[1] -> "bbb"
	args[2] -> "ccc"
}

### Package

- 클래스를 분류하는 문법
- bitcamp-mystudy/    // GIT 저장소
- ㅏ java-lang/    // Project 폴더 (root)
- ㅣ  ㅏ app/    //main project
- ㅣ  ㅣ  ㅏ src/    //
- ㅣ  ㅣ  ㅣ  ㅏ main/    //
- ㅣ  ㅣ  ㅣ  ㅣ  ㅏ java/    //source 폴더
- ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅏ study/    //package
- ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅏ lang/    //package
- ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅏ Test.java
- ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅣ  ㅏ

Gradle 8.2 이전에는 Project 폴더 (ex. java-lang) 밑에 바로 src 폴더를 두었으나
Gradle 8.2 이후 (현재 gradle 8.5 사용중) Project 폴더 내에 main project 파일을 두고 그 아래에 src 폴더가 생김 (sub project가 생길 것을 대비)

main 밑에 java 폴더가 존재하는 이유는 최근 프로젝트는 하나의 언어만 사용하는 것이 아니라 성능의 향상을 위해서라면 기꺼이 다른 언어도 섞어 사용하기 떄문에 이를 대비하는 것 (polyglot Programmer)

How to Test.java compile and run
1. javac -d classpath study/lang/Test.java
2. java -cp classpath study.lang.Test

### 주석 (comment)

1. traditional comment
/* 
-
-
-
\*/

2. end of line comment
//

### javadoc 주석
/**
	클래스에 대한 설명
\*/
class A {
	/** 필드에 대한 설명 \*/
	int a;
	/** 메서드에 대한 설명 \*/
	void m(){-}
}

-> javadoc 사용 시 javadoc 주석 추출해서 HTML API문서를 만듦

API(Application Programming Interface) 문서?
-> App. Programing 할 때 사용하는 Class나 Method의 사용 설명서

- .class 파일에는 주석이 포함되지 않음

### Annotation 주석
- Java 컴파일러나 JVM에게 전달하는 특별한 정보

@Data
class A{
	@Autowired int a;
	@Override void m(){-}
	-
	-
	-
}

- @ 로 시작하며, .class 파일에 포함될 수 있음

### Literal
 - 값을 표현한 것

1. 수
	1. 정수
		1. 100 <- 4byte
		2. 100L, 100l <- 8byte
	2. 부동소수점
		1. 3.14f, 3.14F <- 4byte
		2. 3.14 <- 8byte
2. 문자
	1. '가','A','8','@','#' <- 2byte
3. 논리값
	1. true, false <- 4byte <- JVM엔 boolean 변수가 없지만, 대신 boolean 변수를 컴파일 시 JVM int로 변환하여 사용, 배열인 경우 1byte
4. 문자열
	1. "가", "abc", "123"
5. null
	- 주소 없음을 의미

### Primitive Data Type
- 자바에서 데이터를 구분하는 기본 분류

1. 정수
	1. byte (1 byte) : -128 ~ 127        ⎤ ==크기에 따라 literal을==
	2. short (2 byte) : -32768 ~ 32767   ⎦ ==구분하는 문법이 없다==
	3. int (4 byte) : 약 -21억 ~ 21억 ==*Default*==
	4. long (8 byte) : 약  -922경 ~ 922경
2. 부동소수점
	1. float (4 byte)
	2. double (8 byte) ==*Default*==
3. 논리 - boolean (int 또는 byte)
4. 문자 - char (2 byte) : 'A'
5. 문자열

### 문자 literal

- 'A'
- '\\u유니코드값' (역슬래시)
	- 유니코드값 : 문자에 대해 2byte 숫자를 부여
	- A = 0x0041
	- B = 0x0042
	- a = 0x0061
	- b = 0x0062
	- 가 = 0xAC00
	- 각 = 0xAC01
문자는 전기적 신호로 저장
비트 신호로 저장
비트 신호를 쉽게 표기하기 위해 2진수를 사용
2진수를 좀 더 쉽게 표기하기 위해 16진수를 사용
컴퓨터간에 저장의 일관성을 위해 문자를 저장하는 규칙을 정의
-> character set (문자집합)

### 문자 집합 ASCII (7bit)

128 = 33의 출력 불가능 제어 문자 + 95개의 출력 가능한 문자 (대, 소문자 알파벳, 숫자, 32개의 특수 문자, 공백 문자)

sp(공백) - 010_0000 (0x20)
? - 011_1111 (0x3f)
\= - 011_1101 (0x3d)
% - 010_0101 (0x25)
cr(cage return) - 000_1101 (0x0d)
lf(line feed) - 000_1010 (0x0a)
A - 100_0001 (0x41)
B - 100_0010 (0x42)
C - 100_0011 (0x43)
.
.
a - 110_0001 (0x61)
b - 110_0010 (0x62)
c - 110_0011 (0x63)

엔터 = 0x0d 0x0a (cr, lf) (위치 초기화, 개행)

### 문자집합 

ISO-8859-1 = ASCII(7bit) + a(alpha, 1bit)
a(alpha) -> 8859-2,3,4,5,6 ~

ISO-8859-1 + KOR (완성형 2350자) -> EUC-KR (16bit, 국제표준)
EUC-JP
EUC-CN

MS949 (2byte, a.k.a cp949) = EUC-KR + a(alpha) = 11172자

Unicode (4byte) 실제는 최대 21bit 사용
국제표준
한글, 영어 모두 2byte 사용
자바에서 문자를 다룰 때 사용

UTF-8 = Unicode 변형 

URL 인코딩
1. "가각간" 검색 (9byte)
2. UTF-8 변환 EA B0 80 EA B0 81 EA B0 84 (16진수, 9byte)
3. 문자로 변환 "%EA%B0%80%EA%B0%81%EA%B0%84" (27글자, 27byte)
4. 코드로 변환 25 45 41 25 42 30 25 ~~~~

### 숫자를 메모리에 저장

1. sign-Magnitude
부동소수점에서 가수부 저장 시 사용
00001101 (13)
10001101 (-13)

2. 1's 보수
00001101 (13)
11110010 (-13)

3. 2's 보수 
정수를 저장할 때 사용하는 규칙
00001101 (13)
11110011 (-13)

4. Excess-k
부동소수점의 지수부 저장 시 사용
bias 값을 더해서 저장
1. k값 (bias값) 구하기
K = 2<sup>(비트-1)</sup>-1 = 2<sup>(8-1)</sup>-1 = 2<sup>7</sup>-1 = 128-1 = 127
128 + 127 = 255 -> 1111 1111
  1 + 127 = 128 -> 1000 0000
  0 + 127 = 127 -> 0111 1111
 -1 + 127 = 126 -> 0111 1110
 -127 + 127 = 0 -> 0000 0000
 13 + 127 = 130 -> 1000 1100
-13 + 127 = 114 -> 0111 0010

부동소수점을 메모리에 저장

12.375 -> 1100.011
정규화 1100.011 -> 1.100011 x 2<sup>3</sup> -> .100011 x 2<sup>3</sup>
- 가수부 = 100011
- 지수부 = 3 (11<sub>2</sub>)

32bit (float)
- 부호비트 1bit
- 지수부 (excess-k) 8bit 
	- 0000_0011 -> 3 + 127 -> 1000_0010
- 가수부 (sign-magnitude) 23bit
- 0 1000_0010 100_0110_0000_0000_0000_0000
- 0100 0001 0100 0110 0000 0000 0000 0000
- 41 46 00 00

12 -> 1100
0.375 -> 0.011

0.375 * 2 = 0.75 -> 0
0.75 * 2 = 1.5 -> 1
0.5 * 2 = 1.0 -> 1

### 값을 메모리에 저장

문자 --문자집합 규칙-> 2진수 -> 메모리
정수 --2의 보수 규칙-> 2진수 -> 메모리
부동소수점 --IEEE-754규칙-> 2진수 -> 메모리
색상 -> 2진수 -> 메모리
소리 -> 2진수 -> 메모리
값 -> 2진수 -> 메모리

### 변수
- 데이터를 저장하는 메모리
- 변수 선언 -> 메모리를 준비시키는 명령문

메모리타입(Data Type) 메모리명(변수명);

메모리명(변수명) = 값;
= : assignment operator (대입 연산자)

- Primitive Data Type
	- 정수
		- byte (1)
		- short (2)
		- int (4)
		- long (8)
	- 부동소수점
		- float (4)
		- double (8)
	- 논리
		- boolean(4, 1)
	- 문자
		- char (2)
- User Defined Data Type
	- Class (클래스)

Data Type의 역할 - 메모리 사용을 제어

int i;
float f;
i = 30; // 실제 메모리 0x00_00_00_1E -> 00000000_00000000_00000000_00011110
f = 30; // 실제 메모리 0x41_F0_00_00 -> 0 1000001_1 1110000_00000000_00000000

### 개발도구와 프로젝트 폴더

Project
- java-lang/
- ㅣ
- ㅏ settings.gradle
- ㅏ app/
- ㅣ ㅏ .settings/
- ㅣ ㅣ ㅏ 설정파일
- ㅣ ㅏ .project
- ㅣ ㅏ .classpath

IntelliJ IDE
- workspace

Project를 IntelliJ IDE workspace에 import 하고싶다면, settings.gadle만 가져가면 됨
근데 Eclipse IDE workspace에 import 하고싶다면, app내의 .settings/설정파일, .project, .classpath가 있어야만 eclipse가 프로젝트 폴더로 인식
해당 파일들은 gradle로 만들 수 있음


### GIT 저장소와 Gradle 프로젝트

- git/
	- bitcamp-mystudy/ <- GIT 저장소 폴더
		- java-lang/
		- myapp/
		- .git/ <- GIT 백업

- a/ <- gradle 프로젝트 폴더
	- settings.gradle
	- build.gradle
	- pox.xml
	- build.xml

- b/ <- 메인 프로젝트 폴더
	- settings.gradle
	- app/ <- 서브 프로젝트 폴더
		- build.gradle

gradle 프로젝트 폴더에
build.gradle 파일과 settings.gradle 파일이 같이 있고, app 폴더가 없다면 옛날 버전 gradle 프로젝트 폴더임

### 부동소수점 메모리 크기와 값의 범위

1. 4byte
- 소수점을 빼고 숫자의 자릿수를 셌을 때, 7자리까지 거의 정확하게 저장됨

2. 8byte
- 15자리까지 거의 정확하게 저장된다.

유효자릿수를 초과하면 값이 짤려서 들어갈 가능성이 높다.

정확하게 말할 수 없다 -> 2진수로 변환하는 과정에서

### 부동소수점 계산 시 주의

float f1 = 32.17541f;
float f2 = 23447.12f;
float f3 = f1 + f2;

==> 7자리 초과
- 그래서 부동소수점은 기본으로 8byte 사용을 권장, 리터럴도 8byte일 때 접미사를 안붙임

6 805 64693 27705 77196 23408 36696 90338 50880