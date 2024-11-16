# React 1장부터 Routing까지

---

### jsx의 논리 표현식의 결과인 불리언 값은, 숫자나 문자열과 달리 페이지에 렌더링되지 않기 때문에, 주로 조건식 렌더링에서 사용합니다.

```jsx
const isDone = false;
<h1>
    {isDone ? "hi" : "bye"}
</h1>
```

### jsx는 원시 자료형만 받을 수 있습니다.

```jsx
const obj = {name:"abcd"};
{obj} // error
```

---

### 리액트에서는, 데이터를 전달할 때 Props라는 단일 객체 형태로 전달합니다.
```jsx
<Comp data1={"ab"} data2={"cd"} />

const Comp = ({ data1, data2 }) => { . . . }
```

---

### useState는, 값을 변경하며 리렌더링합니다.

### 드롭다운 입력 폼에서 option의 key 프로퍼티에 데이터를 주어야 State가 데이터를 선택할 수 있습니다.

---

### 부모 컴포넌트가 리렌더되면, 자식도 함께 리렌더됩니다.

## Lifecycle

- 마운트 : 컴포넌트를 페이지에 처음 렌더링할 때
- 업데이트 : State나 Props의 값이 바뀌거나, 부모 컴포넌트가 리렌더해 자신도 리렌더될 때
- 언마운트 : 더 이상 페이지에 컴포넌트를 렌더링하지 않을 때

### useEffect를 이용하여 동적 변수가 변경될 때마다 콜백 함수를 실행합니다. useEffect는 렌더링이 끝난 다음에 실행됩니다.

```jsx
useEffect(() => {
    // 마운트, 업데이트 시 실행
    const intervalID = setInterval(() => {
        console.log("깜빡")
    }, 1000);

    // 업데이트 되기 직전 실행
    return () => {
        console.log("클린업");
        clearInterval(intervalID);
    }
});
```

---

### useReducer를 사용하여, 상태 변화 코드를 컴포넌트 외부에 작성합니다.

```jsx
function reducer(state, action) {
    switch(action.type) {
        "INCREASE": {return . . .}
        default: {return . . .}
    };
}

const Comp = () => {
    const [count, dispatch] = useReducer(reducer, 0);

    dispatch({ type: "INCREASE", data: 1});
};
```

---

## 리액트 앱에서의 연산 최적화는, 메모이제이션 기법을 사용합니다.

1. useMemo : 함수의 반환값을 기억해서, State 변수가 변했을 때만 콜백 함수를 다시 호출합니다.
```jsx
const { totalCount, doneCount, notDoneCount } = analyzeTodo();

const aT = useMemo(() => { analyzeTodo() }, [stateV]);
```
2. React.memo : 부모 컴포넌트에서 전달한 Props가 변경되지 않는 한 리렌더되지 않습니다. 리렌더 할 시에 함수를 다시 생성하지 않는 useCallback과 함께 사용합니다.
```jsx
const MemoizedComp = React.memo(Comp);

const CompA = React.memo(() => {
  console.log("컴포넌트가 호출되었습니다.");
  return <div>CompA</div>;
});

// 두 번째 인수로 판별 함수를 전달할 수 있습니다. a가 변경될 때만 리렌더합니다.
function areEqual(prevProps, nextProps) {
  if(prevProps.a === nextProps.a) {
    return true; // true 반환 시 리렌더 X
  } else {
    return false; // false 반환 시 리렌더 O
  }
}

const MemoizedComp1 = React.memo(Comp, areEqual);
```

### 최적화할 때 유의할 점
1. 최적화는 항상 마지막에
2. 연산량이 많은 것만 최적화
3. 컴포넌트 분리가 잘 되어있는지 확인 후 최적화
4. 이것은 그저 리액트 최적화일 뿐이며 웹 최적화는 따로 배워야 한다

---

## Context

### Context는 컴포넌트 트리 전체 또는 일부를 대상으로 데이터를 공급하기에, 컴포넌트 사이의 데이터 교환 구조를 파악하기 어렵게 만드는 Props Drilling 문제를 해결할 수 있습니다.

### 같은 문맥 아래의 컴포넌트들을 하나로 묶습니다.

### 예시 (Main은 Body의 자식)
```jsx
import React from 'react';

// createContext로 Context를 생성합니다.
// defaultValue는 생략 가능합니다.
const MyContext = React.createContext(defaultValue);

// ContextName.Provider로 데이터를 공급할 컴포넌트를 묶습니다.

// Provider 컴포넌트는, Props로 공급할 데이터를 받아
// 컴포넌트 트리에서 자신보다 하위에 있는 모든 컴포넌트에 데이터를 공급합니다.
...
<MyContext.Provider value={data}>
  <Body/>
</MyContext.Provider>

// in Main.js
function Main() {
  // useContext로, 해당 Context가 공급하는 값을 반환합니다.
  const data = useContext(MyContext);
  ...
}
```

### Context는 리렌더 문제로 인해 반드시 컴포넌트 밖에서 생성해야 합니다.

### Context의 Provider 또한 컴포넌트이므로, 다른 컴포넌트들과 똑같이 리렌더된다고 생각하면 됩니다.

### 불필요한 리렌더 발생 방지를 위해서는 Context를 중복하는 것도 필요할 때가 있습니다.