# React 더보기

## 목차
- [1. JS 기본 함수들](#1-js-기본-함수들)
- [2. React Hook](#2-react-hook)
    - [2-1. useState](#2-1-usestate)
    - [2-2. useRef]()
    - [2-3. useReducer]()
- [4. 금주의 프로젝트](#4-금주의-프로젝트)

## 1. JS 기본 함수들

map

filter

## 2. React Hook
React Hook은 React 16.8 버전에서 처음 도입된 기능으로, 함수형 컴포넌트에서 state와 생명주기 기능을 사용할 수 있도록 해주는 함수입니다.

### 2-1. useState
`const [score, setScore] = useState(0);`\
useState는 컴포넌트 내에서 상태를 나타내는 변수를 만들어줍니다.

위 예시는 0점으로 시작하는 score 변수를 만들어서 setScore로 컨트롤할 수 있게 하는 코드입니다.

```
const scoreUp = () => {
    setScore(score + 1);
};
```

![image](https://github.com/user-attachments/assets/ba0037b4-4430-46c4-b509-930cabb02e4e)

이런 식으로 setScore에는 score와 score의 타입에 맞는 변수를 매개로 넘겨주면 됩니다.



```
const onSubmit = () => {
        if (!content){ // 왜 안 될까요
            inputRef.current.focus();
            alert('내용을 입력해주세요.');
            return;
        }
        onCreate(content);
        setContent('');
    };
```
