# Redux 사용하는 이유?
- `props` 문법 대신 사용
- `state` 변경 관리할 때

## props 대신 사용

```
# React 웹 개발

index.html 
  ∟ 배경 component
     ∟ 메뉴 component
        ∟ 글자 component
```

만약 배경 component에서 `state` 라는 변수를 만들었을 때, 이건 다른 component에서는 사용을 못한다. <br/>
=> 하위 component에 `props`로 전달해야 한다.

그러나, component가 너무 많으면 `props 문법`을 많이 사용해야하는 문제가 발생한다.

> 이럴 때 `redux`를 설치해서 사용한다.

### Redux 사용하면
`store.js`를 생성하여 `state`를 보관한다.<br/>
그러면 `props`없이 모든 component에서 사용할 수 있다.

```jsx
// index.js

import { Provider } from 'react-redux';
import { createStore } from 'redux';

const 체중 = 100;

function reducer(state = 체중, action) {
  return state;
}

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>
  document.getElementById('root')
)
```
```jsx
// App.js

import './App.css';
import { useSelector } from 'react-redux';

function App() {
  const 꺼내온거 = useSelector( (state) => state );

  return (
    <div className="App">
      <p>몸무게 : {꺼내온거}</p>
    </div>
  )
}
```

## state 관리
component에서 `store.js`에 저장된 `state`를 사용하면서 각 `state`값을 변경한다면?

### state 수정방법
`store.js`에 저장된 `state`에 대해 미리 수정 방법을 정의해둔다.<br/>
component는 `state`에 대해 수정 요청만 가능하다.

=> 추적에 용이하다.

```jsx
// index.js

import { Provider } from 'react-redux';
import { createStore } from 'redux';

const 체중 = 100;

function reducer(state = 체중, action) {
  // 수정 방법 정의
  if (action.type === '증가') {
    state++;
    return state;
  } else if (action.type === '감소') {
    state--;
    return state;
  } else {
    return state;
  }
}

let store = createStore(reducer);

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>
  document.getElementById('root')
)
```
```jsx
// App.js

import './App.css';
import { useSelector, useDispatch } from 'react-redux';

function App() {
  const 꺼내온거 = useSelector( (state) => state );
  // component에서 state 수정 요청 --> dispatch
  const dispatch = useDispatch();

  return (
    <div className="App">
      <p>몸무게 : {꺼내온거}</p>
      <button onClick={()=>{ dispatch({type : '증가'}) }}>더하기</button>
    </div>
  )
}
```