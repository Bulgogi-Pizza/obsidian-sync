* 참고 문헌 : eomcs-docs/devtool-userguide/mysql-settings.txt
## 1. 로그인

### 로그인

$mysql -u root -p
- -h 서버주소
- -u 아이디
- -p : 패스워드 입력할 예정

### 사용자 생성

create user '아이디'@'호스트' identified by '암호';

아이디 : 로그인 ID
호스트 : 접속 허용 서버
- 도메인
- IP주소
- % (외부 모든 서버)

### 사용자 비밀번호 변경

alter user '사용자'@'호스트' identified by '암호';
