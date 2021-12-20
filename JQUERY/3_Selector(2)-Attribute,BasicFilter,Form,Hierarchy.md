# Selector(2)-attribute, basic filter, form, hierarchy
작성일시: 2021년 11월 3일 오후 4:04

## 예제 2

선택자 사용해서 css 적용하기

```css
body, input {font-size: 24px}
input[type=checkbox] {width: 24px;height: 24px}
.pinkBG {background: rgb(241, 47, 199)}
.greenText {color: green}
.yellowBG {background: yellow}
.redBG {background: red}
.whiteText {color: #fff}
.redBrd {border: 2px solid #f00}
.blueBrd {border: 2px solid #00f}
.greenBG {background: green}
.redOL {outline: 2px solid #f00}
```

### #1. basic selecter

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="utf-8">
  <title>제이쿼리 - 선택자</title>
  <!-- 제이쿼리 가져오기 -->
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script type="text/javascript">
	<!-- 문서가 준비되었는지 확인하기 -->
    $(document).ready(function () {
      /* basic selector */
      // red라는 아이디를 가진 요소에 분홍색 배경 적용
      $("#red").addClass("pinkBG");
      // blue라는 클래스를 가진 요소에 초록색 글자색 적용
      $(".blue").addClass("greenText");
      // 모든 span에 노랑색 배경색 적용
      $("span").addClass("yellowBG");
	  });
</head>

<body>
  <!-- basic selector -->
  <p id="red"><span>제이쿼리</span>를 이용하여 스타일 적용하기</p>
  <p class="blue"><span>스타일시트</span>의 선택자를 그대로 사용 가능합니다.</p>
</body>

</html>
```

### #2. attribute selecter

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="utf-8">
  <title>제이쿼리 - 선택자</title>
  <!-- 제이쿼리 가져오기 -->
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script type="text/javascript">
	<!-- 문서가 준비되었는지 확인하기 -->
    $(document).ready(function () {
     /* attribute selector */
      // "blog.naver.com"이라는 값을 사용하는 요소에 빨간색 배경 적용
      $("a[href='blog.naver.com']").addClass("redBG");    // <-- 적용되지 않음 (완전 똑같아야 되는거니까)
      /* 적용시키려면
          $("a[href='http://blog.naver.com']").addClass("redBG");
          $("a[href*='blog.naver.com']").addClass("redBG");
          $("a[href$='blog.naver.com']").addClass("redBG"); */

      // "naver"가 들어 있는 모든 요소에 빨간색 배경 적용
      $("*[href*='naver']").addClass("redBG");
      // a 태그내에 target 속성을 사용하는 요소에 하얀색 글자 적용
      $("a[target]").addClass("whiteText");
	  });
</head>

<body>
  <!-- attribute selector -->
  <p><a href="http://blog.naver.com" title="네이버 블로그로 이동">네이버 블로그</a></p>
  <p><a href="http://cafe.naver.com" target="_blank">네이버 카페</a></p>
</body>

</html>
```

**Selector - Attribute**

태그들이 가지고있는 속성과 값을 이용하는 선택방법 / 사용방법상의 정의는 대괄호 [ ]

`$(" selector [ attr = 'value' ] ").~~();
         ↑       ↑        ↑
       <img     width = "200"  src="  " >`

<aside>
💡 **따옴표 사용 주의**

- 큰 따옴표(" ") 외부에 사용했으면 내부에는 작은 따옴표(' ') 사용
- 작은 따옴표(' ') 외부에 사용했으면 내부에는 큰 따옴표(" ") 사용
- 동급 따옴표를 사용하고 싶으면 역슬래시(\)사용
ex)     `"   \"   \"   "`
          `'   \'    \'  '`
</aside>

연산기호가 연속될 때 ?는 항상 앞에, =는 항상 뒤에

`$(" selector[ attribute ?= 'value' ]").~~();`

> **일부 종류**
>
> 1.  **Contains Prefix**
> 똑같은 단어이거나 똑같은 단어에 -로 연결되어있는 모든 것 선택
> 2. **Contains**
> 값에 그런 단어가 들어있기만 하면 선택
> 3. **Contains Word**
> 값에 그 철자가 단어(앞뒤로 공백이 있는)의 형태있는 것 선택
> 4. **Equals**
> 정확하게 확실하게 완벽하게 값이 같아야 선택

