# 호이스팅 (hoist)

```jsx
function foo(){
  console.log(hoist);       // undefined  ////오류가 생기지 않음
  var hoist  = '호이스팅';
  console.log(hoist);       // 호이스팅
}

foo();
```
변수 선언을 끌어 올린다.

다음과 같다.
```jsx
function foo(){
  /* 1) 변수 선언 끌어올림 */
  var hoist
  /* 2) 호이스트 호출 */
  console.log(hoist);          // undefined
  /* 3) 변수 할당 */
  hoist = '호이스팅';         // 호이스팅
  /* 4) 할당된 상태로 실행 */
  console.log(hoist);         // 호이스팅
}

foo();
```
`var`를 사용하지 않는 것으로 방지할 수 있다.

`let`을 사용하면,
```jsx
function foo(){
  console.log(hoist);           // ERROR, cannot access 'hoist' before initialization
  let hoist = '호이스팅';
  console.log(hoist);
}

foo();                          // ERROR, cannot access 'hoist' before initialization
```
내부적으로는 호이스팅되었지만 사용자한테는 그러지 않은 것처럼 보인다.

let으로 선언된 변수는 스코프 시작에서 변수의 선언까지<br/>
일시적 사각지대(Temporal Dead Zonel TDZ)에 빠지기 때문이다.

- `var`는 변수 선언과 함께 undefined로 초기화되어 메모리에 저장된다.
- `let`, `const`는 초기화되지않은 상태로 선언만 메모리에 저장된다. --> ERROR<br/>
  초기화되지않으면 변수를 참조할 수 없다.

### 변수 생성 단계
1. 선언 단계
    - 변수를 실행 컨텍스트의 변수 객체에 등록한다.
    - 이 변수 객체는 스코프가 참조하는 대상이 된다.
2. 초기화 단계
    - 변수 객체에 등록된 변수를 위한 공간을 메모리에 확보한다.
    - 변수는 undefined로 초기화된다.
3. 할당 단계
    - undefined로 초기화된 변수에 실제 값을 할당한다.
    <br/>
    <br/>

- `let` 키워드로 선언된 변수는 선언 단계와 초기화 단계가 분리되어 진행된다.<br/>
  즉, 스코프에 변수를 등록(**선언 단계**)하지만<br/>
  **초기화 단계**는 변수 선언문에 도달했을 때(코드 실행 후) 이뤄진다.<br/>

  ***초기화 이전에 변수에 접근***하려고 하면 참조 에러가 발생한다.
- 따라서 스코프의 시작 지점부터 초기화 시작 지점까지는 변수를 참조할 수 없다.<br/>
  스코프의 시작 지점부터 초기화 시작 지점까지의 구간을 ‘일시적 사각지대(Temporal Dead Zone; TDZ)’라고 한다.
***