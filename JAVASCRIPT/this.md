# this

1. 스코프와도 관련이 있다.
2. 자바스크립트에는 객체가 함수, 배열, 일반적인 객체가 있다. 객체에도 영향을 준다.

코드를 작성할 때의 시점과 실행될 때 시점에서 차이가 생길 수 있다.

### 암시적 바인딩

- 전역공간에서의 this => window
- 함수에서의 this => window (전역공간을 가리킨다.)
- 메소드에서의 this => 호출되는 대상의 객체

### 명시적 바인딩

this가 예상치 못하게 동작하기때문에 이를 좀더 바라보기 쉽도록 해준다.<Br/>
함수에 내장된 메소드를 이용한다.

```jsx
const person = {
  name: "현식",
  sayName: function(){
    return this.name + '입니다.';
  },
};

const zero = {
  name: "베이스",
  sayName: function(){
    return this.name + '입니다.';
  },
};

function sayFullName(firstName){
  return firstName + this.sayName()
}
```
- #### call
sayFullName을 호출하기 전에 call() 메소드를 부른다.
```jsx
const result = sayFullName.call(person, '장');
```
첫 번째 인자 : 명시적으로 조작하고 싶은 this의 대상을 넣는다.<br/>
두 번재 인자 : 원본함수(sayFullName())가 갖는 인자를 넣는다.

- #### apply
배열을 인자로 받을 수 있다.
```jsx
const result = sayFullName.apply(person, ['장', 'Jand']);
```
인덱스 번호로 호출이 가능하다.

- #### bind
묶어 놓는다.
```jsx
const sayFullNamePerson = sayFullName.bind(person);
const sayFullNameZero = sayFullName.bind(zero);

console.log(sayFullNamePerson('장'));
console.log(sayFullNameZero('제로'));
```
this를 고정시켜서 사용할 수 있다.
***