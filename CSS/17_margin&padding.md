# margin & padding
작성일시: 2021년 9월 6일 오후 4:19

> **여백 속성**

## margin
1. 바깥쪽 여백(위치)
2. margin-top / margin-right / margin-bottom / margin-left
3. margin : top right bottom left<br/>
margin : top right bottom (same right)<br/>
margin : top/bottom right/left<br/>
margin : all<br/>
4. margin : auto<br/>
상하 여백 0, 좌우 여백 동일<br/>
(블럭 요소 가운데 정렬)
= margin: 0 auto

<aside>
💡 text-align: center
  인라인 요소 가운데 정렬

</aside>

---

## padding
1. 안쪽 여백(크기)
2. margin 사용법과 동일

---

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Margin & padding</title>
  <style type="text/css">
    #header {
      width: 800px;
      height: 200px;
      background: #ff9300;

      /* margin-top:50px;
      margin-right:100px;
      margin-bottom: 150px;
      margin-left: 200px*/

      /* margin: TOP RIGHT BOTTOM LEFT */
      /* margin: 50px 100px 150px 200px */

      /* margin: TOP RIGHT BOTTOM (same RIGHT) */
      /* margin: 50px 100px 150px */
      /* => margin: 50px 100px 150px 100px */

      /* margin: TOP RIGHT (same TOP) (same RIGHT) */
      /* margin: 50px 100px */
      /* => margin: 50px 100px 50px 100px */

      /* margin:100px */
      /* => margin: 100px 100px 100px 100px */
    }

    #content {
      width: 800px;
      height: 200px;
      background: #7bd85f;
      /* margin: auto; */
      /* margin: 0 auto */
      /* text-align: center */
    }

    #footer {
      width: 800px;
      height: 200px;
      background: #3c9df0;
      /* padding-top:50px;
      padding-right:100px;
      padding-bottom:150px;
      padding-left:200px */

      /* padding: TOP RIGHT BOTTOM LEFT */
      /* padding: 50px 100px 150px 200px */

      /* padding: TOP RIGHT BOTTOM (same RIGHT) */
      /* padding: 50px 100px 150px */
      /* => padding: 50px 100px 150px 100px */

      /* padding: TOP RIGHT (same TOP) (same RIGHT) */
      /* padding: 50px 100px */
      /* => padding: 50px 100px 50px 100px */

      /* padding:50px */
      /* => padding: 50px 50px 50px 50px */
    }

    /* padding은 안쪽 영역이니까 박스 크기가 바뀔 수 있다. */
    /* padding과 border도 크기에 영향을 준다. */
  </style>
</head>

<body>
  <div id="header">
    상단 로고, GNB, topmenu 등
  </div>
  <div id="content">
    페이지별 내용, LNB, 배너, 게시판, 퀵메뉴 등
  </div>
  <div id="footer">
    각종 연락처 정보, 관리자 정보, 약관 및 정책, 카피라이트 등
  </div>
</body>

</html>
```

---

## box-sizing

![Box Model](../images/boxmodel.png)

Box Model

1. **Box Width : 100%**
  - width: 100% + padding: 100px + border: 100px = 100% + 400px

2. **Box Width : auto**
  - width + padding + border = 100%<br/>
  여기서 padding과 border가 없으면 width: 100%와 width: auto 똑같음

3. **box-sizing : border-box**
  - width + padding + border = width
  - width: 80%; padding:100px; border:100px = 80% + 400px
  - width: 80%; padding:100px; border:100px; box-sizing:border-box = 80%

<aside>
💡 box-sizing 기본값은 content-box
</aside>