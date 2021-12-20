# DOM Core(2)-속성접근
작성일시: 2021년 10월 21일 오후 4:22

## Excercise 01.

HTML 문서 내 태그들의 **속성에 접근**하기

> **HTML**
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>속성 접근</title>
</head>

<body>
  <p>
    <img src="images/img01.jpg" id="big_img" alt="원본 이미지" abc="TEST">
  </p>
  <p class="thumb_img">
    <img src="images/img01.jpg">
    <img src="images/img02.jpg" onclick="changeImage()">
    <img src="images/img03.jpg">
    <img src="images/img04.jpg">
  </p>
</body>

</html>
```

> **CSS**
>

```css
#big_img {
width: 640px; height: 426px;}

.thumb_img img {
width: 152px; height: 101px;
margin-right: 5px; cursor: pointer}
```

![출력 화면](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dadb6ace-8f7a-42c7-a089-94feb437a6f0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075415Z&X-Amz-Expires=86400&X-Amz-Signature=d353b5b82237874e685e015e4e7d278ac79213b2dc8ae1ffc55c26777a6a429d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

출력 화면

> **JAVASCRIPT**
>

```jsx
function changeImage() {
  // 필요할 때 마다 가져오는 것 보단
  // 한 번만 가져와서 필요할 때 사용하는게 장치한테 좋음

  /* 객체 생성 (내가 제어할 객체를 만듦) */
  var big_img = document.getElementById("big_img");

  /*   속성값 가져오기   */
  // HTML-DOM : **★기존 html 요소★**의 모든 속성 사용 가능
  alert(big_img.alt);         // <--big_img의 alt 속성 가지고 와줘.
  console.log(big_img.src);   // <--요즘 test 방법 (개발자 도구 console 탭에서 확인)
  console.log(big_img.id);
  console.log(big_img.alt);
  console.log(big_img.abc);   // <--원래 있는 속성이 아니기 때문에 출력되지 않음

  console.log("HTML-DOM : " + big_img.abc);

  // DOM-Core : 코드에 작성된 모든 속성 사용 가능
  big_img.getAttribute("alt");                 // <--big_img의 속성 가지고와, alt 속성
  console.log(big_img.getAttribute("alt"));
  console.log(big_img.getAttribute("abc"));    // <--해당 속성 가지고 올 수 있다.

  console.log("DOM Core : " + big_img.getAttribute("abc"));
}
```

![함수 실행 결과](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/524d4c79-e18e-44f4-b9a4-9857bd00ef83/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075427Z&X-Amz-Expires=86400&X-Amz-Signature=09102807f4c62ffb1a7f1fff746277f6233d7845d34f6b33d6c1d88a7abd9b61&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

함수 실행 결과

```jsx
⭐객체와 값 구분⭐

var **big_img** = document.getElementById("big_img");
var **score** = 10;

obj . property = value ;
obj . method ( param ) ;

**big_img**는 사물이라서 **obj 위치**로 오고
**score**은 값이라서 **value, param 위치**로 간다.
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f8514ad4-fc7a-461c-ac0c-3b0c72c0a49f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075438Z&X-Amz-Expires=86400&X-Amz-Signature=95435e96c661673c36d0299818ae3740c66161165469c6599043489ff58b3780&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

## Excercise 02.

HTML 문서 내 태그들의 **속성값 추가**하기

```jsx
function changeImage() {
  // 객체 생성 (내가 제어할 객체를 만듦)
  var big_img = document.getElementById("big_img");

  /*  속성값 변경하기
      : 지정한 속성이 없는 경우 해당 속성 추가  */

  **// HTML-DOM**
  big_img.alt = "큰 이미지 보기"      // <--이미지 클릭하면 alt 변경됨
  big_img.abc = "큰 이미지 보기"      // <--원래 속성이 아니어서 바뀌지않음

  /* 속성값 추가 */
  big_img.title = "큰 이미지로 보기"  // <--원래 속성이라서 추가 o
  big_img.def = "큰 이미지로 보기"    // <--원래 속성아니라서 추가 x

  **// DOM Core**
  big_img.setAttribute("alt", "큰 이미지로 보기");
  /* 값을 변경할 때는 **get -> set**
      set은 parameter가 2개 (어떤 속성을, 어떤 값으로) 바꾼다. */
  big_img.setAttribute("abc", "큰 이미지로 보기");

  /* 속성값 추가 */
  big_img.setAttribute("title", "큰 이미지로 보기");
  big_img.setAttribute("def", "큰 이미지로 보기")
}
```

![이미지 클릭 전](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5ff19d8c-c96e-44f6-82c2-8d9d486c50b9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075447Z&X-Amz-Expires=86400&X-Amz-Signature=30ffea7b7282ececf1f18e70895b0617ef12e63374a158321548eaed4fecac77&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

이미지 클릭 전

![이미지 클릭 후 title 값이 변경](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4ad5642b-7ea9-411b-870e-5ca2c2c2fc0f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T075454Z&X-Amz-Expires=86400&X-Amz-Signature=369c7c1dc0f8b26c7c3c619d62820cb65de91b51f3e07ed3ff8df35b6a8818a2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

이미지 클릭 후 title 값이 변경

---