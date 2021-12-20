# mobile web 확인하기
작성일시: 2021년 8월 26일 오후 1:22

1. 웹 페이지 준비 (webform.html)
2. 폼 요소 작성 후 텍스트 필드 추가
3. FTP로 계정에 접속
4. 해당 .html 파일 옮기고 주소로 접속 (웹, 모바일)

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>웹 폼(web form)</title>
</head>

<body>
  <h2>웹 폼(web form)</h2>
  <form name="" action="insert.php" method="post">
     <p>
       text
       <input type="text" name="" id="">
     </p>
  </form>
</body>

<html>
```

---

1. 모바일은 화면이 작기 때문에 화면 크기에 맞는 콘텐츠를 만들어야 하고,
2. 모바일 장치에 필요한 코드가 필요하다.

화면크기가 작으니까 모바일 크기에 적합한 디자인 설계를 해라.

장치 특성에 맞는 코드가 필요할 수 있다.

이 외에는 일반 홈페이지 만드는것과 똑같다.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

> **- Viewport : 반응형 웹이나, 모바일 웹에서 꼭 필요함
 - Width=device-width : Body의 기본크기를 장치 크기에 맞춰라.
 - Initial-scale=1.0 : 처음에 보이는 크기 (100%)**

 - User-scalable=no : 사용자가 조절 못하게 함
 - Max-, min- : 최대, 최소 크기
    >>이 두개는 더 이상 지원하지 않음
>

![왼쪽-태그 삭제 전 / 오른쪽-태그 삭제 후](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/51162fd6-5170-45de-bf31-93d3d9ce2daa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072033Z&X-Amz-Expires=86400&X-Amz-Signature=3d677b43f80e1f5f2269a6a5cbbe6b705b65b80e1b59609f717ddc5696ecfecf&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

왼쪽-태그 삭제 전 / 오른쪽-태그 삭제 후

---

사용한 태그에 따라 모바일 화면에서도 특성이 나타난다.

![<input type="text"> 적용시 키보드가 나타난다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bab18382-610d-4ef0-98fb-b25b5046081f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072044Z&X-Amz-Expires=86400&X-Amz-Signature=872e769d810e34e61872d7c1c2ca1058cd73cff77a69aee35a26487a47acea21&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

<input type="text"> 적용시 키보드가 나타난다.

---

```html
<p>
  운영자에게 <a href="mailto:메일주소">메일</a>을
</p>

<p>
  운영자에게 <a href="tel:전화번호">전화</a>를
</p>

<p>
  운영자에게 <a href="mms:전화번호">메세지</a>를
</p>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/10e04c53-3693-4298-8ca7-c975e2e1f260/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T072054Z&X-Amz-Expires=86400&X-Amz-Signature=3594c7e214857b1d882800a83015d701c0522f8a28a2c55efad3b964dfbf39a5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

해당 링크를 클릭하면 관련 애플리케이션 기능이 동작한다.

---