# Sass

### css / sass / scss
 - ### css
```css
p{
  color: red;
}
p span {
  color: blue;
}
a:hover, a:focus{
  color: blue;
}
```
 - ### sass
```sass
p
  color: red
  span
    color: blue
a
  &:hover,
  &:focus
    color: blue;
```
 - ### scss
```scss
p{
  color: red;
  span{
    color: blue;
  }
}
a{
  &:hover,
  &:focus{
    color: blue;
  }
}
```
Sass와 Scss는 Nesting 구조(중첩)가 있다.

## Sass
stylesheet language로 이를 컴파일 해서 CSS로 만든다.<Br/>
(sass파일 자체로는 적용이 안되기때문에 꼭 컴파일 과정을 거쳐야 한다.)

Sass는 indent가 중요하다. 잘못되면 error가 뜬다.

## Scss
Sass와 달리 명확하게 bracket{ }을 사용하여 구분지을 수 있다.

- CSS 코드가 한 파일이라면
    - 가독성 저하
    - 중복코드 생성
    - 코드 수정 어려움
    - css 작업 속도 느려짐

***
## Sass 7-1 패턴
7개의 파일을 만들어서 최종적으로 1 파일을 만들어낸다.

1. base/<br/>
    reset, 전체 스타일에서 기본이 되어야 할 스타일 정의
2. components/<br/>
    button이나 dropdown, input 등
3. layout/<br/>
    컴포넌트보단 큰 개념, gnb, header, footer, form 등
4. pages/<br/>
    컴포넌트와 레이아웃이 혼합된 하나의 홈페이지
5. themes/<br/>
    다크테마, 라이트테마
6. abstracts/<br/>
    변수나 함수 등
7. vendors/<br/>
    외부리소스파일 (jquery ui 등)

파일명에 '_'가 붙는 경우 @import 되어 사용될 것으로 파악한다.


## @import
css는 가장 아래에 작성된 것이 최신으로 덮어 씌여 진다.<Br/>
=> 작성하는 순서 중요하다.

main.scss에 import한다면
```scss
@import './abstracts/variables.scss';
@import './abstracts/mixins.scss';
@import './base/reset.scss';

...
```
변수 같이 가장 기본으로 정의된 파일이 위에 존재하고<Br/>
base폴더 밑에는 네이밍 순서 맞춰서 정리하면 된다.


## variables
변수 정의하여 여러페이지에 공통으로 적용할 때 사용한다.<Br/>
수정할 때는 변수 파일에 들어가서 변수만 수정하면 된다.
```scss
$variableName: value;
```

## @mixin
말줄임표를 사용한다고 하면
```scss
@mixin ellipsis {
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
```
위의 스타일은 하나의 세트이기 때문에 mixin으로 묶어준다.<Br/>
하나의 묶음으로 사용해서 필요한 곳에 include하면 된다.
```scss
p{
  @include ellipsis;
}
```

그리고 `@mixin`에 변수를 받을 수 있다.
```scss
@mixin bg-img($bg-url, $bg-position: center, $bg-size: contain. $bg-color: transparent){
  background-image: url($bg-url);
  background-repeat: no-repeat;
  background=postiion: $bg-postiion;
  backgournd-size: $bg-size;
  background-color: $bg-color;
}

.bg{
  @include bg-img('http://~~', center, contain, white);

  // 이렇게 적어도 기본값 적용되어 출력된다.
  @include bg-img('http://~~');
}
```
변수는 순서에 맞춰서 작성해야하고,<Br/>
기본값으로 지정하고 싶은게 있을 경우 `:`하고 값을 써준다.


## @function
결과값을 반환하는 역할이기 때문에 원하는 속성값 위치에 function 이름을 작성한다.
```scss
@function half-opacity($color){
  $color: rgba($color, .5);
  @return $color;
}

h1{
  font-size: 10px;
  text-align: center;
  color: half-opacity(red);
}
```
***