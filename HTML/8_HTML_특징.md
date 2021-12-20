# HTML 특징
작성일시: 2021년 8월 23일 오후 5:39

```html
*HTML
  1. "<"와 ">" 사이에 명령어(tag, element) 작성
    이스케이프 문자 (entity type)
      &nbsp; : 띄어쓰기 / non-breaking spacing (줄 바꾸지말고 간격을 만들어.)
```

```html
  2. 시작태그와 종료태그로 구성
```

```html
  3. 태그는 중첩 가능하면 종료태그는 나중에 작성한 태그먼저 작성
    -<div><p><a></div></p></a>    (x)
    -<div><p><a></a></p></div>    (o)
```

```html
  4. 종료태그가 없거나 생략 가능한 태그
    -종료태그가 없는 태그 : br, img, hr, meta, input,...
    -종료태그가 생략 가능한 태그 : 주석, p, option,...
```

```html
  5. 반드시 종료 선언(xhtml)
    -종료태그가 없는 태그 : 태그 뒤에 "/" 표기
      ex) <br> ---------------------> <br />
          <img src=""> -------------> <img src="" />
    -종료태그 생략 가능한 태그 : 반드시 종료태그 작성

    xhtml에서는 무조건 닫아.

    xhtml은 html5를 발표한 이 후 사용되지 않음.
    하지만 실무에 갔을 때 이미 만들어진 것을 유지, 보수 할 수 있음

    ex) NAVER 페이지 소스에서 meta 태그 끝에 /가 있는 경우는
        xhtml 시절에 만들어져서 남아있는 것. html5에서 안고쳐도 되니까.

        <meta property="og:title" content="네이버">
          og : open graphic tag / 문자나 카톡으로 사이트 주소를 보낼 때 이미지, 제목, 주소가 출력됨.
```

```html
  6. 디버깅을 하지 않음
    잘못된 부분이 있어도 알려주지 않음.
    정확하게 알고 쓰는게 중요하다.
```

```html
  7. 반드시 대소문자 구분(xhtml)
    -모든 태그와 속성은 소문자로만 작성
```

```html
  8. 문서 상단에 반드시 DOCTYPE 선언
```

---

```html
*태그의 형식
  <명령어 속성 = "속성값">

  <tag     property  = "value">
  <element attribute = "value">

  <a href="http://naver.com">네이버</a>
```

---

```html
*속성의 특징
  1. 태그와 속성, 속성과 속성은 공백으로 구분
    ex) <a href="#">    <o>
        <ahref="#">     <x>

  2. 여러 개의 속성을 사용할 수 있지만(A)
    ex) A : <img src="/" width="길이" height="높이">    <o>

     같은 속성을 두 번 이상 사용 불가(B)
    ex) B : <img src="/" width="300" width="400">       <x>

  3. 하나의 속성에는 값을 한 개만 지정
    ex) <img src="/" width="300, 400">                  <x>

  4. 속성값은 원래의 이름이 한글인 경우를 제외하고 한글 사용 불가
    ex) <img width="300">     <o>
        <img width="삼백">    <x>

    예외 태그 : meta
      <meta name="keywords" content="영화, 한국영화, 외국영화">
      앞(name)에서는 질문을 하고 뒤(content)가 답하는 구조
      -name : 이 페이지에서 어떤 keywords가 검색될 건지

  5. 속성값에는 " " 생략가능 (xhtml에서는 생략 불가)
    생략가능하지만 생략하지 마라.
```

---

> **웹접근성연구소([https://www.wah.or.kr:444/index.asp](https://www.wah.or.kr:444/index.asp))**에서
한국성 웹 콘텐츠 접근성 지침 2.1 (KWCAG 2.1) 24page 보면 검사항목 24개 볼 수 있다.

콘텐츠 간의 구분 : 배경색, 테두리, 여백

6.4.2. (제목 제공) 페이지, 프레임, 콘텐츠 블록에는 적절한 제목을 제공해야 한다.
   페이지 : <title>
   프레임 : <frame title=" ">
   콘텐츠 블록 : <h1> ~ <6>

⭐7.1.1. (기본 언어 표시) 주로 사용하는 언어를 명시해야 한다.
   웹 표준성에서는 검사 안 하지만 접근성에서는 검사한다.

8.2.1. (웹 애플리케이션 접근성 준수) 콘텐츠에 포함된 웹 애플리케이션은 접근성이 있어야 한다.
   Youtube 에서 공유누르면 링크 가져올 수 있음
   ex) <iframe width="560" height="315" src="[https://www.youtube.com/embed/6QcTHBJv_pE](https://www.youtube.com/embed/6QcTHBJv_pE)" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

   iframe은 웹 화면을 뚫어서 그 뒤에 있는 컨텐츠를 보이게 해주는 원리라고 생각하면 됨.
   iframe안에서 'tab' 눌렀는데 밖으로 못 빠져나온다? -> 접근성 위반

**네이버 웹접근성 연구소 ([https://nuli.navercorp.com/](https://nuli.navercorp.com/)) :** 기본 지침서 있음(코딩 컨벤션)
>

---