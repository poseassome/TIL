### javascript 실행 과정
> #### `<head>`에 삽입

HTML파일에서 `<head>`에 `<script src="main.js">`코드를 작성하면,<bt/>
브라우저는 위에서부터 한 줄 한 줄 코드를 분석한다.

한 줄 한 줄 분석한 것을 CSS와 병합하여 DOM 요소로 변환한다.

HTML을 parsing하다가 `<script>`를 만나면 HTML parsing을 잠시 멈추고 필요한 스크립트파일을 서버에서 다운받고 실행한 다음에 다시 HTML을 parsing한다.
```
parsing HTML --> blocked(fetching js / executing js) --> parsing HTML => (page is ready)
```
만약 js파일이 크다면 사용자가 웹페이지를 보는데까지 많은 시간이 걸린다.

> #### `<body>`에 삽입
브라우저가 HTML을 쭉 parsing하고 페이지가 준비가 된 다음에 스크립트파일을 받아오고 실행한다.
```
parsing HTML --> (page is ready) --> fetching js --> executing js
```
HTML페이지가 javascript 의존적이라면 사용자가 정상적인  페이지를 보기까지 시간이 걸린다.

***
# async
`<head>`에 `<script>`을 삽입하되 **asyn**이란 속성갑을 작성한다.

**asyn**는 boolean타입의 속성값으로 선언하는 것만으로도 true로 설정되어서 속성을 사용할 수 있다.

브라우저가 코드를 한 줄씩 읽다가 `<script>`를 만나면 스크립트 파일을 병렬로 다운을 받고 다시 parsing을 한다.<br/>
스크립트파일 다운로드가 완료되면 그 때 parsing을 멈추고 다운로드받은 js파일을 실행한다.<BR/>
실행을 다 하고나서 남은 HTML을 parsing한다.
```
parsing HTML --->   blocked  ---> parsing HTML ==> (page is ready)
   fetching js -┘ executing js -┘
```

다운로드 시간이 절약되는 장점이 있지만,<br/>
parsing이 완료되기 전에 스크립트 파일이 실행되면 DOM요소 조작에 있어, 요소가 아직 정의되지 않았을 수 있다.

스크립트 파일이 실행되는 동안 parsing이 멈추기 때문에 사용자가 페이지를 보는데 시간이 걸린다.

# defer
`<head>`에 `<script>`을 삽입하되 **defer**이란 속성갑을 작성한다.

브라우저가 코드를 한 줄씩 읽다가 `<script>`를 만나면 스크립트 파일을 병렬로 다운을 받고 나머지 HTML을 끝까지 parsing을 한다.<br/>

parsing이 끝나고 나서 다운로드 받은 스크립트 파일을 실행한다.
```
parsing HTML -----> (page is ready) --> executing js
 fetching js -┘
```

***
## 차이점
- ### head + async
`<script>`파일이 여러 개일 떄, 순서에 상관없이 먼저 다운로드가 끝난 스크립트파일부터 실행한다.

- ### head + defer
`<script>`파일이 여러 개일 떄, 다운로드 받은 후 페이지가 준비됐을 때 순서대로 스크립트 파일을 실행한다.