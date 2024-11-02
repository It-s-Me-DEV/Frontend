# React 더보기

## 목차
- [1. JS 기본 함수들](#1-js-기본-함수들)
- [2. React Hook](#2-react-hook)
    - [2-1. useState](#2-1-usestate)
        - [2-1-1. useState in TS](#2-1-1-usestate-in-ts)
    - [2-2. useRef](#2-2-useref)
- [3. 금주의 프로젝트](#3-금주의-프로젝트)

## 1. JS 기본 함수들
`map()` 함수는 배열을 순회하며 배열 내의 원소에 대하여 어떤 작업을 실행할지 지정해주고 변환된 값을 변환해줍니다. for문 없이 반복문을 실행 + 새로운 배열을 생성할 수 있는 셈입니다!

`filter()` 함수는 배열을 순회하며 콜백 함수의 True, False 여부에 따라 True인 값들만 반환합니다.

`includes()` 함수는 filter에 쓰면 유용할 함수입니다. 배열 또는 문자열에 매개변수로 입력한 요소가 포함되는지 확인하고 Boolean 값을 반환합니다.

```
const searchResult = () =>{
        return search === "" ? todo : todo.filter((item) => item.content.toLowerCase().includes(search.toLowerCase()));    
    };
```
filter과 includes의 사용 예시입니다. 입력값(search)이 없으면 todo를 반환하고 입력값이 todo의 요소들 중에 일치하는 것이 있으면 일치하는 것만 반환하게 만들었습니다.

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

### 2-1-1. useState in TS
```
const [score, setScore] = useState<number>(0);

const scoreUp = () => {
    setScore(score + 1);
};
```
TypeScript에서는 타입지정을 엄격하게 하다 보니 useState에 제네릭 타입을 명시해주는 것이 좋습니다.
지정하지 않더라도 큰 상관은 없었습니다.

### 2-2. useRef
Ref는 Reference의 줄임말로 Ref 객체로 DOM을 조작할 수 있습니다.

DOM에서 포커스 설정, 스크롤 위치 관리, DOM 요소의 크기 측정 등을 하거나\
렌더링을 유발하지 않고 값을 저장해야 할 때 사용할 수가 있습니다.


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
위의 예시는 값이 입력되지 않았을 때 input 태그에 커서가 깜빡깜빡하게 만들어주는 기능입니다. 하지만 잘 작동하지 않아서 주석 처리해뒀네요..

`forwardRef`을 사용하면 컴포넌트의 Ref을 부모 컴포넌트의 DOM 노드를 노출할 수 있습니다.

<b>사용 예시:</b>\
메뉴 바깥 영역을 클릭하면 메뉴가 닫히는 기능을 구현해야 할 때,
메뉴 컴포넌트가 Nav바 내부에 위치하고 있기 때문에,\
메뉴 영역에 해당하는 ref를 Nav 컴포넌트에서 정의해준 후 Hamburger 컴포넌트에 props로 전달해서 제어해주기 위해 forwardRef로 감싸 전달받은 ref를 사용해줌.

## 3. 금주의 프로젝트
교재 「한 입 크기로 잘라 먹는 리액트」 p.289의 Todo 리스트를 완성했습니다.

![image](https://github.com/user-attachments/assets/2c4dc1b4-b52d-486e-a409-96e798e306ed)

CRUD 기준에 맞추어 제작을 했고, 검색 기능이 있습니다.

![image](https://github.com/user-attachments/assets/0f7a9a28-88ab-4881-8858-ead970446029)

이렇게 요소를 추가할 수 있고

![image](https://github.com/user-attachments/assets/b177ebef-1b7a-44f6-aea4-14873438e747)

요소 삭제와 검색을 할 수 있습니다.
