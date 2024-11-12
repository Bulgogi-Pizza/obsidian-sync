## Java package - 클래스를 분류하고 문법 폴더로 구현

1. 패키지명
	- 조직명.제품명.역할명. ------
	- 조직명 : Domain Name 사용, 정렬하기 편하게 거꾸로 사용
	- com.microsoft
	- com.oracle
	- com.bitcamp
	- com /
	- ㅏ microsoft/
	- ㅏ oracle/
	- ㅏ bitcamp

## markdown - HTML 태그보다 더 간결한 방식으로 문서의 형식을 지정하기 위해 만든 포맷

.md -> HTML 변환기 -> .html

## Array(배열)

- int[] arr = new int[5];
- new int[5] -> 배열의 인스턴스(instance) 실체적인 예
- int[] arr -> 배열 레퍼런스 -> 배열 인스턴스의 주소를 담는 변수
- index 최대 크기 : 메모리 할당 최대치 or Integer.MAX_VALUE - 2 (java VM Specification에 나와있음)

## 배열 레퍼런스와 가비지

- 주소를 잃어버려 사용할 수 없는 인스턴스 -> Garbage
- Garbage가 계속 생성되면 memory leak 오류 발생
- JVM 강제 종료
- JVM은 메모리가 부족하면, Garbage를 찾아 제거 -> Garbage collector

## Garbage Collector와 Reference Count

``` java
int[] arr1 = new int[3];
// ex) 200번지로 시작하는 int 자료형 배열 3칸 선언
// 인스턴스 200, 카운트 arr1

int[] arr2 = new int[4];
// ex) 300번지로 시작하는 int 자료형 배열 4칸 선언
// 인스턴스 300, 카운트 arr2


int[] arr3 = arr1;
// arr1의 인스턴스 200 부여, 카운트 arr1, arr3

arr1 = new int[2];
// ex) 400번지 int 자료형 배열 2칸 부여
// 인스턴스 200 카운트 arr1 제거, 400 카운트 arr1

arr3 = arr2;
// 인스턴스 200 카운트 Null (Garbage)
// 인스턴스 300 카운트 arr2, arr3
// 인스턴스 400 카운트 arr1
```
가비지 콜렉터는 **메모리가 부족할 때** 가비지를 청소함


## 배열 초기값
- 배열은 생성되는 즉시 자동으로 초기화 됨

`int[] arr1 = new int[3];` -> 0으로 초기화
`float[] arr2 = new float[2];` -> 0.0으로 초기화
`char[] arr3 = new char[4];` -> '\u0000'으로 초기화 **공백 아님**
`boolean[] arr4 = new boolean[3];` -> false로 초기화
`String[] arr5 = new String[3];` -> null로 초기화 (String은 레퍼런스이기 때문에 주소값이 없다는 뜻인 null로 초기화)

## 배열 초기화

`int[] arr1 = new int[]{100,200,300};` -> 3개 만듦
`int[] arr2 = {100,200,300}` -> new int[] 생략 가능
`int[] arr3;`
`arr3 = {100,200,300};` -> 레퍼런스를 만든 후 따로 배열을 생성할 때 생략 불가!

## 인스턴스와 메서드

인스턴스
- 피연산자

레퍼런스.메서드();

레퍼런스
- 도구를 실행하는 데 사용할 기본 데이터가 있는 인스턴스의 주소
- 도구를 실행할 때 필요한 데이터
- 피연산자(operand)

메서드
- 도구
- 연산자(operator)

()
- 도구를 실행할 때 사용할 추가 데이터

## 클래스 메서드와 인스턴스 메서드

### Math.abs(-100); (클래스.메서드)
- return 100

Math
- 클래스
- abs() 도구를 실행하는데 기본 Data는 필요 없음

abs
- 메서드

(-100)
- abs() 를 실행할 때 사용할 Data
- argument

예) 자전거.움직인다(힘);

## System.out.println("Hello"); (인스턴스.메서드)

