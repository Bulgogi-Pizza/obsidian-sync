## #레퍼런스 #reference
- 메모리의 주소를 보관하는 변수 ex) 배열
- `int[] arr1 = new int[5]` 에서 `arr1`

## #인스턴스 #instance
- 값을 저장하기 위해 확보된 메모리
- `int[] arr1 = new int[5]` 에서 `new int[5]` 로 할당된 메모리

```java
class Person {
    String name;
}

public class Main {
    public static void main(String[] args) {
        // Person 객체의 인스턴스를 생성하고, 이를 p라는 참조변수가 가리키게 함
        Person p = new Person();
        
        // p는 Person 객체의 참조 (reference)
        // new Person()은 Person 클래스의 인스턴스 (instance)
    }
}
```

## #new
- 메모리를 확보하는 명령
- 리턴 값은 확보된 메모리의 시작 주소

## #가비지 #garbage
- 주소를 잃어버려 사용할 수 없는 인스턴스(메모리)
```java
int[] arr1;
arr1 = new int[5];
arr1[0] = 100;
arr1 = new int[] {200, 200, 200};
//처음 초기화한 new int[5]의 메모리는 garbage가 됨
```

## #파라미터 #parameter 와 #아규먼트 #argument

parameter : 매개변수
argument : 인자

``` java
int parseInt(String s){

}

Interger.parseInt("100");
```
s -> parameter (argument를 담을 변수)
100 -> argument (method를 호출할 때 parameter에 전달하는 값)

실무에서는 parameter와 argument를 구별하지 않고 호칭

## #method #메서드 , #method_body #method_signature #method_call

```java
public static void main(){
	m1(); // method_call
	m1();
	m1();
}


static void m1() // method_signature 
{
	System.out.println("Hello");
} //method_body
```

## #Annotation, #애노테이션


## #접근제어자, #private, #default, #protected, #public
private = 같은 클래스 내에서만 가능
(default) = 같은 클래스나 같은 패키지 내에서만 가능
protected = 같은 패키지 or 서브 클래스인 경우 자신의 멤버라면 접근 가능
public = 다른 패키지, 다른 클래스 모두 가능

## #JVMStack, #Heap, #StringConstancePool
JVMStack - 
Heap - 
StringConstancePool - String 상수 리터럴이 저장되는 공간

## #immutable, #mutable 
immutable 객체 - 인스턴스의 데이터가 한번 정해지면 변하지 않는 객체 (ex.String)
그래서 String 레퍼런스에 또 다른 String 인스턴스 값을 저장하려 할 때, 값이 바뀌는 것이 아니라 다시 생성됨 
mutable 객체 -인스턴스의 데이터를 변경할 수 있음 (ex.StringBuffer, StringBuilder)

## #GRASP

General Responsibility Assignment Software Patterns
- 객체지향 설계에서 객체의 책임을 할당하는 데 도움을 주는 일련의 원칙과 패턴
- 객체지향 시스템을 설계할 때 객체 간의 협력을 어떻게 구성할지를 결정하는 데 사용
- 설계자가 소프트웨어의 유지보수성과 유연성을 높이는 데 도움을 줌
- Craig Larman이 "Applying UML and Patters"에서 제안한 것

### #Information_Expert #정보_전문가

> [!info] Information Expert
> - 책임을 수행하는 데 필요한 정보를 가지고 있는 객체에게 책임 할당
> - 이를 통해 응집도가 높은 설계를 유도

```java
// 도서관 시스템에서, 책 대출 기록을 관리하는 책임은 '대출 기록' 정보를 가지고 있는 'Loan' 객체에 할당

class Loan {
	private Book book;
	private User user;
	private Date dueDate;

	public Loan(Book book, User user, Date dueDate) {
		this.book = book;
		this.user = user;
		this.dueDate = dueDate;
	}

	public boolean isOverdue() {
		return new Date().after(dueDate);
	}
}
```

### #Creator #생성자

> [!info] Creator
> - 특정 객체를 생성할 책임을 다른 객체에게 할당하는 원칙
> - 생성할 객체와 밀접하게 관련된 객체에게 생성 책임을 부여

```java
// 도서관 시스템에서, 'Library' 객체는 'Book' 객체를 생성
class Library {
	public Book createBook(String title, String author) {
		return new Book(title, author);
	}
}
```

### #Controller #조정자

