# Practice(1)
작성일시: 2021년 11월 4일 오후 6:01

## Practice 01_scale

이미지 위에 마우스 올리면 이미지 커지게 하기

### 1) jqeury 적용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scale</title>
  <style type="text/css">
    .m1 {width: 200px; height: 200px; overflow: hidden; margin-bottom: 20px;}
    .m1 img {width: 200px; height: 200px; position: relative;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
      $(".m1 img").mouseenter(function () {
        $(this).animate({ width: 220, height: 220, left: -10, top: -10 });
      });
      $(".m1 img").mouseleave(function () {
        $(this).animate({ width: 200, height: 200, left: 0, top: 0 });
      });
    });
  </script>
</head>

<body>
  <div class="m1">
    <img src="images/img01.jpg">
  </div>
</body>

</html>
```

![마우스 올리기 전](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dac99b34-3e66-4913-bcb1-4ffa3eb810c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081025Z&X-Amz-Expires=86400&X-Amz-Signature=46f3ab33c303d95a8784963f1cc1927aedec9494881dc742dddb621b983e359d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

마우스 올리기 전

![마우스 올린 후 (이미지 확대)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/63f2163d-588d-4404-a0a9-26c8da26e549/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081033Z&X-Amz-Expires=86400&X-Amz-Signature=89d3532967cc375345e02b7cf977d1096b3b56276825e2088f718fb4af7484e9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

마우스 올린 후 (이미지 확대)

<aside>
💡 **CSS**와 차이점은 **scale되는 위치**가 다름
   => **크기 차이의 절반만큼 left, top 이동**시키면 중심처럼 보임

</aside>

### 2) CSS 적용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scale</title>
  <style type="text/css">
		.m2 {width: 200px; height: 200px; overflow: hidden; margin-bottom: 20px;}
    .m2 img {width: 200px; height: 200px; position: relative; transition: transform 0.5s;}
    .m2 img:hover {transform: scale(1.1, 1.1);}
  </style>
</head>

<body>
	<div class="m2">
    <img src="images/img01.jpg">
  </div>
</body>

</html>
```

---

## Practice 02_fade

어두운 이미지로 있다가 마우스 올리면 이미지 밝아지게 하기

