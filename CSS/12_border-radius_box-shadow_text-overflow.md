# border-radius / box-shadow / text-overflow
작성일시: 2021년 8월 27일 오후 5:13

## border-radius

Box model 외각선의 곡률 지정

 - 사용 방법
       border-radius:[length]
 - 속성 값

1. length: 곡률의 크기
2. border-top-left-radius 으로 개별 지정 가능

---

## box-shadow

: 지정된 요소의 그림자 설정<br/>
(shadow의 모양이 box이기 때문에 box다.)

 - 사용방법
       box-shadow:[dx] [dy] [blur] [spread] [color] [set]
 - 속성

1. dx : 그림자의 가로방향 위치
2. dy : 그림자의 세로방향 위치
3. blur : 흐려짐 정도
4. spread : 번짐 정도
5. set : 그림자의 형태
    - outset : 요소 바깥쪽으로 그림자가 떨어짐 (기본값)
    - inset : 요소 안쪽으로 그림자가 떨어짐


```css
/* 첫번째 작성 */
    #box {
      font-size: 45px;
      text-align: center;
      line-height: 100px;
      color: #fff;
      width: 800px;
      height: 100px;
      background-color: #ff3399;
      box-shadow: 5px 10px 5px 5px #000;
    }

/* 두번째 작성 */
    body {
      margin: 0px;
      padding: 0px;
    }

    #box {
      font-size: 45px;
      text-align: center;
      line-height: 100px;
      color: #fff;
      height: 100px;
      background-color: #ff3399;
      box-shadow: 0px 6px 3px 3px #999;
    }
```

---

## text-overflow

overflow되는 text의 표시를 지정

 - 사용방법
    text-overflow:속성값
 - 속성

1. clip : 지정된 영역의 크기로 잘라낸다.
2. ellipsis : 지정된 영역의 크기에 맞게 말줄임표 표시

```css
body {
      font-size: 20px;
    }

#textBox p {
      margin: 0 auto;
      margin-bottom: 10px;
      border: 1px solid #333;
      padding: 10px;
      width: 90%;
      white-space: nowrap;   /* 중요 */
      overflow: hidden;   /* 중요 */

    }

#textBox .clipText {
      text-overflow: clip;
    }

#textBox .ellipsisText {
      text-overflow: ellipsis;
    }
```

![Untitled](../images/css_4_1.png)

<aside>
💡 text-overflow는 overflow와 whtie-space와 같이 사용한다.

</aside>

---