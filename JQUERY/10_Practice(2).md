# Practice(2)
작성일시: 2021년 11월 5일 오후 4:39

## Practice 04_ribbon

**팝업** 종류

1. **1세대 팝업 (브라우저 팝업)** : html 따로 만들어져 나오는 팝업
                                              지금은 웹 접근성(사용자가 의도하지 않은 창은 띄우지 않는다)때문에 사라짐
2. **2세대 팝업 (레이어 팝업)** : 내용이 담긴 팝업, 사용자의 브라우저 차을 가린다는 단점이 있음
3. **3세대 팝업 (리본 팝업)** : 상단에 배너처럼 존재 하는 것

    ex) 네이버, 쿠팡에서 사용한다. (오늘 하루 안보기 기능 사용하여 한 번 닫으면 새로고침해도 다시 안 생김)


### 1) jqeury 적용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ribon pop</title>
  <style type="text/css">
		body {overflow-y: scroll;}
    body, div {margin: 0; padding: 0;}
    .wrap {text-align: center; background: url('images/bg_wrap.jpg') repeat-x;
           position: relative; top: 70px;}
    .pop {background: #a9e3f9 url('images/banner.jpg') no-repeat center;
          height: 70px; position: absolute; width: 100%;}
    .pop a {display: block; width: 38px; height: 38px; background: url('images/close.jpg') no-repeat;
            text-indent: -9999px; position: absolute; right: 16px; top: 16px;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
			$(".pop a").click(function () {
        $(".wrap").animate({ top: 0 });
      });
    });
  </script>
</head>

<body>
	*<!-- banner -->*
  <div class="pop">
    <a href="#">닫기</a>
  </div>
  <div class="wrap">
    <header></header>
    <main>
      <img src="images/content.jpg" alt="">
    </main>
    <footer></footer>
  </div>
</body>

</html>
```

해당 코드가 나오기 전 과정

1. `<script>` 처음 작성

    ```jsx
    $(document).ready(function () {
    	$(".pop a").click(function () {
        $(".pop").slideUp();
    	});
    });
    ```

2. `<script>` 수정

    ```jsx
    $(document).ready(function () {
    	$(".pop a").click(function () {
        $(".wrap").animate({ top: "-70px" });
    	});
    });
    ```

    브라우저에서 작동하지 않고 Error도 없다.

    그렇다면 문제는 HTML, CSS에 있는 것 CSS 수정하러 간다.

3. `<style>`에서 `.wrap`에 `position: absolute`를 준다.

    ```css
    .wrap {text-align: center; background: url('images/bg_wrap.jpg') repeat-x;
    			 position: absolute; top: 70px;}
    ```

    내려간 `.wrap`을 동작하면 위로 올라가도록 `<script>`를 작성한다.

4. `<script>`을 수정한다.

    ```jsx
    $(document).ready(function () {
    	$(".pop a").click(function () {
        $(".wrap").animate({ top: 0 });
    	});
    });
    ```

    ![**position: absolute**가 되면 **width**를 따로 지정해주지 않는 이상 **0**이 되므로
    저렇게 공백이 생긴다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/34918edc-939f-4250-aea3-0bbadc0d1a4d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081250Z&X-Amz-Expires=86400&X-Amz-Signature=3114a7e67cb09a0cd8213e13a98566af701e5cc1f674303b319b63e05e4252e1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

    **position: absolute**가 되면 **width**를 따로 지정해주지 않는 이상 **0**이 되므로
    저렇게 공백이 생긴다.

    다시 `.wrap`의 `<style>`를 수정한다.

5. `.wrap`의 `position`을 `relative`로 수정하고,
그에 맞게 `<script>`도 수정한다.

    ```jsx
    $(document).ready(function () {
    	$(".pop a").click(function () {
        $(".wrap").animate({ top: "-70px" });
    	});
    });
    ```

    ```css
    .wrap {text-align: center; background: url('images/bg_wrap.jpg') repeat-x;
    			 position: relative; top: 0px;}
    ```

    scroll이 생기는 것을 없애기 위해
    `.pop` `position: absolute` 를 추가한다.


1. `.pop`의 `<style>` 수정한다.

    ```css
    .pop {background: #a9e3f9 url('images/banner.jpg') no-repeat center;
          height: 70px; position: absolute; width: 100%;}
    ```

    `.pop`에 `absolute`를 부여함에 따라
    `.wrap`이 브라우저 최상단으로 올라가기 때문에 `top`을 수정해준다.

2. `.wrap`에 `top: 70px;` 작성한다.

    ```css
    .wrap {text-align: center; background: url('images/bg_wrap.jpg') repeat-x;
    			 position: relative; top: 70px;}
    ```

3. `<script>` 수정한다.

    ```jsx
    $(document).ready(function () {
    	$(".pop a").click(function () {
        $(".wrap").animate({ top: 0 });
    	});
    });
    ```

    여기서 동작하면서 화면이 흔들리는 문제가 발생한다.

    `body`에 **scroll** 생기게 해서 해결한다.

4. `body`에 `overflow` 작성한다.

    ```css
    body {overflow-y: scroll;}
    ```


<aside>
💡 *요소에 다 `position`있으면*

*코딩 순서상 밑에 있는 것이 위층에 있음*

                                                          *-->  그래서 `z-index` 사용*

</aside>

---

## Practice 05_gnb

GBN에 마우스 가져가면 하위메뉴들 보이기

### 1) jqeury 적용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>gnb</title>
  <style type="text/css">
		body, header, nav, div, ul, li {margin: 0; padding: 0;}
    ul, li {list-style: none;}
    a {text-decoration: none;}
    header {padding-top: 80px; border-bottom: 1px solid #333; height: 40px;}
	  .gnb h2 {position: absolute; left: -9999px; top: -9999px;}

    .gnb>ul {width: 1000px; height: 40px; margin: auto;}
    .gnb>ul>li {font-size: 20px; font-family: "나눔고딕"; float: left;
					      width: 17%; margin-right: 3%; background: #333; height: 40px; line-height: 40px; text-align: center; position: relative;}
    .gnb>ul>li>a {display: block; height: 40px;}
    .gnb ul ul {padding-top: 20px; width: 100%; position: absolute; left: 0;
					      top: 40px; background: #aaa; display: none;}
    .nav_bg {width: 100%; height: 240px; background: #eee; display: none;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">

	</script>
</head>

<body>
	<header>
    <nav class="gnb">
      <h2>주요메뉴</h2>
      <ul>
        <li class="menu01"><a href="#">주메뉴</a>
          <ul>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
          </ul>
        </li>
        <li><a href="#">주메뉴</a>
          <ul>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
          </ul>
        </li>
        <li><a href="#">주메뉴</a>
          <ul>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
          </ul>
        </li>
        <li><a href="#">주메뉴</a>
          <ul>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
          </ul>
        </li>
        <li><a href="#">주메뉴</a>
          <ul>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
            <li><a href="#">하위메뉴</a></li>
          </ul>
        </li>
      </ul>
    </nav>
    <div class="nav_bg"></div>
  </header>
</body>

</html>
```

