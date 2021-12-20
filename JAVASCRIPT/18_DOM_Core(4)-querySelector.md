# DOM Core(4)-querySelector
작성일시: 2021년 10월 21일 오후 5:41

## Excercise 04.

querySelector를 사용하여 객체에 접근하고 버튼을  클릭하여 글자를 출력한다.

> **HTML**
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>객체 접근</title>
</head>

<body>
  <form name="form2" action="" method="">
    <p>* 버튼을 클릭하면 텍스트 필드에 글자가 나타납니다.</p>
    <p class=txt_box>
      <input type="text" name="txt_nm" id="txt_id" class="txt_cls">
      <button type="button" onclick="printText()">글자 출력</button>
    </p>
  </form>
</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fa6189b7-53a5-49e3-bae0-5e32b93802a7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075658Z&X-Amz-Expires=86400&X-Amz-Signature=5fd87fae25a9f4cb85042147290a4fa243883f59421819ba2aea148ca60c9e77&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

> **JAVASCRIPT**
>

```jsx
function printText() {
  // getElement
  var box = document.getElementById("txt_id");           //<--브라우저에서 id값만 적용됨 / 나머지 적용 안됨
  var box = document.getElementsByClassname("txt_cls");
  var box = document.getElementsByName("txt_nm");
  var box = document.getElementsByTagname("input");
  var box = document.getElementsByTagnameNS("localhost", "input");

  /*
      querySelector : CSS Selector 사용
      document.querySelector(" CSS Selctor");

      querySelectorAll이 있는데 아직 브라우저에서 완벽히 지원되지 않음
  */

  var box = document.querySelector("input");
  var box = document.querySelector(".txt_cls");
  var box = document.querySelector("#txt_id");

  box.value = "글자 출력하기";
};
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/39bc2df0-d97e-4560-a180-057b8781e7be/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075707Z&X-Amz-Expires=86400&X-Amz-Signature=060b0a8b2239f6fefda6d8466444bd39ac1dc360cd88449a803565b79713083f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---