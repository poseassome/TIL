# 태그(3) [앵커, 이미지, 글자, 테이블]
작성일시: 2021년 8월 9일 오후 9:20

> **<a>**
서로 다른 웹페이지 사이를 이동하거나 웹페이지 내부에서 특정한 위치로 이동할 때 사용

**href="url"**
  -이동할 위치
**target="_blank"**
  -새창으로 열림
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- 외부 웹페이지로 이동 -->
  <!-- hyper text reference(참조) -->
  <!-- HTTP: hyper text transfer protocol -->

  <!-- HTML 파일을 전송하기 위한 통신 규약 -->
  <!-- s(secure): 보안적으로 전송 -->
  <a href="https://www.naver.com">네이버</a>

  <!-- www: 서버컴퓨터종류, 웹서비스 -->
  <!-- blog: 블로그 서비스(service)-->
  <a href="https://www.google.com" target="_blank">구글</a>
</body>

</html>
```

> **href="#id"** id값을 넣을 수도 있음
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <ul>
    <!-- href="#id값", 내부화면으로 이동 -->
    <li><a href="#menu-1">Menu - 1</a></li>
    <li><a href="#menu-2">Menu - 2</a></li>
    <li><a href="#menu-3">Menu - 3</a></li>
  </ul>

  <!-- id: 태그의 유일한 이름 -->
  <!-- 영어로만, 띄어쓰기 X, 단어연결 하이픈(-) -->
  <h1 id="menu-1">Menu - 1</h1>
  <p>
    내용입니다. <br>
    내용입니다. <br>
  </p>
  <h1 id="menu-2">Menu - 2</h1>
  <p>
    내용입니다. <br>
    내용입니다. <br>
  </p>
  <h1 id="menu-3">Menu - 3</h1>
  <p>
    내용입니다. <br>
    내용입니다. <br>
  </p>
</body>

</html>
```

---

> **<img>**
이미지를 삽입할 때 사용

**src="url"**
  가져올 이미지의 주소 (내부파일, 외부파일, 데이터url)
**alt=""**
  이미지가 안뜨면 나타날 텍스트
**width=""  height=""**
  이미지의 크기
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- img: 이미지를 삽입할 때 -->
  <!-- src(source): 이미지 주소 -->

  <!-- .: 현재 폴더 위치 -->
  <!-- /: 하위 폴더 또는 파일 -->

  <!-- C:\Users\higom\OneDrive\바탕 화면\git2021-master\git2021-master\1-html-css\example\ch01 -->
  <!-- \: 윈도즈 계열의 운영체제에서만 -->
  <!-- /: 웹, 리눅스, 유닉스, 맥 -->

  <!-- width: 너비값 -->
  <!-- height: 높이값 -->
  <img height="200" src="./img/penguin.jpg">
</body>

</html>
```

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- 외부 이미지 -->
  <!-- URL:(Unified Resource Lpcator): 웹 상의 파일의 위치를 나타냄 -->

  <!-- alt(alternative text): 대체 텍스트(글자) -->
  <!-- 1. 이미지 주소가 잘못됐거나 파일이 삭제됐거나 등등... 링크 깨졌을 때 표시하는 방법-->
  <!-- 2. 이미지를 볼 수 없는 웹브라우저에서 표시 -->
  <!-- 3. 시각장애인 리더기에서 글자를 읽어줌 -->
  <!-- 4. 검색엔진에서 찾아가는 키워드 -->
  <img alt="닭볶음탕" width="200"
    src="https://recipe1.ezmember.co.kr/cache/recipe/2019/01/31/e8cab950076b23a80f16dd7858dd514e1.jpg">
</body>

</html>
```

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- 파일 -> 문자열(문자여러개, base64) -->
  <!-- 페이지 자체에 파일을 넣는 방법 -->

  <!-- base64문자열로 변환하면 원래 파일 크기보다 33% 증가 -->
  <!-- data URL -->

  <img
    src="data:image/jpeg;base64,/ (생략)"
    alt="펭귄">

</body>

