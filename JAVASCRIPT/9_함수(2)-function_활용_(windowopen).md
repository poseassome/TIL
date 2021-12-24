# 함수(2)-function 활용(window.open)
작성일시: 2021년 10월 12일 오후 3:13

### 웹사이트에서 버튼을 눌렀을 때 팝업창이 나오게 하기

- **준비 :**
    1. 버튼이 존재하는 팝업창이 열릴 웹사이트(main.html)

        ```html
        <!DOCTYPE html>
        <html lang="ko">

        <head>
          <meta charset="UTF-8">
          <meta http-equiv="X-UA-Compatible" content="IE=edge">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>main</title>
          <style type="text/css">
            body {
              font-size: 24px;
            }
          </style>

          <script type="text/javascript">
            function win_open() {
        			window.open("pop01.html", "a", "width=300, height=400, left=0, top=0");
            };
          </script>
        </head>

        <body>
          <button type="button" onclick="win_open()">팝업 1</button>
          <button type="button">팝업 2</button>
        </body>

        </html>
        ```

    2. 출력될 팝업창 (pop01.html, pop02.html)

        ```html
        <!DOCTYPE html>
        <html lang="ko">

        <head>
          <meta charset="UTF-8">
          <meta http-equiv="X-UA-Compatible" content="IE=edge">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>팝업 1</title>
          <style type="text/css">
            body {
              background: rgb(72, 130, 255);
              font-size: 24px;
              color: #fff;
            }
          </style>

          <script type="text/javascript">

          </script>
        </head>

        <body>
          첫 번째 팝업입니다.
        </body>

        </html>
        ```

        ```html
        <!DOCTYPE html>
        <html lang="ko">

        <head>
          <meta charset="UTF-8">
          <meta http-equiv="X-UA-Compatible" content="IE=edge">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>팝업 2</title>
          <style type="text/css">
            body {
              background: rgb(153, 95, 219);
              font-size: 24px;
              color: #fff;
            }
          </style>

          <script type="text/javascript">

          </script>
        </head>

        <body>
          두 번째 팝업입니다.
        </body>

        </html>
        ```

- **기본 내용 :**
    - `window.open("팝업될 문서 경로", "팝업된 문서 이름", "옵션(크기, 위치, bar 표시 등");`

        <aside>
        💡 `"팝업된 문서 이름"` : 똑같은 이름의 창이 여러 개 뜨지 않게 해주는 역할

        </aside>

    - 파일 불러오는 방법(4)

          1. 다른 사이트에 있는 자원을 이용할 때는 **http**로 시작

          2. 내부 폴더는 **"폴더이름/"**

          3. 나올 때는 **"../"**

          4. 끝날 때는 **"이름.확장자"**


- **Result :**

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f29af71f-89d5-4966-acb0-d77efc8762bd/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T074519Z&X-Amz-Expires=86400&X-Amz-Signature=5849f70cfa92aeb0a93e3b0aa4f51ff957862a038c90cd44b792496e80a4a5ff&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


---

### (응용) 함수 하나만 사용해서 팝업창 2개 띄우기

- **main.html**

    ```html
    <!DOCTYPE html>
    <html lang="ko">

    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>main</title>
      <style type="text/css">
        body {
          font-size: 24px;
        }
      </style>

      <script type="text/javascript">
        function win_open(page, name, left) {
          window.open(page, name, "width=300, height=400, left=" + left + ", top=0");
        };
      </script>
    </head>

    <body>
      <button type="button" onclick="win_open('pop01.html','a', 0)">팝업 1</button>
      <button type="button" onclick="win_open('pop02.html','b', 300)">팝업 2</button>
    </body>

    </html>
    ```

    <aside>
    💡 속성 사이에 변수 넣을 때 **"+변수+"**

    </aside>

- **Result :**

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/19cbc2db-a84a-4889-b8f2-eeed6d9789e8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T074532Z&X-Amz-Expires=86400&X-Amz-Signature=2d69bed18007afadd354b077993835a9906e37e59378c1263eaca402ed777067&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


---

### (응용) 팝업창 닫기를 만들어서 닫기(window.close 사용)

- **[닫기] 만들기 2가지**

    > 1) <html>내에 <script> 작성
    >
    - pop01.html

    ```html
    <!DOCTYPE html>
    <html lang="ko">

    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>팝업 1</title>
      <style type="text/css">
        body {
          background: rgb(72, 130, 255);
          font-size: 24px;
          color: #fff;
        }
      </style>

      <script type="text/javascript">
        function win_close() {
          window.close();
          // 매개변수 없음
          // window.close는 window.open으로 연 것에만 사용한다.
        };
      </script>
    </head>

    <body>
      첫 번째 팝업입니다.<br>
      <a href="#" onclick="win_close()">[닫기]</a>
    </body>

    </html>
    ```

    > 2) 인라인 방식으로 작성
    >
    - pop02.html

    ```html
    <!DOCTYPE html>
    <html lang="ko">

    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>팝업 2</title>
      <style type="text/css">
        body {
          background: rgb(153, 95, 219);
          font-size: 24px;
          color: #fff;
        }
      </style>

      <script type="text/javascript">

      </script>
    </head>

    <body>
      두 번째 팝업입니다.<br>
      <a href="#" onclick="javascript:window.close();">[닫기]</a>
    </body>

    </html>
    ```

- **Result**

    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3c44612f-5576-4cd8-9718-30b9b0440913/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211220%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211220T074545Z&X-Amz-Expires=86400&X-Amz-Signature=0bb8b87e6d5f0d7c799bd3f86a7b36b3dce4c8a014f910089d45f91c200f79cf&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)


---