
## 포트번호

- 호스트에서 실행 중인 서버 프로그램을 구분하는 번호
- 1024 ~ 49151 사이의 값 사용
- 1 ~ 1023 사이의 포트 번호는 특정 서버가 사용하기 위해 미리 예약된 번호
- 가능한 사용하지 않는 것이 좋음
- 유명 프로그램의 포트 번호도 가급적 사용하지 않는 것이 좋음
	- Oracle DBMS(1521), MySQL DBMS(3306), 프록시 서버(8080) 등
- 같은 컴퓨터에서 다른 프로그램이 이미 사용중인 포트 번호는 지정할 수 없음

## 연결 (서버)

- 서버(Server)
	- 네트워크 연결을 기다리는 쪽

```JAVA
// 1. 다른 컴퓨터의 연결 요청 기다림 (대기열에 요청을 올려둠)
//    - 대기열 기본 개수 = 50
//    - 대기열을 초과하여 요청이 들어왔을 때에는 서버 응답 X
ServerSocket serverSocket = new ServerSocket(포트번호, 대기열크기);

// 2. 연결을 기다리는 클라이언트가 있다면 연결 승인
Socket socket = serverSocket.accept();

// 3. 사용 종료 후 닫기
socket.close();
serverSocket.close();
```

## 연결 (클라이언트)

- 클라이언트(Client)
	- 연결을 요청하는 쪽

```JAVA
// 1. 다른 컴퓨터와 네트워크로 연결 (대기열에 등록)q
//    - 서버와 연결되면 Socket 객체 생성
//    - 서버와 연결될 때까지 리턴 X
//    - 서버에 연결할 수 없으면 예외 발생 (기본 타임아웃 시간까지)
Socket socket = new Socket("127.0.0.1", 8888);

// 2. 사용 종료 후 닫기 (연결 끊기)
socket.close();
```

## 입출력 스트림 + 데코레이터

- 소켓 객체를 통해 읽고 쓸 수 있도록 입출력 스트림을 얻음
- 연결된 클라이언트로 데이터를 보내고 받으려면 입출력 스트림을 꺼내야 함
- 소켓이 리턴해준 입출력 스트림에 적절한 데코레이터를 붙여서 사용


```JAVA
// PrintStream, Scanner
// 텍스트 형식의 출력 작업 지원
PrintStream out = new PrintStream(socket.getOutputStream());
Scanner in = new Scanner(socket.getInputStream());

// 사용 종료 후 닫기
in.close();
out.close();
```

```JAVA
// ObjectXXXXXStream
// 객체를 직렬화(출), 역직렬화(입)하여 입출력
#직렬화 #역직렬화
ObjectOutputStream out = new ObjectOutputStream(socket.getOutputStream());
ObjectInputStream in = new ObjectInputStream(socket.getInputStream());

// 사용 종료 후 닫기
in.close();
out.close();
```

```JAVA
// DataXXXXXStream
// 기본 데이터 타입을 이진 형식으로 입출력

// 버퍼를 가지지 않은 데이터 입출력 스트림
DataOutputStream out = new DataOutputStream(socket.getOutputStream());
DataInputStream in = new DataInputStream(socket.getInputStream());

// 버퍼를 가지는 데이터 입출력 스트림
DataOutputStream out = new DataOutputStream(new BufferedOutputStream(socket.getOutputStream()));
DataInputStream in = new DataInputStream(new BufferedOutputStream(socket.getInputStream()));

long filesize = in.readLong(); // out.writeLong(file.length());
String filename = in.readUTF(); // out.writeUTF(file.getName());

// 파일 데이터 읽기
File file = new File("temp/ok_" + filename);
FileOutputStream outFile = new FileOutputStream(file); // NoneBuffered
BufferedOutputStream outFile = new BufferedOutputStream(new FileOutputStream(file)); // Buffered

for (long i = 0; i < filesize; i++) {
    outFile.write(in.read());
}

// 파일 데이터 보내기
File file = new File("경로");
FileInputStream inFile = new FileInputSream(file); // NoneBuffered
BufferedInputStream outFile = new BufferedInputStream(new FileInputStream(file)); // Buffered


int b;
count = 0;
while ((b = fileIn.read()) != -1) {
    out.write(b);
    count++;
    if (count % 1024 == 0) {
        System.out.println("1KB 보냄!");
    }
}
out.flush();

// 사용 종료 후 닫기
inFile.close();
outFile.close();
in.close();
out.close();
```

