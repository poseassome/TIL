# Element Level
작성일시: 2021년 8월 26일 오후 5:49

> ** 요소 레벨(Element Level) **<br/>
태그가 어떻게 보여지는가에 대한 구분

## 블록 레벨 (Block Level)
-독립된 행을 갖는 요소 집합
  - 크기 지정, 위치 조정 가능(*)
  - p, h1~h6, ul, il, li, div, table...
  - 다른 블록 레벨 요소와 인라인 요소 포함 가능
  - p, h, dt, address 같은 일부 요소는 다른 블록 포함 불가

```html
<!DOCTYPE html>
<html lang="KO">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>요소레벨</title>
  <style type="text/css">

  </style>
</head>

<body>
  요소 레벨은 태그가 <p class="brd">어떻게 보여지는가에</p> 대한 구분입니다.

  <div class="box">
    <p>블럭 요소는 독립된 행을 가지는 요소입니다.</p>
    <p>블럭 요소는 독립된 행을 가지는 요소입니다.</p>
    <p>블럭 요소는 독립된 행을 가지는 요소입니다.</p>
    <p>블럭 요소는 독립된 행을 가지는 요소입니다.</p>
    <p>블럭 요소는 독립된 행을 가지는 요소입니다.</p>
    <p>블럭 요소는 독립된 행을 가지는 요소입니다.</p>
  </div>

</body>

</html>
```

**Default width**: 100% (실제값은 auto)<br/><br/>
**Default height**: 0       (실제값은 auto)<br/>
    내부 콘텐츠가 있으면 콘텐츠 만큼의 높이를 가진다.<br/>
    이때, 감싸는 block의 height가 없어야 한다.

**overflow: visible(기본값) / hidden / scroll / auto**<br/>
  - scroll : 수직, 수평으로 무조건 스크롤 바가 생기지만 내용이 넘치는 방향에 대해서만 활성화가 됨
  - auto : 넘치는 내용 만큼 자동으로 스크롤 바가 생성됨.

<aside>
💡 **속성 기본값을 아는 것이 중요한 이유?**<br/>
  반응형 웹사이트에서 필요하다.<br/><br/>

  if, 큰 화면에서 필요했던 코드가 작은화면에서 필요없어질 때,<br/>
  작은화면에서 그 코드를 지워버리면 코드가 적용안되는 것이 아니라 큰 화면과 똑같은 속성을 갖게 됨.

  → 필요하지 않은 코드는 지우는 것이 아니라 기본값으로 변경해야 한다.

</aside>

---

## 인라인 레벨 (Inline Level)

-범위 표시 요소의 집합
  - 크기(예외: img), 위치 조정 불가
  - a, em, strong, img, span...
  - 블록 레벨 요소는 포함할 수 없고 인라인 요소만 포함 가능
  - 높이 속성 사용 불가

```html
<!DOCTYPE html>
<html lang="KO">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>요소레벨</title>
  <style type="text/css">
		a {
      width: 200px;
      height: 200px;
      border: 2px solid #f00;
      display: inline-block;
    }
  </style>
</head>

<body>
  <p>인라인 요소는 <a href="#">위치와 크기를</a>지정할 수 없습니다.</p>
</body>

</html>
```

`<a>`에 position을 적용하면 a의 레벨이 바뀜<br/>
inline → block

보통은 display로 요소 레벨을 직접 변경한다.<br/>v
display: none / block / inline / inline-block<br/>
             어떻게 보이게 할 것인가를 결정하는 것

  vs. visibility (공간을 유지하되 보이지 않음)

---

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="ko">

<head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  <title>요소 레벨</title>
  <style type="text/css">
    body {
      font-size: 24px;
    }
  </style>
</head>

<body>
  <p>
    <a href="#">
      블럭요소는 블럭 요소와 인라인 요소를 포함할 수 있다.
    </a>
  </p>

  <!-- HTML5에서는 예외적으로 <a>는 block요소를 포함할 수 있다. -->
  <!-- Error -->
  <a href="#">
    <p>
      블럭요소는 블럭 요소와 인라인 요소를 포함할 수 있다.
    </p>
  </a>

  <div>
    <p>
      블럭요소는 블럭 요소와 인라인 요소를 포함할 수 있다.
    </p>
  </div>

  <!-- 예외 요소 -->
  <!-- Error -->
  <p>
  <div>
    블럭요소는 블럭 요소와 인라인 요소를 포함할 수 있다.
  </div>
  </p>

</body>

</html>
```

<aside>
💡 블럭요소 안에 인라인 요소가 존재할 수 있다.

```html
  <p> <a></a> </p>
```

💡 인라인 요소안에 블럭 요소가 존재할 수 없다.
```html
  <a> <p></p> </a>
```

💡 블럭요소 안에 블럭요소가 존재할 수 있지만 예외가 있다.
```html
  <p> <div></div> </p>
```
</aside>