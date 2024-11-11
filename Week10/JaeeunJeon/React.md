# React 협업 개발
React 프로젝트에서 여러 명이 함께 작업할 때는 역할을 명확히 나누는 것이 중요합니다.

### 1. 협업 방식
#### 페이지 단위로 분담
- 각 개발자가 특정 페이지를 담당하여 독립적으로 작업합니다. (예: 홈, 할 일 추가, 설정)
- 페이지가 독립적이므로 통합할 때 충돌이 적고, 각자 효율적으로 작업할 수 있습니다.

#### 컴포넌트 단위로 분담
- 복잡한 UI나 페이지는 세부 컴포넌트로 나눠서 작업합니다. (예: 입력 폼, 할 일 목록, 필터 컴포넌트 등)
- 컴포넌트의 재사용성을 높이고, UI가 복잡할 때 효과적입니다.

#### 공통 컴포넌트 및 스타일링 작업
- 버튼, 모달 등 여러 곳에서 쓰이는 공통 컴포넌트와 스타일을 담당하는 역할을 지정하면 디자인 일관성을 유지할 수 있습니다.

### 2. 상태 관리 및 데이터 흐름
- 페이지 간 상태가 필요하면 Redux나 Context API 사용을 결정하고 데이터 흐름을 미리 정리합니다.

***

# To Do List 클론 코딩 (App.js)
### 1. 초기 데이터 설정 (Mock Data)
```javascript
const mockTodo = [
  {
    id: 0,
    isDone: false,
    content: "React 공부하기",
    createdDate: new Date().getTime(),
  },
  {
    id: 1,
    isDone: false,
    content: "빨래 널기",
    createdDate: new Date().getTime(),
  },
  {
    id: 2,
    isDone: false,
    content: "노래 연습하기",
    createdDate: new Date().getTime(),
  }
]
```
- mockTodo는 테스트용 초기 데이터로 할 일 리스트의 기본 구조를 제공합니다.

### 2. 고유 ID 생성 (useRef 사용)
```javascript
const idRef = useRef(3);
```
- 각 할 일 항목에 고유한 ID를 부여하기 위해 useRef를 사용합니다.

### 3. 상태 관리 (useState 사용)
```javascript
const [todo, setTodo] = useState(mockTodo);
```
- todo는 할 일 리스트 상태이며, setTodo로 업데이트합니다.

### 4. Create: 할 일 추가 함수 (onCreate)
```javascript
const onCreate = (content) => {
  const newItem = {
    id: idRef.current,
    content,
    isDone: false,
    createdDate: new Date().getTime(),
  };
  setTodo([newItem, ...todo]);
  idRef.current += 1;
};
```
- 새로운 할 일 항목을 생성하며, 고유한 ID와 생성일을 기록하고 todo 배열에 추가합니다.

### 5. Update: 할 일 완료 상태 토글 함수 (onUpdate)
```javascript
const onUpdate = (targetId) => {
  setTodo(
    todo.map((it) =>
      it.id === targetId ? { ...it, isDone: !it.isDone } : it
    )
  );
};
```
- targetId에 해당하는 항목의 isDone 상태를 반전시킵니다.

### 6. Delete: 할 일 삭제 함수 (onDelete)
```javascript
const onDelete = (targetId) => {
  setTodo(todo.filter((it) => it.id !== targetId));
};
```
- targetId와 일치하는 항목을 삭제하여 todo 상태를 갱신합니다.

### 7. 컴포넌트 연결
`
<Header />
<TodoEditor onCreate={onCreate} />
<TodoList todo={todo} onUpdate={onUpdate} onDelete={onDelete} />
`
- Header, TodoEditor, TodoList 컴포넌트가 렌더링되며, 필요한 함수와 상태를 props로 전달합니다.
