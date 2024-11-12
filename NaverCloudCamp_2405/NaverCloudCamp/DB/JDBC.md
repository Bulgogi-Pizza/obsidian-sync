# JDBC 프로그래밍 절차

1. getConnection() -> DriverManager
	1. jdbc:mysql://study/1111
2. DriverManager -> connect()
3. 등록된 Driver로 DBMS 연결
	1. OracleDriver
	2. SQLServerDriver
	3. Driver (MySQL)
4. DriverManager가 Connection return
