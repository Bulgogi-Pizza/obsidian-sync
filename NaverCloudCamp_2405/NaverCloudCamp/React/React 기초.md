
# React
- 싱글 페이지 어플리케이션
- 실제로는 index.html 페이지 하나이지만,
- 메뉴를 불러올 때마다 div 태그를 계속 바꿔가면서 페이지를 바꾸는 것
- 기존에는 메뉴를 들어갈 때마다 서버에서 데이터를 불러와야 해서 느렸지만
- React, Vue.js 는 싱글 페이지의 div 내에서 갱신이 이루어짐

## #Routing
- 메뉴를 클릭할 때마다 react 컴포넌트를 매핑시킨 후 보여지게 하는 것
- Mapping -> Rendering
- npm install react-router-dom을 사용하여 패키지를 설치하면 자동으로 package.json에 추가되며 패키지가 적용됨
- react-router-dom에서 BrowserRouter라는 것을 브라우저에서 라우팅 할 때 일반적으로 가장 많이 사용함

```jsx
import Home from "./pages/Home";
import About from "./pages/About";
import React from "react";
import { Routes, Route, Link } from "react-router-dom"
  
function App() {
	return (
		// html 문법처럼 보이지만 사실 jsx 문법이라고 하는 게 더 정확
		// html 문법처럼 사용할 수 있지만 100% 동일하지는 않음
		<div className="App">
			<nav>
				<Link to="/">Home</Link> | <Link to="/about">About</Link>
				{/* <a href="/">Home</a> 과 같은 문장 */}
			</nav>
			
			{/* Link된 URL로 이동 시 라우팅 할 element에 react component 지정 */}
			<Routes>
				<Route path="/" element={<Home />} />
				<Route path="/about" element={<About />} />
			</Routes>
		</div>
	);
}
  
export default App;
```

# npm init react-app 프로젝트명

#npm - node package manager
프로젝트명(없으면 생성) 아래에 react 앱 프로젝트 생성

## 리액트 앱 기본 프로젝트 구조

프로젝트명(my-app)
	node_modules/
		뭔가 겁나 많음, react 프로젝트를 개발하기 위해 필요한 다양한 자바스크립트 모듈이 설치된 것
		npm으로 설치된 모든 모듈은 해당 폴더에 들어가게 될 것
	public/
		결국 우리가 react로 개발한 파일은 js로 만들어지게 되어 있음
		index.html 파일 하나로 구동하게 되는데, 로고, 파비콘 등 정적 요소와 함께 돌아감
	src/
		react 코드를 개발할 폴더
		index.js - npm start 할 시 가장 먼저 실행될 파일이라고 이해하면 됨(일단은!)
		npm start 할 때 작동되는 페이지의 소스 보기를 하면 public/index.html이 보이긴 함 근데! 코드를 잘 보면 bundle.js 기반으로 구동되는데, index.js 등으로 만든 리액트 파일이 npm start 할 때마다 bundle.js에 들어가게 되는 것
		-> 결국? index.js(기반) -> bundle.js -> 실행
	package-lock.json
	package.json
		이미 react외에 노드 기반 패키지 해봤으면 알겠지만, 노드 패키지에 대한 정보를 담고 있음
		npm start 시 해당 파일 내의 scripts{start}에 저장된 명령어가 실행되는 것, default = "react-scripts start"
		npm run build, test 등도 똑같음
		eslintConfig - 코드가 올바르게 작성되고 있는지
		production

# npm start

# npm run build

# import React from 'react';
- <React.SctirctMode>, <App /> 등의 태그를 사용하기 위해서 자바에서 xml, html 태그를 js 내에서 사용할 수 있게끔 import 한것 (jsx)

# index.html
```html

<body>
	<div id="root"></div> <!-- -->
</body>

```

# index.js
```jsx
import React from 'react'; // jsx를 위해 react import
// js에서 xml, html 태그를 모두 사용 가능하게 함 (jsx)

import ReactDDOM from 'react-dom/client';
import './index.css';
import App from './App'; // App.js를 의미 (*.js의 경우 확장자 생략 가능)
import reportWebVitals from './reportWebVitals';

// index.html의 id="root" 를 가진 태그를 가져온 것
const root = ReactDOM.createRoot(document.getElementById('root'));
// 선언된 root (index.html의 id="root")에 렌더하겠다.
root.render(
	// 나중에 html로 렌더링 될 예정인데, <div id="root"> </div> 로 들어갈 예정
	// StrictMode = 원격 모드를 사용하겠다.
	<React.StrictMode> 
		<App /> // App.js 내부의 코드가 반환되어 삽입됨
	</React.StrictMode>
);

// 웹 퍼포먼스를 측정하기 위한 자바스크립트 라이브러리
// 아직은 이해하지 않아도 괜찮음
// 어쨋든 리액트 앱에 대한 웹 퍼포먼스를 측정하기 위해서 있는 거다.
reportWebVitals();


```

# App.js
```jsx
import logo from './logo.svg';
import './App.css';

function App() {
	return (
		// jsx 코드들
		<div className="App">
			<header className="App-header">
				<img src={logo} className="App-logo" alt="logo" />
				<p>
				Edit <code>src/App.js</code> and save to reload.
				</p>
				<a
				className="App-link"
				href="https://reactjs.org"
				target="_blank"
				rel="noopener noreferrer"
			>	
				
				Learn React
				</a>
			</header>
		</div>
	);
}
  
export default App;
```

# React 컴포넌트

- 크케 클래스형 컴포넌트와 함수형 컴포넌트가 존재

## 클래스형 컴포넌트
```jsx
import React, {Component} from "react";

class Home extends Component {
	render() {
		return <h1>Home 화면입니다.</h1>
	}
}

export default Home;
```

## 함수형 컴포넌트
```jsx
import React from "react";

function Home() {
	return <h1>Home 화면입니다.</h1> 
}

export default Home;
```

## 컴포넌트 선택
둘 중에 무얼 사용해도 큰 상관은 없지만, 요즘은 함수형 컴포넌트가 더 많이 쓰이기에 함수형 컴포넌트를 사용해서 개발 시작
# create react-app

# 스테이트
값을 동적으로 관리하기 위한 저장소

```jsx
const [num, setNumber] = useState(0); // 기본값 0을 갖는 변수 num과 세터함수 setNumber 저장
// num = 변수
// setNumber = setter함수
const increase = () => {
	sestNumber(num + 1);
}

const decrease = () => {
	setNumber(num - 1);
}
```