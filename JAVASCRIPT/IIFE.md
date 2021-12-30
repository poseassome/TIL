# IIFE (즉시 실행 함수 표현)
Immediately Invoked Function Expression

함수를 작성하고 호출할 때는 `()`를 붙인다.
```jsx
fucntion func(){

}

func();
```
여기서 `func()`를 `( )` 안에 넣는다.
```jsx
(function func() {})();
```
즉시 실행 함수는 함수를 괄호안에 넣고 바로 실행시켜주는 것이다.
```jsx
/* 주로 다음과 같이 표기함 */
(function(){

})();
```

#### 사용하는 이유?

함수 공간이 있으면 명확하게 새로운 스코프를 만들어낼 수 있다.
```jsx
(function(){
  var aName = 'Barry':    // Barry
})();
```

```jsx
/* var는 함수 스코프라서 다음과 같은 문제가 있다. */
if(true){
  var temp = 'hello';
}
console.log(temp);        // hello

/* let이 생기면서 블럭 스코프로 구분된다. */
if(true){
   let temp = 'hello';
}
console.log(temp);        // temp is not defined
```

var를 사용했을 때 접근하지 못하도록 즉시실행 함수를 사용한다.
```jsx
if(true){
  (function(){
  var temp = 'hello';
  console.log(temp);      // hello    //// 내부적으로는 사용가능
  })()
}
console.log(temp);        // temp is not defined
```

==> IIFE : 블럭 스코프를 흉내내는 새로운 스코프를 만들어 낸다.
```jsx
(function(){    // IIFE 시작
                // IIFE 내부 동작 코드
})();            // IIFE 종료
```
영역이 침범되지 않도록 꼭 `;`를 붙여줘야 한다.
<br/><br/>

숨겨야할 데이터나 변수를 즉시 실행 함수 내부에 작성한다.<br/>
(외부에서 접근할 수 없기 때문에)
***