### 메뉴 하나씩 나타나게 하기(1)

```jsx
$(document).ready(function () {
	$(".menu01").mouseenter(function () {
    $(".menu01 ul").slideDown("fast");
  });
});
```

### 메뉴 하나씩 나타나게 하기(2)_ this사용

```jsx
$(document).ready(function () {
	$(".gnb>ul>li").mouseenter(function () {
	  $(this).find("ul").stop().slideDown("fast");
  });
	  $(".gnb>ul>li").mouseleave(function () {
	    $(this).find("ul").stop().slideUp("fast");
  });
});
```

**`find()`**는 자식, 후손 모두 선택 가능,
	     지시사항없으면 무조건 첫번째 것임, ()안에 찾을 거 작성하면 됨

**`children()`**은 자식만 선택한다.

### 하위메뉴 전체 나타나게 하기

```jsx
$(document).ready(function () {
	$(".gnb>ul>li").mouseenter(function () {
    $(".gnb ul ul").stop().slideDown("fast");
  });
  $(".gnb>ul>li").mouseleave(function () {
    $(".gnb ul ul").stop().slideUp("fast");
  });
});
```

### 전체 배경색과 함께 나타나게 하기

```jsx
$(document).ready(function () {
	$(".gnb>ul>li").mouseenter(function () {
    $(".gnb ul ul, .nav_bg").stop().slideDown("fast");
  });
  $(".gnb>ul>li").mouseleave(function () {
    $(".gnb ul ul, .nav_bg").stop().slideUp("fast");
  });
});
```

### **발생하는 문제 (1)**

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d871f9d1-ae44-4b07-a80c-36503e3e275a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081307Z&X-Amz-Expires=86400&X-Amz-Signature=b6944b59d677450255c6b3fa4b2b54cb70853530adfa675d41aa97f150b28eef&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

주메뉴 사이 간격이 있어서 그 사이에 마우스가 있을 때
`mouseleave`로 인식해서 하위메뉴가 사라진다.