> [!info] Controller
> - 시스템 이벤트를 처리하는 책임을 가지는 객체를 정의
> - 일반적으로 사용자 인터페이스와 도메인 로직 사이의 중재 역할을 함

```java
// 웹 애플리케이션에서, 'OrderController'는 사용자 요청을 처리
class OrderController {
	public void handleOrderRequest(int orderId) {
		Order order = Order.find(orderId);
		order.process();
	}
}
```

### #Low_Coupling #낮은_결합도

> [!info] Low Coupling
> - 객체들 간의 의존성을 최소화하여 시스템의 유연성과 재사용성을 높임
> - 결합도가 낮은 설계는 유지보수가 용이

```java
// 'PaymentProcessor'와 'Order' 간의 결합도를 낮추기 위해 인터페이스를 사용
interface PaymentProcessor {
	void processPayment(Order order);
}

class PayPalProcessor implements PaymentProcessor {
	public void processPayment(Order order) {
		// PayPal payment processing logic
	}
}

class Order {
	private PaymentProcessor paymentProcessor;

	public Order(PaymentProcessor paymentProcessor) {
		this.paymentProcessor = paymentProcessor;
	}

	public void completeOrder() {
		paymentProcessor.processPayment(this);
	}
}
```

### #High_Cohesion #높은_응집도

> [!info] High Cohesion
> - 하나의 객체가 밀접하게 관련된 책임만을 가질 수 있도록 설계
> - 응집도가 높은 객체는 이해하기 쉽고 유지보수가 용이

```java
// 'User' 클래스는 사용자 관련 책임만 가짐
class User {
	private String name;
	private String email;

	public User(String name, String email) {
		this.name = name;
		this.email = email;
	}

	public void updateEmail(String newEmail) {
		this.email = newEmail;
	}
}
```

### #Polymorphism #다형성

다형성 (_명사_)
- 1.
    생명 같은 종(種)의 생물이면서도 어떤 형태나 형질이 다양하게 나타나는 현상. 예를 들면 암수에 따라 크기, 형태, 색깔따위가 차이 나는 것이다.

> [!info] Polymorphism
> - 변하는 행위를 캡슐화하고, 상속과 인터페이스를 통해 다형성 구현
> - 이를 통해 코드의 유연성과 확장성을 높임

```java
// 서로 다른 'Notification' 타입을 처리하기 위해 다형성을 사용

interface Notification {
	void send();
}

class EmailNotification implements Notification {
	public void send() {
		System.out.println("Sending email notification");
	}
}

class SNSNotification implements Notification {
	public void send() {
		System.out.println("Sending SMS notification");
	}
}
```

### #Pure_Fabrication #순수_가공

> [!info] Pure Fabrication
> - 도메인 모델에 직접적으로 존재하지 않지만, 설계의 유연성과 재사용성을 높이기 위해 인공적으로 만들어진 클래스
> - 예를 들어, 데이터베이스 접근 클래스 등이 해당

```java
// 'DataMapper' 클래스는 데이터베이스 접근을 담당
class UserMapper {
	public User findUserById(int userId) {
		// Database access code to find a user by ID
		return new User("John Doe", "john@example.com");
	}
}
```

### #Indirection #간접

> [!info] Indirection
> - 두 객체 사이의 직접적인 연결을 피하고, 중간 객체를 통해 간접적으로 연결
> - 이는 결합도를 낮추고 설계의 유연성을 높이는 데 도움을 줌

```java
// 'ServiceLocator'를 사용해 서비스 객체를 찾음
class ServiceLocator {
	public static PaymentProcessor getPaymentProcessor() {
		return new PayPalProcessor();
	}
}

class Order {
	private PaymentProcessor paymentProcessor;

	public Order() {
		this.paymentProcessor = ServiceLocator.getPaymentProcessor();
	}

	public void completeOrder() {
		paymentProcessor.processPayment(this);
	}
}
```

### #Protected_Variations #변경_보호

> [!info] Protected Variations
> - 변경이 발생할 가능성이 있는 지점을 식별하고, 이를 캡슐화하거나 인터페이스로 보호
> - 이를 통해 변경의 영향을 최소화하고 시스템의 안정성을 높임

