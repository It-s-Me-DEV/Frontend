# React & TypeScript

## 목차
- [1. React Hook](#1-react-hook)
    - [1-1. useEffect](#1-1-useeffect)
    - [1-2. useReducer](#1-2-usereducer)
    - [1-3. useMemo](#1-3-usememo)
- [2. contextAPI](#2-contextapi)
- [3. tailwindCSS](#3-tailwindcss)

## 1. React Hook
### 1-1. useEffect
리액트 컴포넌트는 '마운트 - 업데이트 - 언마운트'의 생애 주기를 가집니다. 이 생애 주기 동안에 컴포넌트는 렌더링 과정을 거치기도 하고 렌더링 없이 특정 값만 변할 수도 있습니다. 이러한 변화를 감지하여 변화할 때마다 함수를 실행하게 만들 수 있는 훅이 바로 useEffect입니다!

`useEffect(callback, [dependencies?])`

useEffect의 콜백 함수가 dependencies 배열에 속하는 것들의 변화가 감지되었을 때 실행됩니다.

dependencies 는 선택사항입니다.
아무 것도 입력되지 않았을 때에는 컴포넌트가 리렌더링되면 콜백 함수가 실행됩니다.\
https://shinbian11.tistory.com/103 참고

deps 요소가 여러 개 있을 때도 마찬가지로 모든 경우에 로직이 실행됩니다.
```
useEffect(() => {
        console.log(count);
    }, [count]);

    return(
        <div>
            <h3>숫자 세기</h3>
            <b>{count}</b><br/>
```
![image](https://github.com/user-attachments/assets/8378a83c-e50c-4680-9f9b-841b3fee8887)

useEffect의 콜백 함수는 반환값이 없거나 clean up 함수를 반환해야 합니다.

그래서 async - await 함수를 사용하려면 함수 내에서만 구현하거나 다른 방법을 찾아야 합니다.\
https://lakelouise.tistory.com/308

### 1-2. useReducer
`useReducer(reducer, initialState)`

useReducer은 useState와 같이 상태관리를 위하여 사용되는 훅이다.
상태전환에 사용된다는 점에서 둘 사이에 큰 차이가 없거나 useReducer이 더 범용적이라고 생각되기도 하는데, 무슨 차이가 있는지 알아보자면,

| 특징      | useState                | useReducer                        |
| ------- | ----------------------- | --------------------------------- |
| 용도      | 간단한 상태 관리               | 복잡한 상태 관리, 순수 함수 활용               |
| API     | useState(initialState)  | useReducer(reducer, initialState) |
| 상태 업데이트 | setState 함수를 통해 직접 값 변경 | dispatch 함수를 통해 action 객체 전달      |
| 장점      | 간단하고 직관적                | 복잡한 로직 관리에 용이, 순수 함수 활용           |
| 단점      | 복잡한 로직에는 부적합            | 초기 설정이 복잡할 수 있음                   |

이런 식으로 대조해볼 수 있겠습니다. 

교재 예시를 통해 활용 방법을 보자면
```
const reducer = (state, action) => {
    switch(action.type){
        case "INCREASE" :
            return state + action.data;
        case "DECREASE" :
            return state - action.data;
        case "RESET" :
            return action.data;
        default :
            return state;
    }
}
const TestComp = () => {
    const [count, dispatch] = useReducer(reducer, 0);

    return(
        <div>
            <h3>숫자 세기</h3>
            <b>{count}</b><br/>
            <button onClick={() => dispatch({ type : "INCREASE", data : 1})}>+</button>
            <button onClick={() => dispatch({ type : "DECREASE", data : 1})}>-</button>
            <button onClick={() => dispatch({ type : "RESET", data: 0})}>초기화</button>
        </div>
    );
}
```
이런 식으로 count를 조작할 때의 함수를 컴포넌트 함수 외부로 빼내어 사용이 가능하다는 특징이 있고, 좀 더 세부적인 상태 변화를 다룰 수 있어 차별점이 있습니다.

### 1-3. useMemo
`const v = useMemo(callback, [dependencies])`

useMemo는 Memoization을 사용하는 방법입니다. 용어부터 생소해서 조금 검색을 해보았는데, 결국 메모리를 효율적으로 다루는 방법이고 알고리즘 중에 Dynamic Program과 일맥상통한다고 할 수 있습니다.

어떨 때 이 기능을 쓰면 좋을까요?\
아무래도 무거운 함수 등이 여러 번 실행되는 걸 방지하는 데에 쓰는 것이 좋을 것입니다.

```
import { useState } from "react";
 
const hardCalculate = (number) => {
  console.log("어려운 계산!");
  for (let i = 0; i < 200000000; i++) {} // 생각하는 시간
  return number + 10000;
};

const easyCalculate = (number) => {
  console.log("쉬운 계산!");
  return number + 1;
};

function App() {
  const [hardNumber, setHardNumber] = useState(1);
  const [easyNumber, setEasyNumber] = useState(1);

  const hardSum = hardCalculate(hardNumber);
  const easySum = easyCalculate(easyNumber);

  return (
    <div>
      <h3>어려운 계산기</h3>
      <input
        type="number"
        value={hardNumber}
        onChange={(e) => setHardNumber(parseInt(e.target.value))}
      />
      <span> + 10000 = {hardSum}</span>
      
      
      <h3>쉬운 계산기</h3>
      <input
        type="number"
        value={easyNumber}
        onChange={(e) => setEasyNumber(parseInt(e.target.value))}
      />
      <span> + 1 = {easySum}</span>
    </div>
  );
}

export default App;
```
https://velog.io/@jinyoung985/React-useMemo%EB%9E%80 참고

hardCalculate는 for문이 2억번 돌아가서 시간이 오래 걸리는 함수입니다.
계산기에서 버튼을 누르면 useState의 함수가 작동해 컴포넌트가 재렌더링되고 이는 hardCalculate가 재작동하게 만들게 됩니다.
심지어 easyCalculate를 쓸 때에도 딜레이가 발생하게 되죠. 이러면 너무 비효율적입니다.

이때 `const hardSum = hardCalculate(hardNumber);` 를
```
const hardSum = useMemo(() => {
    return hardCalculate(hardNumber);
  }, [hardNumber]);
```
이렇게 바꿔보겠습니다.

변경 후에는 hardNumber가 바뀌는 게 아닌 이상 딜레이가 생기지 않게 됩니다. 

## 2. contextAPI

앞서 만든 Todo리스트 앱에서 가장 큰 문제가 있었습니다. 이는 Props drilling 문제인데 Prop을 가장 하위 자녀 클래스에 있는 컴포넌트로 보내주기까지 똑같은 작업을 너무 많이 수행해야 한다는 뜻입니다.

App → TodoList로, TodoList → TodoItem으로 똑같은 함수 onUpdate, onDelete를 전달해주어야 합니다.

물론 이 앱에서는 2단계의 전달뿐이었지만 단계가 늘면 늘수록 작성해야 할 코드가 증가하지 않을까요? 

![image](https://github.com/user-attachments/assets/d6217f39-f205-4883-ab2a-6239009807a5)

React 자체적으로 있는 Context 기능을 통해서 같은 문맥에 있는 컴포넌트에서 데이터를 공급할 수 있는 기능을 배워보겠습니다.

실무에서는 Redux라는 라이브러리를 이용해서 이런 Prop을 관리한다고 알고 있는데 비슷한 기능인 것 같습니다.


## 3. TailwindCSS
앱을 수정하는 과정에서 React에서는 마우스 hover를 처리할 때 조금 복잡한 과정을 거친다는 것을 알게 되었습니다. 귀찮은 과정을 거치기보다 편하게 가기 위해 TailwindCSS를 도입해보았습니다.

```
npx tailwindcss init
```
터미널 환경에서 설치하면 프로젝트에 `tailwind.config.js`라는 파일이 생성되며 TailwindCSS를 사용할 수 있게 되었습니다.

`postcss.config.js` 로 설치하여 @ 문법에 오류가 생기지 않게 하였고, index.css의 맨 앞에
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```
를 추가해주었습니다!

Tailwind 문법이 조금 복잡하긴 한데, 구글에 사용하고 싶은 기능을 검색하면 바로 Tailwind의 공식 문서가 친절하게 나와 설명해주어서 CSS를 옮기는 데에 큰 문제가 없었습니다. 추가로 AI의 도움으로 바로 클래스명을 받아서 쓸 수 있었습니다.

![image](https://github.com/user-attachments/assets/b362acb4-d5be-4ed4-9ee0-eddb5a8eaa12)
