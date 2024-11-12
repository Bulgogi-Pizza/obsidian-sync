## Object 클래스
```java
class A{}
// 1. compiler가 변환시킴 (class A extends Object{})
// 2. 그 다음 컴파일 (A.class)
```

A 클래스는 Object 클래스를 자신의 것 처럼 사용할 수 있음(상속)
- Object class = super class = parent class
- A class = sub class = child class

A클래스는 Object클래스를 링크함
- Object 클래스의 코드를 제 것처럼 사용.
- 포함한 것이 아님

Object는 모든 클래스의 최상위 클래스임

class A extends B {}
super class = B = parent class
sub class = A = child class

## instance of
그것 p = 삽살개
p는 삽살개인가? (p instanceof 삽살개)
p는 개인가? (p instanceof 개)
p는 포유류인가? (p instanceof 포유류)
p는 동물인가? (p instanceof 동물)

Object <- Vehicle <- Car <- Truck

Truck t = new Truck();
- Object의 인스턴스 변수, Vehicle의 인스턴스 변수, Car의 인스턴스 변수, Truck의 인스턴스 변수
- t {200 번지}
- t instanceof Truck (t가 가리키는 인스턴스는 Truck설계도에 따라 만들었는가?)
- t 는 Truck의 인스턴스인가? true
- t 는 Vehicle의 인스턴스인가? true

## Object.toString()

- return => FQCN@16진수해시값 (Fully-Qualified Class Name,FQN=QN 완전만족 클래스 이름)

## hashCode()와 equals() 활용

HashSet (key, value) 
- key = hashcode
- value = 인스턴스 주소

add() 
- hashCode()의 리턴값을 key로 사용해 저장

![[Pasted image 20240624115518.png]]


## String

String s1;
s1 = new String("Hello");
String s2 = new String("Hello");
String s3 = "Hello";

JVM Stack
- main()
	- s1 (String의 레퍼런스) \[200]
	- args
	- s2 (String의 레퍼런스) \[300]
	- s3 \[400]

Heap
- (s1 값, 주소) \[200]
	- "Hello"... (String의 인스턴스)
- (s2 값, 주소) \[300]
	- "Hello"... (String의 인스턴스)

String pool
- \\\[400]
	- "Hello" (String 인스턴스) (s3 때문에 만들어짐)


## 다형적 변수와 형변환

Object obj = new String("Hello"); // String 인스턴스를 Object 클래스의 레퍼런스 obj에 생성
obj.메서드(); // Object의 메서드 사용 가능!

String s = (String) obj;
s.메서드(); // String의 메서드 사용 가능!

- 개념적
자동차 -> 자동차
자동차 -> 버스
자동차 -> 트럭
가능

- 기술적
Score (.kor, .eng, .math, .sum, .compute(){sum = kor + eng + math})
Score2 extends Score (.art, .music, .compute2(){sum = kor + eng + math + art + music})

```java
Score s1 = new Score(); // Score의 인스턴스 생성
s1.compute(); // 가능

Score s = new Score2(); // Score (kor, eng, math, sum)와 Score2 (art, music)의 인스턴스 생성
// but s 는 Score 클래스이기 때문에, Score의 메서드만 사용 가능
s.compute();

```

## new String(바이트 배열)

\[b0]\[a1]\[b0]\[a2]\[30]\[31]\[32]\[41]\[42]\[43] // byte\[] bytes

--> new String(bytes)
--> file.encoding (JVM 프로퍼티) --> 변환 (UTF-16BE) --> String 인스턴스 생성

System.out.printf("JVM의 file.encoding=%s\n", System.getProperty("file.encoding"));
--> Eclipse의 경우 UTF-8 인데, Eclipse IDE는 클래스를 실행할 때
-Dfile.encoding=UTF-8 JVM 프로퍼티를 설정하기 때문
따라서 Eclipse에서 실행하면 byte 배열의 값을  UTF-8 문자 코드라고 가정하고
UTF-16BE 코드로 변환


## Linked List의 구동 원리

1. 입력
	- list.append("홍길동")
	- 200\\\[value - "홍길동"]\[next - null] 
	- -> 데이터를 저장할 바구니(node) 준비
	- 
	- list.append("임꺽정")
	- 200\\\[value - "홍길동"]\[next - 300]  
	- 300\\\[value - "임꺽정"]\[next - null]
	- -> 새 노드 생성, 기존 노드의 next에 새 노드 연결
	- 
	- list.append("유관순")
	- 200\\\[value - "홍길동"]\[next - 300] 
	- 300\\\[value - "임꺽정"]\[next - 400] 
	- 400\\\[value - "유관순"]\[next - null]
	- 

2. 조회
	- list.getValue("")

3. 

4. 삭제

## merge

<<<<<<<< 
내 코드

===========
서버에서 받아온 코드

\>>>>>>>>>>>

## this와 super
this 레퍼런스로 메서드를 호출하면,
=> ==**인스턴스 클래스(this의 실제 클래스, 예: A4)에서부터**== 메서드를 찾아 호출한다.
=> 현재 클래스에 메서드가 없으면 수퍼 클래스에서 메서드를 찾는다.
=> 메서드를 찾을 때까지 최상위 클래스까지 따라 올라간다.
this.m();

