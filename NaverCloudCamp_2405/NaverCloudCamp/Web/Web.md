# 쿠키

## 쿠키란?

- 서버에 의해 응답받은 정보가 브라우저에 저장되는 데이터 저장 방식
- 주로 인증정보에 사용
- 클라이언트측에서 저장을 하기보다, 서버쪽에서 HTTP 응답헤더 set-cookie에 내용을 넣어 응답하면 브라우저가 해당 내용을 저장
- 해당 쿠키를 생성하도록 한 서버(사이트)에 접속할 때마다 쿠키의 내용이 요청헤더에 담겨 함께 전달됨

## 쿠키 저장 순서

1. 사용자가 로그인을 요청하면 서버가 응답헤더 set-Cookies에 정보를 저장해 응답
2. 브라우저가 해당 정보를 쿠키에 자동 저장
3. 같은 도메인 (명시에 따라 서브도메인포함)에 정보를 요청하면 요청 HTTP Cookie헤더에 인증정보가 함께 담겨 서버로 요청
4. 서버가 요청 헤더를 읽어 사용자를 식별

## 쿠키에 접근하기

- 자바스크립트를 통해 쿠키에 접근하거나 쿠키를 작성하는 것이 가능
- document.cookie속성을 사용하면 됨
- cookie 프로퍼티는 데이터 프로퍼티가 아닌 접근자 프로퍼티!