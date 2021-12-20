# <input>-2
작성일시: 2021년 8월 26일 오후 4:48

> (HTML5에서) 추가된 type 속성값

1. 날짜 관련 type
     -datetime
     -week
     -month
     -date
     -time
 2. email
 3. url
 4. search
 5. number
 6. range
 7. tel
 8. file
>

---

> **1. 날짜 관련 type**
>

```html
1. 날짜 관련 type
   -datetime
    <input type="datetime">
    <input type="datetime-local">

   -week
    <input type="week">

   -month
    <input type="month">

   -date
    <input type="date">

   -time
    input type="time">
```

```html
<p>datetime
  <input type="datetime">
</p>

<p>datetime-local
  <input type="datetime-local">
</p>

<p>week
  <input type="week">
</p>

<p>month
  <input type="month">
</p>

<p>date
  <input type="date">
</p>
```

![세부 옵션들은 해당 브라우저가 지원해준다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9502b173-07b2-4e3e-9f33-46b15efa99b2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072112Z&X-Amz-Expires=86400&X-Amz-Signature=b3bedb2936558d7fe42f400233b5bac7973dc1fa21884b1a320cd9e78993d728&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

세부 옵션들은 해당 브라우저가 지원해준다.

---

> **2. email**
>

```html
2. email
   <input type="email">
```

```html
<p>email
  <input type="email">
</p>
```

![e-mail 형식을 인지하기 때문에 알림창이 뜬다](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/35dae1cf-ae65-4694-a2a1-5e1619b35b6b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072120Z&X-Amz-Expires=86400&X-Amz-Signature=a6ba09e47f7433bdef3fef903759cac39cac9e859253b1ef5a94767c2a94abc4&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

e-mail 형식을 인지하기 때문에 알림창이 뜬다

---

> **3. url**
>

```html
3. url
   <input type="url">
   -작성할 때는 http:// 부터 쓴다.
```

```html
<p>url
  <input type="url">
</p>
```

![작성은 http:// ~](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/52020ee8-9209-465f-a951-aa06a0b0b649/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072130Z&X-Amz-Expires=86400&X-Amz-Signature=1c169e9c51449b4a2dddfa313c536601c3d70fcfdb14c4f04c82d33610dafc35&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

작성은 http:// ~

---

> **4. search**
>

```html
4. search
   <input type="search">

   -(tmi) explore 하위 버전에서는 모든 text 입력창에 'x'가 생김

      ex) Daum 페이지 소스
          input::-ms-clear{display:none}

          vendor prefix : 브라우저별 접두어  //-ms-
```

```html
<p>search
  <input type="search">
</p>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a412f489-1b60-43a4-b111-dcee5085ac34/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072139Z&X-Amz-Expires=86400&X-Amz-Signature=0e3dc3306e220057397b296fea7750e2607b6573bcf90431260a49a2c02a6bd3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

> **5. number**
>

```html
5. number
   <input type="number" min="1" max="100">
```

```html
<p>number
  <input type="number" min="1" max="100">
</p>
```

![min, max 범위의 숫자만 유효하다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b3b2db43-3982-4491-8d52-5ab65fd10342/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072148Z&X-Amz-Expires=86400&X-Amz-Signature=9f9fc314fe8823055dc02110748081b180b5e74b06f0fae5eaeffc1e67cfcc4d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

min, max 범위의 숫자만 유효하다.

---

> **6. range**
>

```html
6. range
  <input type="range" min="0" max="100" step="10" value="0">
```

```html
<p>range
  <input type="range" min="0" max="100" step="10" value="0">
</p>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/232da60f-3122-4678-926d-213750285a4a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072159Z&X-Amz-Expires=86400&X-Amz-Signature=8323a587b89a824c2d93212ef237ed9d899325619c23bfb334312caaa943e694&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

> **7. tel**
>

```html
7. tel
   <input type="tel">
```

```html
<p>tel
  <input type="tel">
</p>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4c5f1e43-616d-4cc1-af46-b76a8acaafe6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072209Z&X-Amz-Expires=86400&X-Amz-Signature=df597f987738c30e7e32da1004303cd7cb8f359794f9cdc40049c2aaae601479&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

> **8. file**
>

```html
8. file
   <input type="file" accept="image/*" multiple>

   -옛날에는 이미지 파일만 선택 가능하게 만들려면,

    JS이용해서 파일명을 거꾸로 읽어 '.'만날 때 까지,
    그 글자가 jpg,..랑 똑같아? 판단시킴

   -지금은 accept를 이용해서 특정 파일만 볼 수 있게 됨.

   -multiple을 추가해서 여러 개의 파일 선택 가능하다.
```

```html
<p>file
  <input type="file" accept="image/*" multiple>
</p>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/80714d21-57d6-407b-9783-f322995ae39f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072218Z&X-Amz-Expires=86400&X-Amz-Signature=99a3a3d90c28876ba0dd41f46a6dcb15bdcf14ef0ffbbc1776060a9d96f6b157&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---