super 레퍼런스로 메서드를 호출하면,
=> **==수퍼 클래스(메서드가 소속된 클래스의 수퍼 클래스, 예: A)에서==** 메서드를 찾아 호출한다.
=> 수퍼 클래스에 없으면 그 상위 클래스로 따라 올라간다.
=> 오버라이딩 하기 전의 메서드를 호출하고 싶을 때 유용하다.
super.m();


## UML
![[Pasted image 20240708101436.png]]


### 설계 패턴

- 설계 패턴 -> 어떤 문제에 대한 검증된 해결 방식
- 검증된 해결 방식 -> 재사용성 증가, 유지보수 유리
- SOLID, GRASP에 부합

Creational Patterns (생성 패턴)
	- Factory Method
	- Singleton
		- 오로지 한 개의 인스턴스
		- 스태틱 필드가 낫지 않습니까? -> 그런 경우도 당연히 있다.
		- 인스턴스를 한 개만 만들어서 써야 할 상황이 있으면 어떻게 해결하겠냐
		- 생성자를 private으로 만들어서 new로 생성하지 못하도록 막은 뒤에
		- static method로 호출해서 만들게 한다.
		- getInstance로 호출할 때 오직 같은 인스턴스를 반환하도록 함
	- Prototype
	- Abstract Factory

Structural Patterns (구조 패턴)
	- Adapter
		- print 예제에서, 과거 프린터에 워터마크 기능이 추가된 신형 print
		- 기존 규칙에 다라 만들어진 걸 새 규칙에 맞춰 재사용하고 싶을 때 사용
		- Printer -> P1, P2 (기존 프린터 객체)
		- Printer2 -> P3, P4 (새 프린터)

Begavioral Patterns (행위 패턴)
	- Templete Method
		- 기본적인 흐름을 다 정해놓고, 세부적인 행위만 커스터마이징 하고 싶을 때 사용
		- 템플릿에서 사용할 메서드는 추상 메서드로 만들고, 서브 클래스에서 구현하도록 함
		- 러브레터, 래퍼토리레터의 예제에서 봤음
		- Print에 기본 구조를 만들어 놓고, (머릿말, 꼬리말, sign) 어떻게 사용할 지는 서브 클래스에서 구현하도록 함. 이것이 템플릿 메서드


### Iterator 설계 패턴

List
- 입력 순서대로 저장
- get(index)로 접근

Set
- 해시값으로 저장 위치 결정
- 중복 X
- toArray()로 받아서 접근해야 함 (하나씩 못꺼냄)

Map
- 키 객체로 값 저장
- key 중복 X
- value 중복 O
- get(key)로 접근

==문제점==
- 자료구조에 따라 데이터를 조회하는 방법이 다르다!

==해결==
- List, Set, Map의 조회 코드를 캡슐화하고, 사용 규칙을 통일한다.

\<\<interface>>
Iterator
+hasNext()
+next()

객체를 사용하는 쪽 -> Client 라고 부른다.
List, Set, Map의 조회 코드를 캡슐화하고, 사용 규칙을 통일한다.

### 중첩 클래스

before
AbstracitList.java
ListIterator.java

after
LinkedList.java include -> 

### Generic 문법 사용하기

## GoF의 Composite 설계 패턴
-> 객체가 트리 구조로 포함관계일 때

### before

App -> ==**<\<interface>> Command**== <- BoardCommand, ProjectCommand, UserCommand

App
- 메뉴 UI 제공

BoardCommand
- 게시판 메뉴 UI
- 게시판 CURD 처리

ProjectCommand
- 프로젝트 메뉴 UI 제공
- 프로젝트 CRUD 처리

UserCommand
- 회원 메뉴 UI 제공
- 회원 CURD 처리

문제점
- 메뉴 UI 제공 코드 중복
- Command 객체가 여러 개의 일을 수행

해결방법
- 메뉴 UI제공 코드를 캡슐화 -> 객체로 분리
- SOLID 원리 구현
- S -> Single Response Principle

### after

App.execute() -> <\<interface>>Menu <- MenuItem, MenuGroup

## lambda

```java
interface Player {
	void play();
}

// 추상메서드가 1개있는 인터페이스를 'Functional Interface'라 부른다.

class MyPlayer implements Player {
	public void play() {abcabc}
}

Player obj = new Player() {
	public void play() {abcabc}
}

Player obj = () -> {abcabc};

// -> functional interface인 경우 람다문법으로 구현 가능
```



### 파일 입출력

## Multi-tasking

- 한 개의 CPU로 여러 작업을 병행하여 처리

1. 윈도우 기준, 실행 파일(.exe)을 메모리에 로딩(Loading, 메모리에 프로그램을 올리는 과정)
2. 프로세스(실행중인 명령) 생성
3. 생성된 프로세스를 CPU에 로딩

1. 멀티 프로세싱
- Process -> 종료
-         fork -> 
- 별도의 실행으로 동시에 수행해야 할 작업이 있다면, 복제(fork)

concurrent - 병행 (1cpu, n-process)
parallel - 병렬 (n-cpu, m-process)



