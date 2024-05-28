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
