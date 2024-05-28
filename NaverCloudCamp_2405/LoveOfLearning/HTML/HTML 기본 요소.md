<hr>
## HTML 스타일(Style)

HTML 요소의 style 속성(attribbue)을 이용하면 CSS 스타일을 HTML 요소에 직접 설정할 수 있음
그러나 이러한 style 속성을 이용한 방법은 오직 단 하나의 HTML 요소에만 스타일을 적용할 수 있음

>[!pencil] 문법
><태그이름 style="속성이름:속성값">

<hr>
### 배경색 변경
style 속성을 이용하여 배경색을 변경하는 예제
~~~html
<h1 style="background-color:green">
	style 속성을 이용한 배경색 변경
</h1>
~~~
<h1 style="background-color:green">
	style 속성을 이용한 배경색 변경
</h1>
<hr>
### 글자색 변경
style 속성을 이용하여 글자색을 변경하는 예제
~~~html
<h1 style="color:maroon">
	style 속성을 이용한 글자색 변경
</h1>
~~~
<h1 style="color:maroon">
	style 속성을 이용한 글자색 변경
</h1>
<hr>
## 글자 크기 변경
style 속성을 이용해 글자 크기를 변경하는 예제
~~~html
<h1 style="font-size:250%">
	style 속성을 이용한 글자 크기 변경
</h1>
~~~
<h1 style="font-size:250%">
	style 속성을 이용한 글자 크기 변경
</h1>
<hr>
## 문단 정렬 변경
style 속성을 이용해 문단 정렬을 변경하는 예제
~~~html
<h1 style="text-align:center">
	style 속성을 이용한 문단 정렬 변경
</h1>
~~~
<h1 style="text-align:center">
	style 속성을 이용한 문단 정렬 변경
</h1>
<hr>
## 여러 스타일 설정
style 속성을 이용해 여러 CSS 스타일 적용
~~~html
<h1 style="background-color:blue; color:white; font-size:120%; text-align:center">
	style 속성을 이용해 한번에 스타일링
</h1>
~~~
<h1 style="background-color:blue; color:white; font-size:120%; text-align:center">
	style 속성을 이용해 한번에 스타일링
</h1>
<hr>
>[!info] Info
>style 속성값에 사용되는 CSS 속성(property)과 속성값들은 세미콜론(;)을 이용하여 구분

>[!tip] tip
>CSS 속성을 하나만 사용할 때나, 여러 개의 CSS 속성 중 맨 마지막 CSS 속성은 세미콜론(;)을 생략할 수 있음

## HTML 색(Color) 표현
HTML에서 색을 표현하는 방법은 다음과 같이 세 가지 방법이 있음

1. 색상 이름으로 표현
2. RGB 색상값으로 표현
3. 16진수 색상값으로 표현

<hr>

### 색상 이름으로 표현
W3C에서 정의한 16개의 HTML4 표준 색상 이름은 다음과 같음
<aside style="color:aqua; font-size:150%">aqua</aside>
<aside style="color:blue; font-size:150%">blue</aside>
<aside style="color:gray; font-size:150%">gray</aside>
<aside style="color:lime; font-size:150%">lime</aside>
<aside style="color:navy; font-size:150%">navy</aside>
<aside style="color:purple; font-size:150%">purple</aside>
<aside style="color:silver; font-size:150%">silver</aside>
<aside style="color:white; font-size:150%;background-color:black">white</aside>
<aside style="color:black; font-size:150%">black</aside>
<aside style="color:fuchsia; font-size:150%">fuchsia</aside>
<aside style="color:green; font-size:150%">green</aside>
<aside style="color:maroon; font-size:150%">maroon</aside>
<aside style="color:olive; font-size:150%">olive</aside>
<aside style="color:red; font-size:150%">red</aside>
<aside style="color:teal; font-size:150%">teal</aside>
<aside style="color:yellow; font-size:150%">yellow</aside>

>[!info] Info
>HTML에서 색상 이름은 대소문자를 구분하지 않음

<hr>

### RGB 색상값으로 표현

~~~html
<h1 style="color:rgb(0,0,255)">RGB 색상값으로 표현된 파란색</h1>
<h1 style="color:rgb(0,128,0)">RGB 색상값으로 표현된 녹색</h1>
<h1 style="color:rgb(192,192,192)">RGB 색상값으로 표현된 은색</h1>
<h1 style="color:rgb(0,128,128)">RGB 색상값으로 표현된 청록색</h1>
<h1 style="color:rgb(255,0,0)">RGB 색상값으로 표현된 빨간색</h1>
~~~
<h1 style="color:rgb(0,0,255)"> RGB </h1>

<hr>

### 16진수 색상값으로 표현
각각 00부터 FF까지의 범위를 가짐
color:#RRGGBB
~~~html
<h1 style="color:#0000FF">16진수 색상값으로 표현된 파란색</h1>
<h1 style="color:#008000">16진수 색상값으로 표현된 녹색</h1>
<h1 style="color:#C0C0C0">16진수 색상값으로 표현된 은색</h1>
<h1 style="color:#008080">16진수 색상값으로 표현된 청록색</h1>
<h1 style="color:#FF0000">16진수 색상값으로 표현된 빨간색</h1>
~~~
<h1 style="color:#0000FF">16진수</h1>

