# Router 접근 제한 구현

React로 로그인, 회원가입 등을 구현하면서 필요하다고 느낀 것이 로그인 상태 여부에 따른 페이지 접근 제한이었다.

- 로그인 전 상태
  - 로그인 폼
  - 아이디 찾기 / 비밀번호 찾기
- 로그인 상태
  - 마이페이지
  - 정보 조회 / 수정
- 관리자 로그인 상태
  - 회원 목록 등

### 처음에
`isLogin.js`를 만들어서 <br/>
로그인 시 **localStorage**에 저장되는 `idx`값의 유무에 현재 컴포넌트를 보여줄지, <Br/>
이전 페이지로 이동할 지 결정했다.

```jsx
// isLogin.js

const isLogin = () => {
   if(!localStorage.getItem('idx')) {
     alert("접근 할 수 없는 페이지입니다.");
     window.location.replace('/');
   }
 };

 export default isLogin;
```

여기서 발생하는 문제가 접근 권한이 없을 때,<br/>
접근 불가 알림창을 띄운 후 접근 제한된 페이지가 잠깐 보였다가 페이지가 이동하는 것이었다.

그래서 로그인 전 상태 / 로그인 상태 / 관리자 로그인 상태별 컴포넌트를 만들어서 그 안에서 `route`을 생성하도록 수정했다.

## `<PrivateRoute />`, `<NonLoginRoute />`, `<AdminRoute />`

검색을 하면 보통 `react-router-dom v5`인거 같고 내가 사용중인 건 `v6`여서 작성하는데에 있어서 차이가 있었다.

### 바뀐 점
- `<Switch />` => `<Routes />` 네이밍 변경
- `<Routes />`에서 컴포넌트 렌더링 속성이 **component**에서 **element**로 변경
    ```jsx
    // v5
    <Route path='/user' component={UserInfo} />

    // v6
    <Route path="/user" element={<UserInfo />} />
    ```
- `<Redirect />` => `<Navigate />` 변경
- 중첩 라우팅
    ```jsx
    // v5
    <BrowserRouter>
      <Routes>
        <Route path="web/*" element={<Web />}>
          <Route path=":id" element={<WebPost />} />
        </Route>
      </Routes>
    </BrowserRouter>

    // v6
    <BrowserRouter>
      <Routes>
        <Route path="web/*" element={<Web />} />
      </Routes>
    </BrowserRouter>
    ```

해당 기능을 구현하는데에 있어서 필요한 사항은 이정도인 것 같고, 이 외에도 변경점이 더 있다.

```jsx
// App.js

import React from 'react';
import { Routes, Route } from 'react-router-dom';
import PrivateRoute from './PrivateRoute';
import UserPage from './components/UserPage';

function App() {
   const access = localStorage.getItem('idx');

   return (
     <div className="App">
       <React.Fragment>
        <Routes>
          {/* Private */}
          <Route
            path="/mypage"
            element={
              <PrivateRoute 
                authenticated={access}
                component={<UserPage />}
              />
            }
          />
        </Routes>
        </React.Fragment>
     </div>
   );
```
여기서 `access`는 **localStorage**에 저장되는 `idx`값이다.

```jsx
// PrivateRoute.js

import React from 'react';
 import { Navigate } from 'react-router-dom';

 function PrivateRoute({ authenticated, component: Component }) {
   return (
     authenticated ? Component : <Navigate to='/' {...alert("접근할 수 없는 페이지입니다.")} />
   )
 }

 export default PrivateRoute 
```
로그인해야만 접근할 수 있는 페이지는 위와 같이 `idx`값이 있으면 전달된 `Component`를 보여주고 아니면 알림창을 띄우고 home으로 이동하도록 했다.

`<NonLoginRoute />`, `<AdminRoute />`에 대해서도 동일한 방식으로, 보여줄 Component와 아니면 이동할 페이지를 지정해줬다.