SQL은 대소문자 구분 없음

# DDL (Data Definition Language)

**-DB 객체(테이블, 뷰, 프로시저, 함수, 트리거) 등을 생성, 변경, 삭제하는 SQL 명령-**

## 데이터베이스

### 데이터베이스 생성
```SQL
create database 데이터베이스명 옵션들...;

create database testdb 
	default character set utf8 
	default collate utf8_general_ci;
```
### 데이터베이스 조회
```SQL
show databases;
```
### 데이터베이스 삭제
```SQL
drop database 데이터베이스명;
```
### 데이터베이스 변경
```SQL
alter database 데이터베이스명 옵션들...;
```

## 테이블

### 테이블 생성
```SQL
create table 테이블명 (
	컬럼명 타입 NULL여부 옵션,
	컬럼명 타입 NULL여부 옵션,
	...
	컬럼명 타입 NULL여부 옵션
);

create table test01 (
	name varchar(50) not null,
	kor int not null,
	eng int not null,
	math int not null,
	sum int not null,
	aver float not null
);
```

### 테이블 정보 보기
```SQL
describe 테이블명;
desc 테이블명; -- 실무에선 해당 명령을 많이 씀

desc test01;
```

### 테이블 삭제
```SQL
drop table 테이블명;

drop table test01;
```

### 테이블 컬럼 옵션

#### null 허용
- 데이터를 입력하지 않아도 됨
```SQL
create table test1 (
	no int,
	name varchar(20)
);
```

#### not null
- 데이터를 입력하지 않으면 입력/변경 거절
```SQL
create table test1 (
	no int not null,
	name varchar(20)
);

insert into test1(no, name) values(null, 'bbb'); -- 실행 오류
```

#### 기본값 지정
- 입력 값을 생략하면 해당 컬럼에 지정된 기본값이 대신 입력됨
```SQL
create table test1(
	no int not null,
	name varchar(20) default 'noname',
	age int default 20
);

insert into test1(no, age) values(1, 30);
--          test1(no, name, age) values(1, 'noname', 30);
```

### 컬럼 타입

#### int
- 4바이트 크기의 정수 값 저장
- 기타
	- tinyint(1바이트)
	- smallint(2바이트)
	- mediumint(3바이트)
	- bigint(4바이트)

#### float
- 부동소수점 저장

#### numeric = decimal
- 전체 자릿수와 소수점 이하의 자릿수를 정밀하게 지정 가능
- numeric(n, e) : 전체 n 자릿수 중 소수점 e 자릿수
	- 예) numeric(10,2) : 12345678.91
- numeric : numeric(10, 0) 과 같음
- 소수점은 반올림 처리됨

#### char(n)
- 최대 n개의 '문자'를 저장
- 0 <= n <= 255
- 고정 크기를 가짐
- 한 문자를 저장해도 n자를 저장할 크기를 사용
- 메모리 크기가 고정되어 검색 시 빠름
- DBMS 중에 고정 크기인 컬럼의 값을 비교 시 빈자리까지 검사하는 경우가 있음
- 즉 c1='abc'에서는 데이터를 찾지 못하고 c1='abc  '여야만 데이터를 찾는 경우가 있음
- mysql은 고정크기 컬럼이더라도 빈자리 무시하고 데이터 찾음

#### varchar(n)
- 최대 n개의 '문자'를 저장
- 0 ~ 65535 바이트 크기를 가짐
- n 값은 문자 집합에 따라 최대 값이 다름
	- ISO-8859-n : 65535자
	- UTF-8 : 21844자
- 가변 크기를 가짐
- 한 문자를 저장하면 한 문자 만큼의 메모리 차지
- 메모리 크기가 가변적이라 검색 시 느림

#### char(n) vs varchar(n)

- char(n)
	- 고정형
	- 데이터베이스를 생성할 때 지정한 charset에 따라 한 글자의 메모리 크기가 결정됨
	- 저장된 글자 개수에 상관없이 무조건 5글자를 저장할 메모리 크기 가짐
	- char(5) 'aaa' = 'aaa__(공백)'

- varchar(n)
	- 가변형
	- 글자 개수만큼 메모리 크기를 가짐
	- varchar(5) 'aaa' = 'aaa'

#### text
- 긴 텍스트를 저장할 때 사용하는 컬럼 타입
- text(65535), mediumtext(약 1.6MB), longtext(약 4GB)
- 오라클의 경우 long(2GB)과 CLOB(character large object)(4GB)이 있음

#### date
- 날짜 정보를 저장할 때 사용
- 년, 월, 일 정보를 저장
- 오라클의 경우 날짜 뿐 아니라 시간 정보도 저장
```SQL
insert into test1(c1) values('2022-02-21');
```

