
### break label
```java
myloop:
	while (x <= 9) {
		while (y <= 9) {
			System.out.println("test" + x + y);
			if (x == 5 && y == 5){
				break myloop;
			}
			y++;
		}
		x++;
	}
System.out.println("종료!!");
```
- x와 y가 모두 5일 때, break 제어문을 통해 하나의 루프를 탈출하는 것이 아닌, myloop에 소속된 문장을 탈출함


### for (변수타입 변수 : 배열 or Iterable 구현체)
- 배열 전체를 반복하거나 컬렉션 객체(java.util.Iterable 구현체) 전체를 반복할 때 유용함
```java
String[] names = {"홍길동", "임꺽정", "유관순", "윤봉길", "안중근"};

for (String name : names){
	System.out.println(name);
}
```

### java.util.ArrayList
```java
import java.util.ArrayList;
public class ArrayListTest{
	public static void main(String[] args){
		ArrayList list = new ArrayList();
		list.add("홍길동");
		list.add(3.14f);
		list.add(true);
		list.add(365);
		
		for (int i = 0; i < list.size(); i++){
			System.out.println(list.get(i));
		}
		
		//for 문에 컬렉션도 적용 가능
		//for (변수 선언 : 컬렉션객체) 문장;
		for (Object value : list){
			System.out.println(value);
		}
	}
}
```

### printf("%\[n$]s")
```java
System.out.printf("%d %1$x %1$c\n", 65);
System.out.printf("%3$d %1$x %2$c\n", 65, 66, 67); // 3$(67), 1$(65), 2$(66)
```
출력
65 41 A
67 41 B

### printf("%\[-,+,0]\[사용할공간너비]s)
```java
System.out.printf("'%-10s' '%10s'\n", "홍길동", "임꺽정");
System.out.printf("'%-10d' '%10d'\n", 12345, 12345);
System.out.printf("'%010d' '%07d'\n", 12345, 12345);
System.out.printf("'%+010d' '%+07d'\n", 12345, -12345);
```
출력
'홍길동       ''       임꺽정'
'12345     ''     12345'
'0000012345' '0012345'
'+000012345' '-012345'

\- : 왼쪽 정렬, 안 붙이면 기본 오른쪽 정렬
\+ : 숫자 앞에 부호 붙임
\0 : 앞의 빈자리는 0으로 채움

### 가변 파라미터

가변 파라미터는 반드시 맨 끝에 와야 하고 두 개 이상의 가변 파라미터는 설정 못함
static void m1(String... names, String... emails) - 불가
static void m2(String... names, String a) - 불가

\[리턴타입] 메서드명(타입... 변수) {}
```java
static void hello(String... names) {
	for (int i = 0; i < names.length; i++) {
		System.out.printf("%s님 반갑습니다.\n", names[i]);
	}
}

public static void main(String[] args) {
	hello();
	hello("홍길동", "임꺽정", "유관순");

	String[] arr = {"김구", "안중근", "윤봉길", "유관순"};
	hello(arr);
}
```

### Clone Override

- Clone은 Object Class에서 protected로 정의되어 있어 동일 클래스, 동일 패키지, 상속 클래스(같은 멤버 한정)에서만 접근이 가능한데, 상속 클래스 중 타 인스턴스로 Clone에 접근하기 위해서는 Clone을 Public으로 Override 해서 써야 함

```java
public class Exam0174 {
	static class Engine implements Cloneable {
		int cc;
		int valve;
		
		public Engine(int cc, int valve){
			this.cc = cc;
			this.valve = valve;
		}

		@Override
		public Engine clone() throws CloneNotSupportedException {
		return (Engine) super.clone();
		}
	}

	public static void main(String[] args) throws Exception {
		Engine engine = new Engine(3000, 16);
	
		Engine engine2 = engine.clone();

		System.out.println(engine2.cc);
		engine2.cc = 5000;
		System.out.println(engine2.cc);
		System.out.println(engine.cc);
	}
}
```

- Deepcopy가 잘 진행되는 것을 알 수 있음

### equals(), equalsIgnoreCase()

- equals -> 대소문자 구분 비교
- equalsIgnoreCase -> 대소문자 구분 없이 비교

### getName()

