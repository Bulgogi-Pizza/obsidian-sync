
# 241107 App.js 코드

```JS
import "./App.css";  
import React, { useEffect, useState } from "react";  
import { SidebarProvider } from "./context/SidebarContext";  
import Login from "./pages/login/Login";  
import Router from "./shared/Router";  
import { UserProvider } from "./context/UserContext";  
import { ThemeProvider, createTheme } from "@mui/material/styles";  
import { SocketProvider } from "./context/SocketContext";  
  
const theme = createTheme({  
  typography: {  
    fontFamily: "Pretendard-Regular", // 선택한 폰트 설정  
  },  
});  
  
function App() {  
  const [isLoggedIn, setIsLoggedIn] = useState(false);  
  
  const handleLoginSuccess = () => {  
    setIsLoggedIn(true);  
  };  
  
  return (  
    <ThemeProvider theme={theme}>  
      <UserProvider>        <SidebarProvider>          {isLoggedIn ? (  
            <Router /> // 로그인 후 Router 화면  
          ) : (  
            <Login /> // Login 컴포넌트  
          )}  
        </SidebarProvider>  
      </UserProvider>    </ThemeProvider>  );  
}  
  
export default App;
```

# App.js Logic

[[React 컴포넌트#ThemeProvider|ThemeProvider]]
	[[#UserProvider]]
		[[#SidebarProvider]]
			isLoggedIn ?
				Router :
				[[#Login]]


## UserProvider 
- UserContext = [[React 컴포넌트#createContext|createContext()]] 생성
	```js
	return (
		<UserContext.Provider value={{ userInfo, setUserInfo }}>
			{children}
		</UserContext.Provider>
	);
	```
	- userInfo
		- 초기값으로는 로컬 스토리지에 저장되어있는 userInfo를 저장
		- setUserInfo로 값이 바뀌면 로컬 스토리지의 userInfo 갱신
	- 로컬 스토리지에서 초기값 가져옴
- userInfo -> userInfo가 담겨있는 변수
- setUserInfo -> userInfo set useState

## SidebarProvider
- sidebarOpen의 boolean 변수를 로컬 스토리지에 저장하는 컴포넌트
- toggleSidebar를 호출하면 setOpen에서 현재 상태를 토글하여 open 변수를 설정함
- open -> Sidebar 오픈 여부 변수
- toggleSidebar -> Sidebar 오픈 여부 토글 함수

## Login
- isLoading, setIsLoading - true
- isLoggedIn, setInLoggedIn - localStorage.getItem("token")


# 최초

# 변경사항
- #1
	- UserProvider와 SidebarProvider의 동작 방식 통일
	- SidebarProvider
		- SidebarProvider의 context export 방식
			- useSidebar() => return useContext(SidebarContext)
		- SidebarProvider의 context 사용 방식
			- const { } = useSidebar()
	- UserProvider
		- UserProvider의 context export 방식
			- export const UserContext = createContext();
		- UserProvider의 context 사용 방식
			- const { } = useContext(UserContext);
	-> useSidebar의 방식을 채택하고 UserProvider의 context export 방식을 수정하기로 결정
	-> 결정 사유 : useSidebar는 SidebarContext와 SidebarProvider의 특정 데이터 구조를 캡슐화하여 일관된 API를 제공함 -> useSidebar의 내부 구조에 의존하지 않음
	- TopBar, LoginForm, QuestionListDTO, Profile 파일 수정 완료
- #2
	- LoginProvider 생성
		- isLoggedIn useState를 관리하고, isLoggedIn의 상태가 변하면 로컬스토리지의 값을 변경하는 컴포넌트
- #3
	- SocketProvider 생성

# 발표
## 변경사항
- 도메인 변경
- 댓글 한 번에 2개 등록 막음
- 이전 강의의 투표 및 질의응답, 게시판 등 조회를 위해서는 새로운 아이디 만들기로 결정
- 배치도 그림과 강의실 페이지의 좌석 배치 통일 (진행중)
