# effect, cleanup
작성일시: 2021년 12월 27일 오전 3:41

## useEffect

두 개의 argument를 가지는 function.

첫 번째 argument는 딱 한번만 실행하고 싶은 코드<br/>
두 번째 argument는 array로 변화를 감지할 인자를 작성한다.

```jsx
import { useState } from "react";

function App() {
  const [counter, setValue] = useState(0);
  const [keyword, setKeyword] = useState("");
  const onClick = () => setValue((prev) => prev + 1);
  const onChange = (event) => setKeyword(event.target.value);
  console.log("i run all the time");
  console.log("search for", keyword);
	return (
	    <div>
	      <input value={keyword} onChange={onChange} type="text" placeholder="Search here.." />
	      <h1>{counter}</h1>
	      <button onClick={onClick}>click me</button>
	    </div>
	 );
}
```

위와 같이 작성한 코드는<br/>
브라우저에서 `버튼`을 누르고 `input`에 값을 입력할 때마다 콘솔창에 문자이 실행된다.

이는 **react**가 **state**를 감지하여 state가 변화할 때마다 모든 컴포넌트들을 render하고 있다는 것을 의미한다.

`useEffect()`를 사용하면, state변화가 일어나도 단 한 번만 실행된다.

```jsx
import { useState, useEffect } from "react";

function App() {
  const [counter, setValue] = useState(0);
  const [keyword, setKeyword] = useState("");
  const onClick = () => setValue((prev) => prev + 1);
  const onChange = (event) => setKeyword(event.target.value);
  console.log("i run all the time");
  const iRunOnlyOnce = () => {
     console.log("i run only once.");
   }
  **useEffect(iRunOnlyOnce, []);**
  return (
    <div>
      <input value={keyword} onChange={onChange} type="text" placeholder="Search here.." />
      <h1>{counter}</h1>
      <button onClick={onClick}>click me</button>
    </div>
  );
}
```

useEfeect의 첫 번째 인자로 iRunOnlyOnce라는 함수를 주고, 두 번째 인자는 빈 array를 준다.

브라우저에서 보면 콘솔창에서 처음에만 실행되고,<br/>
버튼을 누르거나해도 다시 실행되지 않는다. 다음과 같이 동일하게 작성할 수 있다.

```jsx
useEffect(() => {
    console.log("I run only once.");
}, []);
```

`keyword`가 변할 때 실행된다.

```jsx
useEffect(() => {
    console.log("I run when 'keyword' changes.");
}, [keyword]);
```

`counter`가 변할 때 실행된다.

```jsx
useEffect(() => {
    console.log("I run when 'counter' changes.");
}, [counter]);
```

`keyword`, `counter`가 변할 때 실행된다.

```jsx
useEffect(() => {
    console.log("I run when keyword & counter changes.")
}, [keyword, counter]);
```

`keyword`가 변할 때 실행되지만 `keyword`의 길이가 5자 이상이어야 한다.

```jsx
useEffect(() => {
  if (keyword !== "" && keyword.length > 5) {
    console.log("search for", keyword);
  }
}, [keyword]);
```

### 전체 코드

```jsx
import { useState, useEffect } from "react";

function App() {
  const [counter, setValue] = useState(0);
  const [keyword, setKeyword] = useState("");
  const onClick = () => setValue((prev) => prev + 1);
  const onChange = (event) => setKeyword(event.target.value);
  console.log("i run all the time");

  useEffect(() => {
     if (keyword !== "" && keyword.length > 5) {
       console.log("search for", keyword);
    }
  }, [keyword]);

  useEffect(() => {
    console.log("I run only once.");
  }, []);

  useEffect(() => {
    console.log("I run when 'keyword' changes.");
  }, [keyword]);

  useEffect(() => {
    console.log("I run when 'counter' changes.");
  }, [counter]);

  useEffect(() => {
    console.log("I run when keyword & counter changes.")
  }, [keyword, counter]);

  return (
    <div>
      <input value={keyword} onChange={onChange} type="text" placeholder="Search here.." />
      <h1>{counter}</h1>
      <button onClick={onClick}>click me</button>
    </div>
  );
}
```

---

## Cleanup function

`useEffect()`에서 **parameter**로 넣은 함수의 **return 함수**

```jsx
import { useState, useEffect } from "react";

function Hello() {
  useEffect(() => {
    console.log("I'm here");
    console.log("Created :)");
    return () => console.log("destroyed :(");
  }, [])
  return <h1>Hello</h1>;
}

function App() {
  const [showing, setShowing] = useState(false);
  const onClick = () => setShowing((prev) => !prev);
  return (
    <div>
      {showing ? <Hello /> : null}
      <button onClick={onClick}>{showing ? "Hide" : "Show"}</button>
    </div>
  );
}

export default App;
```

버튼을 누름에 따라 <u>**showing state**</u>가 변화하고 그에 따라 `<button>`의 내용이 변한다. 그리고 showing이 true일 때 Hello글자가 출력된다.

- 처음 화면 → ‘show’버튼
- 클릭 후 화면 → ‘hide’버튼 + Hello

**“I'm here” / "Created :)"** 문장은 `<Hello />`가 render될 때마다 실행된다.

여기서 `return () ⇒ console.log("destroyed :(");`이 cleanup function 이다.

**"destroyed :("** 문장은 버튼을 눌러서 Hello가 사라질 때 실행되어 콘솔창에 출력된다.

다음과 같이 작성할 수도 있다.

```jsx
function Hello() {
  function destroyedFn() {
    console.log("bye :(");
  }
  function effectFn() {
    console.log("created :)");
    return destroyedFn;
  }
  useEffect(effectFn, []);
	return <h1>Hello</h1>
}
```

```jsx
function Hello() {
	**// () => { }**
	useEffect(() => {
	  console.log("hi :)");
    return () => console.log("bye ;(");
  }, [])

	**// function () { }**
  useEffect(function () {
    console.log("hi :)");
    return function () {
      console.log("hye :(");
    }
  }, [])
	return <h1>Hello</h1>
}
```

---