## 1) jqeury 적용(1)

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scale</title>
  <style type="text/css">
		.fade {width: 200px; height: 200px; position: relative; margin-bottom: 20px;}
    .fade span {display: block; width: 200px; height: 200px; background: #000;
					      position: absolute; left: 0; top: 0; opacity: 0.6;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
		$(function () {
			// 1) <span>에 마우스 효과
       $(".fade span").mouseenter(function () {
	        $(this).animate({ opacity: 0 }, 200);
	      });
	      $(".fade span").mouseleave(function () {
	        $(this).animate({ opacity: 0.4 }, 200);
	      });

      // 2) hover로 표현
	      $(".fade span").hover(function () {
	        $(this).animate({ opacity: 0 }, 200)
	      }, function () {
	        $(this).animate({ opacity: 0.4 }, 200);
	      });
    });
  </script>
</head>

<body>
	*<!-- (위) <span> - <img> - <div> (아레) 순으로 존재하는 중 -->*
  *<!-- <span>의 투명도를 낮춰야 한다. -->*
  <div class="fade">
    <a href="#">
      <img src="images/img02.jpg" width="200" height="200">
    </a>
    <span></span>
  </div>
</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8ca8c861-0962-4acb-ac35-9f76d6d1cae2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081046Z&X-Amz-Expires=86400&X-Amz-Signature=c77138b47f24b56c88c2cf478a99aeea0b59aab00074df49053391c8c5462d9d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

`<span>`의 투명도를 낮춰서

이미지가 보이게 한다.

![마우스 올리기 전](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7b3dbbea-f430-4ebf-87b9-f5a797e08a32/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081052Z&X-Amz-Expires=86400&X-Amz-Signature=d1af1fa9df49808a16090f46edce06a73d7ef9341d52a587de901e32fd559e7f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

마우스 올리기 전

![마우스 올린 후](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/61ac7e23-0e0f-4f1a-8dd0-5d245b7ea4f4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081059Z&X-Amz-Expires=86400&X-Amz-Signature=307514310e2db1e990ecbc3274f3da39948d3db49b7616a5542cd84142fa502b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

마우스 올린 후

## 2) jqeury 적용(2)

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scale</title>
  <style type="text/css">
		.fade2 {width: 200px; height: 200px; background: #000; margin-bottom: 20px;}
    .fade2 img {opacity: 0.4;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
		$(function () {
			$(".fade2 img").hover(function () {
        $(this).animate({ opacity: 1 }, 200)
      }, function () {
        $(this).animate({ opacity: 0.4 }, 200);
      });
    });
  </script>
</head>

<body>
	*<!-- (위) <img> - <div> (아레) 순으로 존재하는 중 -->*
  *<!-- <img>에 투명도를 올려야 한다. -->*
  <div class="fade2">
    <a href="#">
      <img src="images/img02.jpg" width="200" height="200">
    </a>
  </div>
</body>

</html>
```

`<style>`에서 `<img>`의 **opacity**가 낮아서 이미지가 어둡게 보이므로
`<img>`의 **opacity**를 높인다.

## 3) CSS 적용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scale</title>
  <style type="text/css">
		.fade3 {width: 200px; height: 200px; position: relative;}
    .fade3 span {display: block; width: 200px; height: 200px; background: #000;
						     position: absolute; left: 0; top: 0; opacity: 0.6;
						     transition: opacity 0.5s;}
    .fade3 span:hover {opacity: 0;}
  </style>
</head>

<body>
	*<!-- (위) <span> - <img> - <div> (아레) 순으로 존재하는 중 -->
  <!-- <span> 투명도 조절 -->*
  <div class="fade3">
    <a href="#">
      <img src="images/img02.jpg" width="200" height="200">
    </a>
    <span></span>
  </div>
</body>

</html>
```

`<span>`이 `position:absolute`로 가장 위에 존재하고
배경색때문에 이미지가 어둡게 보이므로 :hover시 opacity를 0으로 준다.

---

## Practice 03_position

이미지에 마우스 올리면 낮게있던 불투명배경 올라오게 하기

## 1) jqeury 적용(1)

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scale</title>
  <style type="text/css">
		.m1 {width: 200px; height: 200px; background: url("images/img01.jpg");
		     background-size: 100% 100%; margin-bottom: 20px; position: relative;
		     overflow: hidden;}
    .m1 span {width: 200px; height: 200px; position: absolute; left: 0; top: 160px;
				      background: rgba(0, 0, 0, 0.7); line-height: 200px; font-size: 20px;
				      color: #fff; font-weight: bold; text-align: center;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
			// 1) <span>에 마우스 올리고 <span>이 효과나타내기 (까만 배경에 올려야함)
	      $(".m1 span").mouseenter(function () {
	        $(this).animate({ top: 0 });
	      });

      // 2) <div>에 올리면 <span>이 동작
	      $(".m1").mouseenter(function () {
	        $(".m1 span").animate({ top: 0 });
	      });
	      $(".m1").mouseleave(function () {
	        $(".m1 span").animate({ top: 160 });
	      });
    });
  </script>
</head>

<body>
		<div class="m1">
    <span>TEXT SECTION</span>
  </div>
</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/da3163be-d5a5-4d7f-958c-9494bdf230f4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081115Z&X-Amz-Expires=86400&X-Amz-Signature=ec474bce8ad367cdc92de4a8029fa920b82a4a8a3be42520e8130e345983caab&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/53a8210e-202a-439d-baf4-19160ae3cbd1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081124Z&X-Amz-Expires=86400&X-Amz-Signature=84261796bba30fc11fe33cf7c839e735e909924fca82865c713e52971964c9cd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

HTML 구조상
TEXT SECTION이 하단에
위치해 있음

<aside>
💡 `mouseover`, `mouseout`는 `<div>`에만 적용되서 `<span>`올라오면 가려져서 적용이 안됨.
`mouseenter`는 가려져도 적용받음.

</aside>

![마우스 올리기 전](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/73ab61b1-f77f-49d5-9283-eee8e8f5889c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081132Z&X-Amz-Expires=86400&X-Amz-Signature=ea49bdf95fbc53518eff46a32c4eaca87362b7646f75905af60afae30efb12ed&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

마우스 올리기 전

![마우스 올린 후
(하단의 까만배경이 올라옴)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e5bda836-9119-4a35-bc47-b6668236e958/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T081139Z&X-Amz-Expires=86400&X-Amz-Signature=7e7c908905bbc8a56c122ec92296a729eddc9b9ac4378fcefb1f279353300445&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

마우스 올린 후
(하단의 까만배경이 올라옴)

## 2) jqeury 적용(2)

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scale</title>
  <style type="text/css">
		.m2 {width: 200px; height: 200px; background: url("images/img02.jpg");
		     background-size: 100% 100%; margin-bottom: 20px; position: relative;}
    .m2 span {width: 200px; height: 40px; position: absolute; left: 0;
				      top: 160px; background: rgba(0, 0, 0, 0.6);}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
			$(".m2").mouseenter(function () {
        $(".m2 span").animate({ top: 0, height: 200 });
      });
      $(".m2").mouseleave(function () {
        $(".m2 span").animate({ top: 160, height: 40 });
      });
    });
  </script>
</head>

<body>
	<div class="m2">
    <span></span>
  </div>
</body>

</html>
```

여기서 `<span>`은 jquery(1)과는 다르게 `높이` 자체가 `40px` 이다.

마우스를 올렸을 때 height을 높이고 빠지면 원래 height로 돌아오게 한다.

## 3) CSS 적용(3)

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scale</title>
  <style type="text/css">
		.m3 {width: 200px; height: 200px; background: url("images/img03.jpg");
		     background-size: 100% 100%; margin-bottom: 20px; position: relative;
		     overflow: hidden;}
    .m3 span {width: 200px; height: 200px; position: absolute;
				      left: 0; top: 160px; background: rgba(0, 0, 0, 0.6);
				      transition: top 0.5s}
    .m3:hover span {top: 0;}
  </style>
</head>

<body>
	<div class="m3">
    <span></span>
  </div>
</body>

</html>
```

`<div>` :hover시 `<span>`의 위치를 `top : 0` 으로 이동시킨다.

---