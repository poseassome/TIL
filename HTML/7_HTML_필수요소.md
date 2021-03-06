# HTML 필수요소
작성일시: 2021년 8월 23일 오후 5:38

Editor는 어떤 것을 써도 상관없지만, 수업에서는 Visual studio 사용함.

에디터를 열면 가장 먼저 어떤  폴더를 사용할 것인지 지정을 해줘야함.

그리고 파일을 생성하는데, 확장자를 쓰고 저장하도록함 (NAME.EXT)

> hello.html 파일을 작성하고 웹페이지에서 보려면,
FTP 프로그램을 연결하고 컴퓨터에 있는 해당 파일을 FTP 내부의 HTML 폴더로 Drag and Drop.

웹사이트에 접속했을 때 해당 페이지를 보고싶으면
ID.dothome.co.kr/filename.EXT
으로 접속한다.
>

---

```html
***웹 브라우저 : 인터넷 화면을 보여주는 프로그램**
  (ex : Chrome, Fire Fox, Safari, Opera, Explorer ...)
      많이 쓰는 브라우저 지정, 5대 브라우저 (다양한 환경에서 확인해 볼 필요가 있다.)
      저 5개의 이름이 중요하지않음.
      >>왜 5대 브라우저가 생겼는지에 대한 근원이 중요함.

  내가 만든 화면이 다른 브라우저에서도 잘 보일 수 있도록 만들어야하는 의무가 있음
  이 과정을 'Cross Browsing' 이라고 함.

  >>웹을 만들면 크로스브라우징 꼭 해야함.
_____________________________________________________________________________________

***HTML (Hyper Text Markup Language)**
  :웹 페이지를 작성하는 언어

 웹 문서 / html 문서 / html 페이지
_____________________________________________________________________________________

***웹 페이지 생성**
  1. 저장할 때 확장자는 반드시 .html 또는 .htm
    (.htm은 이제 안씀)
  2. 가장 먼저 보여질 화면의 이름은 반드시 "index.html"
    공통적으로 생략해도 되는 태그를 지정해주고 있음 ->index라고 저장한건 이름 생략할 수 있다.

  맨 처음에 보이는 화면은 main page / 그 외에는 sub page 라고 부르지만
  main page -index.html / sub page -notice.html, event.html, map.html,... 라고 저장되야 된다.
```

---

```html
***표준화 페이지 기본 형식**
  <!DOCTYPE html>
  <html lang="ko">
    <head>
      <meta charset="utf-8">
      <title>문서 제목</title>
    </head>

    <body>

    </body>
  </html>
_____________________________________________________________________________________

  <!DOCTYPE html>
          -Document Type (html 4.01, xhtml 1/0, html 5)
          -설명서 역할, 단 강제성이 없음. 그래서 크로스브라우징 해야함.
  <html lang="ko">
          -기본언어 설정(이 화면에서는 이 언어를 기본으로 사용할거야.)
          -Screen Reader(저시력자 분들) <-조만간 사라질 것으로 보임
            -JAWS/NVDA
            -Sense
          -웹 표준 검사에서는 없어도 되지만, 웹 접근성에서는 필요함. (중요도: 웹 표준 << 웹 접근성)
           웹 접근성은 최악의 경우, 벌금형이 따라옴.
           웹 접근성 검사는 어떻게? 기관에 의뢰 -> KWCAG 2.1 (24가지의 검사항목)
   <head>
      <meta charset="utf-8">
          -어떤 글자를 사용하는지 명시 (언어와 문자는 다름)
          -character(=문자) + set
          -한글 깨지면 무조건 charset !!
          -"euc-kr" : 한글 문자 선언 값, 한글밖에 모르고 특수문자도 깨짐
                      저장할 때 인코딩을 ANSI로 하면 한글이 깨지지 않음
          -선언 값과 저장 값이 상이하면 언어가 깨짐 (원인은 오직 여기 !)
          -문서에 작성한 형식과 저장한 형식이 다르면 생기는 문제.
          -현재 전 세계적으로 charset은 하나밖에 안씀 ->> UTF-8 (원래 사람이 쓰던 언어가 아닌 장치들이 쓰던 언어임)
                                                         모든 언어를 다 알고 있음
      <title>문서 제목</title>
          -Browser나 Screen Reader가 가장 먼저 읽어주는 부분이기 때문에 그 페이지의 키워드를 써주는게 필요하다.
          -보통 Sub page의 내용과 title은 거의 똑같음
          -Main page는 내용이 다양하니까 회사이름, 브랜드 이름 쓰면 됨
    </head>

    <body>

    </body>
  </html>
```