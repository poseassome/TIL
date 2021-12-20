# DOM Core(3)-속성변경
작성일시: 2021년 10월 21일 오후 5:07

## Excercise 03.

하단의 작은 이미지를 클릭하면 상단의 큰 이미지로 보여지게 하기

### 방법 1

> **HTML**
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>속성 접근</title>
</head>

<body>
  <p>
    <img src="images/img01.jpg" id="big_img" alt="원본 이미지" abc="TEST" title="이미지 크게보기">
  </p>
  <p class="thumb_img">
    <img src="images/img01.jpg" onclick="changeImage1()">
    <img src="images/img02.jpg" onclick="changeImage2()">
    <img src="images/img03.jpg" onclick="changeImage3()">
    <img src="images/img04.jpg" onclick="changeImage4()">
  </p>
</body>

</html>
```

> **CSS**
>

```css
#big_img {
width: 640px; height: 426px;}

.thumb_img img {
width: 152px; height: 101px;
margin-right: 5px; cursor: pointer}
```

![출력 화면](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dadb6ace-8f7a-42c7-a089-94feb437a6f0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075415Z&X-Amz-Expires=86400&X-Amz-Signature=d353b5b82237874e685e015e4e7d278ac79213b2dc8ae1ffc55c26777a6a429d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

출력 화면

> **JAVASCRIPT**
>

```jsx
function changeImage1() {
  var big_img = document.getElementById("big_img");
  big_img.src = "images/img01.jpg";
};
function changeImage2() {
  var big_img = document.getElementById("big_img");
  big_img.src = "images/img02.jpg";
};
function changeImage3() {
  var big_img = document.getElementById("big_img");
  big_img.src = "images/img03.jpg";
};
function changeImage4() {
  var big_img = document.getElementById("big_img");
  big_img.src = "images/img04.jpg";
};
```

---

### 방법 2

> **HTML**
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>속성 접근</title>
</head>

<body>
  <p>
    <img src="images/img01.jpg" id="big_img" alt="원본 이미지" abc="TEST" title="이미지 크게보기">
  </p>
  <p class="thumb_img">
    <img src="images/img01.jpg" onclick="changeImage('images/img01.jpg')">
    <img src="images/img02.jpg" onclick="changeImage('images/img02.jpg')">
    <img src="images/img03.jpg" onclick="changeImage('images/img03.jpg')">
    <img src="images/img04.jpg" onclick="changeImage('images/img04.jpg')">
  </p>

  <!-- 또는 -->

  <p class="thumb_img">
    <img src="images/img01.jpg" onMouseOver="changeImage('images/img01.jpg')">
    <img src="images/img02.jpg" onMouseOver="changeImage('images/img02.jpg')">
    <img src="images/img03.jpg" onMouseOver="changeImage('images/img03.jpg')">
    <img src="images/img04.jpg" onMouseOver="changeImage('images/img04.jpg')">
  </p>
</body>

</html>
```

> **JAVASCRIPT**
>

```jsx
function changeImage(img_url) {
  // 객체 생성
  var big_img = document.getElementById("big_img");

  big_img.src = img_url;
   // 또는
  big_img.setAttribute("src", img_url);
}
```

---

### ✔ this

방법 2의 html을 보면

`<img src="images/img01.jpg" onclick="changeImage('images/img01.jpg')">`

동일한 값이 사용된다.

이 때, this를 사용할 수 있다.

> **HTML**
>

```html
!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>속성 접근</title>
</head>

<body>
  <p>
    <img src="images/img01.jpg" id="big_img" alt="원본 이미지" abc="TEST" title="이미지 크게보기">
  </p>
  <p class="thumb_img">
    <!-- this : 프로그래밍 언어에서 나 자신 -->
    <img src="images/img01.jpg" onclick="changeImage(this.src)">
    <img src="images/img02.jpg" onclick="changeImage(this.src)">
    <img src="images/img03.jpg" onclick="changeImage(this.src)">
    <img src="images/img04.jpg" onclick="changeImage(this.src)">
</p>
</body>

</html>
```

<aside>
💡 **직접 작성**
  - 장점 : *필요할 때 필요한 이미지만 불러올 수 있어서 속도가 빠르다. -->*

  - 단점 : *경로를 일일이 수정해야 한다.*

**this 작성**

  - 장점 : *이미지 값을 바꿔도 this.src 수정할 필요 없음, 사용하는 이미지 수가 적음*

  - 단점 : 사용자들이 누르지 않을 수 있는데도 큰 이미지 가져와야함

</aside>

---