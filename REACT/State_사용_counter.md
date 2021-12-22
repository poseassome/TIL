# state 사용
작성일시: 2021년 12월 21일 오후 11:47

# state란

기본적으로 데이터가 저장되는 곳이다.

이전 실습 코드에서 **counter**를 구현하기 위해 필요하다.

---

## 실습코드

이전 작성한 코드에서 함수처리한 변수를 지우고
안의 내용을 `Container`의 `<div>`안으로 옮긴다.

```html
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>
<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  const root = document.getElementById("root");
  const Container = () => (
    <div>
      <h3>Total clicks: 0</h3>
      <button>click me</button>
    </div>
  );
  ReactDOM.render(<Container />, root);
</script>

</html>
```

### counter

1. count가 될 숫자를 변수로 지정한다.

    `let counter = 0;`

    변수를 사용하려면 필요한 자리에 {변수}를 작성한다.

    ```html
    <div>
      <h3>Total clicks: {counter}</h3>
      <button>click me</button>
    </div>
    ```


1. 클릭 시 실행시킬 함수를 작성한다.
`<button>`에 `onclick` 이벤트를 준다.

    ```html
    <!DOCTYPE html>
    <html>

    <body>
      <div id="root"></div>
    </body>
    <script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
      const root = document.getElementById("root");
      let counter = 0;
      function countUp() {
        counter = counter + 1;
      };
        const Container = () => (
          <div>
            <h3>Total clicks: {counter}</h3>
            <button onClick={countUp}>click me</button>
          </div>
        );
      ReactDOM.render(<Container />, root);
    </script>

    </html>
    ```


하지만 이를 실행 하면 count 숫자가 올라가지 않고 0인 상태이다.

- 코드는 순서대로 실행되는데 지금 함수(`countUp`)는 바로 실행안되고 불러야 실행된다.
그럼 당장에 실행되고 있는건 ReactDOM.render() 이다.

    container를 렌더링하고 root에 담는데,
    렌더링한 container는 counter 값을 0으로 가진다.
    => 이제 막 페이지가 로드됐으니까.
    ==> **★어디에도 UI를 새로고침 해주는 코드가 없음**


counter가 증가할 때마다 rerendering을 해줘야 한다.

---

## Rerendering

1. Container 변수를 App으로 바꾸고 작성방식도 `function`으로 바꾼다.
2. counter +1 실행 후 rerendering되도록
ReactDOM.render(<App />, root); 를 추가한다.
3. 여러 번 사용한다면 `function`으로 만들어서 코드를 실행시킨다.

```html
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>
<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  const root = document.getElementById("root");
  let counter = 0;
  function countUp() {
    counter = counter + 1;
    render();
  };
  function render() {
    ReactDOM.render(<App />, root);
  };
  function App() {
    return (
      <div>
        <h3>Total clicks: {counter}</h3>
        <button onClick={countUp}>click me</button>
      </div>
    );
  };
  render();
</script>

</html>
```

기존 HTML 작성 코드에서는 countUp할 때마다 크롬에서 요소의 모든 부분이 업데이트 됐는데, React는 변화하는 UI만을 업데이트 한다.

하지만 이 방법은 rerendering과정을 계속 추가해야 하는 단점이 있다.

---

## State

state에 값을 저장해서 코드를 작성한다.

이전에 작성한

`let counter = 0;`
`function countUp() {   };` 는

`const data = React.useState(0);` 로 작성될 수 있다.

### React.useState()

console.log(data)를 출력하면 Array *[undefined, f]* 가 생성된 걸 확인할 수 있다.

배열의 첫 번째 값은 초기값이고, 두 번째 값은 그 값을 바꾸는 함수(modifier)이다.

React.useState()의 괄호 안에 값을 작성하여 초기값을 변경 할 수 있다.

배열 안에 값은 index를 사용하여 불러 올 수도 있지만 아래 예시처럼 사용할 수도 있다.

```
만약
const food = ["tomato", "potato]
const [myfood1, myfood2] = food;
라고 하면 myfood1은 "tomato"를 출력하고 myfood2는 "potato"를 출력할거다.
```

```html
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>
<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  const root = document.getElementById("root");
  function App() {
    // const data = React.useState(0);
    // const [counter, modifier] = React.useState(0);
    const [counter, setCounter] = React.useState(0);
    const onClick = () => {
      setCounter(counter + 1);
		}
    return (
      <div>
        <h3>Total clicks: {counter}</h3>
        <button onClick={onClick}>click me</button>
      </div>
    );
  };
  ReactDOM.render(<App />, root);
</script>

</html>
```

Rerendering 코드가 없어도 react가 알아서 UI를 변화시킨다.
⇒ **modifier**가 필요한 이유

### Modifier 설정

1. 직접 값 설정하기
2. 함수 전달하기

지금 코드는 현재 값에 +1을 해서 사용하고 있는데, 더 안전한 작성법이 있다.

`setCounter()` 괄호 안에 `function`을 사용한다.

- 함수의 첫 번째 argument는 현재 값
- 함수의 return값이 새로운 state가 되도록 한다.

이는 예상 못한 업데이트가 일어났다해도 혼동 주는 것을 방지해준다.

```html
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>
<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  const root = document.getElementById("root");
  function App() {
    const [counter, setCounter] = React.useState(0);
    const onClick = () => {
      setCounter((current) => current + 1);
    }
    return (
      <div>
        <h3>Total clicks: {counter}</h3>
        <button onClick={onClick}>click me</button>
      </div>
    );
  };
  ReactDOM.render(<App />, root);
</script>

</html>
```

---