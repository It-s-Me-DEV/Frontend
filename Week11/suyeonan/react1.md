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
//header.js
function Header({num1, num2}) {

    return(
        <header>
            <div className="header">
               {num1}+{num2}={num1+num2}
            </div>
        </header>
    );
}
```

- ##### - 주의 )  App 컴포넌트에서 props의 값( 예: num2 )을 전달하지 않으면 오류가 발생 -> defaultProps 이용

```js
//header.js 밑에 내용 추가
Header.defaultProps = {
    num2: 0, 
};
```
---
### 2. jsx
#### (1) 개념
##### - 자바스크립트와 html 태그를 섞어 사용하는 문법
```js
//header.js 밑에 내용 추가
function Header() {
    const number1 = 1;
    const number2 = 2;
    return(
        <header>
            <h1>hello</h1>
            <h2>{number1 + number2}</h2>
        </header>
    );
}

export default Header;
```
#### (2) 규칙
##### - 최상위 태그 규칙: 최상위 태그로 감싸지 않으면 오류가 발생함
```js
// 오류 발생
function Header() {
    return (
        <div>div 1</div>
	    <div>div 2</div> 
    );
}
```
```js
// - 오류 해결1: <React.Fragment> 사용
function Header() {
    return (
      <React.Fragment>
        <div>div 1</div>
     	<div>div 2</div> 
      </React.Fragment>
    );
}
```
```js
// - 오류 해결2: 빈태그 사용
function Header() {
    return (
      <>
        <div>div 1</div>
	    <div>div 2</div> 
      </>
    );
}
```
---
### 3. useState 함수
#### (1) 개념
##### - 사용자 입력 관리 가능함 ex. 입력 폼, 옵션 선택
```js
//문법
const [light, setLight] = useState(“”);
// light는 현재 상태 변수, setLight는 상태 업데이트 함수, useState의 인수가 light의 초기값
```
#### (2) input 태그로 텍스트 입력


![image](https://github.com/user-attachments/assets/bc80710f-323c-48b3-93f1-4028121df869)
```js
import { useState } from "react"; //리액트 라이브러리에서 불러옴

function Body(){
    const [text, setText] = useState("") 
    const handleOnChange = (e) => {
        setText(e.target.value); // setText 함수를 통해 text에 이벤트가 발생한 요소의 현재 값이 저장
    };
    return(
        <div>
            <input value={text} onChange={handleOnChange} /> //텍스트입력시 onChange 이벤트가 발생, handleOnChange 함수 호출
            <div>{text}</div> // text값 출력
        </div>
    );
}

export default Body;
```








