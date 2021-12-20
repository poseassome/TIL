# Effects(3)-Sliding
작성일시: 2021년 11월 4일 오후 5:29

## 3. Sliding

1. **slideDown**
    - 미끄러지는 듯한 효과
    - slidDown( [ duration ] [ , complete ] )

        1) **duration**

        - 애니메이션이 진행되는 시간 (기본값:400)
        - String 타입, Number 타입
        - "slow', "fast", 1/1000s

         2) **complete**

        - function() 타입
        - 해당 대상이 효과를 완료했을 때 실행할 내용

2. **slideUp**
    - slideUp( [ duration ] [ , complete ] )
    - slideDown과 사용방법 동일

3. **slideToggle**
    - 지정된 요소의 slide 상태를 변경
    - slideToggle( [ duration ] [ , complete ] )

---

### 예제 3

클릭할 때 슬라이드 효과 표현

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
        // $("#pop").fadeOut();
        $("#pop").slideUp();
        $("#pop").slideUp(2000);
        $("#pop").slideUp("fast");
        $("#pop").slideUp("slow");
        $("#pop").slideUp("slow", function () {
          alert("slide를 완료하였습니다.");
        });
      });

      $("a:first").click(function () {
        // $("#pop").hide();
        // $("#pop").fadeIn();
        $("#pop").slideDown();
        $("#pop").slideDown(2000);
        $("#pop").slideDown("fast");
        $("#pop").slideDown("slow");
        $("#pop").slideDown("slow", function () {
          alert("slide를 완료하였습니다.");
        });
      });

      $("a:eq(1)").click(function () {
        // $("#pop").Toggle();
        // $("#pop").fadeToggle();
        $("#pop").slideToggle();
        $("#pop").slideToggle(2000);
        $("#pop").slideToggle("fast");
        $("#pop").slideToggle("slow");
        $("#pop").slideToggle("slow", function () {
          alert("slide를 완료하였습니다.");
        });
      });
    });
  </script>
</head>

<body>
  <a href="#">펼치기</a>
  <a href="#">바꾸기</a>
  <div id="pop">
    <a href="#">접기</a>
  </div>
</body>

</html>
```

![위아래로 펼쳐지고 접힌다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/023a4c96-5ac5-40aa-b02d-ababff27c9a9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T080947Z&X-Amz-Expires=86400&X-Amz-Signature=7ce916e188b02b70af5d43629e58ec92c4d9dae308a09e36ad4cc83f3dfa3bff&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

위아래로 펼쳐지고 접힌다.

---