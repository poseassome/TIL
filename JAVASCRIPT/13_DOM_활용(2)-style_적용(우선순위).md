# DOM 활용(2)-style적용(우선순위)
작성일시: 2021년 10월 13일 오후 5:20

## Excercise 03-1.(className)

버튼에 따라 각각 다른 색상으로 text를 변하게 한다.

1. <script>에서 기능의 형태를 작성한다.
2. <body>에서 <button>에 eventhandler를 준다. `onclick="redColor()"`
3. 기능에 참여하는 태그가 어떤 것인지 파악하고 id를 부여한다.  `<p>`
4. 정의한 function 내부 동작을 작성한다.
    - 색이 바뀌어야 하는 text를 메소드로 지정하여 변수로 선언한다.
    - `txt.className = "redText";` 로 `<style> </style>`에 작성된 해당 classname과 연결시킨다.

    <aside>
    💡 <script>안에서 직접 style 적용시, 속성 하나에 대해서만 가능했지만,
    classname을 사용하면 한 번에 여러가지 속성 적용이 가능하다.

    </aside>


```css
.redText {
  color: red;
  border: 2px solid red;
}

.blueText {
  color: blue;
  border: 2px solid blue;
}

.greenText {
  color: green;
  border: 2px solid green;
}
```

```jsx
/* script로 css 적용하는 방법 두 번째 */
// DOM으로 객체 지정하여 해당 객체의 className 실행
// 작성한 여러개의 style을 해당 객체에 적용시킬 수 있다.

function redColor() {
  var txt = document.getElementById("changeText");
  txt.className = "redText";
};
function blueColor() {
  var txt = document.getElementById("changeText");
  txt.className = "blueText";
};
function greenColor() {
  var txt = document.getElementById("changeText");
  txt.className = "greenText";
};
```

```html
</head>

<body>
  <p id="changeText">클릭한 버튼에 따라 다른 스타일이 적용됩니다.</p>
  <p><button type="button" onclick="redColor()">빨강</button></p>
  <p><button type="button" onclick="blueColor()">파랑</button></p>
  <p><button type="button" onclick="greenColor()">초록</button></p>

</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3a5cfc55-be9b-488d-9340-4f829fc05ecd/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075136Z&X-Amz-Expires=86400&X-Amz-Signature=f2cd187dbae71e5d3501674997fbb740703282608a1803ca1393b614aae41a45&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/39eb076c-ea66-4173-a2cf-908e4ba14996/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075147Z&X-Amz-Expires=86400&X-Amz-Signature=247053f827a9c7c1c303bfce8a5765f55d261f0bdb93612b274cf6ea733286bc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/598c215e-f179-4457-81a8-7818ccd2cfa9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075155Z&X-Amz-Expires=86400&X-Amz-Signature=c65e45f8f548bd7563883f4df5bce1470a9dd61963afeeac07ab2ff8311b3be7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

## Excercise 03-2.(우선순위)

버튼에 따라 각각 다른 색상으로 text를 변하게 한다.

1. <script>에서 기능의 형태를 작성한다.
2. <body>에서 <button>에 eventhandler를 준다. `onclick="redColor()"`
3. 기능에 참여하는 태그가 어떤 것인지 파악하고 id를 부여한다.  `<p>`
4. 정의한 function 내부 동작을 작성한다.
    - 색이 바뀌어야 하는 text를 메소드로 지정하여 변수로 선언한다.
    - `txt.className = "redText";` 로 `<style> </style>`에 작성된 해당 classname과 연결시킨다.

```css
.redText {
  color: red;
  border: 2px solid red;
}
```

```jsx
/* <style>에는 .redText에 대한 것만 있을 때 */
function redColor() {
  var txt = document.getElementById("changeText");
  txt.className = "redText";
};
function blueColor() {
  var txt = document.getElementById("changeText");
  txt.style.color = "blue";
};
function greenColor() {
  var txt = document.getElementById("changeText");
  txt.style.color = "green";
};

// 스크립트가 실행안될 때 안되는 원인은 꼭 스크립트 때문만이 아니다.
// 동작될 개체가 필요하고, 어떻게 동작할지 디자인이 필요하고, 어떻게 움직이게 할 건지 움직임이 필요하다.

// html, css, javascript가 얼마나 잘 맞물려있는가.
```

```html
</head>

<body>
  <p id="changeText">클릭한 버튼에 따라 다른 스타일이 적용됩니다.</p>
  <p><button type="button" onclick="redColor()">빨강</button></p>
  <p><button type="button" onclick="blueColor()">파랑</button></p>
  <p><button type="button" onclick="greenColor()">초록</button></p>

</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/781fa532-332d-416d-baa1-b8a5138815ac/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075207Z&X-Amz-Expires=86400&X-Amz-Signature=784a346507d3b8a39baeed8c1b8a63fc711955c67c061c99f0a12360ffa49db9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8f655af5-5fb5-4a27-bc0f-f4ec41eb39ac/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075217Z&X-Amz-Expires=86400&X-Amz-Signature=703663e713a92c1f115c05ea5c41284b202234c9baca0de9727cc4942f2e81f7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

위 코드에서는 버튼[ blue ], [ green ]을 눌러버리면 [ red ]는 적용되지않음(border는 적용됨)
→ css에서 **⭐우선순위⭐**가 있다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/21617d2d-eb85-4181-baff-20766d7920d5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075228Z&X-Amz-Expires=86400&X-Amz-Signature=863275b33900d5e733b49740186cf85a63cb6a6eb2c23cddb52658d2cdf3a5c3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

**⭐우선순위⭐**

우선순위를 점수화하여 점수가 높은 것이 절대적으로 먼저 적용됨.

> **** 우선순위 ****
   !important                   ★★★
   style(inline)                  [1000]
   #b{}                              [100]
   .a{}                                [10]
   p{}                                 [1]
>
>
> `<p class="a" id="b" style="color:red"></p>`
> <우선순위>     **!important  >  style(inline)  >  id  >  a  >  p**
>

---