⇒ `.gnb>ul>li` 의 `width`나, `margin-right`를 수정한다.

```css
.gnb>ul>li {
      font-size: 20px;
      font-family: "나눔고딕";
      float: left;
      width: 17%;         --> 1) width:20%; 수정, margin 제거
      margin-right: 3%;   --> 2) padding으로 수정
      background: #999;
      height: 40px;
      line-height: 40px;
      text-align: center;
      position: relative;
    }
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/98a7b9f6-c7c1-4efc-82a9-e4b0ae87135c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081334Z&X-Amz-Expires=86400&X-Amz-Signature=110aff22d8dca4a9f42e977097da10d9efbc0fc5e6c6f7c38576244c05b157ec&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

### **발생하는 문제 (2)**

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/17db87d9-6f11-4f29-aefc-14a3b6a004aa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081326Z&X-Amz-Expires=86400&X-Amz-Signature=cd23505e32e6b15f7f7efd722e22abe9b247a41633c5fb7ab6137b81019e122a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

주메뉴와 하위메뉴 사이에 공백을 넣으면
( `.gnb ul ul {top: 40px → 80px(변경)}` ),
해당 위치에 마우스가 있을 때 `mouseleave` 된다.

⇒ `top:80px`을 주면 주메뉴와 공백이 생겨서 그 부분에서는 하위 메뉴 사라짐
      --> 여백을 주고싶으면 `padding-top`, `height`으로 여백처럼 보이게 준다.

```css
.gnb ul ul {
      padding-top: 20px;
      width: 100%;
      position: absolute;
      left: 0;
      top: 40px;     --> 삭제 / padding-top: 80px 수정
      background: #aaa;
      display: none;
    }
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/290c950f-4887-4802-96ed-da516424f4c4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081344Z&X-Amz-Expires=86400&X-Amz-Signature=e7ca331d8fe48025b814ff0b5e27d3f2b57a661c6f9344745b14f9e378addd38&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

### **발생하는 문제 (3)**

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/33d0db28-1467-45d9-8731-7773f6360fee/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081350Z&X-Amz-Expires=86400&X-Amz-Signature=ab8fef449d98045309f5671b986735e4cd980963502f162f865678950dd1dd37&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

position: absolute를 쓰면 inline-block되서 내부 content가 없으면 크기가 없다.
그래서 width, height 꼭 지정해준다.

```css
.gnb ul ul {
      padding-top: 20px;
      width: 100%;
      position: absolute;
      left: 0;
      top: 40px;
      background: #aaa;
      display: none;
    }

    .nav_bg {
      width: 100%;
      height: 240px;
      background: #eee;
      display: none;
    }

 /* position:absolute주고 내부에 content없으면 width 0이니까 width 꼭 주기 */
```

---

## Practice 06_tab

탭메뉴와 그 내용 만들기

탭 메뉴와 인덱스가 동일한 탭스가 보여져야 한다.

