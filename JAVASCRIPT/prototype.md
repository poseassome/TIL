# 프로토타입

자바스크립트는 프로토타입 기반 언어이다.

### constructor (생성자)

```jsx
function Person(name, age){
  this.name=name;
  this.age=age;
}
```
```jsx
const jang = new Person('jang', 99);
const hs = new Person('hs', 99);

jang.constructor.name;    // Person
hs.constructor.name;    // Person
/* 생성자 함수를 가리키고 있다. */
```
<br/>
<br/>

```jsx
const obj = {};
const arr = [];
const func =function () {};
const str = new String('str');

obj.constructor.name    // object
arr.constructor.name    // array
func.constructor.name   // function
str.constructor.name    // string
```
만드는 모든 값들이 프로토타입을 내부적으로 가지고 있고,<br/>
프로토타입을 통해서 어떤 생성자로부터 생성됐는지 유추할 수 있다.

비유를 하자면 부모의 유전자를 물려받는다.<br/>
(array에 sort()를 추가한적 없는데 사용 할 수 있듯이)

prototype을 사용하여 속성을 추가하면 부모에만 추가가 된다.

`instanceof`로도 확인 가능하다.
```jsx
obj instanceof Object;     // true
```
<br/>
<br/>

### `__proto__`

브라우저에서 비표준으로 제공.<br/>
`__proto__`를 사용해 프로토타입에 접근할 수 있다.

사용하지 않는 것을 추천한다.

`Object.getPrototypeOf` 이나 `Object.setPrototypeOf` 사용