```java
// 'PaymentProcessor' 인터페이스를 통해 결제 처리 구현을 보호
interface PaymentProcessor {
	void processPayment(Order order);
}

class PayPalProcessor implements PaymentProcessor {
	public void processPayment(Order order) {
		// PayPal payment processing logic
	}
}

class StripeProcessor implements PaymentProcessor {
	public void processPayment(Order order) {
		// Stripe payment processing logic
	}
}

class Order {
	private PaymentProcessor paymentProcessor;

	public Order(PaymentProcessor paymentProcessor) {
		this.paymentProcessor = paymentProcessor;
	}

	public void completeOrder() {
		paymentProcessor.processPayment(this)
	}
}
```

## #SOLID 


### #Single_Responsibility_Principle #단일책임원칙

- 클래스는 하나의 책임만 가져야 함
- 즉, 클래스를 변경해야 하는 이유는 오직 하나뿐이어야 함
- 
### #Open_Closed_Principle #개방-폐쇄원칙

- 소프트웨어 개체(클래스, 모듈, 함수 등)는 확장에는 열려 있어야 하고, 수정에는 닫혀 있어야 함

### #Liskov_Substitution_Principle #리스코프치환원칙

### #Interface_Segregation_Principle #인터페이스분리원칙

### #Dependency_Inversion_Principle #의존관계역전원칙

- Liskov Substitution Principle (리스코프 치환 원칙)
- Interface Segregation Principle (인터페이스 분리 원칙)
- Dependency Inversion Principle (의존관계 역전 원칙)



## #Interface

- 메소드의 집합을 정의하는 타입
- 
- 추상 클래스
	- 서브 클래스에게 공통 변수 공통 메서드를 상속해주는 문법
- 인터페이스
	- 클래스가 반드시 가져야 할 메서드를 정의하는 것
	- 객체 사용 규칙을 정의하는 문법

- **목적**
	1. 표준화
		- 클래스들이 특정 메소드를 반드시 구현하도록 강제함으로써, 일관된 방식으로 동작하도록 표준화
	2. 다형성
		- 서로 다른 클래스들이 같은 'interface'를 구현함으로써, 공통의 인터페이스 타입을 통해 객체를 다룰 수 있게 함, 이는 코드의 유연성과 확장성을 높임
	3. 구현의 분리
		- 인터페이스를 통해 구현 세부 사항을 숨기고, 인터페이스를 사용하는 코드가 구체적인 구현에 의존하지 않도록 함

- **특징**
	- 메소드 선언 : 인터페이스는 구현체가 반드시 제공해야 하는 메소드의 서명을 포함하지만, 실제 구현은 포함하지 않음
	- 다중 상속 : 자바와 같은 언어에서 클래스는 단일 상속만 가능하지만, 인터페이스는 여러 개 구현 가능

- **이점**
	- 코드 재사용성 : 인터페이스를 사용하면 서로 다른 클래스들이 동일한 인터페이스를 구현함으로써, 코드를 재사용하기 쉬움
	- 유연성 : 코드가 인터페이스를 통해 상호작용하면, 구현체를 쉽게 교체할 수 있어 유연성이 높아짐
	- 유지보수성 : 인터페이스를 사용하면 코드의 각 부분이 분리되어 유지보수와 확장이 용이함

- **예제**
```java
// 인터페이스 정의
interface PaymentProcessor {
	void processPayment(double amount);
}

// 인터페이스 구현
class PayPalProcessor implements PaymentProcessor {
	public void processPayment(double amount) {
		System.out.println("Processing payment of $" + amount + " through PayPal.");
	}
}

class StripeProcessor implements PaymentProcessor {
	public void processPayment(double amount) {
		System.out.println("Processing payment of $" + amount + " through Stripe.");
	}
}

// 인터페이스 사용
public class PaymentService {
	private PaymentProcessor processor;

	public PaymentService(PaymentProcessor processor) {
		this.processor = processor;
	}

	public void makePayment(double amount) {
		processor.processPayment(amount);
	}

	public static void main(String[] args) {
		PaymentProcessor paypal = new PayPalProcessor();
		PaymentProcessor stripe = new StripeProcessor();

		PaymentService paypalService = new PaymentService(paypal);
		PaymentService stripeService = new PaymentService(stripe);

		paypalService.makePayment(100.0);
		stripeService.makePayment(100.0);
	}
}

```


## #UML #Unified_Modeling_Language

- James, Grady, IvaiYagopson 3 Amigo


## #DesignPattern

