# Events
작성일시: 2021년 11월 3일 오후 4:40

## 이벤트 적용

javascript의 경우, `obj. eventHandler= function ( ){ };`

jquery의 경우, `$(" selector ").event(function( ){ });`

---

## 예제 1(1) - element 색 바꾸기

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>이벤트</title>
  <style type="text/css">
    table {border: 1px solid #aaa; margin: 20px; text-align: center; font-weight: bold; font-size: 20px;}
    td {border: 1px solid #aaa; width: 100px; height: 100px;}
    .sel {background: #f00; color: #fff; font-weight: bold;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
      $("td:eq(0)").addClass("sel");
    });
  </script>
</head>

<body>
  <h2>* 이벤트</h2>
  <table>
    <tr>
      <td>#1</td>
      <td>#2</td>
      <td>#3</td>
      <td>#4</td>
      <td>#5</td>
    </tr>
  </table>
</body>

</html>
```

---

## 예제 1(2) - 클릭할 때 element 색 바꾸기

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>이벤트</title>
  <style type="text/css">
    table {border: 1px solid #aaa; margin: 20px; text-align: center; font-weight: bold; font-size: 20px;}
    td {border: 1px solid #aaa; width: 100px; height: 100px;}
    .sel {background: #f00; color: #fff; font-weight: bold;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
	    $("td:eq(0)").click(function () {
        $("td:eq(0)").addClass("sel");
      });
    });
  </script>
</head>

<body>
  <h2>* 이벤트</h2>
  <table>
    <tr>
      <td>#1</td>
      <td>#2</td>
      <td>#3</td>
      <td>#4</td>
      <td>#5</td>
    </tr>
  </table>
</body>

</html>
```

---

## 예제 1(3) - 마우스와 닿으면 element 색 바꾸고 빠지면 돌아오기

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>이벤트</title>
  <style type="text/css">
    table {border: 1px solid #aaa; margin: 20px; text-align: center; font-weight: bold; font-size: 20px;}
    td {border: 1px solid #aaa; width: 100px; height: 100px;}
    .sel {background: #f00; color: #fff; font-weight: bold;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
			/* mouseenter */
      $("td:eq(0)").mouseenter(function () {
        $("td:eq(0)").addClass("sel");
      });

      /* mouseleave */
      $("td:eq(0)").mouseleave(function () {
        $("td:eq(0)").removeClass("sel");
      });
    });
  </script>
</head>

<body>
  <h2>* 이벤트</h2>
  <table>
    <tr>
      <td>#1</td>
      <td>#2</td>
      <td>#3</td>
      <td>#4</td>
      <td>#5</td>
    </tr>
  </table>
</body>

</html>
```

---

## 예제 1(4) - this 사용하기

```jsx
$("td:eq(0)").mouseenter(function () {
			∥
	$("td:eq(0)").addClass("sel");
});
```

효과를 받는 대상과 가지는 대상이 같은 경우에 `this` 사용

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>이벤트</title>
  <style type="text/css">
    table {border: 1px solid #aaa; margin: 20px; text-align: center; font-weight: bold; font-size: 20px;}
    td {border: 1px solid #aaa; width: 100px; height: 100px;}
    .sel {background: #f00; color: #fff; font-weight: bold;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
			/* mouseenter */
      $("td").mouseenter(function () {
        $(this).addClass("sel");
       });

      /* mouseleave */
      $("td").mouseleave(function () {
        $(this).removeClass("sel");
      });
    });
  </script>
</head>

<body>
  <h2>* 이벤트</h2>
  <table>
    <tr>
      <td>#1</td>
      <td>#2</td>
      <td>#3</td>
      <td>#4</td>
      <td>#5</td>
    </tr>
  </table>
</body>

</html>
```

---

## 예제 1(5) - hover 사용하기

**hover**

> **hover = mouseenter + mouseout**  합쳐진 것으로,
>
>
> `$("selector").hover(function(){ },function(){ });`
> function이 2개가 필요하다.
>

```jsx
<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>이벤트</title>
  <style type="text/css">
    table {border: 1px solid #aaa; margin: 20px; text-align: center; font-weight: bold; font-size: 20px;}
    td {border: 1px solid #aaa; width: 100px; height: 100px;}
    .sel {background: #f00; color: #fff; font-weight: bold;}
  </style>
  <script type="text/javascript" src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script type="text/javascript">
    $(document).ready(function () {
			$("td").hover(function () {
        $(this).addClass("sel");
      }, function () {
        $(this).removeClass("sel");
      });
    });
  </script>
</head>

<body>
  <h2>* 이벤트</h2>
  <table>
    <tr>
      <td>#1</td>
      <td>#2</td>
      <td>#3</td>
      <td>#4</td>
      <td>#5</td>
    </tr>
  </table>
</body>

</html>
```

---