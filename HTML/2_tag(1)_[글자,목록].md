# 태그(1) [글자, 목록]
작성일시: 2021년 8월 9일 오후 5:39

> **meta** information 입력

해당 문서의 언어, 문자코드표 설정
>

```html
<html lang="ko">

<head>
  <!-- meta: 웹 페이지의 추가 정보를 브라우저에 전달 -->
  <!-- charset(character set): -->
  <!-- 글자집합 -> 문서에서 사용할 문자코드표 -->

  <!-- 현재문서는 유니코드 (unicode) 문자코드표를 사용함 -->
  <!-- 전세계의 글자를 사용해서 작성할 수 있음 -->
  <meta charset="utf-8">
  <!-- title: 브라우저에 탬/창에 표시해주는 내용(문서제목) -->
  <title>HTML5 웹페이지입니다.</title>

</head>

</html>
```

---

> header tag **<h1> ~ <h6>**
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- h숫자: 제목 태그 , 숫자가 클 수록 작아짐 -->
  <h1>Header 1</h1>
  <h2>Header 2</h2>
  <h3>Header 3</h3>
  <h4>Header 4</h4>
  <h5>Header 5</h5>
  <h6>Header 6</h6>
</body>

</html>
```

---

> 문단태그 **<p>**
하나의 단락을 만들 수 있으며, 위아래 행을 띄어준다.

**<hr>** 수평선 / **<br>** 행을 나눠줌

특수문자 쓰는 방법
  - **&lt;**  =[<]   /   **&gt;**  =[>]   /   **&amp;**  =[&]   /   **&nbsp;**  =[  ]
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- h: header, 제목 -->
  <h1>제목입니다.</h1>
  <!-- p: paragraph, 단락 -->
  <!-- 단락별로 행 띄어쓰기를 해줌 -->

  <!-- html의 컨텐트 빈공간(white-space)은 띄어쓰기 1칸으로 인식 -->
  <!-- br, meta: 닫는태그가 없음, 내부에 컨텐트가 없음 -->
  <!-- br: 밑으로 한줄 내려줌 -->
  <p>
    <!-- br: break -->
    내용입니다. <br>
    내용입니다.
    내용입니다. <br>
    내용입니다. <br>
    <!-- 이스케이프(escape)문자: 특수기호문자 -->
    &lt; 그림1 &gt;
    <!-- lt(less than): 보다 작은 -->
    <!-- gt(greater than): 보다 큰 -->

    <!-- a < b: a가 b보다 작다. lt -->
    <!-- a > b: a가 b보다 크다. gt -->

    <!-- &: ampersand -->
    &amp;&amp;&amp;

    <!-- &nbsp; : 띄어쓰기 -->
    내용입니다. &nbsp;&nbsp;&nbsp;내용입니다.
    내용입니다.
    내용입니다.
    내용입니다.
    <!-- hr(horizontal rule): 수평줄 -->
    <hr>
    내용입니다.
    내용입니다.
    내용입니다.
  </p>
</body>

</html>
```

---

> 리스트 관련 태그
**<ol>** : 순서가 있음
**<ul>** : 순서가 없음
**<li>**  : 리스트 목록
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- ul: unorderd list, 순서가 없는 목록 -->
  <ul>
    <!-- li: list item, 목록 안에 한개의 요소(element) -->
    <li>Facebook</li>
    <li>Twitter</li>
    <li>Google</li>
  </ul>
  <!-- ol: ordered list, 순서가 있는 목록 -->
  <ol>
    <li>Facebook</li>
    <li>Twitter</li>
    <li>Google</li>
    <li>Naver</li>
  </ol>

</body>

</html>
```

---