```java
// BufferedXXXXXStream
// 입출력 성능을 향상시키기 위해 데이터를 버퍼링

BufferedOutputStream bufferedOut = new BufferedOutputStream(out);
BufferedInputStream bufferedIn = new BufferedInputStream(in);

bufferedOut.write(data);
bufferedOut.flush();

int data = bufferedIn.read();

// 사용 종료 후 닫기
bufferedIn.close();
bufferedOut.close();
in.close();
out.close();
```

### 그 외 데코레이터

1. PushbackInputStream
- 기능 : 읽은 데이터를 다시 스트림에 푸시백 할 수 있음

2. LineNumberInputStream
- 기능 : 읽은 데이터에서 줄 번호를 추적

3. CipherXXXXXStream
- 기능 : 데이터를 암호화 복호화 하여 입출력

4. Zip, GZIPXXXXXStream
- 기능 : 데이터를 ZIP,GZIP형식으로 압축하여 입출력

5. CheckedXXXXXStream
- 기능 : 데이터를 체크섬하여 무결성 확인 입출력

## 입출력 메서드
### writeInt
### writeByte
### writeFloat
### writeUTF
### readInt
### readByte
### readFloat
### readUTF

## Stateful, Stateless

### Stateful
- 한번 연결 후 요청이 완전히 끝날 때 까지 요청이 끊어지지 않고 계속해서 수행됨

이점
- 연결되어 있는 동안 클라이언트의 작업 결과를 계속 유지할 수 있음
- 요청에 대한 응답이 빠름
- 영속성이 필요한 작업을 처리하는데 유리
- 작업 시간 = (데이터 전송 시간) + (작업 처리 시간) + (데이터 수신 시간)

단점 
- 다중 클라이언트 요청 시 한 클라이언트의 요청이 끝날 때 까지 다른 클라이언트의 요청을 받지 못함
	- 해결책 : 별도의 스레드로 분리하여 독릭접으로 실행하게 함
- 서버 메모리를 많이 차지함

예시
- 게임 서버 연결 : 서버에 한 번 연결되면 게임을 마칠 때까지 데이터를 주고받음
- 화상 통신 : 한 번 연결하면 연결을 끊을 때까지 데이터를 주고받음
- 채팅 서버 : 전용 클라이언트를 이용한 채팅 (유튜브 라이브 방송 채팅)
- 텔넷 : 원격 제어 프로그램
- FTP : 파일 전송 프로그램
- 오프라인 예: 건강보험문의, 상담 등

### Stateless
- 한번 연결 후 하나의 요청을 처리한 뒤 바로 연결을 끊음

이점
- 다중 클라이언트 요청 시 여러 요청을 순차적으로 처리할 수 있음
- 메모리를 적게 사용함

단점
- 연결이 끊어져 클라이언트의 작업 결과를 유지할 수 없음
	- 해결책 : 클라이언트의 요청을 저장하는 변수를 선언함
- 요청할 때마다 매번 서버에 연결해야 하기 때문에 실행 시간이 많이걸림
- 작업 시간 = (연결하는데 걸린 시간) + (데이터 전송 시간) + (작업 처리 시간) + (데이터 수신 시간)

예시
- HTTP 통신 : 웹 브라우저가 서버에 연결한 후 요청을 하고 서버가 응답한 후 연결 끊음
- 메신저 : 메신저 서버에 연결하고 메시지 전송 후 연결 끊음
- 메일 전송 : 메일서버에 데이터 전송 후 연결 끊음

해결책 예시 (서버)
```java
static Map<Long, String> resultMap = new HashMap<>();
static int clientNum = 1;

public static void main(String[] args) throws Exception {
	ServerSocket ss = new ServerSocket(8888);

	while (true) {
		Socket socket = ss.accept();
		processRequest(socket);
	}
}

static void processRequest(Socket socket) throws Exception {
	try (Socket socket2 = socket;
		DataInputStream in = new DataInputStream(socket.getInputStream());
		DataOutputStream out = new DataOutputStream(socket.getOutputStream());) {
		
		long clientId = in.readLong();
		String result;
		
		if (clientId == 0) {
			clientId = clientNum;
			++clientNum;
			System.out.println("신규 고객 요청 처리");
			result = new String();
		} else {
			System.out.println("기존 고객 요청 처리");
			result = resultMap.get(clientId);
		}
		result += in.readUTF();
		
		resultMap.put(clientId, result);
		out.writeLong(clientId);
		out.flush();
	}
}
```

## 소켓 정보

```java
ServerSocket ss = new ServerSocket(8888);
Socket socket = ss.accept();
InetSocketAddress remoteAddr = (InetSocketAddress) socket.getRemoteSocketAddress();

// 연결된 클라이언트의 주소
remoteAddr.getAddress();
// 연결된 클라이언트의 포트
remoteAddr.getPort();
```

## Connection-Oriented