Java의 디자인 패턴은 소프트웨어 설계에서 자주 반복되는 문제를 해결하기 위한 일반적인 솔루션을 제공. 각 패턴은 특정한 문제 상황에 적합하며, 사용하면 코드의 재사용성, 확장성, 유지보수성을 높일 수 있음. 디자인 패턴은 크게 생성(Creational), 구조(Structural), 행동(Behavioral) 패턴으로 분류

### 1. **생성 패턴 (Creational Patterns)**

   객체 생성과 관련된 패턴으로, 객체 생성 과정을 캡슐화하여 클라이언트 코드에 유연성을 제공

   - **싱글톤 패턴 (Singleton Pattern)**
     - **상황:** 클래스의 인스턴스가 오직 하나만 필요할 때 사용. 예를 들어, 애플리케이션 전체에서 공유해야 하는 설정 정보나 로그 파일 등을 관리할 때 유용
     - **사용:** 단일 인스턴스의 생성을 제어하고, 어디서나 동일한 인스턴스를 사용하도록 보장

   - **팩토리 메소드 패턴 (Factory Method Pattern)**
     - **상황:** 객체 생성 로직이 복잡하거나, 생성되는 객체의 유형이 동적으로 결정될 필요가 있을 때 사용
     - **사용:** 객체 생성을 서브클래스에서 담당하게 함으로써, 클라이언트 코드에서 객체 생성 로직을 분리

   - **추상 팩토리 패턴 (Abstract Factory Pattern)**
     - **상황:** 관련된 객체들(제품군)의 생성을 일관되게 해야 할 때 사용합니다. 예를 들어, 서로 다른 UI 테마에 따라 다양한 UI 컴포넌트를 생성할 때 유용
     - **사용:** 인터페이스를 통해 관련된 객체들의 군을 생성하는 방법을 제공

   - **빌더 패턴 (Builder Pattern)**
     - **상황:** 복잡한 객체를 단계별로 생성하거나, 생성 과정에서 다양한 옵션을 조합해야 할 때 사용합니다. 예를 들어, 복잡한 생성자 파라미터가 있는 객체를 생성할 때 유용
     - **사용:** 객체 생성 과정에서 유연성을 제공하고, 객체를 구성하는 다양한 부분을 독립적으로 조립할 수 있음

   - **프로토타입 패턴 (Prototype Pattern)**
     - **상황:** 생성할 객체의 종류가 프로토타입을 복제해서 생성할 수 있을 때 사용합니다. 새로운 객체를 만들기보다 기존 객체를 복사하여 성능을 개선할 수 있음
     - **사용:** 새로운 객체를 생성할 때 비용이 많이 들거나 복잡한 경우에 기존 객체를 복제하여 사용

### 2. **구조 패턴 (Structural Patterns)**

   클래스나 객체를 조합해 더 큰 구조를 만드는 패턴으로, 객체 간의 관계를 정의하는 데 중점을 둠

   - **어댑터 패턴 (Adapter Pattern)**
     - **상황:** 기존 클래스의 인터페이스가 요구사항과 맞지 않을 때 사용합니다. 예를 들어, 새로운 인터페이스에 맞게 기존 클래스를 재사용하고 싶을 때 유용
     - **사용:** 서로 다른 인터페이스를 가진 클래스를 연결하여 호환성을 제공

   - **브리지 패턴 (Bridge Pattern)**
     - **상황:** 추상화와 구현을 분리하여 서로 독립적으로 변경할 수 있게 할 때 사용합니다. 예를 들어, UI의 플랫폼별 구현을 독립적으로 관리하고 싶을 때 유용
     - **사용:** 추상화와 구현을 별도의 클래스 계층으로 분리하여 둘을 독립적으로 확장할 수 있도록 함
  
   - **컴포지트 패턴 (Composite Pattern)**
     - **상황:** 객체들이 부분-전체 관계를 가질 때 사용합니다. 예를 들어, 트리 구조의 데이터를 처리할 때 유용
     - **사용:** 개별 객체와 그 객체들의 모음을 동일하게 취급할 수 있도록 구조화

   - **데코레이터 패턴 (Decorator Pattern)**
     - **상황:** 객체에 기능을 동적으로 추가하거나 확장할 때 사용합니다. 예를 들어, 다양한 방식으로 객체의 기능을 조합해야 할 때 유용
     - **사용:** 상속 대신 구성(composition)을 사용하여 객체의 기능을 확장

   - **퍼사드 패턴 (Facade Pattern)**
     - **상황:** 복잡한 서브시스템을 단순하게 사용할 수 있도록 인터페이스를 제공할 때 사용합니다. 예를 들어, 복잡한 라이브러리의 사용을 간소화할 때 유용
     - **사용:** 서브시스템의 여러 복잡한 인터페이스를 하나의 간단한 인터페이스로 통합

   - **플라이웨이트 패턴 (Flyweight Pattern)**
     - **상황:** 대량의 객체를 메모리 효율적으로 관리할 때 사용합니다. 예를 들어, 동일한 데이터를 공유하는 여러 객체를 효율적으로 관리할 때 유용
     - **사용:** 공유 가능한 객체들을 플라이웨이트로 만들어 메모리 사용을 최소화
  
   - **프록시 패턴 (Proxy Pattern)**
     - **상황:** 접근 제어나 비용이 많이 드는 리소스의 관리를 위해 대리 객체를 사용할 때 사용합니다. 예를 들어, 원격 서비스나 파일 시스템 접근을 제어할 때 유용
     - **사용:** 실제 객체에 대한 접근을 제어하거나, 그 접근 전후에 별도의 작업을 수행

