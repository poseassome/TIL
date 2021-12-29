# transition / animation
작성일시: 2021년 8월 27일 오후 6:05

## 전환효과 (transition)

CSS 속성이 변화할 때 애니메이션

2차원 변환 (transform) 함수

- 사용방법<br/>
transition : 변환속성 애미메이션시간

- 속성 값
  1. 변환속성 : 변환할 속성
  all로 지정되면 모든 속성 영향
  2. 애니메이션시간 : 애니메이션 재생 시간(duration) 지정

변환 함수
   - translate(translateX, translateY) : 지정된 값만큼 이동
   - scale(scaleX, scaleY) : 지정된 값만큼 확대 및 축소
   - skew(angleX, angleY) : 지정된 값만큼 기울림
   - rotate(angleZ) : 지정된 값만큼 회전

```css
#transitionBox img {
      transform: rotate(0deg);
      border: #ccc solid 5px;
      opacity: 0.2;
      transition: all 2s;
    }

#transitionBox img:hover {
      transform: rotate(30deg);
      border: #396 solid 5px;
      opacity: 1;
    }
```

![회전하며 투명도가 낮아짐](../images/css_6_1.png)

회전하며 투명도가 낮아짐

```css
#transitionBox {
      width: 320px;
      height: 240px;
      overflow: hidden;
    }

#transitionBox img {
      transform: scale(1, 1);
      border: #ccc solid 5px;
      opacity: 0.2;
      transition: all 2s;
    }

#transitionBox img:hover {
      transform: scale(1.2, 1.2);
      border: #396 solid 5px;
      opacity: 1;
    }
```

![이미지가 칸을 넘지않고 커지며 투명도가 낮아짐](../images/css_6_2.png)

이미지가 칸을 넘지않고 커지며 투명도가 낮아짐

---

## animation

CSS의 속성값 변화를 애니메이션

1. keyframes : 효과 작성, 키프레임 지정 /만드는 부분
    - from : 시작 프레임 설정
    - to : 끝 프레임 설정
    - 중간 키프레임 : %단위로 지정


2. animation : 효과 적용 /실행시키는 부분
    - aniamtion-name : 설정된 keyframe 지정
    - animation-duration : 실행 시간 지정
    - animation-transition-count : 반복 횟수 지정
    - animation-timing-function : 속도 형태 지정
    - animation-delay : 대기 시간 지정
    - animation-direction : 진행 상태 지정


```css
@keyframes anitest {
      from {
        opacity: 1.0;
        transform: rotate(0deg)
      }

      50% {
        opacity: 0.1;
      }

      to {
        opacity: 1.0;
        transform: rotate(360deg)
      }
    }

img {
      animation-name: anitest;
      animation-delay: 2s;
      animation-duration: 4s;
      animation-iteration-count: infinite;
      animation-timing-function: ease-in-out;
      animation-direction: alternate;
    }
```

![Untitled](../images/css_6_3.png)

- infinite : 무한대로 반복

- alternate : 정방향에서 역방향으로 움직임

- ease-in-out : 느려졌다 보통이었다 느려짐

---