# Callback (1)

> ### 1. 동기와 비동기
javascript는 동기적이다. => 호이스팅이 된 이후부터 코드 작성 순서대로 동기적으로 실행된다.
- *호이스팅?* var 변수, function 함수 선언들이 자동적으로 제일 위로 올라가는 것

**비동기 - 언제 코드가 실행될 지 예측할 수 없는 것**
예시)
```jsx
console.log("1");
setTimeout(function(){
  console.log("2");
},1000);
console.log("3");

// 1초 뒤 "2"를 출력해라.
```
`setTimeout()`: 지정한 시간이 지나면 callback함수를 실행해라
```
1
3
2
```
<br/>

> ### 2. callback
callback은 항상 비동기일 때만 사용하는가? NO

#### Synchronous callback
```jsx
function printImmediately(print){
  print();
}
printImmediately(()=> console.log('hello'));
```

#### Asynchronous callback
```jsx
function printWithDelay(print, timeout){
  setTimeout(print, timeout);
}
printWithDelay(()=> console.log('async callback'),2000);
```
<br/>

> ### 3. callback chain 문제점
- 가독성이 너무 떨어진다.
- 로직을 한번에 이해할 수 없다.

```jsx
'use strict';

// Callback Hell example
class UserStorage {
  loginUser(id, password, onSuccess, onError) {
    setTimeout(() => {
      if (
        (id === 'ellie' && password === 'dream') ||
        (id === 'coder' && password === 'academy')
      ) {
        onSuccess(id);
      } else {
        onError(new Error('not found'));
      }
    }, 2000);
  }

  getRoles(user, onSuccess, onError) {
    setTimeout(() => {
      if (user === 'ellie') {
        onSuccess({ name: 'ellie', role: 'admin' });
      } else {
        onError(new Error('no access'));
      }
    }, 1000);
  }
}

const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your passrod');
userStorage.loginUser(
  id,
  password,
  user => {
    userStorage.getRoles(
      user,
      userWithRole => {
        alert(
          `Hello ${userWithRole.name}, you have a ${userWithRole.role} role`
        );
      },
      error => {
        console.log(error);
      }
    );
  },
  error => {
    console.log(error);
  }
);
```