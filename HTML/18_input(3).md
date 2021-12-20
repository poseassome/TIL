# <input>-3
작성일시: 2021년 8월 26일 오후 5:06

> input element의 새로운 attribute

~xhtml : <tag property ="value">
HTML5 : <element attribute ="value">

1. placeholder
2. autofocus
3. required
>

---

> 1. placeholder
>

```html
1. placeholder
   <input type="text" placeholder="아이디">
```

```html
<p>placeholder
  <input type="text" placeholder="아이디">
</p>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3a3be49e-5788-4ec7-b980-45fe5f7d7c3e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072234Z&X-Amz-Expires=86400&X-Amz-Signature=0ee775dfcd3f2e475d03a2c048aee043905b84f495d81f3bff39bfb92ea8a0a8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

> 2. autofocus
>

```html
2. autofocus
   <input type="text" autofocus>

   <a>, <form>에만 생기지만 (tabindex)를 이용해서 이 외에도 적용시킬 수 있음.
   화면 켜서 시작하면 커서가 생기게 해

   한 페이지에 한 번만 사용
```

```html
<p>autofocus
  <input type="text" autofocus>
</p>
```

![페이지를 열면 지정 위치에 커서가 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5db998ab-6613-4cdf-b6ba-8fa6d8115f2a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072244Z&X-Amz-Expires=86400&X-Amz-Signature=034e9bc7eb1b62c660697b21653fd344729a31bcd9f1a26dd1b8bcb42dee64cd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

페이지를 열면 지정 위치에 커서가 있다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5172afd8-5bc9-440d-8660-5888b92c7d5e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072328Z&X-Amz-Expires=86400&X-Amz-Signature=cebada66a47877a62057676d25e38a0e3e311f364e26b6a05006bb88d43c1699&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

> 3. required
>

```html
3. required
   -필수 입력 항목 지정
   -title 속성을 이용하여 추가 메세지 지정 가능
   -mobile 일부 구현

   <input type="text" required="required" title="ex) 010-0000-0000">

   <body>안에 있는 모든 요소에서 사용 할 수 있음
```

```html
<p>required
  <input type="text" required="required" title="ex) 010-0000-0000">
</p>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4542587d-5d02-4cb6-9570-2d409100e3c2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072252Z&X-Amz-Expires=86400&X-Amz-Signature=cbb1613c139d52699c201c1dd0a815d20840d63de4d4765da8d038e44776fdc6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

> 여기에 웹 접근성이나 표준성을 향상시키기위한 방법이 더 있음

---------------------접근성 향상 마크업 시---------------------
5. <input> 요소들은 <label>과 함께 사용
6. <input> 요소들은 <fieldset>이나 <div>안에 작성
>

```html
* 관련 태그(속성)
      1. fieldset : 양식의 소그룹
         -일정한 기준, 목적, 의미가 있음
         -단순히 디자인때문이면 <div>로 묶어줌

      2. legend : fieldset의 제목

      3. label : 필드와 텍스트의 그룹
         -<label> 하나는 하나의 <input>에 붙인다.

         -사용방법 2가지
          1) <label>안에 텍스트, <input>을 같이 쓴다.
              입력창 옆 텍스트에 커서 표시가 안되고, 텍스트 누르면 입력창에 커서 표시됨.
              screen reader에서도 아이디 쓰는 곳이라고 알려줌

          2) <label>안에 텍스트만 담는다.
              <label for="id값">
               (label>라벨지에 이름써서 (for)위치에 붙이기
               한 곳에 한 번만 사용한다.

      4. for(속성) : 연결하고자 하는 필드의 id 값 작성
```

```html
<form name="" action="" method="">
    <fieldset>
      <legend>로그인</legend>
      <p>
        <label>
          아이디
          <input type="text" name="uid" id="uid">
        </label>
      </p>
      <p>
        <label for="pwd">
          비밀번호
        </label>
        <input type="password" name="pwd" id="pwd">
      </p>
    </fieldset>

    <fieldset>
      <legend>연락처 정보</legend>
      <p>전화번호
        <input type="text" name="mobile" id="mobile">
      </p>
      <p>이메일
        <input type="text" name="email" id="email">
      </p>
    </fieldset>
  </form>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1463fc96-e5c3-4cc9-ab31-10af12f59121/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072302Z&X-Amz-Expires=86400&X-Amz-Signature=3a55a24f8a94f745cfb30e0c6d19d45a668bf69feb008a3ab7202424bdf9846a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---