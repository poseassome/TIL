# HTTP (Hyper Text Transfer Protocol)

HTML문서를 주고받는 프로토콜.<br/>
서로 정해진 양식과 규칙을 주고 받는다.

브라우저는 문서를 요청하고 요청에 대한 결과로 서버는 문서를 준다.

***
# Ajax (Asynchronous Javascript and Xml)

xml을 잘 사용하지 않고 JSON을 사용한다.

문서를 주고받지 않고 데이터 통신이 일어난다.

무한 스크롤 - 한 번에 모든 정보를 불러오지 않고 스크롤을 내리면 정보가 출력된다. / 사용자에게 유려하게 정보를 보여주기 위함.

***
# XMLHttpRequest

전체 페이지 새로고침을 하지않고 서버로부터 데이터를 받아온다.

#### JSON 테스트 서비스
- [JSONplaceholder](https://jsonplaceholder.typicode.com/)<br/>
빈 문서에 JSON을 나타낸다.

### XMLHttpRequest 사용하기
```jsx
// XMLHttpRequest을 인스턴스로 만든다.
const xhr = new XMLHttpRequest();
// 준비가 됐을 때 실행되도록
xhr.onreadystatechange = function(){
  // xhr은 상태를 가진다 => 네트워크 상태
  if(xh.readyState === xhr.DONE) {    // 네트워크 상태가 DONE일 때를 이미 내부적으로 가지고 있음
    if(shr.status===200){  // 성공
      console.log(xhr.response);
    } else {               // 실패
      console.error('error');
    }
  }
}

// GET 서버통신으로 가져온다.
xhr.open('GET', 'https://jsonplaceholder.typicode.com/todos/1');
shr.send();

{
  /* 정 보 출 력 */
}
```
JSON placeholder에서 통신 양식을 정의하고 있다.

***
# fetch

XMLHttpRequest을 사용할 필요가 없다.<br/>
(과거에는 jquery.ajax를 사용했다.)

```jsx
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then((repsonse)=>resopnse.json())
  .then((json)=>console.log(json));
```
(then 체인 사용)

1. URL로 fetch 요청
2. fetch 응답 객체를 받아옴
3. 응답 객체가 JSON으로 되어있기 때문에 순수 JS 객체로 변환한다.

***
# JSON

- JSON.parse()<br/>
    - JSON을 자바스크립트 객체로 변환
    - 서버에서 데이터를 가져올 때 사용
- JSON.stringify()<Br/>
    - 일반적인 자바스크립트 객체를 JSON으로 변환
    - 서버로 데이터를 보낼 때 사용

```jsx
const obj = {x:5, y:6};

const json = JSON.stringify({x:5, y:6});
const jsonParseObj = JSON.parse(json);    // {"x":5, "y":6}

console.log(typeof obj);              // object
console.log(typeof json);             // string
console.log(typeof jsonParseObj);     // object
```

Javascript로 프론트엔드 개발을 하는데<br/>
Java, Python, Ruby, Go 등 백엔드 언어가 다르기 때문에 <Br/>
JSON으로 소통을 하고 가공할 때는 각자 JSON을 변환해서 사용한다.

요즘은 axios를 사용한다.
***