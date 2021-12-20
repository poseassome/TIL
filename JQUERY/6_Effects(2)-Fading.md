# Effects(2)-Fading
작성일시: 2021년 11월 4일 오후 5:14

## 2. Fading

1. **fadeIn**
    - 대상을 서서히 나타나게
    - `$("대상").fadeIn( [ duration ] [ , complete ] )`

        1) **duration**

        - 애니메이션이 진행되는 시간
        - String 타입, Number 타입
        - **"slow", "fast", 1/1000s**

        2) **complete**

        - **function() 타입**
        - 해당 대상이 효과를 완료했을 때 실행할 내용

2. **fadeOut**
    - 대상을 서서히 사라지게
    - fadeIn과 사용방법 동일

3. **fadeTo**
    - 지정된 opacity 값까지 fade
    - $("대상").fadeTo( duration, opacity [ , complete ] )
    - duration : fadeIn과 동일
    - opacity : Number 타입, 0~1 사이의 값만 사용
    - complete : fadeIn과 동일

4. **fadeToggle**
    - 지정된 대상의 opacity를 변경
    - fadeToggle( [ duration ] [ , easing ] [ , complete ] )

---

### 예제 2

클릭할 때 보이거나 사라지기

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
      $("a:last").click(function () {
        // $("#pop").hide();
        $("#pop").fadeOut();
        $("#pop").fadeOut(2000);
        $("#pop").fadeOut("fast");
        $("#pop").fadeOut("slow");
        $("#pop").fadeOut("slow", function () {
          alert("fadeOut을 완료하였습니다.")
        });
      });

      $("a:first").click(function () {
        // $("#pop").show();
        $("#pop").fadeIn();
        $("#pop").fadeIn(2000);
        $("#pop").fadeIn("fast");
        $("#pop").fadeIn("slow");
        $("#pop").fadeIn("slow", function () {
          alert("fadeIn을 완료하였습니다")
        });
      });

      $("a:eq(3)").click(function () {
        // $("#pop").Toggle();
        $("#pop").fadeToggle();
        $("#pop").fadeToggle(2000);
        $("#pop").fadeToggle("fast");
        $("#pop").fadeToggle("slow");
        $("#pop").fadeToggle("slow", function () {
          alert("fadeToggle을 완료하였습니다");
        });
      });
    });
  </script>
</head>

<body>
  <a href="#">보이기</a>
	<a href="#">50%</a>
	<a href="#">100%</a>
  <a href="#">바꾸기</a>
  <div id="pop">
    <a href="#">감추기</a>
  </div>
</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a1fb9570-ddc2-475c-b720-6331feab0af0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T080930Z&X-Amz-Expires=86400&X-Amz-Signature=dce77822e3361d6a38226ad06597470ec3ee0a2dccfd55fd58921a3da395852d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

**Opacity 50%, 100% 지정하기**

1. `**fadeTo()**`의 특징
    1. 투명도의 최대값이 바뀐다.
    2. fadeTo로 바뀐 값은 다시 fadeTo로 바꾼다. (그래서 100%가 필요함)
2. `<script>` 작성

    ```jsx
    $("a:eq(1)").click(function () {
      $("#pop").fadeTo("slow", 0.5,);
    });

    $("a:eq(2)").click(function () {
      $("#pop").fadeTo("slow", 1);
    });
    ```


---