<hr>

## HTML 배경 (Background)

1. 배경을 다른 색으로 변경
2. 배경을 다른 이미지로 변경

<hr>

### 배경을 다른 색으로 변경
~~~html
<style>
    body { background-color: lightblue; }
    h1 { background-color: rgb(255,128,0); }
    p { background-color: #FFFFCC; }
</style>123
~~~

<hr>

### 배경을 다른 이미지로 변경
background 속성을 이용하면 HTML 요소의 배경을 이미지로 설정 가능
~~~html
<태그이름 background="이미지주소">
~~~
>[!example] Example
>&lt;body background="/examples/images/img_background_good.png"&gt;
>..
>&lt;/body&gt;

>[!tip] Tip
>배경으로 이미지를 사용하면 웹 페이지의 로딩 시간이 증가하므로, 보통은 작은 사이즈의 이미지를 패턴으로 만들어 배경 이미지로 반복 설정

<hr>

## HTML 링크 (Link)
하이퍼 링크(hyperlink) = 링크(link)
>[!pencil] 문법
>&lt;a href="링크주소"&gt;HTML 링크&lt;/a&gt;

a 태그의 href 속성은 링크를 클릭하면 연결할 페이지나 사이트의 URL 주소를 명시함
a 태그는 텍스트나 단락, 이미지 등 다양한 HTML 요소에 사용 가능

>[!example] 예제
>&lt;a href="https://www.tcpschool.com/html/html_basic_links"&gt;
>	&lt;h2&gt;이 링크를 클릭해 보세요!&lt;/h2&gt;
>&lt;/a&gt;

<a href="https://www.tcpschool.com/html/html_basic_links">  
	<h2>이 링크를 클릭해 보세요!</h2>  
</a>
<hr>

### target 속성
a 태그의 target 속성은 링크로 연결된 문서를 어디에서 열 지 명시함
- \_blank : 링크로 연결된 문서를 새 창이나 새 탭에서 오픈.
- \_self : 링크로 연결된 문서를 현재 프레임(frame)에서 오픈. (default)
- \_parent : 링크로 연결된 문서를 부모 프레임(frame)에서 오픈.
- \_top : 링크로 연결된 문서를 현재 창의 가장 상위 프레임(frame)에서 오픈.
- 프레임(frame)이름 : 링크로 연결된 문서를 지정된 프레임(frame)에서 오픈.

>[!example] 예제
>\<h2\>\<a href="www.google.com" target="\_blank"\>blank\</a\>\</h2\>
>\<h2\>\<a href="www.google.com" target="\_self"\>self\</a\>\</h2\>
>\<h2\>\<a href="www.google.com" target="\_parent"\>parent\</a\>\</h2\>
>\<h2\>\<a href="www.google.com" target="\_top"\>top\</a\>\</h2\>
>\<h2\>\<a href="www.google.com" target="\myframe"\>myframe\</a\>\</h2\>
>
>\<iframe name="myframe" style="width:50%; height: 330px"\>\</iframe\>

<h2><a href="www.google.com" target="_blank">blank</a></h2>  
<h2><a href="www.google.com" target="_self">self</a></h2>  
<h2><a href="www.google.com" target="_parent">parent</a></h2>  
<h2><a href="www.google.com" target="_top">top</a></h2>  
<hr>

### 링크의 상태(state)

링크의 상태 네 가지

| 링크의 상태  | 설명                           |
| ------- | ---------------------------- |
| link    | 아직 한 번도 방문한 적이 없는 상태 (기본 설정) |
| visited | 한 번이라도 방문한 적이 있는 상태          |
| hover   | 링크 위에 마우스를 올려놓은 상태           |
| active  | 링크를 마우스로 누르고 있는 상태           |
기본 링크 style
~~~html
<style>
	a:link {color: teal;}
	a:visited {color: maroon; text-decoration: none}
	a:hover {color: yellow; text-decoration: none}
	a:active {color: red; text-decoration: none}
</style>
~~~

<hr>

### 페이지 책갈피

a 태그의 name 속성을 이용하면 간단한 책갈피를 만들 수 있음
책갈피를 통해 가고 싶은 위치에 a 태그를 만들고 name 속성을 작성
그 다음 작성한 name 속성값을 이용하여 a 태그에서 링크를 걸면 됨

~~~html
<a href="#bookmark"><p>제목 3으로 가기</p></a>
blar blar
<h2><a name="bookmark"></a>제목 3</h2>
~~~

<hr>

## HTML 이미지(Image)

이미지란 2차원 평면 위에 그려진 시각적 요소를 의미

주로 사용되는 이미지 종류
- JPEG 이미지
- GIF 이미지
- PNG 이미지

<hr>

### 이미지의 삽입

img 태그 사용, empty tag 임

>[!pencil] 문법
>\<img src="이미지주소" alt="대체문자열">

alt 속성은 이미지가 로딩될 수 없는 상황에서 이미지 대신 나타날 문자열을 설정

~~~html
<img src="https://www.tcpschool.com/lectures/jpg_ex_img.jpg" alt="이미지가 없나">
<img src="test" alt="이미지가 진짜 없나">
~~~

<hr>

### 이미지의 크기 설정

style로 이미지 크기 설정 가능
width와 height 속성으로 너비와 높이를 픽셀단위로 설정할 수도 있음
근데 이건 HTML5 표준에는 적합하지만 CSS를 이용한 내부 스타일 시트나 외부 스타일 시트와 상관없이 이미지의 원래 크기를 유지하려면 style 속성을 사용하는 것이 좋음

~~~html
<style>
	img{
		width:100%;
		border: 1px solid black;
	}
</style>
blar
<img src="https://www.tcpschool.com/lectures/jpg_ex_img.jpg" alt="html size" width="320" height="214">
<img src="https://www.tcpschool.com/lectures/jpg_ex_img.jpg" alt="style size" style="width:320px; height:214px">

~~~

<hr>

### 이미지에 링크(link) 설정

이미지에 a 태그를 이용하여 링크를 설정할 수 있음

~~~html
<a href="https://www.tcpschool.com/" target="_blank">
	<img src="https://www.tcpschool.com/lectures/jpg_ex_img.jpg" alt="flower" style="width:320px; height:214px">
</a> 
~~~

<hr>

### 이미지 맵 만들기

map 태그를 이용해 이미지 맵을 제작할 수 있음
이미지 맵이란 이미지의 일부를 클릭할 수 있도록 만들어서 버튼처럼 사용하는 기능
img 태그의 usemap 속성을 map 태그의 name 속성과 연결하면 이미지와 맵 사이의 관계가 설정됨
map 태그는 하나 이상의 area 태그를 가지며, 이 area 태그가 바로 버튼과 같은 역할을 함

~~~html
<img src="https://www.tcpschool.com/examples/images/img_imagemap.jpg" alt="진실 혹은 거짓" usemap="#vending" style="width:320px; height:240px" />
	<map name="vending">
		<area shape="rect" coords="90,60,180,130" alt="거짓" href="https://ko.wikipedia.org/wiki/%EA%B1%B0%EC%A7%93%EB%A7%90">
		<area shape="rect" coords="210,200,70,130" alt="진실" href="https://ko.wikipedia.org/wiki/%EC%A7%84%EC%8B%A4">
	</map>
~~~

<hr>

## HTML 리스트

리스트란; 여러 요소들을 일렬로 나열한 목록이나 명단

- 리스트 종류
	- 순서가 없는 리스트(unordered list)
	- 순서가 있는 리스트(ordered list)
	- 정의 리스트(definition list)

<hr>

### 순서가 없는 리스트

순서가 없는 리스트는 ul 태그로 시작하며, 여기에 포함되는 각각의 리스트 요소는 li 태그로 시작
각각의 리스트 요소 앞에는 기본 마커(marker)로 검정색의 작은 원(bullet)이 위치

~~~html
<ul>
	<li>사과</li>
	<li>멜론</li>
	<li>바나나</li>
</ul>
~~~

CSS의 list-style-type 속성으로 리스트 요소 앞에 위치하는 마커 모양 변경 가능

- disc : 검정색 작은 원 모양 (기본)
- circle : 흰색 작은 원 모양
- square : 사각형 모양

~~~html
<ul style="list-type: circle">
	<li>수박</li>
	<li>참외</li>
	<li>옥수수</li>
</ul>
~~~

<hr>

### 순서가 있는 리스트

순서가 있는 리스트는 ol 태그로 시작하며, 각각의 리스트 요소는 li 태그로 시작
기본 마커로 아라비아 숫자가 위치

~~~html
<ol>
	<li>사과</li>
	<li>멜론</li>
	<li>바나나</li>
</ol>
~~~

이 또한 CSS의 list-style-type 속성으로 리스트 요소 앞에 위치하는 마커 모양 변경 가능

- decimal : 숫자 (기본)
- upper-alpha : 영문 대문자
- lower-alpha : 영문 소문자
- upper-roman : 로마 숫자 대문자
- lower-roman : 로마 숫자 소문자

~~~HTML
<ol style="list-style-type: upper-alpha">
	<li>밥</li>
	<li>김</li>
	<li>국</li>
</ol>
~~~

<hr>

### 정의 리스트(description list)

정의 리스트는 용어와 그에 대한 정의를 모아놓은 리스트로 dl 태그로 시작
dt 태그에는 용어의 이름이 들어가고, dd 태그에는 해당 용어에 대한 정의가 들어감

~~~html
<dl>
	<dt>호박</dt>
	<dd>- 박과의 한해살이 덩굴성 채소</dd>

	<dt>상추</dt> <dd>- 국화과의 한해살이 또는 두해살이풀</dd>
</dl>