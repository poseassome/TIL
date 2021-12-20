# Practice(3)
작성일시: 2021년 11월 5일 오후 6:55

오픈소스로 다양한 제이쿼리 플러그인들이 있다. 잘 찾아서 적용하는 것도 하나의 기술이다.

제이쿼리 홈페이지에서도 확인해볼 수 있다.

---

## Practice 08_외부 플러그인 적용하기

### bxSlider 적용하기

1. [https://bxslider.com/install/](https://bxslider.com/install/) 접속한다.
2. The Easy Way의 코드들 복사해서 붙여넣기 하면 따로 옵션을 수정할 수 없다.
3. The Other Ways 방법으로 적용시킨다.
    1. Download jquery.bxslider.zip 파일을 받아서 압축을 푼다.
    2. 효과를 적용시킬 html 파일이 있는 폴더에 css / js / images 폴더를 생성해서 해당하는 폴더로 파일을 옮긴다.

### 1) jqeury 적용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>gnb</title>
  <script src="js/jquery-3.6.0.min.js"></script>
	**<!-- 제이쿼리 파일 먼저 불러온다. -->**
	<script src="js/jquery.bxslider.js"></script>
  <script>
		$(document).ready(function () {
      $('.slider').bxSlider();
      $('.gallery').bxSlider();
    });
	</script>
</head>

<body>
	<div class="slider">
    <div>I am a slide.</div>
    <div>I am another slide.</div>
  </div>

  <p>&nbsp</p>
  <p>&nbsp</p>
  <p>&nbsp</p>
  <p>&nbsp</p>
  <p>&nbsp</p>

  <div class="main_image">
    <h2>주요소식</h2>
    <ul class="gallery">
      <li>
        <a href="#">
          <img src="images/img1.jpg" alt="">
        </a>
      </li>
      <li>
        <a href="#">
          <img src="images/img2.jpg" alt="">
        </a>
      </li>
      <li>
        <a href="#">
          <img src="images/img3.jpg" alt="">
        </a>
      </li>
    </ul>
  </div>
</body>

</html>
```

### 효과의 양식을 수정하려면,

해당 CSS 파일을 수정하면 효과를 받는 여러 개의 요소가 영향을 받기 때문에
수정할 css를 복사, 붙여넣기하고 효과를 변경할 요소에 따로 지정하고 내용을 수정한다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0d44007d-133f-4d8b-b692-cef2ab267ce3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081428Z&X-Amz-Expires=86400&X-Amz-Signature=8f19490e582449abad902e2d2c11b0a1c56cde30c41a0f7560e15062a69fb9a5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![상단은 원본의 효과를 받아서 테두리, 그림자 등이 있지만,
하단은 해당 효과를 지워버렸기에 없다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8c9bd3fb-237f-4f20-8fe1-aa6f239ee0f6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081443Z&X-Amz-Expires=86400&X-Amz-Signature=e46f0db3fd4fda1c46c1ab0f0076195510dc5f1205baad5c364a98240721ef1f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

상단은 원본의 효과를 받아서 테두리, 그림자 등이 있지만,
하단은 해당 효과를 지워버렸기에 없다.

### 효과의 옵션도 수정할 수 있다

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d4f5b42c-568b-4c9e-91d4-80b5e66b5b0e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081452Z&X-Amz-Expires=86400&X-Amz-Signature=35a6aa7c26669d648082c7cd8d6320f8dd31f57f05f1ab1a32b4bc476b004a1e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

사이트에서 다양한 옵션을
제공해주고 있으며 참고해서
작성한다.

```jsx
$(document).ready(function () {
  $('.slider').bxSlider();
  $('.gallery').bxSlider({ mode: "fade", auto: true });
});
```

⇒ 이미지가 흐려지면서 자동으로 변경된다.

---