# Effects(4)-Animate
작성일시: 2021년 11월 4일 오후 5:39

## 4. animate

1. **animate**
    - CSS로 제어 가능한 속성을 변화시키는 메소드
    - `animate( properties [ , duration ] [ , easing ] [ , complete ] )`
        - **properties** : CSS로 제어 가능한 속성과 값, 여러 개 사용 가능
        - **duartion** : **Number** 또는 **String** 타입
                        애니메이션 진행시간 (기본값:400)
        - **easing** : **String** 타입
                     가속효과 (기본값:swing)
        - **complete** : `Function()` 타입
                         효과가 완료 되었을 때 실행할 내용


2. 이 외 메소드들은 animate을 지원해주는 메소드들

---

### 예제 4

클릭할 때 애니메이션 효과 적용

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
    #pop {width: 200px; height: 120px; position: absolute;
		      left: 50px; top: 50px; background: #09f;}
    .big_box {width: 800px; height: 300px;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
			$("a:first").click(function () {
				// *1) CSS로 적용*
         $("#pop").width(800).height(800);
         $("#pop").css({ width: "800px", height: "300px" });      // <-- css()는 인라인방식으로 적용됨

				// 2*) animate로 적용*
				 $("#pop").animate({ width: "800px", height: "300px" });
         $("#pop").animate({ width: "800px", height: "300px", left: 200, top: 200 });

				// *이전에 학습한 효과들도 표현 가능*
         $("#pop").animate({ height: 0 });         // <-- slide
         $("#pop").animate({ opacity: 0 });        // <-- fade
         $("#pop").animate({ opacity: 0 }, 0);     // <-- hide
      });

      $("a:last").click(function () {
				// *1) CSS로 적용*
         $("#pop").css({ width: 200, height: 150 });      // <-- 단위 px이면 " px" 생략가능

				// 2*) animate로 적용*
				 $("#pop").animate({ width: "200px", height: "150px" });
         $("#pop").animate({ width: "200px", height: "120px", left: 50, top: 50 }, 2000);
      });
    });
  </script>
</head>

<body>
	<a href="#">크게</a>
  <a href="#">작게</a>
  <div id="pop"></div>
</body>

</html>
```

![크게 누르기 전](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b411215c-fd58-4e6e-af8c-9e06fbfd4cc5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081006Z&X-Amz-Expires=86400&X-Amz-Signature=b264b114e9072a4a6db77a5455a6e5c4f8702d61a595b8441b64999bef39519c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

크게 누르기 전

![크게 누른 후](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8e555e2e-fcf1-4e61-8b95-485750964b00/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081013Z&X-Amz-Expires=86400&X-Amz-Signature=bed80d5688f4887de9a4ccfb838db20ea57c85e2cf4bc458217e22deb006ad15&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

크게 누른 후

animate 효과를 지원해서 표현할 수도 있음

1. 지연 시간을 주려면 `.delay()` 사용

    ```jsx
    $("a:first").click(function () {
      $("#pop").delay(2000).animate({ width: "800px", height: "300px", left: 200, top: 200 }, 2000);
    });
    ```

2. 두 가지 이상 animate 효과를 맞물려서 같이 적용 시키려면 `.stop()` 사용
ex) 1번 동작을 하다가 2번 동작 실행 시키면 중간에 2번으로 넘어가기

    ```jsx
    $("a:first").click(function () {
      $("#pop").stop().animate({ width: "800px", height: "300px", left: 200, top: 200 }, 2000);
    });

    $("a:last").click(function () {
      $("#pop").stop().animate({ width: "200px", height: "120px", left: 50, top: 50 }, 2000);
    });
    ```

    ![크게 누르고 작게를 누르면 바로 작게 동작으로 연결](Effects(4)-Animate%20676511248c1a44dbb3baacce1536cb4f/Untitled%202.png)

    크게 누르고 작게를 누르면 바로 작게 동작으로 연결


---