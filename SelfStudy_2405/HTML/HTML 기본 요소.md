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

## RGB