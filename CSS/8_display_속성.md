# display 속성
작성일시: 2021년 8월 10일 오전 12:52

> **display**
  **none**: 태그를 화면에서 보이지 않게 함
>

```html
<html lang="ko">

<head>
  <meta charset="utf-8">
  <style>
    #box {
      /* 화면에서 안 보임 */
      display: none;
    }
  </style>
</head>

<body>
  <span onclick="showBox()">Show</span>
  <div id="box">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Non sit magnam consequuntur, animi quasi vero tempora sed
    illo porro dolorum sequi id, iusto odio assumenda vel ullam! Perspiciatis, facere a.
  </div>
  <script>
    function showBox() {
      //vanilla javascript
      document.querySelector("#box").style.display = "block";
      //jquery
      //$("#box").show();
    }
  </script>
</body>

</html>
```

> **display**
  **inline**: 왼쪽에서 오른쪽으로 표시
  **inline-block: inline:** 표시방식이지만 크기를 지정할 수 있다.
>

```css
.box {
      width: 100px;
      height: 200px;
      border: 1px solid black;
    }

 .box:nth-child(1) {
      /* inline 형식은 너비/높이를 지정할 수 없음 */
      display: inline;
    }

 .box:nth-child(2) {
      /* inline과 같이 옆으로 붙음 */
      /* block과 같이 너비/높이를 지정할 수 있다. */
      display: inline-block;
    }
```

![display%20%E1%84%89%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A5%E1%86%BC%206355908f2b7049069eccf178caa68935/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cb9a80a1-cd1b-46d2-97ad-7767269bdd5d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T070948Z&X-Amz-Expires=86400&X-Amz-Signature=7e15ff02838be570e329069800143799d1aca312b77ca8b988e2751d0cdb0a02&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---