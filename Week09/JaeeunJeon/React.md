## React 개념 정리

### 1. JSX

#### JSX란?
JSX (JavaScript XML)는 React에서 UI를 설명하기 위해 사용되는 자바스크립트 확장 문법이다. <br/>
JavaScript 코드 안에 HTML과 비슷한 코드를 작성할 수 있게 하여 컴포넌트 구조를 시각적으로 쉽게 이해할 수 있다.

#### JSX를 사용하는 이유
- 가독성: HTML 구조와 유사하여 코드가 읽기 쉽다.
- 성능: JSX는 자바스크립트로 컴파일되어 성능을 최적화한다.
- 컴포넌트 작성: JSX를 사용하면 컴포넌트를 정의하기가 쉬워지고, 모듈화와 재사용이 용이하다.

#### JSX 문법 규칙
1. 단일 부모 요소: 각 JSX 표현식은 반드시 하나의 부모 요소를 가져야 한다 (필요 시 `<div>`로 감싸야 함).
2. Self-Closing 태그: 자식 요소가 없는 태그는 self-closing 형식으로 닫아야 한다 (`<img />`).
3. 자바스크립트 표현식: {}를 사용하여 JSX 내에서 자바스크립트 표현식을 사용할 수 있다 (예: {변수명}).
4. className 사용: JavaScript의 예약어인 class 대신 className을 사용해야 한다.

```jsx

// 예시
const Welcome = () => {
  const user = "Alice";
  return (
    <div className="welcome">
      <h1>Hello, {user}!</h1>
      <p>Welcome to React.</p>
    </div>
  );
};
```

### 2. Props

#### Props란?
Props (속성)는 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 방법이다. <br/>
Props는 컴포넌트에 동적인 값을 전달하여 컴포넌트를 더 재사용 가능하고 유연하게 만든다.

#### Props를 통해 값 전달하기
Props는 JSX 구문에서 속성 형태로 전달된다.

```
// 부모 컴포넌트
const App = () => {
  return <Greeting name="Alice" />;
};

// 자식 컴포넌트
const Greeting = (props) => {
  return <h1>Hello, {props.name}!</h1>;
};

```
위 예제에서 name="Alice"는 App에서 Greeting 컴포넌트로 전달된다.

#### 컴포넌트를 Props로 전달하기
컴포넌트 또한 Props로 전달할 수 있어 복잡한 UI 구성을 가능하게 한다.

```
const App = () => {
  return (
    <Layout header={<Header />} footer={<Footer />} />
  );
};

const Layout = (props) => {
  return (
    <div>
      {props.header}
      <main>Main Content</main>
      {props.footer}
    </div>
  );
};
```
위 예제에서 `<Header />`와 `<Footer />` 컴포넌트는 `<Layout />`에 Props로 전달된다.

### 3. 이벤트 처리

#### 이벤트 핸들링
React에서 이벤트는 자바스크립트와 비슷하게 처리되지만, camelCase로 이름을 작성하고 JSX 문법을 사용한다.

```
const Button = () => {
  const handleClick = () => {
    alert("Button clicked!");
  };

  return <button onClick={handleClick}>Click Me</button>;
};
```

#### 이벤트 핸들러
이벤트 핸들러는 사용자 액션(클릭, 입력 등)에 반응하는 함수이다.<br/>
React에서는 이벤트 핸들러를 함수로 정의하고 요소에 연결한다.

```
// 이벤트 핸들러
const handleClick = () => {
  console.log("Button was clicked!");
};

// JSX에서 사용
<button onClick={handleClick}>Click Me</button>;
```

#### 이벤트 객체 사용하기
React에서는 e라는 이벤트 객체를 제공하여 이벤트에 대한 정보를 포함한다. <br/>
이벤트 타입, 타겟 요소 등을 확인할 수 있다.

```
const InputField = () => {
  const handleChange = (e) => {
    console.log("Current Value:", e.target.value);
  };

  return <input type="text" onChange={handleChange} />;
};
```
위 예제에서 e.target.value는 입력 값이 변경될 때마다 현재 값을 가져온다.

***

## React 컴포넌트와 상태 관리

### 1. State

#### State란?
State는 React 컴포넌트 내부에서 동적인 데이터를 관리하기 위한 객체이다. <br/>
사용자의 입력, 네트워크 요청, 시간의 경과 등과 같이 변할 수 있는 데이터를 state로 저장한다.

#### State 사용법
React에서 state를 정의하고 업데이트하려면 useState 훅을 사용한다. <br/>
useState는 초기 상태 값을 받아들이고, 현재 상태와 상태를 업데이트할 수 있는 함수를 반환한다.

```
import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0); // count라는 state와 setCount라는 업데이트 함수 정의

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
};
```
- useState(0): 초기값을 0으로 설정하여 count라는 state 변수를 만든다.
- setCount: count의 값을 변경하는 함수이다.

#### set 함수란?
set 함수는 state를 업데이트하는 데 사용되며, 새로운 상태 값을 인자로 받는다. <br/>
React는 set 함수가 호출되면 컴포넌트를 재렌더링하여 UI를 최신 상태로 유지한다.

```
// 예시: 상태를 조건에 따라 업데이트
const toggleStatus = () => {
  setIsActive(!isActive); // 이전 상태와 반대로 설정
};
```

#### State로 사용자 입력 관리하기
state를 사용하여 사용자의 입력을 관리하면, 입력된 값에 따라 UI가 즉시 업데이트된다.

```
import React, { useState } from 'react';

const InputForm = () => {
  const [inputValue, setInputValue] = useState(""); // 입력 값을 저장할 state

  const handleChange = (e) => {
    setInputValue(e.target.value); // 입력값이 변경될 때마다 state 업데이트
  };

  return (
    <div>
      <input type="text" value={inputValue} onChange={handleChange} />
      <p>Current Input: {inputValue}</p>
    </div>
  );
};
```
- value={inputValue}: 입력 필드의 값을 inputValue state와 연결한다.
- onChange={handleChange}: 사용자가 입력할 때마다 handleChange 함수가 호출되어 state가 업데이트된다.

### 2. useRef

#### useRef란?
useRef는 React 훅 중 하나로, DOM 요소나 컴포넌트에 직접 접근해야 할 때 사용된다. <br/>
useRef로 생성된 객체는 컴포넌트의 전체 라이프사이클 동안 유지되며, 재렌더링 시 값이 초기화되지 않는다.

#### useRef 사용법

```
import React, { useRef } from 'react';

const InputFocus = () => {
  const inputRef = useRef(null); // 초기값으로 null을 설정하여 참조 생성

  const handleFocus = () => {
    inputRef.current.focus(); // inputRef가 참조하는 요소에 focus
  };

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Click the button to focus" />
      <button onClick={handleFocus}>Focus Input</button>
    </div>
  );
};
```
- useRef(null): inputRef라는 참조 객체를 생성한다. 초기값은 null로 설정한다.
- inputRef.current: ref가 연결된 DOM 요소를 가리킨다. current를 통해 요소에 접근하고, 메서드나 속성을 사용할 수 있다.

#### State와 Ref의 차이
- State는 값이 변경될 때마다 컴포넌트를 재렌더링한다. (화면이 갱신된다)
- useRef는 값이 변경되더라도 컴포넌트를 재렌더링하지 않는다. (화면이 갱신되지 않는다) 단지 참조 객체를 업데이트한다.
