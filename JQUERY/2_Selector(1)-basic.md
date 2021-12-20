# Selector(1)-basic
작성일시: 2021년 11월 2일 오후 5:35

# Intro

앞서 배운 javascript에서 css 사용법은 2가지

1)   obj.style.prop="value"
      <elem style="prop:value"s

2)    css -    .txt{ }
       js -      obj.className="txt"
       html - <elem class="txt"

---

## Selector - Basic

1. **$("element")**

    특정 엘리먼트(태그) 지정

    ```jsx
    ex) $("tr").addClass("blue");
    ```

2. **$("#id")**

    - 특정 아이디 지정

    ```jsx
    ex) <a href="#" id="test">LINK</a>
        $("#test").addClass("red");
    ```


1. **$(".class")**

    - 특정 클래스 지정

    ```jsx
    ex) <a href="#" class="test">LINK</a>
        $(".test").addClass("blue");
    ```


1. **$("selector1, selector2, selectorN")**

    - 다중 선택자, 여러 개의 선택자에 동시에 효과 적용

    ```jsx
    ex) $("h2, h3, h4").addClass("pink");
        $("h2, #test, .hidden").addClass("pink");
    ```


---

## 예제 1

```jsx

<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>제이쿼리 스타일 적용</title>
  <style type="text/css">
    body {font-size: 24px;}
    .pink {background: #f6f;}
    .greenText { color: #0f0;}
    table {width: 800px; height: 240px; border: 1px solid #999; text-align: center;}
    td {border: 1px solid #999;}
    .whiteText {color: #fff;}
  </style>

  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
      // red라는 아이디를 가진 요소에 분홍색 배경 적용
      $("#red").addClass("pink");

      // blue라는 클래스를 가진 요소에 초록색 글자색 적용
      $(".blue").addClass("greenText");

      // 모든 td에 분홍색 배경색 적용
      $("td").addClass("pink")

      // 분홍색 배경색이 적용된 요소에 흰색 글자색 적용
      /* $(".pink").css("color", "white"); */
      $("#red, td").addClass("whiteText");
      $(".pink").addClass("whiteText");
    });
  </script>
</head>

<body>
  <p id="red">제이쿼리를 이용하여 스타일 적용하기</p>
  <p class="blue">스타일시트의 선택자를 그대로 사용 가능합니다.</p>
  <table>
    <tr>
      <td>첫 번째 셀</td>
      <td>두 번째 셀</td>
      <td>세 번째 셀</td>
      <td>네 번째 셀</td>
    </tr>
  </table>
</body>

</html>
```

---