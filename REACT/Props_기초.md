# Props
작성일시: 2021년 12월 23일 오후 10:32

# Props

부모 컴포넌트에서 자식 컴포넌트에 데이터를 보낼 수 있게 해주는 방법<br/>
(컴포넌트는 어떤 JSX를 반화하는 함수)

---

## Props 사용하여 button 두 개 만들기

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
  function SaveBtn() {
    return <button style={{
      backgroundColor: "tomato",
      color: "white", padding: "10px 20px",
      border: 0, borderRadius: 10
    }}> Save Changes</button >;
  }
  function ConfirmBtn() {
    return <button style={{
      backgroundColor: "tomato",
      color: "white", padding: "10px 20px",
      border: 0, borderRadius: 10
    }}>Confirm</button>;
  }
  function App() {
    return (
      <div>
        <SaveBtn />
        <ConfirmBtn />
      </div>
    );
  };
  ReactDOM.render(<App />, root);
</script>

</html>
```

이렇게 필요한 만큼 컴포넌트를 만들고 컴포넌트를 삽입하여 출력할 수 있다.

하지만 스타일과 같은 공통된 부분의 코드를 반복해서 작성해야 한다.방법<br/>
⇒ Props를 사용하여 코드를 단순하게 작성할 수 있다.

작성한 `<SaveBtn />`, `<ConfirmBtn />` 컴포넌트를 지우고 `**Btn**` 컴포넌트 하나만을 다시 작성한다.

`**App` 컴포넌트**에는 **`<Btn />`** 두 개를 작성한다.방법<br/>
이 상태에서 화면을 출력하면 content가 똑같은 버튼 두 개가 나타난다.

**Props를 줘서 버튼을 구분하도록 한다.**

`<Btn />`에 Props를 작성하는데, 이름은 임의로 작성해도 괜찮다.

모든 컴포넌트들은 ()로 argument(인자)를 받는다.방법<br/>
⇒ 이 인자의 이름이 **Props(properties, 컴포넌트로부터 전달받는)**

```jsx
<Btn banana="Save Changes" />

// 이렇게 작성하는 것은
// Btn()함수를 불러서 banana라는 인자를 보내는 것과 돌일하다.

Btn({banana:"Save Changes"})

// <button>내부 내용대신 {props.banana}로 출력할 수 있다.
// 또는 props는 잘 쓸 일이 없고 props는 object이기 때문에
// {} 중괄호를 열고 {banana}라고 출력해도 된다.
```
```
function Btn(props){

  console.log(props);

}                    ⇒  console창에서 <Btn />의 속성들을 볼 수 있다.
```
`<Btn />`에 같은 속성명을 쓰고 값을 다르게 주는 것으로 content를 다르게 출력 할 수 있다.  `{props.banana}` 또는 `{banana}`

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
  // function Btn(props) {
  function Btn({ banana, big }) {
    // console.log(props);
    return <button style={{
      backgroundColor: "tomato",
      color: "white", padding: "10px 20px",
      border: 0, borderRadius: 10,
      fontSize: big ? 18 : 16
    }}>{banana}</button >;
  }
  function App() {
    return (
      <div>
        <Btn banana="Save Changes" big={true} />
        <Btn banana="Continue" big={false} />
      </div>
    );
  };
  ReactDOM.render(<App />, root);
</script>

</html>
```

---