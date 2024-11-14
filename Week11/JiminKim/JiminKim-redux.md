# React & More

## 목차
- [1. contextAPI & Redux](#1-contextapi--redux)
- [2. React Hook](#2-react-hook)
    - [2-1. useCallback](#2-1-usecallback)
    - [2-2. useContext](#2-2-usecontext)
- [3. React Routing](#3-react-routing)

## 1. contextAPI & Redux
contextAPI나 Redux나, React 환경에서 골칫거리인 Prop Drilling 문제를 해결하기 위해 사용되는 기능입니다.\
둘 다 사용하는 이유가 비슷하고 Provider 문법을 사용하나 차이점을 조금 살펴보자면,

![image](https://github.com/user-attachments/assets/e0c37de4-0a6d-48d8-bd41-b7b55ade415e)

contextAPI는 이런 식으로 Provider에 하위 컴포넌트 트리를 달고 그 트리 내에서는 전역 변수처럼 Prop을 사용할 수 있게 만들어줍니다.

![제목 없음](https://github.com/user-attachments/assets/2784833e-8c70-41be-acd2-45e00f848341)

그에 반해 Redux는 아예 Store을 따로 두어 DOM 어디에서든지 값을 꺼내어 쓸 수 있습니다. 조금 더 범용성이 있는 것이지요.
또한 Redux는 자체적으로 리듀서가 있습니다. 그래서 React 자체 기능과 Redux 사이의 차이점을 살펴보겠습니다.

| 기능    | Context API                 | useReducer                      | Redux                                 |
| ----- | --------------------------- | ------------------------------- | ------------------------------------- |
| 목적    | 컴포넌트 트리 전체에 값을 전달           | 복잡한 상태 업데이트 관리                  | 전역 상태 관리, 예측 가능한 상태 변화                |
| 특징    | 간단한 상태 공유, Prop Drilling 해결 | 순수 함수를 통한 상태 변화, 복잡한 로직 처리 가능   | 중앙 집중식 저장소, 액션, 리듀서, 미들웨어 등 다양한 기능 제공 |
| 적용 시기 | 간단한 상태 공유, 작은 규모의 앱         | 복잡한 로직의 상태 관리, 여러 컴포넌트 간의 상태 공유 | 대규모 앱, 복잡한 상태 관리, 협업 환경               |

Redux를 React 환경에서 사용할 수 있도록 도와주는 강의가 있어서 한 번 공유해봅니다!\
**[Redux 강의 링크](https://egghead.io/lessons/react-setup-the-currency-conversion-calculator?pl=modernizing-a-legacy-redux-application-with-react-hooks-c528)**

또한 기본적으로 Redux가 대규모 프로젝트에서 조금 더 빛을 발하기도 하고 기능도 더 많아 공부해볼 가치가 있다고 생각합니다.

### Redux 레포지토리들
**[``react-redux``](https://github.com/reduxjs/react-redux)**
**[``redux-undo``](https://github.com/omnidan/redux-undo)** 
**[``redux-devtools``](https://github.com/reduxjs/redux-devtools?tab=readme-ov-file)** 


## 2. React Hook
![image](https://github.com/user-attachments/assets/45d52cb2-1315-4a65-aecc-8d708e126d72)

훅이 참 많네요..
React에서 공식적으로 제공하는 훅 말고도 커스텀 훅도 만들 수 있다고 합니다. 이번엔 다루지는 않을 예정입니다.

### 2-1. useCallback
컴포넌트의 부모 컴포넌트가 리렌더링될 때마다 컴포넌트도 리렌더링되게 만들어져 있다면, 이런저런 상황에서 계속해서 불필요한 리렌더링이 실행될 수 있습니다.\
이런 상황들을 최적화하기 위해 메모이제이션을 사용하지만 메모이제이션이 먹통이 되는 상황도 존재합니다.

예를 들면 함수를 포함하는 컴포넌트가 리렌더링되어 함수가 재생성이 된다면, 그 함수 자체가 바뀌는 게 아니라고 하더라도 함수의 주소값이 변하는 일이 일어나 함수가 교체된 것으로 프로그램이 인식, 컴포넌트가 리렌더링되게 되는 상황이 발생할 수 있습니다.

결론적으로는 함수가 재생성되는 것을 막아야 하는 상황들이 생긴다는 것이고, 이때 활용할 수 있는 훅이 useCallback입니다.

`const memoedFunc = useCallback(func, [dependencies])`

### 함수형 업데이트
하지만 useCallback을 사용할 때 주의할 점은 콜백 함수가 state를 다룰 때 state를 추적하기 힘들다는 것입니다.
이것을 방지하기 위해 함수형 업데이트를 사용할 수 있습니다.

```
const onCreate = useCallback(() =>{
    setState([newItem, ...state]);
}, []);
```
이런 식으로 useCallback을 사용하면 망합니다.\
useCallback을 호출한 시점의 state를 저장하고 state의 변화를 감지할 수가 없게 되기 때문입니다.\
이걸 방지하기 위해서 우리는 함수형 업데이트를 사용해보겠습니다.

```
const onCreate = useCallback(() => {
    setState((state) => [newItem, ...state]);
}, []);
```
setState에서 콜백 함수를 전달하는 함수형 업데이트를 사용하면 state의 최신 상태로 전달해줄 수 있어 문제를 해결할 수 있습니다.

교재의 예제에서는 useState이 아닌 useReducer을 사용하고 있어 문제는 없었습니다. (Reducer은 항상 최신 state를 인수로 받기 때문)

## 2-2. useContext
이 부분을 다루기 전에 Context의 개념에 대해 미리 숙지하여야 해서 먼저 공부하였습니다.

**[#1번](#1-contextapi--redux) 참고.**

```
const TodoContext = React.createContext(defaultValue);
```
defaultValue는 Provider 노드가 없을 때 사용될 값이며 코드를 제대로 작성한다면 아마 쓸 일은 없을 것 같습니다.

`Context`를 만들었다면 `Provider`으로 `Context`를 전달해줍니다.

```
  return (
    <div className="App">
      <Header/>
      <- 이런 식으로 ! ->
      <TodoContext.Provider value={{todo, onCreate, onUpdate, onDelete}}>
        <TodoEditor />
        <TodoList />
      </TodoContext.Provider> 
    </div>
  );
```
그리고, Context에서 데이터를 받아올 컴포넌트에서 `useContext`를 사용합니다.
```
const { todo, onUpdate, onDelete } = useContext(TodoContext);
```
이런 식으로 여러 단계에 걸쳐서 Prop을 전달할 필요없이 App에서 데이터를 전달받았습니다.

## 3. React Routing
리액트는 일단 한 페이지 내에서 모든 이벤트를 처리하는 웹 앱을 만드는 데 유용한 도구이고,
라우팅은 기본적으로 보통 백엔드에서 처리하는 부분이지만, 아무튼 간에 리액트로 여러 페이지를 지원하겠다 하면 이런 기능을 활용할 수 있습니다.

```
npm install react-router-dom
```
터미널에서 react-router-dom을 설치해줍니다.

그 후 라우팅을 지원하기 위해서는 두 곳에 설정을 해주어야 하는데,
index.jsx와 App.jsx 모두 설정을 해주겠습니다.

```
import { BrowserRouter } from "react-router-dom";

root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
)
```
App을 BrowserRouter로 감싸주고, 

```
import { Routes, Route } from "react-router-dom";
...

App () => {
  return (
    <div className="App">
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/login" element={<Login />} />
      </Routes>
    </div>
  )
}
```
이런 식으로 접속해서 / 뒤에 오는 url에 따라 다양한 페이지를 보여줄 수 있습니다.\
라우팅은 이 기능보다는 추후 next.js에서 더 다뤄보도록 하겠습니다.
