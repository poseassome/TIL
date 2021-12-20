# position
작성일시: 2021년 9월 7일 오후 5:23

## **position**

  1. 움직이는 방법
  2. 위치 속성과 함께 사용

- **위치 속성**
    1. top / right / bottom / left
    2. position 속성이 없는 경우 이동 불가
    (값이 static인 경우 제외)
    3. right, bottom은 position값이 absolute, fixed, sticky인 경우 사용 가능
    -position: absolute;
      right: Npx (o)
    -posittion: relative;
      right: Npx (x)
    4. 기준의 속성명 위치에서 대상의 속성명 위치까지의 거리

---

## position 속성값

> **1.  static**

  1) 기본값
  2) 지정된 요소를 일반 요소(p, h 등)처럼 사용
  3) 위치, 레이어 변경 불가
  4) 태그가 작성된 순서대로 배치
  5) margin: auto  사용가능
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <title>static</title>
  <style type="text/css">
    #header {
      width: 800px;
      height: 150px;
      background: #ff9900;
      left: 100px;
    }

    #content {
      width: 800px;
      height: 150px;
      background: #99cc00;
      position: static;
      left: 100px;
    }

    #footer {
      width: 800px;
      height: 150px;
      background: #0099ff;
      position: static;
      margin: auto;
    }
  </style>
</head>

<body>
  <div id="header"></div>
  <div id="content"></div>
  <div id="footer"></div>
</body>

</html>
```

![static](position%208e3763e91c4a48fca2aa68527922f051/Untitled.png)

static

> **2.  absolute**

  1) 위치 독립적 - 다른 요소의 영향 받지 않음
  2) 동일한 기준 안에서는 모든 요소가 동일한 기준점 사용
  3) margin: auto 사용 불가 (but, 가운데 정렬은 할 수 있음)
  4) 위치, 레이어 이동 가능

-요소가 inline이면 inline-block으로 바꿔서 이동함
-float처럼 위로 뜨는 개념이다.
 float / position: absolute / position: fixed
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <title>absolute</title>
  <style type="text/css">
    #header {
      width: 800px;
      height: 150px;
      background: #ff9900;
      position: absolute;
      left: 50px;
      top: 50px;
    }

    #nav {
      width: 200px;
      height: 50px;
      background: #ff0;
      position: absolute;
      left: 50px;
      top: 150px;
    }

    #content {
      width: 800px;
      height: 450px;
      background: #99cc00;
      position: absolute;
      left: 50px;
      top: 200px;
    }

    /* #footer {
      width: 800px;
      height: 150px;
      background: #0099ff;
      position: absolute;
      left: 150px;
      top: 150px;
    } */
  </style>
</head>

<body>
  <div id="header">
    <div id="nav"></div>
  </div>

  <div id="content"></div>
  <div id="footer"></div>
</body>

</html>
```

![content 뒤에 nav가 있다.](position%208e3763e91c4a48fca2aa68527922f051/Untitled%201.png)

content 뒤에 nav가 있다.

### 레이어

1. 요소들간의 층(앞/뒤)
2. z-index 속성 사용
3. 1부터 시작하는 정수 사용
4. 순서와 무관하며 높은 숫자가 앞
5. 속성을 지정하지 않는 경우 나중에 작성된 요소가 앞
6. 임의로 생성된 값은 실제 값보다 무조건 뒤
7. position 속성과 함께 사용

- 형제 요소일 때, z-index가 높으면 앞에 위치함
- 부모-자식관계에서 부모는 십의 자리, 자식은 일의 자리다.
자식에게는 부모의 십 자리가 부여됨.
- 하위요소(자식)의 순서를 바꾸고 싶으면 그의 부모의 z-index를 수정한다.

![참고 그림](position%208e3763e91c4a48fca2aa68527922f051/Untitled%202.png)

참고 그림

> **3. relative**

  1) 요소가 작성된 순서대로 배치
  2) 위치, 레이어 변경 가능
  3) 모든 요소가 독립된 중심점 사용
  4) margin: auto 사용 가능
  5) 다른 요소의 영향 있음

  -absolute의 중심점은 모두가 웹페이지의 왼쪽 최상단이지만
   relative는 각 요소의 시작위치의 왼쪽 최상단이다.
  -하나의 요소가 움직여도 다른 요소의 위치가 이동하지 않음
   (absolute는 당겨서 이동한다.)
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <title>relative</title>
  <style type="text/css">
    #header {
      width: 800px;
      height: 150px;
      background: #ff9900;
      position: relative;
      left: 50px;
      top: 50px;
    }

    #nav {
      width: 600px;
      height: 50px;
      background: #ff0;
      position: relative;
      left: 150px;
      top: 80px;
    }

    #content {
      width: 800px;
      height: 150px;
      background: #99cc00;
      position: relative;
      left: 100px;
      top: 100px;
    }

    #footer {
      width: 800px;
      height: 150px;
      background: #0099ff;
      position: relative;
      left: 150px;
      top: 150px;
    }
  </style>
</head>

<body>
  <div id="header">
    <div id="nav"></div>
  </div>
  <div id="content"></div>
  <div id="footer"></div>
</body>

</html>
```

![relative](position%208e3763e91c4a48fca2aa68527922f051/Untitled%203.png)

relative

### 기준의 정의

1. 움직이는 대상의 position이 relative인 경우
-부모요소가 기준
2. 움직이는 대상의 position이 absolute인 경우
-position 속성은 position 속성을 가지는 상위 요소가 기준
-상위 요소 중 position 속성을 가지는 요소가 없는 경우
document가 기준

![Untitled](position%208e3763e91c4a48fca2aa68527922f051/Untitled%204.png)

분홍색 div에 left: 100px를 주면 얘는 position이 존재한다는 거다.
position: relative 면 부모요소로부터 left 이동
position: absolute 면 (나를 감싸고 있는 모든 것(상위요소)에 position이 없을 때) 무조건 body 기준
position이 있는 상위요소(가장 가까운 요소)가 있으면 그거 기준으로 이동

> **4.fixed**

  1) 스크린을 기준으로 지정된 위치에 고정
  2) 스크롤 시에도 처음 고정된 위치에서 보여지는 속성값
  3) margin: auto 사용 불가
  4) 레이어 사용 가능
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <title>fixed</title>
  <style type="text/css">
    #header {
      width: 100%;
      height: 100px;
      background: #ff9900;
      position: fixed;
      left: 0;
      top: 0;
      z-index: 10;
    }

    #content {
      width: 800px;
      height: 150px;
      background: #99cc00;
      position: relative;
      left: 100px;
      top: 200px;
    }

    #footer {
      width: 300px;
      height: 400px;
      background: #0099ff;
      position: absolute;
      left: 400px;
      top: 600px;
    }
  </style>
</head>

<body>
  <div id="header"></div>
  <div id="content"></div>
  <div id="footer"></div>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
  <p>1</p>
</body>

</html>
```

![가장 상단 header는 제자리에 있다.](position%208e3763e91c4a48fca2aa68527922f051/Untitled%205.png)

가장 상단 header는 제자리에 있다.

*parallax scrolling

> **5.sticky**

내가 지정한 위치에 도달하기 전에는 scrolling이 되지만
도달하고서는 fixed 상태

하지만 쓰지마라, IE 하위버전에서 호환안됨.
-script 사용한다.
>