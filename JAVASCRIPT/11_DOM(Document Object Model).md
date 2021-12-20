# DOM(Document Object Model)
작성일시: 2021년 10월 13일 오후 4:31

## DOM(Document Object Model) 방식

DOM은 원래 html 용어로, **자바스크립트가 태그들을 쉽게 선택**할 수 있도록 만든 방식이다.

- html 요소에 접근하는(태그들을 선택하는) 표준화된 방식
- 기존 name 속성과 태그별 접근 방식에서 벗어나 오브젝트의 종류에 상관없이 id 속성을 사용하여 요소에 접근하는 방식

---

`getElementById("요소")` 객체의 생성

---

## Practice.

버튼을 누르면 text창에 글자가 출력된다.

name으로 지정하지말고 메소드를 사용한다.
`getElementById("선택할 요소의 ID값")`

재사용할 일이 많으면, 변수로 선언하여 사용한다.

```jsx
function printText() {
  // object.method( )
  // object.property = value

  document.getElementById("txt1").value = "글자 출력하기";
  // <body>에 가면 "txt1"이란 ID를 가지고 있는 태그를 가지고와라

  // 실무에서는 이렇게 사용
  let tf = document.getElementById("txt1");
  // tf는 <input>을 가리킨다.
  tf.value = "글자 출력하기";       // 변수의 재사용성
}
```

```html
</head>

<body>
  <form name="form1" action="" method="">
    <p>* 버튼을 클릭하면 텍스트 필드에 글자가 나타납니다.</p>
    <p>
      <input type="text" name="txt1" id="txt1">
      <button type="button" onclick="printText()">글자 출력</button>
    </p>
  </form>
</body>

</html>

```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/34d88395-0682-4f11-bfd9-b43961bfedb6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075016Z&X-Amz-Expires=86400&X-Amz-Signature=0295ef666afa972ba730857f5d8d4dcd78e90102651d4447df11c33f8ead5173&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---