# github-page 배포
작성일시: 2021년 12월 30일 오전 2:04

## github-page로 배포하기

```jsx
npm i gh-pages  // 설치
```

package.json 에서 build라는 script코드 확인한다.

```json
"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test",
  "eject": "react-scripts eject"
},
```

이 스크립트를 실행하면 웹사이트의 production ready code를 생성한다.<br/>
→ 모든 코드가 압축되고 최적화된다.

```jsx
npm run build
```

코드를 실행하면 **build**라는 폴더 생긴다.

이 폴더를 github에 **push**해야 한다.<br/>
push 전에 `package.json`으로 가서 하단 마지막 `}` 윗줄에 그 위 `}`에 `,` 찍고
"homepage"라고 적는다.

```jsx
"homepage": "[https://username.github.io/레파지토리이름](https://username.github.io/%EB%A0%88%ED%8C%8C%EC%A7%80%ED%86%A0%EB%A6%AC%EC%9D%B4%EB%A6%84)"
"homepage": "[https://poseassome.github.io/MovieApp](https://poseassome.github.io/MovieApp)"
```

그리고 `package.json`에서 script 추가 한다.

```json
"deploy": "gh-pages -d build",
"predeploy": "npm run build"
```

deploy는 gh-pages를 실행시키고 build 폴더를 가져간다.<br/>
deploy를 실행하면 pre-가 먼저 실행되고 npm run build를 실행한다.

`npm run deploy` 실행

---