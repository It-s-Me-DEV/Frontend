# React & TypeScript

## 목차
- [1. React Hook](#1-react-hook)
    - [1-1. useEffect](#1-1-useeffect)
    - [1-2. useReducer](#1-1-useeffect)
    - [1-3. useMemo](#1-1-useeffect)
- [2. 금주의 프로젝트](#2-금주의-프로젝트)

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

### 1-2. useReducer


### 1-3. useMemo