</html>
```

---

> 글자 형태 관련 태그

글자를 굵게
**<b> <strong>**

글자를 기울임
**<i> <em>**

밑줄 **<ins>**   취소선 **<del>**
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <p>
    <!--b: 굵게(bold) -->
    <b>이것은</b> 내용입니다.
  </p>
  <p>
    <!-- i: 기울임(italic) -->
    <i>이것은</i> 내용입니다.
  </p>
  <p>
    <!-- strong: 보일때는 굵게, 악센트를 주어서 읽음 -->
    <strong>이것은</strong> 내용입니다.
  </p>
  <p>
    <!-- em: 보일때는 기울여서, 강조문자, 악센트를 주어서 읽음 -->
    <em>이것은</em> <sup>내용입니다.</sup>
  </p>
  <p>
    <ins>이것은</ins><del>내용입니다.</del>
  </p>
  <p>
    <span style="font-weight: bold;">이것은</span>
    <span style="text-decoration: underline;">내용입니다.</span>
  </p>

</body>

</html>
```

---

> 테이블 만들기 **<table>**
테이블의 헤더(시맨틱) **<thead>**
테이블의 내용(시맨틱) **<tbody>**
테이블의 하단(시맨틱 **<tfoot>**

**<tr>** 테이블에서의 한 행 →
**<th>** 테이블의 열의 제목 ↓

**<td>** 테이블의 하나의 셀
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- table: 표, 행(raw)/열(column) -->
  <!-- border: 외각선 -->
  <table border="1" cellspacing="0" width="500">
    <!-- thead: 테이블의 헤더 부분 시맨틱 태그 -->
    <thead>
      <tr>
        <!-- th: table header, 열(column)이름 -->
        <th>이름</th>
        <th>연락처</th>
      </tr>
    </thead>
    <!-- tbody: 테이블의 내용 시맨틱 태그 -->
    <tbody>
      <!-- tr: table raw, 1개의 행 -->
      <tr>
        <!-- td: table data, 1개의 셀 -->
        <!-- td: 실제 컨텐츠 포함됨 -->
        <td>홍길동</td>
        <td>010-1234-5678</td>
      </tr>
      <tr>
        <td>고대근</td>
        <td>010-2636-5411</td>
      </tr>
    </tbody>
    <!-- tfoot: 테이블의 하단영역 시맨틱 태그 -->
    <!-- 주로 요약정보, 알림정보 -->
    <tfoot>
      <tr>
        <td>총 2건입니다.</td>
        <td></td>
      </tr>
    </tfoot>
  </table>
</body>

</html>
```

> <table>속성
  **cellspacing:** 셀 간 간격(셀 테투리처럼 보임)

<td> 속성
  **rowspan**: 행을 칸만큼 늘림
  **colspan**: 열을 칸만큼 늘림
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <table border="1" cellspacing="0" width="500">
    <thead>
      <tr>
        <th>이름</th>
        <th>연락처</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <!-- rowspan(row span) -->
        <!-- row: 행 -->
        <!-- span: 늘려라 -->
        <td rowspan="2">홍길동</td>
        <td>010-1234-5678</td>
      </tr>
      <tr>
        <td>010-2636-5411</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <!-- colspan(column span) -->
        <!-- column: 열 -->
        <!-- span: 늘려라 -->
        <td colspan="2">총 2건입니다.</td>
      </tr>
    </tfoot>
  </table>
</body>

</html>
```

---

> 공간 분할 태그

**<div>**
  block 형식으로 공간을 분할 (쌓아 올려짐)
  -div, h1~h6, p, ol, ul, table, form

**<span>**
  inline 형식으로 공간을 분할 (한 줄 안에 차례차례 위치)
  -span, a, input, 글자 형식 태그
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
</head>

<body>
  <!-- div: division, 공간/영역 분할 -->
  <!-- block형식 표현 -> 위에서부터 아래로 쌓는다. -->
  <div>이것은 내용입니다.</div>
  <div>이것은 내용입니다.</div>
  <div>이것은 내용입니다.</div>

  <!-- span: 공간/영역분할 -->
  <!-- inline형식 표현 -> 왼쪽에서 오른쪽으로 붙임 -->
  <span>이것은 내용입니다.</span>
  <span>이것은 내용입니다.</span>
  <span>이것은 내용입니다.</span><br>
  <div><a href="">링크1</a></div>
  <a href="">링크2</a><br>
  <a href="">링크3</a>
</body>

</html>
```

---