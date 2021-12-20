# <img>
작성일시: 2021년 8월 25일 오후 1:06

> **<img>** : 이미지 삽입 태그

**<img src="파일 위치">**
>

---

![위 예시의 각 이미지 파일을 불러 오려면 다음과 같다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ae830424-fe37-4fde-8b72-d2f9a88804b5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T071710Z&X-Amz-Expires=86400&X-Amz-Signature=8043f5f8aeb392ca5d47915b1cb119cd741e3f3d8b386d946d3f39076e1a53a3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

위 예시의 각 이미지 파일을 불러 오려면 다음과 같다.

```html
-ROOT를 url 폴더로 봤을 때

    **1. jpg을 불러올 때
      <img src="1.jpg">
      <img src="./main/1.jpg">
```

```html
		**2.jpg을 불러올 때
      <img src="images/2.jpg">
      <img src="./main/images/2.jpg">
```

```html
		**3.jpg을 불러올 때
      <img src="../3.jpg">
      <img src="./3.jpg">
```

```html
		**4.jpg을 불러올 때
     <img src="../sub/4.jpg">
     <img src="./sub/4.jpg">
```

- **상대경로**
  내 위치를 기준으로 다른 파일의 위치를 설명
- **절대경로**
  시작하자마자 제일 꼭대기층에서부터 찾는 방법
  './' 나 'C:\~', 'http://', '[ftp://~~](ftp://%7E%7E/)'

> 1) 다른 사이트의 자원을 사용하려고 한다.
     >  무조건 '**http://**' 부터

2) 폴더를 열어서 봐야한다.
     >  '**폴더이름/**'

3) 폴더 바깥으로 나가야한다.
     >  '**../**' (단, 지금있는 폴더에서 한번만 나감)
     >  '**../../**' (두번 나감-두 폴더 밖에)

4) 제일 꼭대기 층으로 한번에 가고 싶으면
     >  '**./**'

5) 경로가 끝날 때는 무조건 '**파일이름.EXT**'
>

---