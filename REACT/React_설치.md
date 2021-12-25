# React 설치
작성일시: 2021년 12월 25일 오후 7:23

# React 설치

node.js를 다운받고 설치가 이루어졌는지 버전을 확인한다.

```
node.js -v
npm -v
npx -v
```

npx로 react을 설치한다.

```
npx create-react-app 폴더명
```

필요한 폴더 및 파일들이 지정한 폴더명으로 만들어지고,
실행하려면 해당 폴더로 이동한 뒤 npm start를 입력한다.

```
cd 폴더명
npm start
```

PropTypes를 설치한다.

```
npm i prop-types

사용할 때는
import PropTypes from "prop-types";
```

---

## 기본 구조 설정

📁src에서 필요한 파일들을 생성한다.

우선 App.js와 index.js 만을 남기고 나머지 파일들은 삭제한다.<br/>
**index.js**를 보면
`import App from ‘./App’` 으로 App.js을 사용하고 있다.

### index.js

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

**App.js** 에 button을 넣을 건데, Button.js를 생성해서 컴포넌트로 불러오도록 한다.

### **Button.js**

```jsx
import PropTypes from "prop-types";
import styles from "./Button.module.css";

function Button({ text }) {
  return <button className={styles.btn}>{text}</button>;
};

Button.propTypes = {
  text: PropTypes.string.isRequired,
}

// App.js에서 Button을 가져오고 싶으니까.
export default Button;
```

style을 적용할 수도 있는데,<br/>
styles.css(button 스타일 작성)를 만들어서 **index.js**에 import하면 해당 문서의 모든 `<button>`에 그 스타일을 적용하게 된다.

특정 요소에만 적용하기 위해 **Button.module.css**파일을 생성하고
그 안에 class를 사용하여 스타일을 지정한다.

```css
.btn {
  color: white; background-color: tomato;
}
```

그리고 이를 **Button.js**에
`import styles from “./Button.module.css”;` 로 적용시킨다.

`<button>`에는 className={styles.btn}을 주고 브라우저에서 확인하면
react가 임의로 클래스명을 준 것을 확인할 수 있다.

**⇒ 클래스명이 충돌하는 것을 방지해준다.**

### App.js

Button.js에 적용한 것과 똑같이 작성한다.

```jsx
import Button from "./Button";
import styles from "./App.module.css";

function App() {
  return (
    <div>
      <h1 className={styles.title}>Welcome back!</h1>
      <Button text={"Continue"} />
    </div>
  );
}

export default App;
```

App.module.css는 다음과 같다.

```css
.title{
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  font-size: 18px;
}
```

---