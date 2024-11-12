
## 01. 자바 프로젝트 준비

- gradle 빌드도구 --> init --> /myapp



## 클래스를 복제해서 사용할 때 문제점

- 코드 중복 -> 변경이 어려움
- 코드에서 버그 발견 -> 버그 수정 -> 복제해서 만든 모든 클래스에 대해 처리해야 함
- 기능 추가 -> 복제해서 만든 모든 크래스에 대해 처리해야 함
- -> 유지보수가 어려움
- -> 코드 재사요이 힘듦

## 해결책) 같은 코드를 사용, 그러나 데이터는 분리

변경 전 (BoardList 스티택 메서드)
(게시판), (공지사항) -> BoardCommand -> BoardList -> (게시글 배열), (공지사항 배열)

변경 후 (BoardList 인스턴스 메서드)
(게시판), (공지사항) -> BoardCommand -> (게시글:BoardList), (공지사항:BoardList)

## 인스턴스와 메서드

레퍼런스.메서드();

A클래스의 레퍼런스, A클래스의 메서드
this 내장 변수는 메서드가 정의된 클래스의 인스턴스 주소를 받기 때문

String s = "hello";
int i = 100;

println(s + "ok"); // 이 때 '+' 연산자는 문자열에 대해 사용되는 연산자
println(i + 200);  // 이 때 '+' 연산자는 정수에 대해 사용되는 연산자
-> 데이터 타입에 따라 사용할 수 있는 연산자

코드를 사람이나 로봇
메서드를 사물로 추상화 하여
모델링 하는 것 -> 객체지향 추상화

Object Oriented Programming



## 29. 파일 입출력 시 Decorator 클래스 활용하기

기능 확장
1. 상속 (study.patterns.ex02.before)
	1. Printer .print() 내용 출력 
	2. <- Printer2 .print() 머리말 출력
	3. <- Printer3 .print() 꼬리말 출력
	4. 등등 기능 추가가 유연하지 않다. 강연결의 문제가 있음

상속 이용 시 꼬이는 상황
	Printer .print() 내용 출력
	Printer2 extends Printer .print() 머리말 출력
	Printer3 extends Printer2 .print() 꼬리말 출력
	Printer4 extends Printer .print() 꼬리말 출력
	Printer5 extends Printer .print() 사인 출력
	등등등 상속하다보면 기능 중복 발생

2. 포함 관계를 이용한 기능 확장 (study.patterns.ex02.after1)
문제점
- 상속처럼 코드 중복 발생
- 기능을 조합하다 보면 포함관계가 복잡해짐

3. GoF의 Decorator 설계 패턴을 이용한 기능 확장 (study.patterns.ex02.after2)
- 여러 기능을 상황에 따라 조합할 경우에 적합
- 기능을 붙였다 떼었다 자유롭게 할 수 있다
- 포함 관계를 이용
![[Pasted image 20240719111302.png]]

## File I/O API와 Decorator 설계 패턴

1. byte stream class = binary 데이터 입출력

<\<abstract>>
InputStream
- FileInputStream extends InputStream <- Component = Data Sink Stream Classes
- ByteArrayInputStream extends InputStream <- Component
- PipedInputStream extends InputStream <- Component
- <\<Decorator>> FilterInputStream extends InputStream <- Decorator = Data Processing Stream Classes
- DataInputStream extends FilterInputStream <- Decorator = Data Processing Stream Classes
- BufferInputStream extends FilterInputStream <- Decorator = Data Processing Stream Classes
- <\<Decorator>> ObjectInputStream extends FilterInputStream <- Decorator = Data Processing Stream Classes

## 30. 파일 입출력 API : 객체 직렬화 / 역직렬화

객체 (인스턴스) --serialize(직렬화)-> byte\[] 
byte\[] --deserialize(역직렬화)-> 객체(인스턴스)
byte\[] (인스턴스 필드의 값 + 클래스 정보(클래스명, 필드명))

직렬화 = serialize = marshaling
역직렬화 = deserialize = unmarshaling

with java.io.Serializable 인터페이스

## 31. 파일 입출력 API : 텍스트 입출력과 CSV 포맷

Comma Separated V...

## 32. File I/O API : JSON 포맷 입출력

JSON : JavaScript Object Notation 문법을 가져와서 만든 포맷

