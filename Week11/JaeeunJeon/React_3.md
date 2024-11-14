# useReducer
'useReducer'은 React에서 'useState'와 같이 상태 관리와 업데이트를 위한 훅(Hook)이다.
## 언제 'useReducer'을 사용?
- 복잡한 상태 업데이트: 여러 상태의 값을 다루거나 상태 업데이트가 복잡해질 때
- 구조화된 상태 관리: 상태 변화를 더욱 구조화된 방식으로 관리하고자 할 때
- 이전 상태에 의존하는 경우: 상태 업데이트가 이전 상태에 의존할 때
## 문법
```javascript
const [state, dispatch] = useReducer(reducer, initialState);
```
- state: 현재 상태
- dispatch: 상태 변화를 일으키는 함수
- reducer: 액션에 따라 상태를 어떻게 변경할지 정의하는 함수
- initialState: 초기 상태
## 예시
<details>
  <summary>useState 예시</summary>

  ![image](https://github.com/user-attachments/assets/d07c8116-516d-4ae9-82e0-3f9fde46d9c7)
</details>
<details>
  <summary>useReducer 예시</summary>

  ![image](https://github.com/user-attachments/assets/15950bbd-da91-4855-bfbb-a0e6eb90d133)
</details>

***

# 리액트 최적화
## 1. useMemo
'useMemo'는 메모이제이션 기법을 이용하여 연산의 결과값을 저장해두고 필요할 때 사용함으로써, 불필요한 함수 호출을 막하주는 리액트 훅이다.
### 언제 'useMemo'를 사용?
- 복잡한 수식이나 대량의 데이터를 처리하는 등 무거운 계산이 필요한 경우
- 컴포넌트가 리렌더링될 때마다 동일한 계산을 반복할 필요가 없어 불필요한 재계산을 줄이고 싶은 경우
### 문법
```javascript
const memoizedValue = useMemo(() => {
  return calculate(data);
}, [data]);
```
- 두개의 인자를 받는다.
  - 첫 번째 인자: 반환값을 기억하고 싶은 함수
  - 두 번째 인자: 의존성 배열, 의존성 배열에 있는 값이 변경될 때만 함수를 다시 실행하여 결과를 갱신

## 2. React.memo
'React memo'는 React에서 컴포넌트가 불필요하게 리렌더링되는 상황을 방지하기 위해 사용하는 기능이다.
메모이제이션 기법을 활용해 이전에 렌더링한 결과를 저장해두고, 다음에 같은 props로 렌더링 요청이 들어오면 저장된 결과를 재사용한다.
### 언제 'React.memo'를 사용?
- 불필요한 리렌더링을 줄이고 싶은 경우
- 복잡한 UI 요소가 있거나, 연산이 많은 컴포넌트에서 사
### 어떻게 동작?
React.memo는 컴포넌트를 감싸서 만든다.

## 3. useCallback
'useCallback'은 컴포넌트가 리렌더링될 때마다 동일한 함수가 다시 생성되지 않도록 메모이제이션하는 리액트 훅이다.
### 왜 사용?
리액트에서는 컴포넌트가 리렌더링될 때마다 내부에 작성된 함수도 새로 만들어진다. 만약 해당 함수가 자주 사용되는 함수거나, 자식 컴포넌트에 props로 전달되는 함수라면 불필요한 리렌더링이 발생할 수 있다. useCallback을 사용하면 특정 의존성 배열에 변화가 생기지 않는 한, 이전에 생성된 함수를 재사용하기 때문에 성능을 개선할 수 있다.
### 언제 'useCallback'을 사용?
- 이벤트 핸들러, API 호출 등 자주 리렌더링되는 컴포넌트의 함수인 경우
- 자식 컴포넌트에 불필요하게 새로운 함수를 전달하는 것을 방지하고 싶은 경우

## 성능 최적화 도구들 차이점
- useMemo: 값이나 결과를 기억해, 매번 계산하지 않고 필요할 때만 계산한다.
- React.memo: 컴포넌트(화면에 렌더링되는 역할) 전체를 기억해, 불필요한 리렌더링을 막는다.
- useCallback: 함수(특정 작업이나 연산을 수행하는 역할) 자체를 기억해, 리렌더링 시 새로 만들지 않는다.
