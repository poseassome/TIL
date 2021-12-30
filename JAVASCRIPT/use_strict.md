# use strict

자바스크립트 언어를 엄격하게 제어해주는 모드
문자열로 선언만 하면 된다.

```jsx
function func(){
  'use strict';
  globalVal = 10;     // globalVal is not defined

  return 'hello';
}

func();     // globalVal is not defined
```
최상위에서 선언하면 부족한 자바스크립트 부분을 엄격하게 제어한다.

위 코드는 globalVal이 밖에 있어야 함수 스코프 동작을 하는 ES6이전 관점에서 func()밖에서 전역변수를 찾아가 값을 만들텐데 use strict이 그걸 차단하고있다.

ES2015년부터 use strict을 모듈에서 기본적으로 사용하고있다.