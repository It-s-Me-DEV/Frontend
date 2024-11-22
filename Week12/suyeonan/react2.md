# 리액트 최적화
### 1. 리액트 최적화란?
##### - 불필요한 리렌더링을 줄여 성능 개선
##### -> 메모이제이션: 결과값을 메모리에 저장해뒀다가 동일한 요청이 들어올시 저장한 결과값을 제공하는 기술
---
### 2. React.memo 기법
#### (1) 개념
```js
const memoizedComp = React.momo(Comp);
```
##### - 메모이제이션을 적용하고 싶은 컴포넌트를 인수로 전달함
##### -> 기존 컴포넌트에서 기능이 추가된, 더 강화된 컴포넌트로 반환함
##### - props 변경 시에만 컴포넌트가 리렌더되도록 함
##### -> 부모 컴포넌트가 리렌더링되어도, props가 변경되지 않으면 자식 컴포넌트를 리렌더링하지 않음
####  (2) 주의
##### - 부모 컴포넌트에서 복잡한 데이터(ex. 함수, 배열 등)를 props 로 전달할 때 문제 발생 
##### -> 리렌더링시 이 데이터가 다시 생성돼 참조값이 변경됨 (동일한 기능을 수행할지라도)
##### -> React.memo는 참조값의 변경을 props 변경으로 판단해 자식 컴포넌트도 리렌더링됨
---
### 3. useCallback 기법
#### (1) 개념
##### - 컴포넌트가 리렌더링될 때 내부에 작성된 함수를 다시 생성되는 것을 방지함
```js
const memoizedFunc = useCallback(func, deps);
// func는 콜백 함수, deps는 의존성 배열
```
##### - 의존성 배열의 값이 바뀔 때 콜백 함수를 다시 생성해 반환
#### (2) 주의
```js
// 의존성 배열로 빈 배열이 전달
const memoizedFunc = useCallback(func, []);
```
##### - 콜백 함수를 어떤 경우에도 생성하지 않음
##### -> React.memo의 문제점을 해결해주는 동시에, 함수 내부에서 사용하는 값이 변경되더라도 초기값만 반환되는 문제 발생함
```js
// 함수형 업데이트 기능 사용시 문제 해결
const increment = useCallback(() => {
  setState(func); 
}, []);

```
##### - setState의 인수로 콜백 함수 전달시 항상 최신 state 값 반환
---
### 4. Lazy Loading
##### - 필요한 리소스(예: 이미지, 컴포넌트, 데이터 등)를 즉시 로드하지 않고, 사용자가 해당 리소스에 접근할 때 로드하는 기술
##### - 초기 로딩 시간, 네트워크 사용량 감소
```js
// 리액트에서 활용
const LazyComponent = React.lazy(() => import('./LazyComponent')); // React.lazy: import()를 활용해 컴포넌트를 동적으로 로드

function App() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense> // Suspense: 로드 중 로딩 상태를 보여줄 UI를 정의
  );
}
```










