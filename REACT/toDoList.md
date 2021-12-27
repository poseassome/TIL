# toDoList
작성일시: 2021년 12월 27일 오후 11:53

## to Do List

`**<App />**`에 `<input>`과 `<button>`을 생성하고,<br/>
`<input>`에는 value와 변화를 감지할 함수를 추가한다.

**useState()**를 사용하여 toDo의 초기값은 “ ”을 주고,<br/>
input의 value변화를 감지할 수 있도록 onChange를 작성한다.

```jsx
import { useState } from "react";

function App() {
  const [toDo, setToDo] = useState("");
  const onChange = (event) => setToDo(event.target.value);
  return (
    <div>
        <input type="text" value={toDo} onChange={onChange} placeholder="Write your to do..." />
        <button>Add To Do</button>
    </div>
  );
}

export default App;
```

이를 `<form>`으로 묶고 onSubmit을 줄 건데, `<button>`을 누르면 새로고침이 된다.<br/>
이는 form이 submit이라는 이벤트를 갖고있기 때문이고 동작하는걸 막기위해
`event.preventDefault();` 를 작성한다.

만약 toDo가 비어있다면 submit되지 않도록 한다. (return;)<br/>
그렇지 않으면 toDo를 추가하도록 한다. + input을 비우면서

```jsx
const onSubmit = (event) => {
    event.preventDefault();
    if (toDo === "") {
      return;
    }
		setToDo("");
  };

...

<form onSubmit={onSubmit}>
	<input .../>
	<button ...>
</form>
```

**to Do**를 받을 array를 만든다.<br/>
일반적인 자바스크립트라면 toDos.push로 배열에 넣었을 것이지만,
react에서는 state를 직접적으로 수정할 수 없다.

값을 변화시키는 setToDos를 이용해야하는데,<br/>
값을 직접 입력하는 방법이 있고 / 함수를 이용하는 방법이 있다.

⇒ 함수의 첫 번째 인자로 현재의 **state** (**currentArray**)를 받아온다.
거기에 input에 입력한 toDo를 추가한다.

배열에 추가하기 위해서 currentArray 요소를 전개 해준다. (**...currentArray**)

```jsx
import { useState } from "react";

function App() {
  const [toDo, setToDo] = useState("");
  const [toDos, setToDos] = useState([]);
  const onChange = (event) => setToDo(event.target.value);
  const onSubmit = (event) => {
    event.preventDefault();
    if (toDo === "") {
      return;
    }
    setToDo("");
    setToDos((currentArray) => [toDo, ...currentArray]);
  };
  return (
    <div>
      <h1>My To Dos ({toDos.length})</h1>
      <form onSubmit={onSubmit}>
        <input type="text" value={toDo} onChange={onChange} placeholder="Write your to do..." />
        <button>Add To Do</button>
      </form>
    </div>
  );
}

export default App;
```

jsx에서 자바스크립트를 넣고 싶으면 중괄호를 이용한다.

- My To Dos (toDos.length) x
- My To Dos ({toDos.length}) o

### array의 요소를 컴포넌트로 만들기

`map()`를 이용한다.

**map()** : array의 모든 요소에 대해 콜백함수 실행 -> return값이 새로운 array에 반환<br/>
map((item)=>fn)

```jsx
import { useState } from "react";

function App() {
  const [toDo, setToDo] = useState("");
  const [toDos, setToDos] = useState([]);
  const onChange = (event) => setToDo(event.target.value);
  const onSubmit = (event) => {
    event.preventDefault();
    if (toDo === "") {
      return;
    }
    setToDo("");
    setToDos((currentArray) => [toDo, ...currentArray]);
  };
  return (
    <div>
      <h1>My To Dos ({toDos.length})</h1>
      <form onSubmit={onSubmit}>
        <input type="text" value={toDo} onChange={onChange} placeholder="Write your to do..." />
        <button>Add To Do</button>
      </form>
      <hr />
      <ul>
        {toDos.map((item) => <li>{item}</li>)}
      </ul>
    </div>
  );
}

export default App;
```

`<li>`로 출력하는데, 콘솔창에 에러가 있다.

같은 컴포넌트의 list를 **render**할 때는 key라는 prop을 넣어줘야 한다.<br/>
기본적으로 react는 list에 있는 모든 irem을 인식하기 때문에.
⇒ key는 고유의 값을 가져야함

map() 설명을 보면 첫번쨰 인자는 value여야 하고 → toDo
두번째 인자는 index 이다.

index를 키값으로 부여한다.

```jsx
{toDos.map((item, index) => <li key={index}>{item}</li>)}
```

---