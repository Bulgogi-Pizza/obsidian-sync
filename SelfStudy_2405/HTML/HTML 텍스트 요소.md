## 제목 (Heading)

HTML은 제목을 표현할 수 있는 다양한 크기의 h 태그를 제공

가장 큼 h1 ——————- h6 가장 작음

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>HTML Headings</title>
</head>

<body>

	<h1>제목1의 크기입니다!</h1>
	<h2>제목2의 크기입니다!</h2>
	<h3>제목3의 크기입니다!</h3>
	<h4>제목4의 크기입니다!</h4>
	<h5>제목5의 크기입니다!</h5>
	<h6>제목6의 크기입니다!</h6>

</body>

</html>
```

<aside>
💡 h 태그의 위아래로는 약간의 여백이 자동으로 삽입됨

</aside>

이런 h 태그는 제목의 표현이라는 기능 외에도, 검색 엔진은 각 웹 사이트의 내용을 바로 이 h 태그를 이용하여 키워드를 수집하고, 그 내용을 파악

따라서 HTML 문서에 포함되는 제목은 h 태그로 작성해야만 검색엔진에 의해 제대로 검색될 확률이 높음

<aside>
💡 HTML 문서의 제목에 해당하는 부분을 big 태그나 bold 태그를 사용하여 표현하지 않도록 해야 함

</aside>

> **종료 태그를 잊지 말자!**

대부분의 웹 브라우저는 종료 태그를 사용하지 않더라도 다음 예제처럼 HTML 문서를 제대로 표현

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>HTML Headings</title>
</head>

<body>

	<h2>종료 태그가 없어도 표현이 잘 될까요?

</body>

</html>
```

하지만 종료 태그가 없으면 예상치 못한 오류나 결과가 발생할 수도 있음

또한, XHTML이나 XML과 같은 문법이 엄격한 언어에서는 종료 태그의 유무를 엄격히 검사, 따라서 가급적 종료 태그를 빠트리지 말고 코드를 작성하는 것이 좋음

## 단락(Paragraph)

단락이란 내용상 끊어서 구분할 수 있는 하나하나의 부분을 의미하며, 문단이라고도 부름

HTML에서는 p 태그를 이용해 다음과 같은 단락을 표현

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>HTML Paragraph</title>
</head>

<body>
	<h1>제목1의 크기입니다!</h1>
	<h2>제목2의 크기입니다!</h2>
	<h3>제목3의 크기입니다!</h3>
	<p>여기서부터 단락입니다.</p>
</body>

</html>
```

<aside>
💡 p 태그의 위아래로 약간의 여백이 자동으로 삽입됨

</aside>

## 띄어쓰기와 줄 나누기

HTML코드에서 띄어쓰기나 줄 나누기를 여러 번 하더라도 웹 브라우저를 통해 나타나는 화면에는 전혀 영향을 주지 못함

웹 브라우저는 여러 번의 띄어쓰기나 줄 나누기를 오직 하나의 띄어쓰기나 줄로만 인식하기 때문임

다음 예제는 웹 페이지에 여러 번의 띄어쓰기와 줄 나누기를 표현하기 위해 작성한 예제

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>HTML Paragraph</title>
</head>

<body>
	<p>
줄을 나누고 싶어서
이렇게 줄을 나눠봤습니다.

과연     그대로     출력이      될까요?
	</p>

</body>

</html>
```

위의 예제는 여러 번의 띄어쓰기와 줄 나누기를 표현하고자 p 태그를 이용하였으나, p 태그 내에서 작성된 여러 번의 띄어쓰기와 줄 나누기는 오직 하나의 띄어쓰기로만 표현됨

<br>태그(break line)를 사용하면 새로운 단락을 만들지 않고도 줄을 나눌 수 있음

<br>태그는 종료 태그가 없는 빈 태그(empty tag)임

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>HTML Paragraph</title>
</head>

<body>
	<p>
줄을 나누고 싶어서<br>
이렇게 줄을 나눠봤습니다.<br>
<br>
과연     그대로   출력이  될까요?
	</p>

</body>

</html>
```

## 텍스트(text) 서식 미리 정의하기

HTML 코드에서 작성한 텍스트 서식을 그대로 표현하려면  pre 태그를 사용

pre 태그(preformatted text) 내에 작성된 텍스트의 모든 띄어쓰기와 줄 나누기는 웹 브라우저에 그대로 표현됨

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>HTML Paragraph</title>
</head>

<body>
	<pre>
줄을 나누고 싶어서
이렇게 줄을 나눠봤습니다.

과연   그대로     출력이 될까요?
	</pre>
	
</body>

</html>
```

<aside>
💡 pre 태그 내에 작성된 텍스트의 글꼴(font)은 고정폭 글꼴(fixed_width font)로 자동변환됨

</aside>

## 수평 가로 구분선

단락을 나눌 때나 내용상의 구분을 표현하고자 할 때 수평 가로 구분선을 사용

hr 태그(horizontal rule)

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>HTML Paragraph</title>
</head>

<body>

	<p>저는 하나의 단락입니다.</p>
	<hr>
	<hr>
	<p>저는 하나의 단락입니다.</p>
	<hr>
	
</body>

</html>
```

## 서식(Formatting)

텍스트에 다양한 효과를 주는 여러 태그

### 강조 효과

텍스트를 굵게 표현하고 싶을 때에는 b 태그(bold text)나 strong 태그를 사용

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML Formatting</title>
</head>

<body>
	<p><b>"이 부분"</b>은 단순히 글씨가 굵은 부분</p>
	<p><strong>"이 부분"</strong>은 중요한 부분이라서 굵게 표현</p>

</body>

</html>	
```

