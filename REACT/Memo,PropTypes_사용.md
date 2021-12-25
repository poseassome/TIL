# Memo, PropTypes
작성일시: 2021년 12월 25일 오후 4:38

## React.memo()

React는 먼저 컴포넌트를 렌더링(rendering) 한 뒤,<br/> 이전 렌더된 결과와 비교하여 DOM 업데이트를 결정한다.

만약 렌더 결과가 이전과 다르다면, React는 DOM을 업데이트한다.

---

이전 작성한 `<Btn />`에 Props를 `text={value}`로 작성하고,<br/>
`const [value, setValue] = React.useState(”Save Changes”);`<br/>
`const changeValue = () ⇒ setValue(”Revert Changes”);`
을 작성한다.

`<button>`을 클릭하면 내용이 바뀌도록 할 것이다.

**onClick**을 사용하는데,<br/>
만약 function Btn 안에 return `<button>` 안에 onClick을 넣으면 이벤트리스너지만<br/>
내가 만든 컴포넌트에 `<Btn />`안에 onClick을 넣은것은 이벤트리스너가 아닌 Props 이다. 단지 Props의 이름이다.

`onClick = {changeValue}`를 내부에 작성하고 해당 Prop을 function Btn에 전달해준다.<br/>
이 때, return `<button>`에 작성하는 **onClick**은 이벤트리스너이며,
onClick={onClick}이 된다.

```jsx
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>
<script src="https://unpkg.com/react@17.0.2/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  function Btn({ text, changeValue }) {
    return <button
      onClick={changeValue}
      style={{
        backgroundColor: "tomato",
        color: "white", padding: "10px 20px",
        border: 0, borderRadius: 10,
      }}>{text}</button >;
  }
  function App() {
    const [value, setValue] = React.useState("Save Changes");
    const changeValue = () => setValue("Revert Changes");
    return (
      <div>
        <Btn text={value} changeValue={changeValue} />
      </div>
    );
  };
  const root = document.getElementById("root");
  ReactDOM.render(<App />, root);
</script>

</html>
```

---

`<Btn text=”Continue”  />`을 하나 더 추가하고,<br/>
console.log(text, “was rendered”);로 rerender되는 것을 확인한다.

첫 번째 버튼은 text가 변화하여 다른 문장이 출력되지만,<br/>
두 번째 버튼은 변화없이 동일한 문장이 출력된다.

이는 전부다 rerender되기 때문인데, 두 번째 버튼의 경우 rerender가 필요없다.

<u>React.memo()</u>를 사용해서 그걸 방지한다.

```jsx
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>
<script src="https://unpkg.com/react@17.0.2/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  function Btn({ text, changeValue }) {
    console.log(text, "was rendered");
    return <button
      onClick={changeValue}
      style={{
        backgroundColor: "tomato",
        color: "white", padding: "10px 20px",
        border: 0, borderRadius: 10,
      }}>{text}</button >;
  }
  const MemorizedBtn = React.memo(Btn);
  function App() {
    const [value, setValue] = React.useState("Save Changes");
    const changeValue = () => setValue("Revert Changes");
    return (
      <div>
        {/* <Btn text={value} changeValue={changeValue} /> */}
        {/* <Btn text="Continue" /> */}
        <MemorizedBtn text={value} changeValue={changeValue} />
        <MemorizedBtn text="Continue" />
      </div>
    );
  };
  const root = document.getElementById("root");
  ReactDOM.render(<App />, root);
</script>

</html>
```

`const MemorizedBtn = React.memo(Btn);` 를 작성하고<br/>
컴포넌트 이름도 `MomorizedBtn`으로 변경한다.

다시 브라우저를 확인하면 text가 변화한 첫 번째 버튼만 rerender되는 것을 확인할 수 있다.

---

## Prop Types

부모로부터 전달받은 prop의 데이터 type을 검사한다. 자식 컴포넌트에서 명시해 놓은 데이터 타입과 부모로부터 넘겨받은 데이터 타입이 일치하지 않으면 콘솔에 에러 경고문이 띄워진다.

패키지가 있으며 이를 script src로 연결시켜준다.

연결 후 콘솔창에 PropTypes를 입력하면 types를 확인할 수 있다.

만약,<br/>
`<Btn text=”Save Changes” fontSize={18}  />`<br/>
`<Btn text={14} fontSize={”Continue”}  />`<br/>
라고 작성하고 Props를 검사한다면 다음과 같다.

```jsx
Btn.propTypes = {
	text: PropTypes.string,
	fontSize: PropTypes.number,
}
```

브라우저 콘솔창을 보면 에러가 난 것을 확인할 수 있다.

그리고 isRequired를 붙이면 필수 요소가 되기 때문에,<br/>
해당 prop을 가지고 있지않으면 에러가 발생한다.

```jsx
<!DOCTYPE html>
<html>

<body>
  <div id="root"></div>
</body>
<script src="https://unpkg.com/react@17.0.2/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/prop-types@15.7.2/prop-types.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  function Btn({ text, fontSize = 30 }) {
    return <button
      style={{
        backgroundColor: "tomato",
        color: "white", padding: "10px 20px",
        border: 0, borderRadius: 10,
        fontSize,
      }}>{text}</button >;
  }
  Btn.propTypes = {
    text: PropTypes.string.isRequired,
    fontSize: PropTypes.number,
  }
  function App() {
    return (
      <div>
        <Btn text="Save Changes" fontSize={18} />
        {/* <Btn text={14} fontSize={"Continue"} /> */}
        {/* <Btn fontSize={14} text={"Continue"} /> */}
        <Btn text={"Continue"} />
      </div>
    );
  };
  const root = document.getElementById("root");
  ReactDOM.render(<App />, root);
</script>

</html>
```

그리고 정의되지않은 변수에 기본값을 줄 수 있는데,<br/>
위 코드에서는 fontSize가 없는 두 번째 버튼에만 fontSize=30을 적용받는다.

---