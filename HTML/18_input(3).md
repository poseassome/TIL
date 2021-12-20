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

![Untitled](input%20-3%203ae23e73beb24a079791b1dbdaadaaf2/Untitled.png)

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

![페이지를 열면 지정 위치에 커서가 있다.](input%20-3%203ae23e73beb24a079791b1dbdaadaaf2/Untitled%201.png)

페이지를 열면 지정 위치에 커서가 있다.

![Untitled](input%20-3%203ae23e73beb24a079791b1dbdaadaaf2/Untitled%202.png)

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

![Untitled](input%20-3%203ae23e73beb24a079791b1dbdaadaaf2/Untitled%203.png)

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

![Untitled](input%20-3%203ae23e73beb24a079791b1dbdaadaaf2/Untitled%204.png)

---