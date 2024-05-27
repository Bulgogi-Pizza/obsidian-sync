- S/W 형상관리 시스템 (S/W Configuration Management System; SCM)
- 모양 변경 관리 = 버전 관리 시스템 (version)
- version -> 변경에 대해 부여한 구분 번호 (식별자)

git

- git (server) ↔ PC (client)
- git-scm.com
- SCM : software configuration management (소프트웨어 형상 관리)
- CLI : command line interface (명령줄 인터페이스) → 글자를 입력하여 명령을 내리는 방식
- CLI 기반에 익숙해져야 함, git client에서 GUI 방식과 CLI 방식이 있는데, CLI 방식에 익숙해지길 권장
- git clone 주소 (github 주소 내 파일 복사)
- git pull (repository 폴더 내에서 업데이트 된 사항만 가져옴)

github,com --운영-> Git Server [bitcamp-study] <-저장소(Repository; Repo.)--

개발자 --사용-> Git Client --서비스 이용-> Git Server

git clone
-> $git clone httls://github.com/eomjinyoung/bitcamp-study
-> github.com 의 eomjinyoung 사용자의 bitcamp-study Repository에서
-> Local의 폴더로 복제

git add / commit / push

git add .
- 현재 폴더 및 하위 폴더의 모든 파일을 백업 대상 파일로 등록

git commit -m "백업 내용"
- -m 은 메세지를 뜻함, 백업 파일 목록에 등록된 파일을 저장소에 보관

git push
- 서버 저장소에 업로드

git pull
- 서버 저장소의 변경 내용 가져오기

build.gradle
- 

Local Repository