out
- 인스턴스
- println()도구를 실행하는 데 필요한 기본 데이터

println
- 메서드

("Hello")
- 추가 데이터

## System.in, System.out, System.err

![[Pasted image 20240611110932.png]]
## 표준 입력 제어

![[Pasted image 20240611112325.png]]
> [!warning] 오타 수정
> cat -> echo

## println()과 출력 시스템 정보

출력 시스템 정보
- 데이터를 어디로 출력해야 하는지에 대한 정보
- -> "출력 스트림"

출력스트림.println("Hello");

출력스트림
- System.out -> 콘솔창
- 파일 출력 스트림 -> 파일로 출력
- 소켓 출력 스트림 -> 네트워크로 출력

## read()와 입력 시스템

입력스트림.read();


## static

추가 정보 없이 사용 가능

## String 사용법

- String s;
- s = null;
- reference 변수이기 때문에 주소가 없다는 뜻의 null을 넣을 수 있음
- String은 primitive 변수가 아님, reference 변수임
- 그래서 s는 reference이고, 인스턴스의 주소를 저장함
- reference 변수 확인법 -> null 넣어보기
- String 리터럴 (ex."aaa")은 별도의 영역에서 관리함
- String 리터럴 영역에 같은 문자열을 가진 인스턴스가 있다면 기존 인스턴스의 주소를 리턴, 없다면 새로 만든 후에 인스턴스주소를 리턴
- new String("aaa")는 리터럴 영역에 "aaa"가 있든 없든 무조건 인스턴스 주소를 리턴
```java
String s = new String("aaa");
String s2 = new String("aaa"); //aaa를 담을 메모리(200번지, String 인스턴스)를 준비하고, s에 그 주소를 넣음
String test = new String("aaa"); //aaa를 담을 메모리(300번지, String 인스턴스)를 준비하고, s2에 그 주소를 넣음

String s3 = "aaa";
String s4 = "aaa";

System.out.println(s == s2); //false
System.out.println(s == s3); //false
System.out.println(s3 == s4); //true
System.out.println(test == s4); //true
System.out.println(test == s3); //true

s3 = "hi";

System.out.println(s3 + s4 + test);
System.out.println(s3 == s4); //true
System.out.println(test == s4); //true
System.out.println(test == s3); //true
```

## String 배열

- String[] menus = new String[]{"회원","팀","프로젝트"----};
- -> 레퍼런스 배열
- menus 주소 = 200
- menus[0] 주소 = 1500 // String literal 영역에서 "회원"이 저장된 메모리 주소
- menus[1] 주소 = 1600 // String literal 영역에서 "팀"이 저장된 메모리 주소

- "회원", "팀" 등의 주소가 연속적으로 만들어지느냐! ㄴㄴㄴ 빈자리가 있으면 채울 뿐임
- 그래서 menus[2] 주소 = 2100, menus[3] 주소 = 1900 쌉가능

## Method - 명령문 묶음

UML(Unified Modeling Language)을 사용해서 코드를 골라 그림으로 표현

## Method

리턴타입 메서드명(파라미터, ...) // method signature = function prototype
{
	명령문
	~~~~~
	~~~~~
} // method body

## JVM의 클래스 실행
![[Pasted image 20240612101548.png]]
## 멀티스레드
![[Pasted image 20240612101959.png]]

## parameter(파라미터)와 argument(아규먼트)

void m1 (String n, int a){
	// String n, int a -> parameter
}
public static void main (){
	m1("ss", 20);
	//"ss", 20 -> argument
}

## JVM Stack

- 메서드가 사용할 로컬 변수 저장됨

## Heap

- new 명령으로 생성한 인스턴스
- Garbage가 존재해 청소 대상 구역

## Method Area

- 클래스 코드
- 클래스 피르
- 상수 리터럴

## 클래스

- 인스턴스 멤버 (this 생략 가능)
	- 인스턴스 메서드
	- 인스턴스 변수

- 스태틱 멤버