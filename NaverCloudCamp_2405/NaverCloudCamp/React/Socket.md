# 소켓의 일반적 사용

- 소켓 생성
- 소켓 연결
- 이벤트 핸들러 설정

위 기능을 특정 구조로 나누어 관리하는 것이 일반적
소켓 관련 코드의 위치와 방식은 애플리케이션의 구조와 목적에 따라 달라질 수 있음

## 1. 소켓 생성 위치

- 생성 위치
	- 애플리케이션의 전역 또는 상위 수준에서 생성
	- React에서는 context나 custom hook을 활용해 소켓 인스턴스를 앱 전반에 걸쳐 사용할 수 있게 설정함
	- 소켓은 앱 전반에서 여러 컴포넌트가 공유할 수 있는 연결 객체로, 중간에 여러 차례 연결을 새로 생성하는 것은 비효율적이기 때문

## 2. 첫 연결 시도 위치

- 연결 시기
	- 애플리케이션 초기화 시(ex-App 컴포넌트의 useEffect 내부) 한 번만 연결을 시도
	- 소켓 연결은 한 번만 맺고 이후에는 유지하는 것이 좋음
	- 연결 후 이벤트 핸들러를 설정하여 데이터를 수신할 준비를 함

## 3. 이벤트 핸들러 위치

- 이벤트 핸들러는 소켓 연결이 설정된 직후에 바로 설정
- 컴포넌트 또는 특정 모듈에서 정의하여 전달
