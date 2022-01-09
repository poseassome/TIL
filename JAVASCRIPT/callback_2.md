# Callback (2)

> ## 1. Promise
자바스크립트안에 내장된 비동기를 간편하게 처리할 수 있도록 도와주는 오브젝트<br/>
(콜백함수 대신 사용)

정해진 장시간의 기능을 수행하고서<br/>
정상적으로 기능이 수행됐다면 성공 메세지와 함께 처리된 결과값을 전달해준다.<br/>
문제가 발생했다면 에러를 전달해준다.

- **state**<br/>
process가 무거운 operation을 수행하고 있는 중인지/ 기능 수행이 완료되어서 성공했는지, 실패했는지

- **Producer와 Consumer의 차이점**<br/>
우리가 원하는 데이터를 제공하는 사람과 제공된 데이터를 사용하는 사람

- ### state
    - #### pendding
    promise가 만들어져서 지정한 operation이 수행중인 상태
    - #### fulfilled
    operation이 성공적으로 끝났을 때의 상태
    - #### rejected
    파일을 찾을 수 없거나 네트워크에 문제가 생겼을 때의 상태

- ### Producer vs Counsumere
    - #### Producer
    : 우리가 원하는 기능을 수행해서 해당하는 데이터를 만들어냄
    - #### Consumer
    : 원하는 데이터를 소비함
<br/>
<br/>

> ## 2. Producer (Promise 생성)
Promise는 클래스이기 때문에 `new`를 사용하여 오브젝트를 생성한다.
```jsx
const promise = new Promise( executor( resolve, reject ) );
const promise = new Promise(( resolve, reject )=>{
    /* 네트워크에서 데이터를 받아오거나 파일에서 큰 데이터를
    읽어오거나 하는 과정이 시간이 걸리기때문에 동기적으로 처리하면
    다음 코드가 실행되지 않기 때문에 이처럼 비동기적으로 실행한다. */
});
```
`executor()` : 콜백함수<br/>
이 콜백함수 안에서도 2가지의 콜백함수가 있다.
  - `resolve` : 정상적으로 수행해서 마지막에 최종 데이터를 전달하는 함수
  - `reject` : 기능을 수행하다가 중간에 문제가 생기면 호출할 함수

promise를 만드는 순간 executor 콜백함수가 바로 실행이 된다.<br/>
=> 만약 promise안에 network통신을 하는 함수를 작성했다면 바로 network 통신을 수행하게 된다.

```jsx
const promise = new Promise(( resolve, reject )=>{
  setTimeout(()=>{
    resolve('success');     // 기능이 정상적으로 수행했을 시
  }, 2000);
});
```
<br/>
<br/>

> ## 3. Consumers
then, catch, finally를 사용하여 값을 받아올 수 있다.
```jsx
promise.then(( value )=>{
  console.log(value);
})
// value는 promise 정상실행 후 resolve 콜백함수를 통해 전달받은 값
```
promise를 잘 수행하면 value를 받아와서 원하는 기능을 수행하는 콜백함수를 전달해준다.

reject는 보통 Error라는 오브젝트를 통해서 값을 전달한다.
```jsx
const promise = new Promise((resolve, reject)=>{
  setTimeout(()=>{
    resolve('success');
    reject(new Error('no network'));
  }, 2000);
})
```
Error에는 어떤 error가 발생했는지 이유를 명시해서 작성한다.<br/>
error handling은 catch를 사용해서 error가 발생했을 때 어떻게 처리할 건지 콜백함수를 작성해주면 된다.
```jsx
promise
  .then((value)=>{
    console.log(value);
  })
  .catch((error)=>{
    console.log(error);
  })
```
promise에 then을 호출하면 promise를 return하고 return된 promise의 catch를 호출할 수 있는 것이다. ==> chain

finally는 성공, 실패 관계없이 마지막에 무조건 호출되는 함수이다.
<br/>
<br/>

> ## 4. Promise chaining
```jsx
const fetchNumber = new Promise((resolve, reject) => {
  setTimeout(() => resolve(1), 1000);
});
// 1초 후 숫자 1을 전달한다.

fetchNumber
  .then(num=>num*2)     // 1 전달받음
  .then(num=>num*3)     // 2 전달받음
  .then(num=>{          // 6 전달받음
    return new Promise((resolve, reject) =>{
      setTimeout(() => resolve(num-1), 1000);
    });
  })
  .then(num => console.log(num));     // 5 전달받음 (실행시간은 총 2초)
```
<br/>
<br/>

> ## 5. Error handling
```jsx
const getHen = () =>
  new Promise((resolve, reject)=>{
    setTimeout(() => resolve('🐓'), 1000);
  });
const getEgg = hen =>
  new Promise((resolve, reject) => {
    setTimeout(() => resolve(`${hen} => 🥚`), 1000);
  });
const cook = egg =>
  new Promise((resolve, reject) => {
    setTimeout(() => resolve(`${egg} => 🍳`), 1000);
  });

getHen()    // 닭을 받아오고
  .then(hen => getEgg(hen))     // getEgg() 함수 실행
  .then(egg => cook(egg))       // cook() 함수 실행
  .then(meal => console.log(meal));     // 요리된 문자열 출력 (총 실행시간 3초)

/* 실행결과
🐓 => 🥚 => 🍳
*/
```
then을 사용하여 value를 전달하고 함수를 실행하는 코드를 좀 더 간단하게 작성할 수도 있다.<br/>
value 한 가지만 받아서 그대로 전달하는 경우 생략이 가능하다.
```jsx
getHen().then(getEgg).then(cook).then(console.log);
// formatter로 한줄로 작성되는데 이는 가독성이 좋지 않다.

getHen() //
.then(getEgg)
.then(cook)
.then(console.log);
```
<Br/>

만약 error가 발생했다면,
```jsx
const getHen = () =>
  new Promise((resolve, reject)=>{
    setTimeout(() => resolve('🐓'), 1000);
  });
const getEgg = hen =>
  new Promise((resolve, reject) => {
    setTimeout(() => reject(new Error(`error! ${hen} => 🥚`)), 1000);
  });
const cook = egg =>
  new Promise((resolve, reject) => {
    setTimeout(() => resolve(`${egg} => 🍳`), 1000);
  });

getHen() //
  .then(getEgg)
  .then(cook)
  .then(console.log)
  .catch(console.log);

/* 실행결과
Error: error!🐓 => 🥚
*/
```

error가 발생해도 정상적으로 모든 코드를 실행시키고 싶다면,
```jsx
getHen() //
  .then(getEgg)
  .catch(error => {     // egg를 받아올 때 문제가 생긴다면 다른 value를 전달한다.
    return '🍞';
  })
  .then(cook)
  .then(console.log)
  .catch(console.log);

 /* 실행결과
🍞 => 🥚
*/
```
<br/>
<br/>

> ## 6. callback example
```jsx
'use strict';

class UserStorage {
  loginUser(id, password) {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        if (
          (id === 'ellie' && password === 'dream') ||
          (id === 'coder' && password === 'academy')
        ) {
          resolve(id);
        } else {
          reject(new Error('not found'));
        }
      }, 2000);
    });
  }

  getRoles(user) {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        if (user === 'ellie') {
          resolve({ name: 'ellie', role: 'admin' });
        } else {
          reject(new Error('no access'));
        }
      }, 1000);
    })
  }
}

const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your passrod');
userStorage.loginUser(id, password)
  .then(userStorage.getRoles)
  .then(user => alert(`Hello ${user.name}, you have a ${user.role} role`))      // 사용자의 역할을 잘 받아온다면
  .catch(console.log);
```