# DOM 활용(3)-style적용(id)
작성일시: 2021년 10월 13일 오후 6:42

## Excercise 04-1.(<body>내부로 이동)

버튼에 따라 각각 다른 색상으로 text를 변하게 한다.

다만, 여기서는 `<button>`에 eventhandler를 주지않고 `<script>`내부에서 정의한다.

1. <script>을 <body>안으로 이동시킨다. (맨 마지막 요소로)
2. <button>에 eventhandler를 지우고, id값을 부여한다. `id="rBtn"`
3. 기능에 참여하는 태그가 어떤 것인지 파악하고 id를 부여한다.  `<p>`
4. <script> 내부 내용을 수정한다.
    - id를 가지는 <button>요소를 변수로 선언한다. `rBtn`
    - `obj.eventHandler= function( ){   };` 형태로 작성할 것
    - 빨강 버튼을 클릭하면 문자의 글자색을 바꾸기 → script로 번역하여 작성
    `rBtn.onclick=function(){   };`

        <aside>
        💡 지금 문장은 `rBtn`을 사용해서 **이미 누가, 언제할건지 나타내고 있어**서 `function`뒤에 `name`을 작성하지 않는다.

        </aside>

    - `function`의 `{   }`에 이전에 작성한 동작 내용을 삽입한다.

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

```html
<p id="changeText">클릭한 버튼에 따라 다른 스타일이 적용됩니다.</p>
<p><button type="button" id="rBtn">빨강</button></p>
<p><button type="button" id="bBtn">파랑</button></p>
<p><button type="button" id="gBtn">초록</button></p>
```

