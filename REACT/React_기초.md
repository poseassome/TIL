# React 기초
작성일시: 2021년 12월 21일 오전 12:14

# React란

사용자 인터페이스를 구축하기 위한 선언적이고 효율적이며 유연한 JavaScript 라이브러리

“컴포넌트”라고 불리는 작고 고립된 코드의 파편을 이용하여 복잡한 UI를 구성한다.

---

## 실습 코드 작성

버튼을 클릭하면 counting이 되는 `html`문서 작성

```html
<!DOCTYPE html>
<html>

<body>
  <span>Total clicks: 0</span>
  <button id="btn">Click me</button>
</body>
<script>
  let counter = 0;
  const button = document.getElementById("btn");
  const span = document.querySelector("span");
  function handleClick() {
    counter = counter + 1;
    span.innerText = `Total clicks: ${counter}`;
  }
  button.addEventListener("click", handleClick);
</script>

</html>
```

현재 코드는 `body`에 출력되는 요소를 작성하고, `id`값을 사용하여 `script`에서 요소를 선택하고, `function`을 사용하여 `event`를 부여하고 있다.

React를 사용하여 코드를 수정해 나간다.

---

## React 사용(1)

react를 사용하기 위해 소스를 import한다.

1. **React**

    애플리케이션이 interactive하도록 만들어 주는 라이브러리

    `<script src="[https://unpkg.com/react@17.0.2/umd/react.production.min.js](https://unpkg.com/react@17.0.2/umd/react.production.min.js)"></script>`

2. **React DOM**

    모든 react element들을 HTML body에 둘 수 있게함

    `<script src="[https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js](https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js)"></script>`


### 1. <span> 출력하기

`<body>`내부는 비운 채 `<script>`안에서 코드를 작성한다.

- **React.createElement( element, { property:  value }, content );**
- **render(무엇을, 어디에 둘 것 인지)**
: react element를 HTML로 만들어 배치한다.

```html
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>

<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script>
  const root = document.getElementById("root");
  const span = React.createElement("span", { id: "sexy-span" }, "Hello I'm a span");

  ReactDOM.render(span, root);
</script>

</html>
```

### 2. <span>, <button> 출력하기

`<button>`도 React.createElement()를 사용하여 생성한다.

두 개의 요소를 같이 출력하기 위해 하나의 `<div>`로 묶는다.

```html
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>

<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script>
  const root = document.getElementById("root");
  const span = React.createElement("span", { id: "sexy-span" }, "Hello I'm a span");
	const btn = React.createElement("button", { onClick: () => console.log('im click'), style: { backgroundColor: "tomato" }, }, "Click me");
	const container = React.createElement("div", null, [h3, btn]);

  ReactDOM.render(container, root);
</script>

</html>
```

이 때, `<button>`에는 `onClick 이벤트`를 부여하여 함수를 실행한다.

---

## React 사용(2)

실제로 React.createElement()를 잘 사용하지 않는다.

**JSX**를 사용하여 코드를 작성한다.

1. **JSX**

    자바스크립트를 확장한 문법

    JSX는 브라우저가 이해하지 못함
    —> React.createElement()처리 필요
    —> **Babel**(코드 변환해주는 역할) 사용

2. **Babel**

    JSX로 생성한 코드를 브라우저가 이해가능한 형태로 바꿈

    `<sciprt type="text/babel">` 스크립트 타입 지정해줘야함.

    이것도 사용하기 위해 소스를 불러와야 한다.
    (여기서는 URL로 불러오지만 이런 방식은 느려서 사용하진 않는다.)


```html
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>

<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script>
  const root = document.getElementById("root");
  const Title = (
    <h3 id="title"
      onMouseEnter={() => console.log("mouse enter")}
    >
      Hello I'm a title
    </h3>);
	const Button = (
    <button
      style={{ backgroundColor: "tomato" }}
      onClick={() => console.log('im click')}
    >
      click me
    </button>);
  const container = React.createElement("div", null, [Title, Button]);</script>

	ReactDOM.render(container, root);
</script>

</html>
```

Babel이 위 코드를 브라우저가 읽을 수 있게 React.createElement() 처리 한다.

---

## React 사용(3)

React.createElement를 사용한 container부분도 수정한다.

container는 Title과 Button을 담아야 한다. 그러나

```jsx
*const Container = <div>Title Button</div>*
```

이렇게 작성하면 텍스트로 인지하고, 변수로 인식을 못한다.

그러므로 만든 변수를 함수로 만들어 가져온다.

1. **Allow function**

    funtion example(){ } 와 동일 / 함수로 만들어서 return하는 것

    `() =>` 붙이면 됨
    const example = () => (<h3 ~~>)

    ```jsx
    /* 둘은 동일한 의미이다. */

    const Title = () => (
        <h3 id="title"
          onMouseEnter={() => console.log("mouse enter")}
        >
          Hello I'm a title
        </h3>);

    function Title() {
      return (
        <h3 id="title"
          onMouseEnter={() => console.log("mouse enter")}
        >
          Hello I'm a title
        </h3>);
    }
    ```

2. **컴포넌트**

    text로 붙여넣은 부분을 요소처럼 작성하여 컴포넌트들을 합친다.
    Title ---> <Title />

    <aside>
    💡 **!! 컴포넌트의 첫 글지는 무조건 대문자 !!**
    소문자면 React와 JSX는 HTML 태그로 인식함

    </aside>


```html
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>

<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script>
	const root = document.getElementById("root");
  const Title = () => (
    <h3 id="title"
      onMouseEnter={() => console.log("mouse enter")}
    >
      Hello I'm a title
    </h3>);
	const Button = () => (
    <button
      style={{ backgroundColor: "tomato" }}
      onClick={() => console.log('im click')}
    >
      click me
    </button>);
	const Container = () => (<div><Title /><Button /></div>);
	ReactDOM.render(<Container />, root);
</script>

</html>
```

---