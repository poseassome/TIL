# 함수(2)-function 활용(alert)
작성일시: 2021년 10월 12일 오후 2:50

### Exercise 01.

버튼을 누르면 알림창이 출력된다.

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>버튼 눌러서 함수 실행하기</title>

  <script type="text/javascript">
    function testFunc() {
      alert("함수를 실행되었습니다.");
    };
  </script>
</head>

<body>
  <!-- 서로다른 객체가 동일한 함수를 호출하는 건 문제가 안됨. -->
  <button type="button" onclick="testFunc()">함수 실행</button>
  <button type="button" onclick="testFunc()">두 번째 버튼</button>
</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/67fd7d16-a921-451d-ba7c-2e23e35cb6b7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T074442Z&X-Amz-Expires=86400&X-Amz-Signature=1879de72492d2bc46e3bf6c78c148bc70d5d3c4af71dc283a1841c9ec476b80f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

### Exercise 02.

하나의 함수를 사용하여 버튼을 눌렀을 때 각각 다른 알림창이 나오게 출력한다.

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>버튼을 눌러서 서로 다른 내용 출력하기</title>
  <script type="text/javascript">
    function testFunc(msg) {  // <---- button이 던진 값을 저장해둘 개체(변수)가 필요함
      alert(msg);
    };

  // testFunc(msg) : 여기 변수는 button에게 값을 받아서 alert에게 전달(연결)해주는 역할         ===> [매개변수]
  // alert(msg)    : 여기 변수는 사용이 목적                                                  ===> [일반변수]
  </script>
</head>

<body>
  <!-- 함수내용이 동일하고 내부 내용이 바뀌는 거면 함수는 1개만 필요하다. -->

  <!-- "11"22"11" 우리는 이렇게 쓰고 싶은데, 장치는 (홀수 ")는 시작 /(짝수 ")은 끝으로 인식한다.     ===> "11"22"33" -->
  <!-- "testFunc(' ')" '' 사용하여 string 입력 -->

  <button type="button" onclick="testFunc('FIRST')">함수 실행</button>
  <button type="button" onclick="testFunc('SECOND')">두 번째 버튼</button>
</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4984db9b-c89e-4c9b-86f4-4956bdc36f65/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T074453Z&X-Amz-Expires=86400&X-Amz-Signature=b82f970ba937160086a32ad6cb7fdd15ef987596c11022384f38ba0db01ad957&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---

### Exercise 03.

다른 내용을 출력하면서 내용을 한번에 보이게 하기

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>버튼을 눌러서 서로 다른 내용 출력하기</title>
  <script type="text/javascript">
    function testFunc(s_name, score) {    // <== 내부에서 실행될 변수와 동일한 변수가 필요함
      /* 알림창 두 번 출력 */
      alert("이름 : " + s_name);
      alert("점수 : " + score);

      /* 알림창 한 번 출력 */
      alert("\'이름\' : " + s_name + "\n점수 : " + score);
    };
  </script>
</head>

<body>
  <button type="button" onclick="testFunc('김철수', 95)">김철수</button>
  <button type="button" onclick="testFunc('이영희', '95')">이영희</button>

  <!-- 함수를 만드는 부분과 실행시키는 부분에서 변수는 순차적으로 매칭된다. -->
  <!-- 내부 실행내용의 순서는 상관없음. -->
</body>

</html>
```

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e6aa1725-693b-4a3c-9938-fddbef78f129/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T074503Z&X-Amz-Expires=86400&X-Amz-Signature=b5016a2aab62836d7ff5071184da4acf0ddcc226f05c551d330492b70847f6c9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

---