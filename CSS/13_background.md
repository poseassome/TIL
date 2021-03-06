# background
작성일시: 2021년 8월 27일 오후 5:23

## ** 기존 배경 속성

- **background-color**: #ffffff or green (or rgb(a))

- **background-image**: url(url)

- **background-repeat**: repeat/no-repeat/repeat-x/repeat-y

- **background-position:left/center/right&top/center/bottom or value** (from left & from top)

- **background-attachment**: fixed/scroll

<br/>
=> background: color url repeat position attachment

이와 같은 기본 속성을 가지는 것이 border, margin, ..

---

## background

1. 기존 배경은 한 번에 하나만 적용이 가능하지만 CSS3에서는 여러 개의 배경을 동시에 적용 가능
    - 먼저 작성된 이미지가 위에서 출력

2. 배경의 범위 및 시작 위치 설정 가능
3. 배경의 크기 조정 가능

```css
body {
      font-size: 30px;
    }

.multiBG {
      height: 200px;
      border: 2px solid #ccc;
      text-align: center;
      background: url(images/LeftTop.png) no-repeat,
        url(images/RightTop.jpg) no-repeat right top,
        url(images/bg.jpg);
    }
```

---

## ** background-size

백그라운드 이미지의 크기 지정

사용방법<br/>
       background-size : x, y

속성 값
1. X%, Y% : 적용되는 요소의 크기에 비례하여 적용
2. Xpx, Ypx: 절대 크기로 배경 이미지 적용
3. cover : 배경 이미지를 늘려 요소 전체에 표시
4. contain : 배경 이미지의 가로 세로 비율을 맞춰 요소에 표시할 수 있는 최대 크기로 표시

```css
div {
      border: 2px solid #73a11a;
      width: 150px;
      height: 200px;
      margin: 5px;
      background: url(images/bg.jpg) right bottom no-repeat;
      float: left;

    }

#box_rel {
      background-size: 100% 100%;
    }

#box_abs {
      background-size: 50px 50px;
    }

#box_cover {
      background-size: cover;
    }

#box_contain {
      background-size: contain;
    }
```

![Untitled](../images/css_5_1.png)

---