### 3. **행동 패턴 (Behavioral Patterns)**

   객체나 클래스 간의 상호작용과 책임 분담을 정의하는 패턴

   - **책임 연쇄 패턴 (Chain of Responsibility Pattern)**
     - **상황:** 여러 객체 중 하나가 요청을 처리해야 할 때 사용합니다. 예를 들어, 이벤트 핸들링 체인이나, 권한 체계에서 유용
     - **사용:** 요청을 여러 객체 중 하나가 처리할 수 있도록 연결된 객체들 간에 전달
  
   - **커맨드 패턴 (Command Pattern)**
     - **상황:** 작업을 객체로 캡슐화하여 작업의 실행, 취소, 재실행 등을 제어할 때 사용합니다. 예를 들어, UI 버튼 클릭 시 수행할 작업을 명령 객체로 표현할 때 유용
     - **사용:** 실행될 기능을 객체로 캡슐화하고, 실행 요청을 클라이언트와 수신자 객체로부터 분리
  
   - **인터프리터 패턴 (Interpreter Pattern)**
     - **상황:** 언어의 문법을 정의하고, 해당 언어로 표현된 문장을 해석할 때 사용합니다. 예를 들어, SQL 파서나 표현식 평가기에서 유용
     - **사용:** 특정 도메인 언어의 문법을 표현하고, 그 문법에 따라 문장을 해석하는 구조를 정의
  
   - **이터레이터 패턴 (Iterator Pattern)**
     - **상황:** 컬렉션의 내부 구조를 노출하지 않고도 컬렉션 내의 모든 요소에 접근할 수 있도록 할 때 사용
     - **사용:** 컬렉션의 요소를 순차적으로 접근할 수 있는 방법을 제공
  
   - **중재자 패턴 (Mediator Pattern)**
     - **상황:** 객체들 간의 복잡한 상호작용을 간단하게 처리하고 싶을 때 사용합니다. 예를 들어, 여러 객체가 서로 통신할 때 중재자를 두어 상호작용을 관리
     - **사용:** 객체들 간의 상호작용을 캡슐화하고, 객체들이 직접 통신하지 않도록 함
  
   - **메멘토 패턴 (Memento Pattern)**
     - **상황:** 객체의 상태를 저장하고 복원해야 할 때 사용합니다. 예를 들어, 되돌리기 기능을 구현할 때 유용
     - **사용:** 객체의 내부 상태를 저장하여 나중에 복원할 수 있도록 함
  
   - **옵저버 패턴 (Observer Pattern)**
     - **상황:** 한 객체의 상태 변화가 다른 객체들에게 자동으로 통보될 필요가 있을 때 사용합니다. 예를 들어, 이벤트 리스너 시스템에서 유용
     - **사용:** 객체 간의 의존 관계를 정의하고, 객체의 상태 변화 시 등록된 다른 객체들에게 자동으로 알림을 보냄
  
   - **상태 패턴 (State Pattern)**
     - **상황:** 객체의 내부 상태에 따라 행동이 달라져야 할 때 사용합니다. 예를 들어, UI 컴포넌트의 상태 변화에 따른 행동 변화를 관리할 때 유용
     - **사용:** 객체의 상태를 객체화하여 상태에 따른 행동을 캡슐화
  
   - **전략 패턴 (Strategy Pattern)**
     - **상황:** 알고리즘을 동적으로 변경해야 할 때 사용합니다. 예를 들어, 정렬 방식이나 경로 탐색 알고리즘을 런타임에 변경할 때 유용
     - **사용:** 특정 작업을 수행하는 다양한 알고리즘을 인터페이스화하고, 클라이언트가 런타임에 알고리즘을 선택할 수 있도록 함
  
   - **템플릿 메소드 패턴 (Template Method Pattern)**
     - **상황:** 알고리즘의 골격을 정의하고, 세부적인 구현은 서브클래스에서 결정할 때 사용합니다. 예를 들어, 여러 단계로 구성된 프로세스를 정의하고 각 단계를 하위 클래스에서 구현할 때 유용
     - **사용:** 알고리즘의 구조를 정의하고, 일부 단계를 서브클래스에서 구현하도록 함
  
   - **비지터 패턴 (Visitor Pattern)**
     - **상황:** 객체 구조에 새로운 연산을 추가할 때, 기존 구조를 변경하지 않고 연산을 추가하고 싶을 때 사용합니다. 예를 들어, 복잡한 객체 구조에서 다양한 연산을 수행할 때 유용
     - **사용:** 연산을 객체 구조 외부에 정의하고, 구조의 각 요소가 해당 연산을 수용하도록 함

