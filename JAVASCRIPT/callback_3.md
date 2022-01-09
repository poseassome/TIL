# Callback (3)

> ## 1. async
promise chain을 좀 더 간단하고 동기적으로 보이도록 만들어준다.<br/>
함수 앞에 async를 작성한다.<br/>
--> 자동적으로 함수안의 코드블럭들이 promise로 변환된다.
```jsx
async function fetchUser() {
  // do network request in 10 secs ...
  return 'ellie';
}

const user = fetchUser();
user.then(console.log);
```
<br/>
<br/>

> ## 2. await
await는 async가 붙은 funcntion 안에서만 사용 가능하다.
```jsx
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}
async function getApple() {
  await delay(3000);    // delay가 끝날 때까지 기다린다.
  return '🍎';
}
async function get Banana() {
  await delay(3000);
  return '🍌';
}

function pickFruits() {
  return getApple().then(apple => {
    return getBanana().then(banana => `${apple} + ${banana}`);
  });
}
pickFruits().then(console.log);
/* 실행결과
🍎 + 🍌
*/
```

`pickFruits()`를 async·await를 사용해서 작성한다.
```jsx
async function pickFruits() {
  const apple = await getApple();
  const banana = await getBanana();     // 사과와 바나나를 다 받아올 때까지 기다린다.
  return `${apple} + ${banana}`;
}
pickFruits().then(console.log);
/* 실행결과
🍎 + 🍌
*/
```
위 코드는 apple과 banana를 따로 기다리고 있다. --> 비효율적<br/>
await를 병렬처리해준다.
```jsx
async function pickFruits() {
  const applePromise = getApple();     // promise를 만들자마자 함수 실행
  const bananaPromise = getBanana();   // promise를 만들자마자 함수 실행
  const apple = await applePromise;
  const banana = await bananaPromise;
  return `${apple} + ${banana}`;
}
pickFruits().then(console.log);
```
<br/>
<br/>

> ## 3. Promise APIs
`Promise.all()` Promise배열을 전달하게 되면 모든 Promise를 병렬적으로 다 받을 때까지 모아준다.
```jsx
function pickAllFruits() {
  return Promise.all([getApple(), getBanana()])
  .then(fruits => fruits.join(' + '));
}
pickAllFruits().then(console.log);
```

`Promise.race()` 가장 먼저 return되는 값을 출력한다.
```jsx
function pickOnluOne() {
  return Promise.race([getApple(), getBanana()]);
}
pickOnlyONe().then(console.log);
```
<br/>
<br/>

> ## 4. callback example
```jsx
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

  async getUserWithRole(user, password) {
    const id = await this.loginUser(user, password);
    const role = await this.getRoles(id);
    return role;
  }
}

const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your passrod');
userStorage
  .getUserWithRole(id, password) //
  .catch(console.log)
  .then(console.log);
```