한번만 생성하고 재생성되지 않는 객체를 만들 때
- 익명 함수 사용

```java
public class Example {
	interface Printer {
		void print();
	}

	Printer printer = new Printer() {
		@Override
		public void print() {
			System.out.println("Hello!");
		}
	}

	printer.print();
}
```

```java
// 1) 로컬 클래스 만들기

class X implements A {
	@Override
	public void print() {
		System.out.println("XXXXX");
	}
}
m1(new X());
  
// 2) 익명 클래스 만들기
A obj = new A() {
	@Override
	public void print() {
		System.out.println("익명 클래스!!!");
	}
};
m1(obj);
  
// 3) 익명 클래스를 파라미터 자리에 바로 삽입
m1(new A() {
	@Override
	public void print() {
		System.out.println("안녕!!!");
	}
});
```

람다 익명 정리

```java
public class Exam0450 {

// 인터페이스의 경우 static으로 선언하지 않아도 스태틱 멤버에서 사용할 수 있다.
	interface A {
		void print();
	}

	static A create5() {
		return new My()::m2;
	}
}

// 컴파일러는 위의 문장을 다음과 같이 바꾼다.
return () -> new My().m2();

// 컴파일러는 위의 문장을 다음과 같이 바꾼다.
return new A() {
	@Override
	public void print() {
		new My().m2();
	}
};

// 컴파일러는 위의 문장을 다음과 같이 바꾼다.
class X implements A{
	@Override
	public void print() {
		new My().m2();
	}
}
return new X();

```