#### time
- 시간 정보를 저장할 때 사용
- 시, 분, 초 정보를 저장
```SQL
insert into test1(c2) values('16:12:35');
```

#### datetime
- 날짜와 시간 정보를 함께 저장할 때 사용
```SQL
insert into test1(c1) values('2022-02-21 16:13:33');
```

#### boolean
## row와 column

| 번호  | 이름  | 이메일   | 암호   | 전화   |
| --- | --- | ----- | ---- | ---- |
| 1   | 홍길동 | hong@ | 1111 | 010- |
| 2   | 임꺽정 | leam@ | 2222 | 010- |
| 3   | 유관순 | yoo@  | 3333 | 010- |
| 4   | 안중근 | ahn@  | 4444 | 010- |
ㅡ 방향 : row = record = tuple
- 탐색 (Selection)
ㅣ 방향 : column = filed = attribute
- 탐색 (Projection)

한 row의 크기가 한 (record + varchar)의 경우 65535 byte가 넘을 수 없다
긴 텍스트를 저장할 때는 text(1.6KB), mediumtext(1.6MB), longtext(4GB)

# DML (Data Manipulation Language)

**-데이터 등록, 변경, 삭제를 다루는 SQL 문법-**

## insert
- 데이터를 입력할 때 사용하는 문법

```SQL
create table test1 (
	no int not null,
	name varchar(20) not null,
	tel varchar(20) not null,
	fax varchar(20),
	pstno varchar(5),
	addr varchar(200)
);

insert into 테이블명 values(값, .....);
insert into table1 values(null, 'aaa', '111', '222', '10101', 'seoul');

-- column 지정해 값 입력 가능
insert into test1(name, fax, tel, no, pstno, addr)
	values('bbb', '222', '111', null, '10101' ,'seoul');

-- no 가 not null이지만 Primary Key + auto_increment 라면
-- 따로 입력해주지 않아도 자동으로 삽입
insert into

-- 여러 값 한 번에 입력 가능
insert into test1(name, tel) values
	('aaa', '1111'),
	('bbb', '2222'),
	('ccc', '3333');

-- select로 가져온 값 입력 가능
-- 단 타입이 같아야하고 담을 공간의 메모리가 충분히 커야함
create table test2 (
	no int primary key auto_increment,
	fullname varchar(20) not null,
	phone varchar(20) not null,
	kor int,
	eng int,
	math int
);

insert into test2(fullname,phone)
	select name, tel from test1 where addr='seoul';
```

## update
- 등록된 데이터를 변경할 때 사용하는 명령

```SQL
update 테이블명 set 컬럼명=값, 컬럼명=값, ... where 조건...;
update test1 set pstno='11111', fax='222' where no=3;

--조건을 지정하지 않으면, 모든 데이터에 대해 변경하니 주의!!!
update test1 set fax='333';
```

## delete
- 데이터를 삭제할 때 사용하는 명령

```SQL
delete from 테이블명 where 조건;
delete from test1 where no=2 or no=3;

--조건을 지정하지 않으면, 모든 데이터가 삭제되니 주의!!!
delete from test1;
```

## autocommit
- mysql은 autocommit의 기본값이 true
- 따라서 명령창에서 SQL을 실행하면 바로 실제 테이블에 적용됨
- 수동으로 처리하고 싶다면 autocommit을 false로 설정
- 실수할 가능성이 있을 땐 autocommit을 false로 하면 비교적 안전하게 처리 가능

```SQL
set autocommit=false;
-- 이제 insert/update/delete를 수행한 후 승인을 해야만 실제 테이블에 적용됨

commit;

-- 마지막 commit 상태로 되돌리고 싶다면
rollback;

-- 예시 1
insert into test1(name, tel) values('xxx', '1111');
insert into test1(name, tel) values('yyy', '2222');
insert into test1(name, tel) values('zzz', '2222');
update test1 set fax='1212' where name='xxx';
delete from test1 where no=1;
rollback; -- 지금까지 작업한 insert, update, delete은 취소

-- 예시 2
insert into test1(name, tel) values('xxx', '1111');
insert into test1(name, tel) values('yyy', '2222');
insert into test1(name, tel) values('zzz', '2222');
commit; -- 지금까지 한 작업을 테이블에 적용

update test1 set fax='1212' where name='xxx';
delete from test1 where no=1;
rollback; -- 마지막 commit 이후에 수행한 insert, update, delete은 취소

```

### autocommit
- insert, update, delete 등 데이터 상태 변경 명령을 실행할 때 즉시 적용

