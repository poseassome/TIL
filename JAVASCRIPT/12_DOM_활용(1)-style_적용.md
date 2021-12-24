# DOM 활용(1)-style적용(function name)
작성일시: 2021년 10월 13일 오후 5:20

## Excercise 01.

색상을 입력하고 버튼을 누르면 해당 색상으로 text의 색이 바뀐다.

1. `<script>`에서 기능의 형태를 작성한다.
2. `<body>`에서 `<button>`에 eventhandler를 준다. `onclick="changeColor()"`
3. 기능에 참여하는 태그가 어떤 것인지 파악하고 id를 부여한다.  `<p>`  `<input>`
4. 정의한 function 내부 동작을 작성한다.
    - 사용자로부터 입력받은 값을 사용하기 위해 변수로 선언한다.
    - 색이 바뀌어야 하는 text에 입력받은 값을 style.color로 사용하도록 한다.

```jsx
function changeColor() {

  /* 재사용을 위한 변수 지정 */
  var color = document.getElementById("sc").value;
  // 우린 값을 주는게 아니라 받아야 하니까

  /*  style 바꾸는 방법  */
  var txt = document.getElementById("changeText");
  /* red로 바꾸기 */
	// txt.style.PROPERTY = "VALUE"
  // txt.style.color = "red";

	  // css의 속성 모두 사용 가능하나 script에서는 특수문자로 명령어사용 못한다.
	  //  => 특수문자 지우고 대문자로 쓴다. (ex. background-color를 backgroundColor)

  /* red 대신에 입력받은 값 사용하기 */
  txt.style.color = color;
};
```

```html
</head>

<body>
  <!-- DOM 방식의 특징 : 종류 상관없다. 다만 id를 가져야 한다. -->
  <!-- 현재 필요한 태그는 2가지 <p id="changeText">, <input id="sc"> -->

  <p id="changeText">버튼을 클릭하면 이 문장의 글자색이 변합니다.</p>
  <p><input type="text" name="sc" id="sc"> 색상 입력</p>
  <p><button type="button" onclick="changeColor()">글자 색상 바꾸기</button></p>

</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2ec6c1ff-65bf-4f25-88cc-f9e361412ff5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075034Z&X-Amz-Expires=86400&X-Amz-Signature=a20baaa6ee9ec108927062acffdf86ce32da485dc6f2ae15efa71179e60f1495&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

## Excercise 02-1.(DOM)

버튼에 따라 각각 다른 색상으로 text를 변하게 한다.

1. `<script>`에서 기능의 형태를 작성한다.
2. `<body>`에서 `<button>`에 eventhandler를 준다. `onclick="redColor()"`
3. 기능에 참여하는 태그가 어떤 것인지 파악하고 id를 부여한다.  `<p>`
4. 정의한 function 내부 동작을 작성한다.
    - 색이 바뀌어야 하는 text를 메소드로 지정하여 변수로 선언한다.
    - `txt.style.color = "red";` 로 바뀌어야 하는 style를 지정한다.

```jsx
function redColor() {
  var txt = document.getElementById("changeText");
  txt.style.color = "red";    // style 뒤에는 속성 하나만 사용할 수 있음
}
function blueColor() {
  var txt = document.getElementById("changeText");
  txt.style.color = "blue";
}
function greenColor() {
  var txt = document.getElementById("changeText");
  txt.style.color = "green";
}
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

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8773a29b-b19c-4e99-8d12-0bc7244cb9ec/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075048Z&X-Amz-Expires=86400&X-Amz-Signature=392788aa0dfa48824e6a3b53758edb9e49e71685b7e2cf5a1981fcacf1d9f07f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3c60b705-88cc-47c9-a128-29d2d9924af2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075057Z&X-Amz-Expires=86400&X-Amz-Signature=275d97e980a3c07aa20fc30fb707d5bed650b671dcfbdcc973a09d4d279599cd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/63f06890-dc8c-49c6-989d-e0a954f74f47/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075105Z&X-Amz-Expires=86400&X-Amz-Signature=d26d9d268976c46c1a89961628f88e9fa56cec1a8f94e6366aecc40da2e7d0c4&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

## Excercise 02-2.(매개변수)

버튼에 따라 각각 다른 색상으로 text를 변하게 한다.

1. `<script>`에서 기능의 형태를 작성한다.
    - 하나의 함수를 작성하고 매개변수 `g_color`를 사용하여 각각 다른 색을 출력하게 한다.
2. `<body>`에서 `<button>`에 eventhandler를 준다. `onclick="redColor()"`
3. eventhandler의 함수에서 `(' ')`안에 사용할 변수를 작성한다.
4. 기능에 참여하는 태그가 어떤 것인지 파악하고 id를 부여한다.  `<p>`
5. 정의한 function 내부 동작을 작성한다.
    - 색이 바뀌어야 하는 text를 메소드로 지정하여 변수로 선언한다.
    - `txt.style.color = g_color;` 로 바뀌어야 하는 style를 지정한다.

        ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4b9474ed-7baf-40a8-af22-4aa691863dfe/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075115Z&X-Amz-Expires=86400&X-Amz-Signature=eaa7cb2ca6070d144157b17060c4da3b7965b83128c3946c8564c37eb39b9590&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


```jsx
function redColor(g_color) {
  var txt = document.getElementById("changeText");
  txt.style.color = g_color;
};
```

```html
</head>

<body>
  <p id="changeText">클릭한 버튼에 따라 다른 스타일이 적용됩니다.</p>
  <p><button type="button" onclick="redColor('red')">빨강</button></p>
  <p><button type="button" onclick="redColor('blue')">파랑</button></p>
  <p><button type="button" onclick="redColor('green')">초록</button></p>

</body>

</html>
```

---