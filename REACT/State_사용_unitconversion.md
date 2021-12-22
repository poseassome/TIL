# state 사용_unitconversion
작성일시: 2021년 12월 23일 오전 12:32

## 시, 분 단위변환을 해주는 기능 구현

App 컴포넌트에 각각 minutes, hours를 입력할 수 있는 `<input>`을 작성하고 `<label>`도 작성한다.

이 때, `<label>`과 `<input>`을 연결해줘야 하는데,<br/>
HTML처럼 **for을 사용하면 안 된다.**
⇒ JSX에서 문법 차이가 있다.

- **for —> htmlFor**
- **class —> className**


`<input>`에 변화가 있을 때 단위 변환이 이루어져야 하기 때문에 <br/>
`onChange={onChange}` 이벤트를 부여하고 내용을 작성한다.

**state**는 `<input>의 값`을 저장하며, 초기 값은 0으로 설정한다.

`<input>의 값`에 접근하기 위해서는 `console.log(event)`로 속성을 확인하여 **event.target.value 경로**를 확인했다. 이는 값을 변화시키는 `setAmount()`에 넣는다.

```jsx
function App(){
	const [amount, setAmount] = React.useState(0);
	const onChange = (event) => {
      setAmount(event.target.value);
    };

	return (
		<div>
		  <label htmlFor="minutes">Minutes</label>
		  <input value={minutes} id="minutes" placeholder="Minutes" type="number" onChange={onChange} />
		</div>
		<h4>You want to convert {amount}</h4>
		<div>
		  <label htmlFor="hours">Hours</label>
		  <input value={Math.round(minutes / 60)} id="hours" placeholder="Hours" type="number" />
		</div>
	);
};
```

만약 **onchagne 이벤트를 지우면** 초기값이 0이기 때문에 사용자가 변경할 수 없게 된다.


### 전환 버튼을 추가하여 시, 분 입력창 활성화를 변경

시의 입력창이 활성화되면 분의 입력창을 불활성화하고,<br/>
 그 반대로도 가능하도록 버튼을 추가한다.

기본으로 분의 `<input>`에 **disabled**을 추가한다.

전환 버튼에 `onClick={onInvert}`이벤트를 추가하고 state도 추가한다.<br/>
state는 disabled의 <U>T / F</u> 이다.

초기값은 false이며, 버튼을 눌러서 함수를 실행하면 값은 reset()하고 현재의 state값의 반대값을 가지게 한다.

- current(현재 state)가 false이면, 클릭 후 true

Hours도 변환을 실행하기 위해 Minutes에 작성한 `onChange={onChange}`를 복사해온다.

하지만 지금 `value={Math.round(minutes/60)}`로 나오게 해놨고<br/>
이는 Minutes에 썼을 때만 단위변환이 일어나야 한다.

Hours에 값 입력하면 입력한 값 그대로 보여줘야함
==> **삼항연산자 사용**

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
  const root = document.getElementById("root");

  function App() {
    const [amount, setAmount] = React.useState(0);
    const [inverted, setInverted] = React.useState(false);
    const onChange = (event) => {
      setAmount(event.target.value);
    };
    const reset = () => setAmount(0);
    // const onFlip = () => setFlipped(!flipped);
    const onInvert = () => {
      reset();
      setInverted((current) => !current);
    };
    return (
      <div>
        <h1>Super Converter</h1>
        <div>
          <label htmlFor="minutes">Minutes</label>
          {/*<input value={minutes} id="minutes" placeholder="Minutes" type="number" onChange={onChange} disabled={flipped === true} />*/}
          <input value={inverted ? amount * 60 : amount} id="minutes" placeholder="Minutes" type="number" onChange={onChange} disabled={inverted} />
        </div>
        <h4>You want to convert {amount}</h4>
        <div>
          <label htmlFor="hours">Hours</label>
          {/*<input value={Math.round(minutes / 60)} id="hours" placeholder="Hours" type="number" disabled={flipped === false} /> */}
          <input value={inverted ? amount : Math.round(amount / 60)} id="hours" placeholder="Hours" type="number" onChange={onChange} disabled={!inverted} />
        </div>
        <button onClick={reset}>Reset</button>
        <button onClick={onInvert}>{inverted ? "Turn back" : "Invert"}</button>
      </div>
    );
  };
  ReactDOM.render(<App />, root);
</script>

</html>
```

---

## 단위 변환 컴포넌트를 추가하여 선택 출력하기

`KmToMiles` 컴포넌트를 추가하여 사용자가 select하여 원하는 단위 변환기를 출력하도록 한다.

**App컴포넌트**에 두 개의 컴포넌트를 담기위해 안에 작성한 내용을 빼주고 바깥에 단위 변환 컴포넌트를 작성한다.

`<select>`, `<option>`과 **삼항연산자**를 사용한다.

여기서 state는 `<select>`의 value이고 어떤 `<option>`을 선택하면 그 `<option>`의 value를 가지게 된다. ⇒ `onChange={onSelect}`

index값에 따라 컴포넌트를 출력하도록 삼항연산자를 사용한다.

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
  const root = document.getElementById("root");

  function MinutesToHours() {
    const [amount, setAmount] = React.useState(0);
    const [inverted, setInverted] = React.useState(false);
    const onChange = (event) => {
      setAmount(event.target.value);
    };
    const reset = () => setAmount(0);
    // const onFlip = () => setFlipped(!flipped);
    const onInvert = () => {
      reset();
      setInverted((current) => !current);
    };
    return (
      <div>
        <div>
          <label htmlFor="minutes">Minutes</label>
          {/*<input value={minutes} id="minutes" placeholder="Minutes" type="number" onChange={onChange} disabled={flipped === true} />*/}
          <input value={inverted ? amount * 60 : amount} id="minutes" placeholder="Minutes" type="number" onChange={onChange} disabled={inverted} />
        </div>
        <h4>You want to convert {amount}</h4>
        <div>
          <label htmlFor="hours">Hours</label>
          {/*<input value={Math.round(minutes / 60)} id="hours" placeholder="Hours" type="number" disabled={flipped === false} /> */}
          <input value={inverted ? amount : Math.round(amount / 60)} id="hours" placeholder="Hours" type="number" onChange={onChange} disabled={!inverted} />
        </div>
        <button onClick={reset}>Reset</button>
        <button onClick={onInvert}>{inverted ? "Turn back" : "Invert"}</button>
      </div>
    );
  };
  function KmToMiles() {
    return <h3>KM 2 M</h3>
  }
  function App() {
    const [index, setIndex] = React.useState("xx");
    const onSelect = (event) => {
      setIndex(event.target.value);
    }
    return (
      <div>
        <h1>Super Converter</h1>
        {/* 컴포넌트 안에 다른 컴포넌트 렌더링함 */}
        <select value={index} onChange={onSelect}>
          <option value="xx">Select your units</option>
          <option value="0">Minutes & Hours</option>
          <option value="1">Km & Miles</option>
        </select>
        <hr />
        {/* javascript 코드 작성 (index값에 따라 내용 보이게) */}
        {index === "xx" ? "Please select your units" : null}
        {index === "0" ? <MinutesToHours /> : null}
        {index === "1" ? <KmToMiles /> : null}
      </div>
    );
  };
  ReactDOM.render(<App />, root);
</script>

</html>
```

---