### 1) jqeury 적용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>tab</title>
  <style type="text/css">
		ul, li, h2, p {margin: 0; padding: 0; list-style: none;}
    a {text-decoration: none;}
    .blind {position: absolute; left: -9999px; height: -9999px;}
    .tab_menu {width: 300px; height: 300px;ㅠborder: 1ps solid #999; position: relative;}
    .tab_menu a {display: block; height: 100%; text-align: center;
					       line-height: 40px; font-size: 16px; font-weight: bold; color: #fff;}
    .list1 {width: 100px; height: 40px; background: rgb(225, 203, 61);
			      position: absolute; top: 0; left: 0;}
    .list2 {width: 100px; height: 40px; background: rgb(157, 246, 84);
			      position: absolute; top: 0; left: 100px;}
    .list3 {width: 100px; height: 40px; background: rgb(74, 789, 255);
			      position: absolute; top: 0; left: 200px;}
    .tab1 {width: 300px; height: 260px; background: rgb(225, 145, 0);
			     position: absolute; left: 0; top: 41px}
    .tab2 {width: 300px; height: 260px; background: rgb(124, 236, 32);
		       position: absolute; left: 0; top: 41px; display: none;}
    .tab3 {width: 300px; height: 260px; background: rgb(29, 146, 241);
		       position: absolute; left: 0; top: 41px;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">

	</script>
</head>

<body>
	<div class="tab_menu">
    <div class="list">
      <h2 class="blind">TITLE</h2>
      <ul>
        <li class="list1"><a href="#">1</a></li>
        <li class="list2"><a href="#">2</a></li>
        <li class="list3"><a href="#">3</a></li>
      </ul>
    </div>

    <div class="tabs">
      <div class="tab1">
        <h2 class="blind"><a href="#">1</a></h2>
        <p>11111</p>
      </div>
      <div class="tab2">
        <h2 class="blind"><a href="#">2</a></h2>
        <p>22222</p>
      </div>
      <div class="tab3">
        <h2 class="blind"><a href="#">3</a></h2>
        <p>33333</p>
      </div>
    </div>
  </div>
</body>

</html>
```

### 하나씩 작성하기

```jsx
$(document).ready(function () {
	$(".list1").click(function () {
    $(".tab1").show();
    $(".tab2").hide();
    $(".tab3").hide();
  });
  $(".list2").click(function () {
    $(".tab1").hide();
    $(".tab2").show();
    $(".tab3").hide();
  });
  $(".list3").click(function () {
    $(".tab1").hide();
    $(".tab2").hide();
    $(".tab3").show();
  });
});
```

### this, index 사용해서 작성하기

```jsx
$(document).ready(function () {
$(".list li").click(function () {
    /* 탭메뉴와 인덱스가 동일한 탭스가 보여진다. */
    var idx = $(this).index();
    $(".tabs div").hide();           // <-- 누가 켜져있는지 알수없으니까 몽땅 감춤
    $(".tabs div").eq(idx).show()    // <-- 내가 클릭한 li와 순서가 같은 div 보여줘
  });
});
```

<aside>
💡 " "안에 변수 직접 작성할 수 없음, 문장으로 작성해야함

  `var show_box = ".tabs div:eq("+idx+")";
  $(show_box).show();`

</aside>

---

## Practice 07_accordion

질문을 클릭하면 답변이 밑에 보여진다.

### 1) jqeury 적용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>accordion</title>
  <style type="text/css">
		div {margin-bottom: 10px;}
    h2, p {padding: 0; margin: 0;}
    h2 {font-size: 14px; cursor: pointer; margin-bottom: 5px;}
    p {height: 100px; background: #eee; margin-bottom: 20px; display: none;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">

	</script>
</head>

<body>
	<div class="qna1">
    <h2>질문 1</h2>
    <p>답변 1</p>
  </div>
  <div class="qna2">
    <h2>질문 2</h2>
    <p>답변 2</p>
  </div>
  <div class="qna3">
    <h2>질문 3</h2>
    <p>답변 3</p>
  </div>
</body>

</html>
```

### 각각 slideDown 적용하기

```jsx
$(document).ready(function () {
	$(".qna1 h2").click(function () {
    $(".qna1 p").slideDown("fast");
  });
  $(".qna2 h2").click(function () {
    $(".qna2 p").slideDown("fast");
  });
  $(".qna3 h2").click(function () {
    $(".qna3 p").slideDown("fast");
  });
});
```

### 각각 slideToggle 적용하기

```jsx
$(document).ready(function () {
	$(".qna1 h2").click(function () {
    $(".qna1 p").slideToggle("fast");
  });
  $(".qna2 h2").click(function () {
    $(".qna2 p").slideToggle("fast");
  });
  $(".qna3 h2").click(function () {
    $(".qna3 p").slideToggle("fast");
  });
});
```

### .next() 사용하기

```jsx
$(document).ready(function () {
	$("div h2").click(function () {
    $(this).next().slideDown("fast");
  });
});
```

### 펼쳐진 건 닫고 클릭한 답변 열기

```jsx
$(document).ready(function () {
	$("div h2").click(function () {
    $("div p").slideUp("fast");     // <-- 열려져있는 요소 누르면 문제생김 (다시 접었다가 펴야하니까)
	  $(this).next().slideDown("fast");
  });
});
```

`.stop()` 사용해서 해소할 수도 있지만 그렇게 작성하지 않음

```jsx
$(document).ready(function () {
$("div h2").click(function () {
    $("div p").stop().slideUp("fast");
    $(this).next().stop().slideDown("fast");
  });
});
```

### .not() 사용해서 클릭한 요소 다음 것 빼고 적용하기

```jsx
$(document).ready(function () {
	$("div h2").click(function () {
    $("div p").not($(this).next()).slideUp("fast");
    $(this).next().slideToggle("fast");
  });
});
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4d923a72-3fd4-44e3-898c-efc777ed724e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081408Z&X-Amz-Expires=86400&X-Amz-Signature=ace5fc87c79765816f3b811ae1b7aeb6e7b3f714d0db0bc2a8e259a2308c6039&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---