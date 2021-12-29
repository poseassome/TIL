# 선택자(selector)
작성일시: 2021년 8월 9일 오후 9:55

> html 문서의 `<head>`안에서 **`<style>`** 이용하여 지정

선택자는 스타일을 적용할 요소를 선택한다.
  **선택자 { 스타일속성: 값; }**
>

```css
<head>
  <meta charset="utf-8">
  <style>
		/*
      선택자(selector)
      : 스타일을 적용할 요소를 선택함

      선택자 {
        스타일속성: 값;
      }
		*/

		/* *: 전체(모든요소)를 선택 */

    /* 1. 스타일은 가장 아래쪽에 설정한 스타일로 적용 */
    /* 2. 하위요소의 스타일이 우선적으로 적용됨 */
    * {
      color: red;
    }

    p {
      color: green;
    }

    * {
      color: blue;
    }

    h1 {
      color: rgb(255, 0, 0);
    }
  </style>
</head>
```

---

> 아이디나 클래스를 이용하여 선택하기도함

**#id**
  해당 아이디 속성을 가지고 있는 태그를 선택
  보통 id는 잘 쓰지 않음

**.class**
  특정한 클래스를 가지고 있는 태그를 선택
>

```css
h1 {
  color: red;
}

/* 스타일을 적용할 때 웬만하면 id는 쓰지 않음 */
/* 주로 개발자들이 사용함 */
/* #id: 해당 id를 가지는 요소를 선택 */
#warning-header {
  color: orange;
}

/* class: 요소들간의 동일한 이름 그룹 */
/* .클래스명: 해당 class명을 가지는 요소를 선택 */
.primary {
  color: green;
}
```

```css
/* 태그.클래스명 */
/* 해당 태그에 해당 클래스가 있는 것만 */
p.text-green {
  color: green;
}
```

```css
/* 부모>자손(자식) */
ul>li {
  background-color: green;
}

/* 클래스선택자와 자손(자식)선택자 응용 */
.menu>li {
  color: white;
}

/* 부모>자손(부모)>자손>..>..>..> */
/* .menu>li>a { */

/* 후손 선택자 */
/* 조상 후손 */
.menu a {
  color: antiquewhite;
}
```

---

> 링크로 스타일 파일을 삽입할 수도 있음
**style.css** 파일 만들어서 link로 첨부함
>

```css
<!-- 링크로 스타일 파일 삽입 -->
  <link rel="stylesheet" type="text/css" href="css/style.css">
```

---