# font, 배경 설정
작성일시: 2021년 8월 10일 오전 1:00

> **font 적용**
  구글 폰트 적용시,
  <link> 정보 찾아서 복사해서 붙여넣음
  font-family도
>

```css
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Gamja+Flower&display=swap" rel="stylesheet">
<style>
    * {
      box-sizing: border-box;
      font-family: 'Gamja Flower', cursive;
    }
</style>
```

---

> **배경 적용**
  하단 참고
>

```css
body {
      background-color: rgb(255, 251, 245);
      color: rgb(150, 72, 0);
      width: 1000px;
      margin: 0 auto;

      background-image: url("https://cdn.pixabay.com/photo/2017/10/22/21/02/food-2879265_960_720.jpg");
      background-size: cover;
      background-attachment: fixed;
      background-position-x: center;
      background-repeat: no-repeat;
    }
```

---