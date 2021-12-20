# CSS 기본 내용
작성일시: 2021년 8월 27일 오후 2:59

- **CSS**
웹 페이지는 구조-html/디자인-css/동작-javascript을 나눠서 만듦
웹 페이지의 표현(디자인)을 나타내는 언어

    현재는 CSS 3 / 레벨이 올라갈수록 효과를 적용할 수 있는 범위가 넓어짐
    효과의 종류와 선택하는 방법이 많아짐

    ---

- **HTML과 CSS 구조 비교**


    [HTML 구조]
    < A B = " C " B = " C " ... >

    [CSS 구조]
    selector (선택자, 효과를 적용할 대상 선택) {
    property(어떤 효과) : value(얼만큼) ;
    B : C ;
    }

    *property는 html에서 B에 속함(속성, attribute)
         - value는 html에서 C에 속함
         - :는 html에서 =에 속함
         - ;는 html에서 띄어쓰기에 속함
         - selector는 효과를 적용할 대상으로 html에서 A에 속함

    *html은 한줄로 쓰지만 css는 상관없음,
      하지만 실무에서는 줄 바꿈이나 들여쓰기는 안하는게 좋음

    ---

- **스타일 적용**
    1. 내부 스타일
    <head>
    <style type="text"> <--스타일 선언문
    selector { property : value }
    </style>
    2. 외부 스타일
    selector { property : value } <--name.css로 저장, 선언문 생략

        <head>
        <link rel="stylesheet" type="text/css" href="name.css">


    사실 스타일 적용 방법은 4가지 (실무에서는 1번, 3번 사용)

    1. **internal style**
    <head>
    <style>
    ~
    </style>
    2. **inline style** - 태그에 직접 작성
    <elem style="prop:val">
    3. **external style** (link 방식)
    NAME.css 따로 저장한 후에
    <head>
    <link rel="" type="" href="NAME.css">
    4. **external style** (import 방식) - 낮은 버전 브라우저에서는 적용 안됨
    <head>
    <style>
    @import "NAME.css";
    </style>

    ---