|       | JavaScript 문법         | JSON 포맷 |
| ----- | --------------------- | ------- |
| 문자열   | "문자열" '문자열'           | "문자열"   |
| 프로퍼티명 | 프로퍼티명 "프로퍼티명" '프로퍼티명' | "프로퍼티명" |
예) 객체
{
"name": "홍길동",
"age": 20,
"working": true,
"address": {"postNo": "01100",
			"city": "seoul"}
}

예) 목록
\["aaa", "bbb", 20, true]
\[{-}, {-}, {-}]

## JSON 라이브러리 (http://json.org)

![[Pasted image 20240722103838.png]]

## Gson 객체 생성과 GoF의 Builder 패턴

건설사가 건물을 짓는 것처럼 여러개의 의존 객체(옵션)가 복합적으로 결합된 객체를 생성할 때 사용하는 설계 패턴

![[Pasted image 20240722104831.png]]

## 37. Application 간에 데이터 공유

Networking API 사용법

Client
Socket(C) 생성

Server
ServerSocket -> Socket(S) 생성

Socket(C) <-> Socket(S) 통신
	Socket(C).OutputStream -> Socket(S).InputStream
	Socket(S).OutputStream -> Socket(C).InputStream

new ServerSocket(포트번호, 대기열크기)
	포트번호 - 통신 식별 번호
	대기열 크기 - 클라이언트 최대 접속 수

Computer1 IPaddr - 127.0.7.1 (대표번호)
Computer2 IPaddr - 127.0.8.5 (대표번호)

통신 시 사용할 구분 번호 - 포트번호 = 내선번호와 같은 역할

### Protocol : 데이터 송수신 규칙

Client
	데이터명 - "users"
	작업명령 - "insert" | "list" | "get" | "update" | "delete"
	전송데이터 - *

Server
	응답상태 - "success" | "failure"
	응답데이터 - *

서버측 통신 객체 - 참여객체들(Participants)

ServerApp (클라이언트 연결 담당)
UserDao (회원 데이터 처리를 담당)
UserDaoSkel (클라이언트와의 통신을 담당)

1. 요청 -> ServerAll
2. 전달 -> UserDaoSkel
3. call -> UserDao
4. 리턴 -> ServerApp
5. 응답 -> Client


Object Request Broker
(클라쪽 브로커)        (서버쪽 브로커)
UserDaoStub -> 요청 -> UserDaoSkel
UserDaoSkel -> call -> UserDao
UserDaoSkel -> 응답 -> UserDaoStub

UserDao

UserXxxCommand call-> UserDaoStub <-응답, 요청-> UserDaoSkel call-> ListUserDao

UserDaoStub - Proxy 객체
- Client 측에서는 스텁 객체를 UserDao 구현체로 사용
- 실제 작업은 Server에서 수행
- 스텁은 통신을 통해 작업을 중개할 뿐이다.

"서버와 통신 부분을 캡슐화해서 클라이언트 객체에게 감춘다"
구현의 자세한 사항을 감춘다!

## Client Application과 Stub

1. 시작 > ClientApp > InitApplicationListener

## 39. 멀티스레드 도입

1. 다중 클라이언트 요청 처리 - stateful

서버 - 클라이언트
- 한 번 요청하면 응답을 주고 받음
- 다만 다른 클라이언트가 있을 경우 뒤에서 대기하고 있음
- 서버와 연결된 클라이언트가 연결을 끊을 때까지 다음 클라이언트는 기다려야 함
- 접속 순서대로 처리

2. 다중 클라이언트 요청 처리 - stateless

서버 - 클라이언트
- 한 번 요청과 응답을 수행하면 바로 연결을 끊음
- stateful 방식 보다 대기 시간이 짧다

3. 다중 클라이언트 요청 처리 - Multi-threading

서버 - 클라이언트
- 여러 클라이언트의 요청을 동시에 처리
- stateful & stateless 방식의 고질적인 문제점 해결
- (요청처리에 시간이 오래걸리면 그 시간만큼 대기해야 한다는 문제점)
- 클라이언트 요청을 순차적으로 처리하던 것에서 병행으로 처리
- 클라이언트 요청 처리를 main의 실행흐름과 분리해서 따로 실행

스레드를 만드는 방법 - main 실행 흐름에서 따로 실행 흐름을 분리하는 방법

class 실행흐름명 extends Thread {
	void run() {
		따로 실행하는 코드
	}
}

