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