b 태그는 단순히 화면의 텍스트를 굵게 표현

strong 태그는 텍스트를 굵게 표현할 뿐 아니라 그 내용이 중요하다는 의미도 함께 포함 (보이는 것은 똑같음)

이탤릭체를 표현하고 싶을 때에는 i 태그(italic text)나 em 태그(emphasized text)를 사용

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML Formatting</title>
</head>

<body>
	<p><i>"이 부분"</i>은 단순히 글씨가 이탤릭체</p>
	<p><em>"이 부분"</em>은 중요한 부분이라서 이탤릭체 표현</p>
	<p><em><strong>"이 부분"</strong></em>처럼 이탤릭과 강조 동시 사용 가능</p>
</body>

</html>	
```

<aside>
💡 검색엔진은 strong 태그나 em 태그를 사용하여 강조된 텍스트를 더 중요하게 인식

</aside>

### 하이라이팅 효과

mark 태그는 텍스트에 하이라이팅(highlighting) 효과를 적용

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML formatting</title>
</head>

<body>
	<p><mark>"이 부분"</mark>만 하이라이팅</p>
</body>

</html>
```

### 삭제 효과

<del> del 태그는 텍스트 중앙에 가로줄을 만들어 텍스트를 지운 것 같은 효과를 내줌 </del>

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML formatting</title>
</head>

<body>
	<p><del>"이 부분"</del>을 지운 것처럼 하기
</body>

</html>
```

### 삽입 효과

<ins> ins 태그(insert)는 텍스트 밑에 가로줄을 만들어 마치 빈 칸에 텍스트를 삽입한 듯한 효과를 줌 </ins>

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML formatting</title>
</head>

<body>
	<p><ins>"이 부분"</ins>을 삽입한 것 처럼</p>
</body>

</html>
```

### 위첨자와 아래첨자 효과

위첨자는 <sup> sup 태그(superscript)를 사용하고</sup>, 아래첨자는 <sub> sub태그(subscript)를 사용해 각각 표현 가능</sub>

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML formatting</title>
</head>

<body>
	<p>X<sup>2</sup> + Y<sup>3</sup> = Z</p>
	<p>물을 나타내는 화학식은 H<sub>2</sub>O입니다.</p>
</body>

</html>
```

## 인용구 (Quotation)

HTML 인용구 표현 방법 2가지

1. 짧은 인용구
2. 블록 인용구

### 짧은 인용구

짧은 인용구는 <q> q 태그(quotation)를 사용하여 표현할 수 있고, 자동으로 앞뒤에 큰따옴표가 붙음 </q>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title> HTML Quotations</title>
</head>

<body>
	<h1>q태그를 이용한 짧은 인용구</h1>
	<p>HTML의 정의는 <q>웹 페이지를 만들기 위한 하이퍼텍스트 마크업 언어</q>입니다.</p>
</body>

</html>

```

### 블록 인용구

길이가 긴 인용문은 <blockquote> blockquote 태그(block quotation)를 사용하여 표현할 수 있음 </blockquote>

blockquote 태그는 이러한 인용 부분을 별도의 단락으로 구분

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML quotation</title>
</head>

<body>
	<p>HTML의 정의</p>
	<blockquote>
	인터넷 서비스의 하나인 월드 와이드 웹을 통해 볼 수 있는 문서를 만들 때 사용하는 프로그래밍 언어의 한 종류이다.
	</blockquote>
</body>
</html>
	
```

### 축약형 표현

HTML에서 용어의 축약형을 표현하기 위해서는 <abbr title="abbr 태그"> abbr 태그(abbreviation)를 사용 </abbr>
abbr 태그 위에 마우스를 위치시키면 title 속성에 명시한 용어의 원형이 나타남

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML quotation</title>
</head>

<body>
	<p><strong><abbr title="HyperText Markup Language 5">HTML5</abbr></strong>
	란 웹 문서를 제작하는 데 쓰이는 프로그래밍 언어인 HTML의 최신규격임</p>
</body>

</html>
```

### 주소 표현

<address> address 태그를 사용하면 주소 표현 가능 </address>

이탤릭체 + 위아래 약간의 공백 자동 삽입

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML quotation</title>
</head>

<body>
	<address>
	서울특별시<br>
	강남구 테헤란로
	</address>
</body>
</html>
```

## 주석(Comment)

주석(comment)이란 개발자가 작성한 해당 코드에 대한 이해를 돕는 설명이나 디버깅을 위해 작성한 구문

다른 HTML 코드와는 달리 웹 브라우저에 뜨지 않음

<aside>
💡 문법 !— 주석내용 —

</aside>

HTML주석의 시작 태그(<!—)에는 느낌표(!)가 있지만 종료 태그(—>)에는 느낌표가 없음

HTML 코드 어느 부분에서든 사용 가능

여러 줄에 걸쳐 작성해도 됨

```html
<!DOCTYPE html>
<!--작성자 : 최동인 -->
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML quotation</title>
</head>

<body>
	<p>이 부분은 조금 어려운 코드</p>
	<!--위처럼
	어려운
	코드라면
	주석을
	달아서
	설명을
	쓰자
	-->
</body>
</html>
```

주석을 중첩하여 사용 시 종료태그 아래의 주석이 웹페이지에 노출되므로 절대 사용하면 안됨

## 엔티티(Entity)

HTML에는 미리 예약된 몇몇 문자가 있고, 이러한 문자를 HTML 예약어(reserved characters)라고 부름

이러한 HTML 예약어를 HTML 코드에서 사용하면, 웹 브라우저는 그것을 평소와는 다른 의미로 해석함