```jsx
/* 변수 선언 내용 지워도 실행된다. 너무 많이 보편화된 방법이라서 */
var rBtn = document.getElementById("rBtn");
// 앞 rBtn(변수)와 뒤 rBtn(id)은 다른 거다.
var bBtn = document.getElementById("bBtn");
var gBtn = document.getElementById("gBtn");

/*
    obj . eventHandler = funcion( ){   };
*/

// 빨강 버튼을 클릭하면 문자의 글자색을 바꾸기
rBtn.onclick = function () {
  var txt = document.getElementById("changeText");
  txt.className = "redText";
};

bBtn.onclick = function () {
  var txt = document.getElementById("changeText");
  txt.className = "blueText";
}

gBtn.onclick = function () {
  var txt = document.getElementById("changeText");
  txt.className = "greenText";
}
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3a5cfc55-be9b-488d-9340-4f829fc05ecd/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075136Z&X-Amz-Expires=86400&X-Amz-Signature=f2cd187dbae71e5d3501674997fbb740703282608a1803ca1393b614aae41a45&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObjects)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/39eb076c-ea66-4173-a2cf-908e4ba14996/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075147Z&X-Amz-Expires=86400&X-Amz-Signature=247053f827a9c7c1c303bfce8a5765f55d261f0bdb93612b274cf6ea733286bc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/598c215e-f179-4457-81a8-7818ccd2cfa9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075155Z&X-Amz-Expires=86400&X-Amz-Signature=c65e45f8f548bd7563883f4df5bce1470a9dd61963afeeac07ab2ff8311b3be7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

해당 형식은 보편화된 형식이라 요소의 변수 선언을 지워도 작동한다.

![Object 흐름](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/90df2652-ea1f-4b2e-a676-360c2c38a783/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075317Z&X-Amz-Expires=86400&X-Amz-Signature=2eb7d60b4309472a8c2046225facfd760af4ff35c022fcf3e3c65339f1fe0888&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

Object 흐름

---

## Excercise 04-2.(<head>내부로 이동)

버튼에 따라 각각 다른 색상으로 text를 변하게 한다.

위에서 작성한 `<script>`를 다시 `<head>`내부로 이동시킨다.

1. <script>을 <head>안으로 이동시킨다. (원래 위치, 내용 수정 X)
2. 실행시키면 동작하지 않는다.

    <aside>
    💡 **javascript**은 **html**과 **공통점**으로 한 줄, 한 줄 실행된다.

       -> 지금 첫문장 `varrBtn = document ~` 가 실행될 때 `**<body>**`에는 없는 상태다.
       -> 그래서 🔴**error** 발생 (*onclick할 게 null 없다*.)

    </aside>

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c8b2ccb4-1bb8-4551-8396-90f01c675d18/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075327Z&X-Amz-Expires=86400&X-Amz-Signature=b0f0679e4e5003faef2af44a8b02bcdeed6ddb3bd6936816fec2102d531359bd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


```css
.redText {
  color: red;
  border: 2px solid red
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
/* script는 필요한 요소가 다 나온 후 어느 위치든 상관없다. (필요한 위치에 삽입) */

/* 지금 이 파일에서는 변수선언 주석처리하면 안됨(에러남) */
var rBtn = document.getElementById("rBtn");
var bBtn = document.getElementById("bBtn");
var gBtn = document.getElementById("gBtn");

rBtn.onclick = function () {
  var txt = document.getElementById("changeText");
  txt.className = "redText";
};

bBtn.onclick = function () {
  var txt = document.getElementById("changeText");
  txt.className = "blueText";
}

gBtn.onclick = function () {
  var txt = document.getElementById("changeText");
  txt.className = "greenText";
}
```

```html
<p id="changeText">클릭한 버튼에 따라 다른 스타일이 적용됩니다.</p>
<p><button type="button" id="rBtn">빨강</button></p>
<p><button type="button" id="bBtn">파랑</button></p>
<p><button type="button" id="gBtn">초록</button></p>
```

---

## Excercise 04-2.(window.onload)

버튼에 따라 각각 다른 색상으로 text를 변하게 한다.

위에서 작성한 `<script>`를 다시 `<head>`내부로 이동시킨다.

문서가 다 작성됐을 때 기능이 실행되도록 조치한다.

1. <script>을 <head>안으로 이동시킨다. (원래 위치, 내용 수정 X)
2. 여기서 바로 실행시키면 동작하지 않는다.
3. 이전 작성한 <script> 내용을 `window.onload =function(){   }` 으로 감싼다.
    - html이 다 작성 됐을 때, function을 실행해라.

```css
.redText {
  color: red;
  border: 2px solid red
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
/* 문서가 준비가 된 다음에 실행해줘 */
window.onload = function () {
  var rBtn = document.getElementById("rBtn");
  var bBtn = document.getElementById("bBtn");
  var gBtn = document.getElementById("gBtn");

  rBtn.onclick = function () {
    var txt = document.getElementById("changeText");
    txt.className = "redText";
  };

  bBtn.onclick = function () {
    var txt = document.getElementById("changeText");
    txt.className = "blueText";
  }

  gBtn.onclick = function () {
    var txt = document.getElementById("changeText");
    txt.className = "greenText";
  }
};
```

```html
<p id="changeText">클릭한 버튼에 따라 다른 스타일이 적용됩니다.</p>
<p><button type="button" id="rBtn">빨강</button></p>
<p><button type="button" id="bBtn">파랑</button></p>
<p><button type="button" id="gBtn">초록</button></p>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3a5cfc55-be9b-488d-9340-4f829fc05ecd/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075136Z&X-Amz-Expires=86400&X-Amz-Signature=f2cd187dbae71e5d3501674997fbb740703282608a1803ca1393b614aae41a45&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/39eb076c-ea66-4173-a2cf-908e4ba14996/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075147Z&X-Amz-Expires=86400&X-Amz-Signature=247053f827a9c7c1c303bfce8a5765f55d261f0bdb93612b274cf6ea733286bc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/598c215e-f179-4457-81a8-7818ccd2cfa9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075155Z&X-Amz-Expires=86400&X-Amz-Signature=c65e45f8f548bd7563883f4df5bce1470a9dd61963afeeac07ab2ff8311b3be7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

### Script 적용방법 2가지

> 1) function에 이름 주고 필요할 때 가져다가 쓰게 하던가
2) id만 주고 사용하던가
>

---