# PHP 사용
작성일시: 2021년 12월 2일 오후 5:12

# Intro

PHP는 서버측에서 실행되는 프로그래밍 언어이다.

동적 웹 페이지(Web page)를 만들기 위해 설계되었으며,
이를 구현하기 위해 **PHP로 작성된 코드를 HTML 소스 문서 안에** 넣으면
PHP 처리 기능이 있는 **웹 서버에서 해당 코드를 인식**하여
작성자가 원하는  **웹페이지를 생성**한다.

---

# 개발환경 설정

PHP는 웹 서버에서 실행되는 언어이기 때문에, 실행 결과를 확인하기 위해서 다음 과정을 거친다.

```
**코드 작성**한다 -> **FTP 계정 접속**한다 -> **계정에 파일** 올린다.
-> test는 반드시 **브라우저에서** 내 홈페이지 주소/파일이름
[http://내 계정.dothome.co.kr/hello.php](http://higomn05.dothome.co.kr/hello.php)
-> **실행 결과** 확인
```

PHP 파일은 실시간으로 확인할 수 없기 때문에 위 절차대로 확인해야 한다.
이는 페이지 운영할 때는 문제가 안되는데, ***개발할 때*** 트래픽 초과되면 더이상 접속 못 한다.

![작성한 php파일을 FTP에서 html 폴더에 올리고 브라우저에서 확인한다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7e4ebb60-ca5f-407e-9d58-4c02d7a18248/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T083440Z&X-Amz-Expires=86400&X-Amz-Signature=9cb9eab80bfb0e7c5d891bef18b824669ee17b1ec5d593f9125013f0edd9eec6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

작성한 php파일을 FTP에서 html 폴더에 올리고 브라우저에서 확인한다.

따라서,

닷홈에서 계정을 만들어준 것처럼 똑같은 웹 서버를 내 컴퓨터에 만들어서 테스트 진행한다.
 ==> 이러한 환경을 만들어주는 프로그램이 `**Apache**`
FTP 계정에 파일을 올리지 않아도 똑같은 `웹 서버`를 제공해준다.

---

## Apache 실행

xampp controller에서 Apache start 누르면 실행된다.
정상 실행을 확인하기 위해 브라우저에 [http://localhost](http://localhost/) 입력하고 접속한다.

실행시 보이는 화면은 `c:\xampp\htdocs` 폴더에 있는 `index.php`에 의해 보이는 화면이다.

브라우저 url을 보면 [http://localhost/dashboard/](http://localhost/dashboard/라고) 라고 되어있으며,
`index.php`에 의해  📁htdocs폴더 > 📁dashboard폴더에 있는 `**index.html**` 이 보여지는 것이다.

### FTP와 Apache 비교

FTP의 **📂html 폴더**가 📂xampp 폴더의 **📂htdocs폴더**와 동일하다.

![각 주소로 접속했을 때 보이는 화면 위치](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1ea4df70-7139-4cc8-b33c-921d8a0842c4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T083451Z&X-Amz-Expires=86400&X-Amz-Signature=800dd952801b59bd05e707f897d50e606b47c6b64b50ba60a32cedf609eedd75&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

각 주소로 접속했을 때 보이는 화면 위치

따라서 우리는 **📂htdocs폴더에서 📂website>📂member 폴더**를 만들어서 php파일을 생성한다.
브라우저에서 [**http://localhost/website/members/파일명.php**](http://localhost/website/members/파일명.php) 로 접속한다.

![위와 같은 경로로 개발과정에서 php파일을 실행할 수 있다.](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3f9ad49e-ada7-4de9-a3a4-455d5e793eb5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T083501Z&X-Amz-Expires=86400&X-Amz-Signature=3ff0a8e70f998609d5f1ee8aca253a90658708e723d768c93ff33d32083d01ee&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

위와 같은 경로로 개발과정에서 php파일을 실행할 수 있다.

---