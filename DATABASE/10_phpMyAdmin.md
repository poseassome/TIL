# phpMyAdmin
작성일시: 2021년 11월 26일 오후 2:12

## Apache

xampp control panel에서 Apache, MySQL 'start'

**`Apache`** 실행하면, 닷홈에 계정을 만든 것처럼 가상의 공간을 제공해줌.

### roofback address

`localhost` 또는 `127.0.0.1`
(모든 컴퓨터의 roofback 주소는 동일한다.)

*whois 홈페이지*에서 웹사이트의 정보를 보여준다.

`cmd`창에 `**ipconfig**`를 입력하면 정보를 알 수 있음.
뒤에 `/all`를 붙이면 더 자세한 정보 볼 수 있음.

### DNS (Domain Name Server)

**IP ==> DNS ==> NAME**

원래 컴퓨터의 이름은 **숫자**로 되어 있다.
내 컴퓨터를 웹 서버처럼 만들었을 때,
컴퓨터의 이름을 글자로 만들었을 때의 이름은 **localhost**이다.

### Apache 실행

브라우저에 [http://localhost](http://localhost/) 입력했을 때 창이 뜨면 정상 작동 중이다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a2cc20d8-ed2f-4936-9764-0396d15e5875/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082948Z&X-Amz-Expires=86400&X-Amz-Signature=17ebc051932e9743b7d4b0b1cea5885ab6fd20aae6e2ec7899a896fb6bd4bdb3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

xampp 폴더에는 phpMyAdmin 이 있다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d7e9e0b9-ae8a-48ff-992d-149fb720186e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T082956Z&X-Amz-Expires=86400&X-Amz-Signature=b7d3153151ef0fa29867244a9b39abb622fb58c09acf8f6550f225ae0f103031&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

브라우저에 [http://localhost/phpmyadmin](http://localhost/phpmyadmin) 입력.
==> MySQL를 GUI로 볼 수 있게 됨.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b06b31a1-a43b-4638-9e64-d39bd660617e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T083003Z&X-Amz-Expires=86400&X-Amz-Signature=193770d534e0baf942310285d76f6753e439415162b64975e1bfc24c3e1458ca&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

## phpMyAdmin

데이터베이스 조작 가능

### 닷홈의 Database 접속

닷홈 홈페이지 로그인 -> 호스팅 관리 -> 상세보기 -> 하단에 '제공내역' MySQL 관리(UTF-8) 주소를 브라우저에 입력 -> phpMyAdmin 로그인

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7da13bd7-2b8d-4b5a-beb4-b76918a74074/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T083014Z&X-Amz-Expires=86400&X-Amz-Signature=dd16288a3f6319e64769ebd3931b20a3ccca9fd19eb0405b7096e21b8b11fd7f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---