# 스코프
변수 유효 범위

### 변수
- var     <= 처음부터
- let     <= ES2015+
- const   <= ES2015+

> var
```jsx
var varVal = '함수-단위';
```
var 유효범위는 함수 스코프

> const
```jsx
const constVal = '블럭-단위';
```
<br/>

## 함수 스코프

```jsx
console.log(num);     // 0
// 함수내부에 있는 변수는 밖으로 꺼내다가 쓸 수가 없다.

function test(){
  var num = 123;
  return 'test';
}
```
```jsx
function test(){
  var num = 123;
  return num;
}

console.log(test());    //123
// 함수의 return 결과로 받아야 한다.
```

내부에서 외부로는 접근 가능하지만,<br/>
외부에서 내부로는 접근 불가능하다.
```jsx
var varVal = '함수-단위';

function test(){
  console.log(varVal);    // 함수-단위
  // 내부에서 외부로 접근가능
}
```
파일의 최상단에 어디서든 접근할 수 있는 변수 ==> **전역변수**

```jsx
var globalVal = '전역 변수';

function outerfunc(){
  console.log(globalVal);
  console.log(innerVal);    // innerVal is not defined
  // 외부에 innerVal이 있는지 확인한다.

  function innerfunc(){
    var innerVal = "함수 내부 지역 변수";
    console.log(globalVal);
    // outerfunc에 globalVal이 있는지 확인
    // 없으니까 한번 더 밖으로 나가서 globalvVal이 있는 지 확인
  }
  innerfunc();
}
outerfunc();
```
<br/>

## 블럭 스코프
```jsx
var globalVal = '전역 변수';

for(var index=0; index<[0, 1, 2].length; indes++){}

function outerfunc(){
  console.log(globalVal);     // 전역 번수

  fucntion innerfunc(){
    var innerVal = '함수 내부 지역 변수';
    console.log(index);       // 3
  }
  innterfunc();
}
outerfunc();
```
for문은 함수가 아니다보니까 var라는 index가 선언과 동시에 할당됐고,<Br/>
3번 돌면서 계속 증가를 했다.

innerfunc()에서 index 확인이 가능하다.<Br/>
<u>만약 var 가 아닌 let으로  바꾸면?</u>

```jsx
for(let index=0; index<[0, 1, 2].length; indes++){}

function outerfunc(){
  console.log(globalVal);     // 전역 번수

  fucntion innerfunc(){
    var innerVal = '함수 내부 지역 변수';
    console.log(index);       // index is not defined
  }
  innterfunc();               // index is not defined
}
outerfunc();                  // index is not defined
```
출력되지않는다.<Br/>
**let, const**는 블럭 단위를 가지기 때문이다.

let으로 바꾸면 for문 안에서만 유효범위를 가지기 때문에 접근할 수가 없다.<Br/>
(let, const 사용하는 것 권장)

```jsx
if(true){
  var b = 'b';
  let a = 'a';
}

console.log(b);     // b
console.log(a);     // a is not defined
```

***
- 전역 스코프
- 지역 스코프
    - 함수 스코프
    - 블럭 스코프

## 전역 스코프
바깥쪽에 위치하고, 그 곳에서 선언한 변수는 어디서든 접근이 가능하다.
```jsx
let foo = 'foo';

{
  console.log(foo);     // foo    ////접근가능
}

function func(){
  console.log(foo);     // foo     ////접근가능
}

if(true){
  console.log(foo);     // foo      ////접근가능
}

func();
```
<br/>

어디서나 접근이 가능하기 때문에 어디서나 바뀔 수 있다.
```jsx
let foo = 'foo';

function func(){
  foo = 'foooo'
  console.log(foo);     // foooo    ////접근가능
}

func();
```
프로그램이 실행되는 시정 ==> 런타임 시점<br/>
전역변수를 사용하면, 프로그램의 실행결과 때 만든 변수들이 어떻게 동작했는지 알기가 어렵다.<br/>
=> 전역공간은 사용하기 쉽지만 실행 결과를 예측하기가 어렵다.

전역공간에서 반대로 내부 블럭에는 접근할 수가 없다.

지역스코프 단위로 코드를 작성하는 것이 좋다.<br/>
=> 지역 변수는 사용하기 어렵지만 실행 결과를 예측하기 쉽다.

***