1. client -> Thread - SQL 전송
2. Thread -> DBMS - 데이터 변경 적용
- Thread : client요청 쿼리를 담당하는 스레드

### 수동 commit
- insert, update, delete 등 데이터 상태 변경 명령을 버퍼(cache)라는 임시 저장소에 보관 후 commit 명령과 함께 적용

1. client -> Thread - SQL 전송
2. Thread -> 버퍼(cache) - 임시 저장
3. client -> Thread - commit 명령 전송
4. 버퍼(cache) -> DBMS - 버퍼에 임시 보관되었던 실행 결과를 실제 테이블에 적용

1. client -> Thread - SQL 전송
2. Thread -> 버퍼(cache) - 임시 저장
3. client -> Thread - rollback 명령 전송
4. 버퍼(cache)에 임시적으로 보관되었던 실행 결과를 삭제

# DQL (Data Query Language)

**-데이터를 조회할 때 사용하는 문법-**

# FK(Foreign Key)

- 다른 테이블의 PK를 참조하는 컬럼
- 테이블의 데이터 간 관계를 파악
- 다른 테이블의 PK를 가리킴
- 없는 PK를 저장할 수 없음

## 다대다 관계를 다루기
![[Pasted image 20240818182508.png]]

## DB에 파일 저장
- 테이블에 파일 저장 vs 파일을 분리해서 저장 (Foreign Key)
	- 테이블에 파일 저장
		- 테이블에 파일 저장 시 파일 안에 파일이 저장되는 방식
		- -> 파일을 읽고 쓸 때 매우 느려짐
	- 파일을 분리해서 저장
		- 테이블에 파일 시스템의 파일 경로 저장
		- 파일 시스템으로부터 파일 불러옴


참조되는 테이블 = Parent 테이블
참조하는 테이블 = Child 테이블
1 대 다의 경우
1이 Parent, 다가 Child인 경우가 많음


다대다인 경우 별도 테이블로 분리하여 저장


# SQL 문장 실행 순서

from -> where -> select -> order by -> 결과 추출

select rno, name, concat(loc,'-',name) as name2 --- 3
from room --- 1
where available=true --- 2
order by loc asc, name2 asc; --- 4

# Join
- 서로 관련된 테이블의 데이터를 연결하여 추출하는 방법

## 1) Cross Join (=Cartesian product)
- 두 테이블의 데이터를 1:1로 모두 연결
```SQL
-- bno 컬럼이 두 테이블에 모두 존재한다.
-- 따라서 어떤 테이블의 컬럼인지 지정하지 않으면 실행 오류!
select bno, title, content, fno, filepath
from board1 cross join attach_file1;

-- select 컬럼이 두 테이블에 모두 있을 경우,
-- 컬럼명 앞에 테이블명을 명시하여 구분하라!
select board1.bno, title, content, fno, filepath, attach_file1.bno
from board1 cross join attach_file1;
  
-- cross join 고전 문법 */
-- cartesian join
select board1.bno, title, content, fno, filepath, attach_file1.bno
from board1, attach_file1;
  
-- 컬럼명 앞에 테이블명을 붙이면 너무 길다.
-- 테이블에 별명을 부여하고 그 별명을 사용하여 컬럼을 지정하라.
select b.bno, title, content, fno, filepath, a.bno
from board1 as b cross join attach_file1 as a;
  
-- as는 생략 가능
select b.bno, title, content, fno, filepath, a.bno
from board1 b cross join attach_file1 a;
  
-- 고전 문법
select b.bno, title, content, fno, filepath, a.bno
from board1 b, attach_file1 a;
```
![[Pasted image 20240813120454.png]]

## 2) Natural Join
- 같은 이름을 가진 컬럼 값을 기준으로 레코드를 연결
- 상관 없는 Using이나 On 없이 사용할 경우 상관없는 데이터끼리 조인될 수 있음
```SQL
-- 같은 이름을 가진 컬럼 값을 기준으로 레코드를 연결한다.
select b.bno, title, content, fno, filepath, a.bno
from board1 b natural join attach_file1 a;
  
-- 고전 문법
select b.bno, title, content, fno, filepath, a.bno
from board1 b, attach_file1 a
where b.bno = a.bno;
```

## 3) JOIN ~ USING(컬럼명)
- 어떤 컬럼값을 기준으로 조인할 지 지정할 수 있음
![[Pasted image 20240818203817.png]]

- 같은 이름을 가진 컬럼이 없을 경우 한계를 맞이함
![[Pasted image 20240818203957.png]]

## 4) JOIN ~ ON (inner join)

## 5) OUTER JOIN