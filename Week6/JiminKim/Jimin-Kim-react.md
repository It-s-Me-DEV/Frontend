# React
## 목차
- [1. React의 개발 구조](#1-react의-개발-구조)
- [2. create-react-app](#2-create-react-app)
- [3. JSX](#3-jsx)
- [4. 금주의 프로젝트](#4-금주의-프로젝트)

## 1. React의 개발 구조

React는 중복 코드를 방지하기 위해 컴포넌트 단위로 코드를 작성합니다. 예를 들어 똑같은 모양의 \<header> 태그를 어느 홈페이지에서 사용한다고 할 때 원래 같으면 페이지를 이동할 때마다 \<header> 부분을 복사 + 붙여넣기해야 합니다.

만약 헤더를 한 번 수정할 일이 생긴다면 모든 페이지의 html 파일을 수정해야겠죠 ... 우리는 그걸 피하기 위해 위 방법을 쓰려고 합니다.

- 컴포넌트 기반의 구조

    자주 사용할 부분만큼을 한 개의 컴포넌트로 하여 제작해두면 여러 페이지에 걸쳐 사용이 가능합니다.

- Virtual DOM을 이용한 업데이트

    여기서 말하는 업데이트란 동적으로 변화하는 웹페이지에서의 페이지 변화를 말합니다.

    결국에 페이지가 변화하려면 브라우저가 페이지를 다시 렌더링해야 하는데 이 과정에서의 시간을 단축하는 것이 사용 경험에 큰 영향을 줍니다.

    우선 DOM이란 Document Object Model, 문서 객체 모델입니다.\
    웹 브라우저는 HTML 문서를 트리 형태로 만들어 페이지를 렌더링합니다.

    우리가 JS 등에서 `document.querySelector()` 이런 식으로 요소를 접근할 수 있던 것도 다 DOM api를 통해 접근한 것입니다.

    ```
    // /index.html
    <head>
    </head>
    <body>
        <div>
            <h1>안녕 월드</h1>
            <button onclick="changeLang()">English</button>
        </div>
    </body>
    <script>
        changeLang() =>{
            const helloWorld = document.querySelector("h1");
            helloWorld.innerText = "Hello World";
        }
    </script>
    ```

    
    ![image](https://github.com/user-attachments/assets/9dd25452-ec12-4d7f-a49c-cde655759ade)\
    DOM이 이런 식으로 구성되어 있다는 것이고 만약에 `button`을 통해 DOM에 접근해 `innerText`를 변경한다면 웹 페이지에 업데이트를 초래할 것입니다.

    이러한 업데이트를 메모리의 Virtual DOM에서 저장해두고 원본 DOM에서 바꿀 부분만 쏙 빼서 저장해줍니다. 이것이 리액트가 성능을 끌어올리기 위해 사용하는 방법입니다.

## 2. create-react-app
node.js 설치 후 `npx create-react-app` 명령어를 치게 되면
```
node_modules/
public/
  ├── favicon.ico
  ├── index.html
  ├── logo192.png
  ├── logo512.png
  ├── manifest.json
  └── robots.txt
src/
  ├── App.css
  ├── App.js
  ├── App.test.js
  ├── index.css
  ├── index.js
  ├── logo.svg
  ├── reportWebVitals.js
  └── setupTests.js
.gitignore
package-lock.json
package.json
README.md
```
react 프로젝트가 생성됩니다.

`npm start` 명령어를 실행하면 package.json에 있는 script 부분에서 `react-scripts start` 가 실행이 되고 :3000에서 리액트 앱이 실행됩니다.

![image](https://github.com/user-attachments/assets/87683430-d17a-4982-aa81-4aae265e121c)

```
// index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

reportWebVitals();

// index.html
<!DOCTYPE html>
<html lang="en">
  <head>
    ~
    <title>React App</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
    
  </body>
</html>
```

일단 기본적으로 index 페이지부터 살펴보니 index.html 파일에는 div#root 하나 말고는 아무 것도 없었습니다.

`index.js` 에서 
```
const root = ReactDOM.createRoot(document.getElementById('root'));
```
'root' div에 root를 만들고 렌더링하는 것을 볼 수 있습니다.
또한 \<App /> 을 통해 App.js를 호출했습니다.

```
<script defer="" src="/static/js/bundle.js"></script>
```
HTML 파일에는 참고로 script 태그가 없어 어떻게 `index.js`를 불러왔나 싶지만 react가 자동으로 `bundle.js`를 생성해 불러와줍니다.

## 3. JSX

React에서 쓸 수 있는 JavaScript 확장 문법입니다.\
주요 특성으로는:
  - html을 그대로 js 파일에 사용 가능
  ```
  const a = <h1>welcome to this page</h1>;
  function App(){
    return (
      <div>
        {a}
        <img src="./dd.jpg" />
      </div>
    )
  }
  ```
  a에 따옴표 같은 것 없이 그대로 h1 태그를 할당해주었습니다. 대신 엄격하게 태그를 잘 닫아주어야 합니다. 이 코드에서도 원래 img 태그는 뒤에 `/`를 쓰지 않는데, jsx 파일을 작성할 때는 적어서 태그를 닫았음을 표시해주어야 합니다.

  또한 return할 때 여러 컴포넌트를 반환해선 안 됩니다. div와 같이 한 개의 최상위 태그로 감싸주고 반환해야 합니다. div 같은 걸 추가하기 싫다면 <></> (fragment)로 감싸주면 됩니다.

  - 자유롭게 변수 불러오기
   ```
  const a = <h1>welcome to this page</h1>;
  function App(){
    return (
      <div>
        {a}
      </div>
    );
  }
  ```
  위의 코드에서 중괄호를 사용하여 html 사이에 js에서 할당한 값을 반환했습니다. 마치 ES6 문법에서 문자열 사이에 ${}을 써서 변수 값을 쓰는 것과 일맥상통하는데 이런 식으로 중괄호를 활용하여 쉽게 값을 가져와 사용할 수 있습니다. 

  - Props

  index.js에서 우리는 `<App />`를 통해 App.js에서의 `App()`을 불러올 수 있었습니다. 여기서 이 `App()`은 함수인데.. 이 함수의 매개변수 역할을 할 수 있는 것이 Props입니다.

  ```
  // index.js
  ...
  const name = "지민";
  root.render(
    <React.StrictMode>
      <App name={name} />
    </React.StrictMode>
  );

  // App.js
  function App(prop) {
    return (
      <div className="App">
        {prop.name}, 안녕하세요!
      </div>
    );
  }

  export default App;
  ```
  index.js 에서 prop에 지정해준 값을 담아넘겨주면 App.js 에서 받아서 쓸 수 있습니다. 이러한 방법으로 여러 컴포넌트를 불러와도 다양한 형태도 표현할 수가 있습니다. 또한 prop은 객체이기 때문에 구조 분해 할당도 가능합니다.

## 4. 금주의 프로젝트

https://nowimseeingcashflow.github.io/

1. Footer와 자기소개 img 및 ul 추가

2. 자기소개와 gnb 메뉴 등 내용 추가

리액트 공부하면서 리액트로 옮겨보겠습니다,,
