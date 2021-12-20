# jquery 개요 및 적용
작성일시: 2021년 11월 2일 오후 4:43

# Intro

자바스크립트에서 요소를 선택하는 방법

`<formname="join">
    <input type=""name="txt" class="box" id="uid">`

`<input>`을 선택하려면

**(기존)** : `<form>`의 `name`을 사용한다. `document.join.txt`

**(DOM)** : 태그 종류들 상관없이 선택 가능 `document.getElementById("uid")`

**(추가)** : `document.querySelector("input OR .box OR #uid")`

---

## jquery

> 자바스크립트 라이브러리
자바스크립트 코드를 간결한 상태로 개발이 가능하다.
>

### 특징

1. **css 셀렉터**

    html 내의 엘리먼트들을 손쉽게 표현 및 사용이 가능

2. **플러그인 아키텍처**

    이미 개발된 많은 플러그인을 쉽고 빠르게 사용
    (이미 효과는 만들어져 있어서 우리꺼에 가져다가 쓰기만 하면 됨.)

3. **메소드 체인**

    여러 개의 기능을 한 줄에 나열하여 불필요한 코드 반복을 줄임

    ```
    obj . property = value
                      **∥**
    obj . method ( parameter )    <- ()는 대부분 명령을 받는다.(tip! 보통 동사를 사용하면 method일 가능성多)
    ```

    **jquery**는 기본적으로 **method 방식**을 사용한다.
      - javascript
        `window.alert()`
        `window.confirm()`                       --> 객체 호출 두 번

      - jquery
        `$(window).alert().confirm()`      --> 객체 호출 한 번

4. **크로스 브라우저**

    브라우저별 발생 이벤트를 각각 지정 해 줄 필요가 없음


*제이쿼리는 여전히 실무에서 빛을 내고 있다. 사용할 수 있는 자원이 많으니까*

---

## 적용 방법

`<scripttype="text/javascript"src="제이쿼리 문서 경로"></script>`

1. **local import**

    - 파일을 다운로드 후 html 문서에 임포트
    - js 파일을 항상 같이 이동
    - 한국 서버에 있는 js 파일을 다른 나라의 사용자가 접속하려 할 경우
      속도 저하 발생 가능

2. **CDN (Content Delivery Network)**

    - 특정 웹 사이트에서 제공하고 있는 파일을 링크
    - 웹 사용 불가 시 스크립트 동작 안됨
    - jquery.com / google.com / microsoft.com


### 다운로드

> **j-Query Download**  [http://jquery.com](http://jquery.com/)
>

1. **minified**

    - 파일을 최소화 시키기 위해 불필요한 공백과 줄바꿈 생략
    - 일반적으로 사용

2. **uncompressed**

    - 코멘트 등 포함
    - 코드 분석 시 사용


---

jquery는 적용하는 법 빼고 두 가지만 알면 됨  -  1. 함수  2. 문법

### 함수

> **selector`($() 함수)`**      <-- `$()` 효과를 주고 싶은 아이를 선택할 때 사용
>
>
> ex) `<input type=""name="txt"class="box"id="uid>`
>       **css** 에서는 `input` / `.box` / `#uid`
>       **jquery** 에서는 `$("input")` / `$(".box")` / `$("#uid")`
>       **script**에서는 `document.querySelector(" ")`
>

### 문법

> jquery(선택자).메소드()
`$(선택자).메소드()`
>
>
>
> $(누구한테).어떤효과를()
> $(누구한테).어떤효과를("")
> $(누구한테).어떤효과를({ })
> $(누구한테).어떤효과를(function(){ })
>
> $(누구한테).어떤효과를().다른효과({ }).다른효과(function(){ })
>

### ready() 메소드

1. javascript의 window.onload 와 같은 기능이지만 이 기능보다 정확하게 동작
2. 스크립트가 먼저 작성되고 body 요소가 나중에 작성되기 때문에 스크립트 오류가 발생하는 것을 방지
3. 문서내에 한 번만 선언
4. `$(document).ready(function(){
   실행할 문정 전체
})`

---

### 예제 1

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>제이쿼리 적용</title>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.4.1.min.js"></script>
  <script type="text/javascript">
    $(function () {
      window.alert("스크립트를 실행합니다.");
    });
  </script>
</head>

<body>

</body>

</html>
```

---

### 예제 2

**제이쿼리 적용할 때 순서**

1. 라이브러리 가져오기
    1. local import
    2. CDN : 외부 주소 참조
2. 문서가 준비되었는지 확인
    1. `$(document).ready(function(){ });`
    문서를 나타내주는 객체들은 " "를 작성하지 않음
3. 기본 세팅 후 웹 브라우저에서 개발자 도구 열어서 오류 있는지 확인한다.

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>제이쿼리 템플릿</title>
  1. 라이브러리 가져오기
    1-1. local import
    <script type="text/javascript" src="jquery/jquery-3.6.0.min.js"></script> -->
    1-2. CDN : 외부 주소 참조 -->
    <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>

  2. 문서가 준비되었는지 확인하기 -->
    <script type="text/javascript">
    // js : window.onload=function(){ };
    // jq : $(document).ready(function(){ });

    $(document).ready(function () {

    });
  </script>
</head>

<body>

</body>

</html>
```

<aside>
💡 선택한 객체가 `document`이고 적용된 method가 `ready`라면 생략할 수 있음
`$(document).ready(function () {   });`
      **↓**
`$(function(){ });`

</aside>

---