\[B, \[L 등 \[ 가 오고 그 뒤에 알파벳이 오는 경우 배열이라는 뜻. B = byte

``` java
System.out.println(obj2.getClass().getComponentType().getName()); //java.lang.String
System.out.println(new int[10].getClass().getComponentType().getName()); //int
System.out.println(classInfo.getName()); //[Ljava.lang.String;

Class compTypeInfo = classInfo.getComponentType();
System.out.println(compTypeInfo.getName()); //java.lang.String
```

### String.intern();

String 레퍼런스가 가리키는 String 인스턴스를 String 상수 풀에 생성, 있으면 기존 것 사용

### a instanceof b

리턴값 : boolean
a가 b의 인스턴스인지 검사

### StringBuffer, StringBuilder

StringBuilder
Thread-Safe 보장 안함
동시에 여러 스레드가 들어와서 값을 바꿀 때 제약을 두지 않음 (막지 않음)
즉, 같은 객체를 여러 스레드가 다룰 수 있을 때는 StringBuffer가 안전함

StringBuffer
Thread-Safe
동시에 여러 스레드가 접근할 것을 대비해서, 호출하는 순간 잠가버림 그러나 잠그고 푸는 데에 시간이 걸리므로 StringBuilder가 안전하지는 않지만 더 빠름

### Arrays.copyOfRange(arr, from, to);

배열 복사

```java
import java.util.Arrays;

arr2 = Arrays.copyOfRange(arr1, 2, 4); //(array, from, to)
```

### Eclipse와 String Encoding Type

-> 기본 문자 포맷 : UTF-8
`String s6 = new String(bytes2, "utf-16");

byte 배열 bytes2를 utf-16으로 인코딩하여 String 레퍼런스 s6에 넣으라는 뜻

### Wrapper 클래스

int i = 100; // int 변수

Interger obj = Integer.valueOf(i); // Integer의 레퍼런스 변수에 Integer의 인스턴스 생성

int i2 = obj.intValue();

int값을 인스턴스에 담는 것 -> 박싱(Boxing)
인스턴스에 있는 값을 Primitive Variable에 다시 꺼내어 넣는 것 -> 언박싱(Unboxing)

Integer obj = 100; // ==> Integer.valueOf(100)

obj는 레퍼런스인데 어떻게 가능한가?
=> 내부적으로 Integer.valueOf(100) 호출 코드로 바뀐다.
=> 즉 int 값이 obj에 바로 저장되는 것이 아니라,
내부적으로 Integer 객체가 생성되어 그 주소가 저장된다.
=> 이렇게 int 값을 자동으로 Integer 객체로 만드는 것을
"오토박싱(auto-boxing)"이라 한다.

### Date d1 = new Date(); // 현재 시각을 저장

Date d2 = new Date(System.currentTimeMillis()); // d1과 같음

System.out.println(d2);

### Calendar.getInstance(); // 현재 날짜와 시각을 저장
Calendar c1;

// 생성자가 있다하더라도 접근 권한이 없으면 호출할 수 없다.
// c1 = new Calendar(); // 컴파일 오류!
// Calendar는 인스턴스 생성을 도와주는 별도의 클래스 메서드(스태틱 메서드)를 제공한다.

c1 = Calendar.getInstance();

System.out.println(c1.get(1)); // year
System.out.println(c1.get(2) + 1); // month
System.out.println(c1.get(5)); // date
System.out.println(c1.get(10)); // hour
System.out.println(c1.get(9)); // am/pm
System.out.println(c1.get(12)); // minute
System.out.println(c1.get(13)); //seconds

System.out.println(c1.get(Calendar.YEAR));
System.out.println(c1.get(Calendar.MONTH) + 1);
System.out.println(c1.get(Calendar.DATE));
System.out.println(c1.get(Calendar.HOUR));
System.out.println(c1.get(Calendar.AM_PM));
System.out.println(c1.get(Calendar.MINUTE));
System.out.println(c1.get(Calendar.SECOND));

### 인스턴스 블럭 Instance Block

{
// 인스턴스 블럭
// 생성자 실행 시 해당 블럭 내의 코드가 가장 먼저 수행됨
}

### Generic 문법

```java
class Node {
	Object value;

}

Node n = new Node();
// node의 value라는 변수에 String, Date, User, Project 등을 담을 수 있음
// -> 다형적 변수
// -> 다형적 변수의 특성상 해당 타입의 서브 클래스객체까지 저장할 수 있음
// -> 특정 타입의 객체만 저장하도록 제한할 수 없을까?
// -> "Generic"
n.value
```

```java
class Node<What> {
	What value;
	// What이 어떤 타입인지 사용할 때 지정
	// 보통 제네릭 타입은 정해져 있는 대문자 하나로 하는 게 국룰
	// -> Type Parameter = 보통 T
	// T (Type)
	// E (Element)
	// K (Key)
	// V (Value)
	// S,U,V (2nd, 3rd, 4th Types)
	// class ClassName<T>
	// T value;
	// 이런식
}

// Node<String> n = new Node<String>();
// 레퍼런스에서 사용할 타입을 지정해줬다면 생략 가능
Node<String> n = new Node<>();

n.value
// -> n.value에는 String 타입의 객체만 저장할 수 있음
```

### try-with-resources catch finally

AutoCloseable 인터페이스
```Java
public interface AutoCloseable {
	void close() throws Exception;
}
```

try (변수 = AutoCloseable 객체) {
	변수 사용
} catch (예외 내용) {
	예외 처리 코드
} finally {
 예외가 발생하든 발생하지 않든 반드시 실행되어야 하는 코드
 example
 - 자원 해제
	 - 네트워크 연결
	 - 파일 핸들
	 - 데이터베이스 연결
 - 정리 작업
	 - 임시 파일 삭제
	 - 잠금 해제
 - 로그 작성
	 - 실행 완료 로그
	 - 상태 로그
}

## public \<T> List\<T> (Class\<T> type)
개념 확인

## public List\<T> (~)
차이 확인

## 클래스 정보 추출

### Reflection API
```java

```

### 메서드 정보 추출
```java
Class<?> clazz = Exam01.class;

// Class<?>.getMethods();
// 해당 클래스에 선언됨 public 메서드 + 상속 받은 public 메서드
Method[] list = clazz.getMethods();

//Class<?>.getMethod(메서드 이름) 
// 해당 클래스에 선언된 public 메서드 + 상속 받은 public 메서드 중에서
// 파라미터가 없는 "m1" 이름을 가진 메서드 추출
Method m1 = clazz.getMethod("m1");

//Class<?>.getDeclaredMethod(메서드 이름)
// public이 아닌 메서드를 찾고 싶다면
Method m2 = clazz.getDeclaredMethod("m2");
```
