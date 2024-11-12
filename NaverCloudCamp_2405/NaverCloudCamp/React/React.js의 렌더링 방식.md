우리가 작성한 컴포넌트는 어떤 과정을 거쳐 렌더링 되는지?

이런 특징으로 인해 갖게되는 장점은 무엇인지?

# 웹 브라우저는 어떻게 동작할까?

## 브라우저는 어떻게 페이지를 화면에 렌더링 할까?

- Critical Rendering Path
![[Pasted image 20240903212315.png]]

1. HTML, CSS 코드를 각각 DOM, CSSOM (CSS Object Model) 으로 변환
- DOM(Document Object Model) - 문서 객체 모델
	- HTML을 브라우저가 해석하기 편한 방식으로 변환한 객체 트리
![[Pasted image 20240903212402.png]]

2. Render Tree 생성
- Render Tree는 웹 페이지의 "청사진" 이라고 볼 수 있음
- 요소들의 배치와 모양 스타일의 모든 정보를 갖고있음

3. Layout
- Render Tree를 기반으로 실제 웹 페이지에 요소들의 배치를 결정하는 작업
- 웹 페이지 내에 요소들이 어떤 위치에, 어떤 사이즈로 존재할건지 결정하는 것

4. Painting
- 실제로 요소들을 화면에 그려내는 과정

## 그렇다면 업데이트는 어떻게 이루어질까?
### #업데이트
- 이벤트에 따라 화면이 실시간으로 변화하는 것
	- ex) 좋아요 버튼 등

- JavaScript가 DOM을 수정하면 업데이트가 발생 함
- DOM이 수정되면 Critical Rendering Path가 다시실행됨
Layout을 다시 하는 것과 Painting을 다시 하는 것은 모든 과정중에 가장 어려움
Reflow, Repaint 라고도 하는데, 특별히 무거운 과정임
3000번 단순히 DOM을 수정하는 것 -> 성능 측정 결과 4500ms 정도가 측정됨
DOM을 딱 한번만 수정하도록 코드를 수정하면 -> 성능 측정 결과 250ms 정도가 측정됨
### 결론
1. 다양한 업데이트가 필요한 경우
2. 동시에 발생한 업데이트를 모아서
3. 다 모였다면 한번에 수정!
-> 다만, 서비스의 규모가 커질 수록 점점 힘들어짐
-> 자바 스크립트만으로 좋은 성능을 처리하는 건 어려운 일일 것!
-> 그때 필요한 게 React JS, 업데이트를 다 모아서 최소한의 수정으로 DOM을 변경할 수 있도록 도와줌, 즉, 추상화가 되어있음 (별도의 렌더링 프로세스가 있음)

# React의 렌더링 프로세스

## Render Phase
- 컴포넌트를 계산하고 업데이트 사항을 파악하는 단계

### -> 컴포넌트 호출
```JavaScript
function App() {
	return (
		<div id="main">
			<p>Hello</p>
		</div>
	);
}
```


### -> React Element 객체 반환
```React
{
	type: "div",
	key: null,
	ref: null,
	props: {
		id: "main",
		children: {
			type: "p",
			key: null,
			ref: null,
			props: {
				children: "Hello",
			},
			// ...
		},
	},
	// ...
}
```

### -> Virtual DOM 이라는 트리 형태로 구조화
- React Element 라고 부르는 객체 값의 모임
- 실제 DOM은 아님
- 값으로 표현된 UI라고 이해하면 편함


## Commit Phase
- 변경사항을 실제 DOM에 반영하는 단계
### -> Virtual DOM을 Actual DOM으로 변환

# React Critical Rendering Path
1. HTML, CSS 파싱
2. 렌더 트리 생성
3. 레이아웃
4. 페인팅

## 업데이트 발생 시

1. Render Phase
	1. Render Phase를 처음부터 다시 실행
	2. 새로운 Virtual DOM 생성
	3. 이전 VDOM과 새로운 VDOM을 비교 (Diffing)
2. Commit Phase
	1. Actual DOM에 반영

-> 동시에 발생한 업데이트를 모아 한번만 DOM을 수정
대부분의 상황에 충분히 빠른 속도로 화면 업데이트가 이루어짐
이 과정을 특별히 Reconciliation(재 조정)이라고 부름