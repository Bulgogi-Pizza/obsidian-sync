## ThemeProvider
- @mui/material/styles/ThemeProvider
- Material-UI에서 제공하는 컴포넌트
- React 앱 전체에 일관된 테마를 적용할 수 있게 해줌
- [[#241107 App.js 코드]]에서는 [[#createTheme]]으로 생성한 커스텀 테마를 앱에 전달하는 역할을 함
- 필요성
	- 테마의 중앙 집중화
	- 유지보수성 향상
	- 디자인 일관성

# createTheme
- @mui/material/styles/createTheme

# createContext
- react/createContext
- 컴포넌트 간 데이터를 쉽게 공유할 수 있도록 Context를 생성하는 데 사용됨
- 일반적으로 props를 통해 부모-자식 관계로 데이터를 전달해야 하지만, createContext를 사용하면 컴포넌트 트리 어디서든 필요한 데이터를 바로 접근할 수 있음