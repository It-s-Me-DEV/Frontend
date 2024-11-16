# 리액트 기초
### 1. 컴포넌트
#### (1) 개념
##### - html 요소를 반환하는 함수
##### - 여러 페이지에서 공통으로 사용하는 코드를 쓸 때 컴포넌트 단위로 만듦
##### ->  리액트는 컴포넌트 기반 구조로 유연성을 띔 즉, 기능 추가시 코드 수정이 적어짐

##### - 주로 함수 컴포넌트 사용하며, 효율성을 위해 컴포넌트는 파일별로 생성

```js
//header.js
function Header() {
    return (
        <header>
            <h1>hello</h1>
        </header>
    );
}

export default Header;
```
```js
//app.js
import Header from "./header";


function App() {
  return (
    <div className="App">
      <Header /> //Header가 app의 retrun문에 포함됨 -> 자식 컴포넌트 / app은 header 컴포넌트를 포함시킴 -> 부모 컴포넌트 
    </div>
  );
}
```

#### (2) props
##### - 컴포넌트에 값을 전달 
##### - 컴포넌트의 공통 기능이 아닌 세부 기능 표현
##### - 이때, 부모 컴포먼트만이 자식 컴포넌트에 전달 가능
```js
//app.js
function App() {
  return (
    <div className="App">
      <Header num1={2} num2={3}  /> 
    </div>
  );
}
```
```js