## 40. DBMS 도입

DB
- 검색, 갱신이 가능하도록 구조화
	- 실시간 접근
	- 동시 공유
	- 데이터 중복 최소화
	- 일관성, 무결성, 보안성
	- (규칙이나 제약조건을 준수, 데이터 신뢰성 확보)

이러한 DB를 관리해주는 프로그램
DBMS
- RDMBS
	- Oracle
	- MS-SQL
	- DB2
	- MySQL
	- MariaDB
	- PostgreSQL
	- Tibero
	- Cubrid
	- Altibase
- MangoDB
- Redis

# 45. MyBatis 도입

---- 기존 ----
DAO
- Java 코드
- JDBC API 사용
- SQL

---- 변경 ----
DAO (call MyBatis)
- Java코드

MyBatis (use SQL)
- JDBC API 사용

SQL

## 퍼시스턴스 프레임워크 (Persistence Framework)

1. SQL Mapper
	- 자바 객체 -> SQL문, 개발자가 직접 작성 -> 테이블

2. OR Mapper
	- 자바 객체 -> (SQL 문, 프레임워크에서 자동생성) -> 테이블

## MyBatis 사용 준비

### 설정파일 준비

```xml
mybatis-config.xml
<?xml version="1.0" // 1.0만 가능
encoding="UTF-8" ?> // 문서를 저장할 때 사용하는 문자 집합
// 반드시 첫 줄에 있어야 함

<!DOCTYPE -- XML 규칙 선언
configuration -- root element (태그)
PUBLIC -- SYSTEM(비공개) 특정 회사에서만 사용되는 규칙일 때

"-//mybatis.org//DTD Config 3.0// EX)" 
-- (+) 국제 공인규칙
-- (-) -- 사설규칙 
-- mybatis.org -- 규칙을 관리하는 조직명
-- DTD -- 규칙 이름
-- EN -- 규칙을 작성한 언어

"https://---/---.dtd">
```

# 49. 웹 어플리케이션 전환 

## Tomcat Servlet Container 도입

1. 기존
	- ServerApp
		- 직접 통신 구현
		- 멀티스레딩 처리
		- 리스너 제어
		- 메뉴 제공

2. 변경
	- ServerApp
		- Tomcat 실행
			- HTTP 프로토콜에 따라 웹 브라우저와 통신
			- 멀티스레딩 처리
			- 리스너 컴포넌트 실행
			- 메뉴대신 URL에 기능 연결

## 리스너 만들기

1. 기존
	- ApplicationListener라는 <\<interface>> 기준에 따라서 구현
	- InitApplicationListener implements ApplicationListener
		- Mybatis 객체 준비
		- DAO 객체 준비
		- 메뉴 준비
		- 커맨드 준비

2. 변경
	- ServletContextListener라는 <\<interface>> 기준에 따라 구현

## ServletContextListener 구동

1. 시작
	- 서블릿 컨테이너

## Servlet 만들기

1. 기존
	- <\<interface>> Command 를 구현한 UserListCommand
		- DBMS에서 회원 목록 조회
		- 클라이언트로 출력

2. 변경
	- <\<interface>> Servlet을 구현한 @WebServlet("url") UserListServlet
		- DBMS에서 회원 목록 조회
		- 클라이언트로 출력

## Servlet 구동

@WebServlet 애노테이션
- 서블릿 컨테이너에 동적 자원을 배치할 때 사용
- 클라이언트 요청이 들어왔을 때 그 요청을 처리할 클래스를 지정
- URL을 이용하여 요청을 처리할 자원을 구분

## 문자열 출력과 한글 깨짐

웹 브라우저가 서블릿 객체에게 요청을 하고
서블릿 객체가 컨텐츠(문자열)를 생성한 뒤
내부 버퍼에 보관하는데, 이 때는 UTF-16BE 방식으로 보관되어있다.
그 후 ISO-8859-1 문자열로 변환해 출력하는데, 문자표에 없는 문자는 '?' 문자로 바꾼다.
그래서 한글이 ? 문자로 출력된다.
출력문을 사용하기 전에 출력할 문자열을 어떤 문자집합으로 변환할 것인지 설정하면 된다.
setContentType()

## setContentType()
- setContentType("MIME타입; 문자집합");
- MIME
	- Multi-purpose
	- Internet
	- Mail
	- Extention
- 컨텐츠의 타입 정보
- 