### #3. hierarchy selecter

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="utf-8">
  <title>제이쿼리 - 선택자</title>
  <!-- 제이쿼리 가져오기 -->
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script type="text/javascript">
	<!-- 문서가 준비되었는지 확인하기 -->
    $(document).ready(function () {
     /* hierarchy selector */
      // 하위 계층에만 테두리 적용
      // $("li").addClass("redBrd");
      // $("ul li").addClass("redBrd");
      // $("ul > li").addClass("redBrd");
      $(".DOMTree>li").addClass("redBrd");
      // 손자 계층에만 테두리 적용
      // $(".DOMTree ul li").addClass("blueBrd");
      $("li li").addClass("blueBrd");
	  });
</head>

<body>
  <!-- hierarchy selector -->
  <ul class="DOMTree">
    <li>ul의 하위 계층</li>
    <li>ul의 하위 계층
      <ul>
        <li>여기는 손자계층</li>
        <li>여기는 손자계층</li>
      </ul>
    </li>
    <li>ul의 하위 계층</li>
  </ul>
</body>

</html>
```

### #4. basic filter selector

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="utf-8">
  <title>제이쿼리 - 선택자</title>
  <!-- 제이쿼리 가져오기 -->
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script type="text/javascript">
	<!-- 문서가 준비되었는지 확인하기 -->
    $(document).ready(function () {
     /* basic filter selector */
      // 첫번째 단락에 초록색 배경 적용
      // $(".basic_filter p:first").addClass("greenBG");
      // $(".basic_filter p:eq(0)").addClass("greenBG");
      $(".basic_filter p:lt(1)").addClass("greenBG");
      // 홀수번째 단락에 분홍색 배경 적용
      // $(".basic_filter p:odd").addClass("pinkBG");
      $(".basic_filter p:not(p:even)").addClass("pinkBG");
	  });
</head>

<body>
  <!-- basic filter -->
  <div class="basic_filter">
    <p>첫 번째 문단</p>
    <p>두 번째 문단</p>
    <p>세 번째 문단</p>
    <p>네 번째 문단</p>
  </div>
</body>

</html>
```

**Selector - Basic Filter**

사용방법상의 정의는 콜론( : )
`$(" selector : Filter ").~~();`

> **일부 종류**
>
> 1. **: animated**
> 움직이고 있는 대상
> 2. **: eq()**
> equal(=)의 의미, index(순번)이 일치하는 것
> $(" selector : eq(index) ").~~();
> 3. **: gt()**
> 내가 어떤 순서 지목하면 그 순서보다 높은 순서 다 가지고 오기
> 4. **: lt()**
> 내가 어떤 순서 지목하면 그 순서보다 낮은 순서 다 가지고 오기
>
>     <aside>
>     💡 **Tip_** HTML에서 < 는 `&lt;` , > 는 `&gt;` 로 표현
>
>     </aside>
>

### #5. form filter selector

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="utf-8">
  <title>제이쿼리 - 선택자</title>
  <!-- 제이쿼리 가져오기 -->
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script type="text/javascript">
	<!-- 문서가 준비되었는지 확인하기 -->
    $(document).ready(function () {
     /* form filter */
      // type값이 text인 요소에 빨간색 배경, 흰색 글자
      // $(":text").addClass("redBG whiteText");
      /* jquery에서 **css() 메소드** 있음
          **.css("prop", "value")**     */
      // $(":text").css("background", "red");
      $(":text").css({ background: "red", color: "white" })

      // 체크된 필드에 테두리 지정
      // $(":checked").addClass("redOL");
      // $(":checked").css({border: "2px solid #f00"});    // <-- 적용안됨
      /* HTML5 이전에는 checkbox외부에 border가 있었는데
          그러면 checkbox 자체 테두리는 뭐라고 하게?
        HTML5 부터 checkbox 자체 테두리를 border라고 하기로 했다.
          그러면 예전에 있던 외부 border는>  ==> outline */
      $(":checked").css({ outline: "2px solid #f00" });
	  });
</head>

<body>
  <!-- form filter -->
  <p><input type="text"></p>
  <p><input type="password"></p>
  <p><input type="checkbox" checked="checked">CheckBox #1</p>
  <p><input type="checkbox">CheckBox #2</p>
</body>

</html>
```

**Selector - Form**

Form에서 핵심은 속성값이다.
속성값으로 selector하면 몇개가 있든 같은 스타일 적용할 수 있다.

<Form> 요소들은 type의 value만 바뀔 것이기 때문에
속성의 값을 필터처럼 사용함.

**.css( ) 메소드**

`obj.css("prop", "value")` 작성

여러 개의 style을 한번에 주고 싶다면,
`obj.css({prop1:"value1", prop2:"value2", ...})`

---