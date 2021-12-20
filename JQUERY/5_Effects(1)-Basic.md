# Effects(1)-Basic
작성일시: 2021년 11월 4일 오후 4:43

## 1. Basic

1. hide()
    - 지정된 요소를 감추기
    - 매개변수 없음
    - `$("대상").hide()`

2. show()
    - 지정된 요소를 보이기
    - 매개변수 없음
    - `$("대상").show()`

3. toggle()
    - 지정된 요소의 속성을 교차
    - `$("대상").toggle()`

---

### 예제

클릭하면 사라지거나 보이기

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>basics</title>
  <style type="text/css">
    body {font-size: 20px;}
    #pop {width: 300px; height: 400px; position: absolute;
					left: 50px; top: 50px; background: #09f;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
      /* hide() */
      $("a:last").click(function () {
        $("#pop").hide();
      });

      /* show() */
      $("a:first").click(function () {
        $("#pop").show();
      });

      /* toggle() */
      $("a:eq(1)").click(function () {
        $("#pop").toggle();
      });
    });
  </script>
</head>

<body>
  <a href="#">보이기</a>
  <a href="#">바꾸기</a>
  <div id="pop">
    <a href="#">감추기</a>
  </div>
</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cc305b89-a105-404d-82b2-e517acc74cd2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T080845Z&X-Amz-Expires=86400&X-Amz-Signature=71bbeed8eb29cee2b754853af54f3ae2a00547bc22f8911414c57e59689265b3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

**보이기**로 **#pop**을 제어하려면

1. `<style>#pop{display : none;}`추가
2. `<script>` 작성

    ```jsx
    $("a:first").mouseleave(function () {
     $("#pop").hide();
    });

    $("a:first").mouseenter(function () {
     $("#pop").show();
    });
    ```


**실시간검색어 유사 기능** 사용하려면

1. `<style>` **#pop** 다시 작성

    ```css
    #pop {width: 300px; height: 400px; position: absolute;
          left: 8px; top: 8px; background: #09f; display: none;}
    ```

2. `<script>` 작성

    ```jsx
    $("#pop").mouseleave(function () {
     $("#pop").hide();
    });

    $("a:first").mouseenter(function () {
     $("#pop").show();
    });
    ```


![mouseenter 전](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4e5170ad-6a35-4d58-b260-d7ee0aa82db1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T080909Z&X-Amz-Expires=86400&X-Amz-Signature=ccbea541e3479be863b3f7ad00f52717ca420e0bda38d3131a58015e62029be6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

mouseenter 전

![mouseenter 후](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a0e7cdc5-c3e9-4c1b-8ee0-f0edb86c1069/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T080858Z&X-Amz-Expires=86400&X-Amz-Signature=e08c4157dfe5262e74a4391b8a76c12a2c4055c898b5ce9d3773dcb9a8c64a30&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

mouseenter 후

---