### #static #non-static #instance

static (정적)
- 클래스나 메소드, 필드에 'static' 키워드가 붙으면, 그것들은 클래스 레벨에서 존재
- 즉, 특정 인스턴스에 종속되지 않고 클래스 자체에 속함
- 


non-static (인스턴스)

### #static-nested-class #non-static-nested-class

## #블로킹메서드 #Blocking-Method

다른 입력이 들어올 때까지, 신호가 들어올 때까지 기다리는 메서드

```java
Scanner in = new Scanner(socket.getInputStream);
in.nextLine(); // 입력값이 들어올 때까지 대기한다. (블로킹 메서드)
```

ServerSocket.accept(); 등

## #프로토콜 #Protocol

클라이언트와 서버 간의 데이터를 주고 받는 통신 규칙을 프로토콜(protocol)이라 함

### #직렬화 #Serialization #역직렬화 #Deserialization
직렬화
- 객체의 상태를 바이트 스트림으로 변환하는 과정
- 이를 통해 객체를 파일, 데이터베이스, 네트워크 등으로 전송할 수있음
- 사용 예 : 객체를 파일에 저장하거나 네트워크를 통해 전송할 때

역직렬화
- 바이트 스트림을 다시 객체로 변환하는 과정
- 직렬화된 데이터를 읽어 객체로 복원
- 사용 예 : 파일에서 객체를 읽어오거나 네트워크를 통해 받은 데이터를 객체로 변환할 때

### #푸시백 #Pushback

푸시백 
- 스트림에서 읽은 데이터를 다시 스트림에 되돌려 놓는 기능
- 이를 통해 다음 읽기 작업에서 다시 읽을 수 있음
- 사용 예 : 파서나 스캐너에게 토큰을 읽다가 다시 돌려놓고 싶은 경우

```java
PushbackInputStream pushbackIn = new PushbackInputStream(new FileInputStream("data.txt"));
int data = pushbackIn.read();
pushbackIn.unread(data); // 데이터를 다시 스트림에 넣음
```


## #Field, #Property

```java
public class User implements Serializable {  
  
  private int no;       // 필드 (field)
  private String name;  // 필드 (field)
  private String email; // 필드 (field)
  
  public int getNo() {return no;}  // getter                          //property
  public void setNo(int no) {this.no = no;} // setter                 //property
  
  public String getName() {return name;}  // getter                   //property
  public void setName(String name) {this.name = name;} // setter      //property
  
  public String getEmail() {return email;}  // getter                 //property
  public void setEmail(String email) {this.email = email;} // setter  //property
}
```

property = getter + setter

setCreateDate() {-}
-> createDate = property Name

## #컴포넌트

- 단일 객체보다는 여러 복합체의 느낌이 강함
- 한 개 이상의 객체로 구성되어 특정 작업을 수행하는 것