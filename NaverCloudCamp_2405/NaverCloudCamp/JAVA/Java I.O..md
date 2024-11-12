## File 클래스
- 디렉토리나 파일을 다룰 때 사용하는 클래스
- 디렉토리나 파일을 생성, 삭제, 변경할 수 있음
- JVM을 실행하는 위치가 현재 폴더

```java
File currentDir = new File("./src/main/java");
System.out.println(currentDir.getName());
```

### File 클래스 메서드

getName() - 현재 폴더명
getPath() - 상대경로명
getAbsolutePath() - 절대경로명
getCanonicalPath() - 계산된 절대경로
length() - 파일 크기
getTotalSpace() - 총 크기
getFreeSpace() - 남은 크기
getUsableSpace() - 가용 크기

isDirectory() - 디렉토리 여부
isFile() - 파일 여부
isHidden() - 감춤 여부
exists() - 존재 여부
canExecute() - 실행 가능 여부

mkdir() - 디렉토리 생성
mkdirs() - 디렉토리 생성 (지정된 경로에 디렉토리가 존재하지 않으면 그 디렉토리도 만듦)
delete() - 디렉토리 삭제

createNewFile() - 파일 생성