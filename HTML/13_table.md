# <table>
작성일시: 2021년 8월 25일 오후 1:07

> 3 x 3 table 만들기
>

```html
<table>
      <thead>
        <tr>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td></td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td></td>
          <td></td>
        </tr>
      </tbody>
    </table>
```

---

> **웹 접근성을 고려한 table 작성**

  우리는 표를 볼 때 합계 정보가 먼저 눈에 들어온다.
  시각장애인분들은 들어서 알아야되는데, 합계가 밑에 있으면 불편하다.
     >> **<thead> 밑에 합계의 내용을 가지는 <tfoot>을 작성**한다.
     >> 보이는 것은 똑같이 밑에 위치한 것으로 보임

   thead / tfoot / tbody : 각 셀들의 역할별 구분
     **thead : 제목
     tfoot : 결과
     tbody : 내용**

     필요하지 않은 태그들은 생략 가능
     태그 사용 시 반드시 위 순서대로 사용
>

> 표의 제목은 <table> 밑에 **<caption>**을 쓴다.
  BUT 일부 screen reader에서는
          caption을 이해하지 못하는 것도 있고,
          summary를 이해하지 못하는 것도 있음

  따라서 **caption과 summary를 같이 작성을 해주는데
  이 때, 같은 속성값을 작성하지 않는다.**
     >>  caption과 summary를 같이 이해할 수 있기 때문에
>

> screen reader가 '분류 값 값 값' 읽기 보다
  '분류 값 분류 값 분류 값' 으로 읽기위한 코딩

  -id(속성) : 제목 셀에 이름 부여
  -headers(속성) : 해당 셀의 제목 셀 지정

   ex) 리더기가 '삼성 태블릿'으로 읽으려면 해당 <td>에 headers="1st_title_id 2nd_title_id" 작성
         (먼저 읽혀야 할 요소 id값 (띄어쓰기) 나중에 읽힐 요소 id값)
>

```html
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>테이블</title>
  <style text="text/css">
    table {
      border: 1px solid #000;
      font-size: 24px
    }

    td,
    th {
      width: 200px;
      height: 100px;
      border: 1px solid #000;
    }

    .sel {
      background-color: #0077ff;
      color: #fff
    }
  </style>
</head>

<body>
  <table summary="삼성, 애플 제품별 가격비교">
    <caption>제조사별 판매가격</caption>
    <thead>
      <tr>
        <th>구분</th>
        <th id="s">삼성</th>
        <th id="a">애플</th>
      </tr>
    </thead>

    <tfoot>
      <tr>
        <th>합계</th>
        <td>320,000</td>
        <td>350,000</td>
      </tr>
    </tfoot>

    <tbody>
      <tr>
        <th id="p">스마트폰</th>
        <td headers="s p">150,000</td>
        <td headers="a p">160,000</td>
      </tr>
      <tr>
        <th id="t">태블릿</th>
        <td headers="s t">170,000</td>
        <td headers="a t">190,000</td>
      </tr>
    </tbody>
  </table>
</body>

</html>
```