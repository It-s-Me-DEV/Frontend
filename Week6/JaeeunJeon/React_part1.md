## 00. 시작하며
리액트는 Node.js 기반의 자바스크립트 라이브러리이다. 따라서 자바스크립트와 Node.js를 모르면 리액트를 다루기 어렵다. 이 단원에서는 리액트를 시작하기 전 알아야 할 필수적인 자바스크립트 개념을 다룬다.

## 01. 자바스크립트

### [1] 변수와 상수

#### 1) 변수
변수는 데이터를 저장할 수 있는 이름이 있는 저장소이다. `let` 키워드를 사용하여 변수를 선언한다.

```javascript
let 변수명 = 값;
```

#### 2) 상수
`const` 키워드를 사용해 상수를 선언할 수 있다. 상수는 한 번 값을 할당하면 변경할 수 없다.

```javascript
const 상수명 = 값;
```

##### 💡 개념 요약:

let은 재할당이 가능한 변수를 선언할 때 사용한다.
const는 재할당이 불가능한 상수를 선언할 때 사용한다.

***

### [2] 형 변환

#### 1) 명시적 형 변
명시적 형 변환은 개발자가 직접 형 변환을 명시하여 수행하는 것이다.

##### (1) `Number` 함수
문자열을 숫자로 변환한다.

```javascript
Number("123");  // 123
```

##### (2) `parseInt` 수
숫자와 문자가 혼합된 문자열을 숫자로 변환한다. 문자열의 첫 문자가 숫자가 아니면 `NaN`을 반환한다.

```javascript
parseInt("123abc");  // 123
parseInt("abc123");  // NaN
```

##### 💡 개념 요약:

명시적 형 변환은 함수들을 통해 수행되며, 변환 실패 시 NaN을 반환할 수 있다.

***

### [3] 반복문

#### 1) 화살표 함
익명 함수를 간결하게 작성할 수 있는 함수 표현식의 단축 문법이다.

```javascript
let funcA = (매개변수) => {
    return 반환값;
};
```

***

### [4] 배열과 메서드
자바스크립트에서는 배열을 쉽게 다룰 수 있도록 다양한 메서드를 제공한다.

#### 1) 요소의 추가와 삭제

##### (1) 요소 추가: `push`, `unshift`
`push`는 배열의 끝에, `unshift`는 배열의 앞에 요소를 추가한다.

```javascript
let arr = [1, 2, 3];
arr.push(4);  // [1, 2, 3, 4]
arr.unshift(0);  // [0, 1, 2, 3, 4]
```

##### (2) 요소 삭제: `pop`, `shift`
`pop`은 배열의 마지막 요소를, `shift`는 배열의 첫 번째 요소를 제거한다.

```javascript
arr.pop();  // [0, 1, 2, 3]
arr.shift();  // [1, 2, 3]
```

#### 2) 배열 순회 메서드

##### (1) `forEach`
배열의 각 요소를 순회하며 함수를 실행한다.

```javascript
arr.forEach((item) => {
    console.log(item);
});
```

#### 3) 탐색 메서드

##### (1) `indexOf`
특정 요소의 인덱스를 반환한다. 요소가 없으면 `-1`을 반환한다.

```javascript
arr.indexOf(2);  // 1
arr.indexOf(5);  // -1
```

##### (2) `includes`
배열에 특정 요소가 있는지 여부를 `true` 또는 `false`로 반환한다.

```javascript
arr.includes(2);  // true
arr.includes(5);  // false
```

***

### [5] Date 객체와 날짜
`Date` 객체는 날짜와 시간을 다루는 데 사용된다. 현재 시간이나 특정 날짜를 설정하고 조작할 수 있다.

#### 1) Date 객체 생성
현재 시간을 기준으로 새로운 `Date` 객체를 생성할 수 있다.

```javascript
let date = new Date();
```

#### 2) Date 객체에서 날짜 요소 얻기
연도, 월, 일, 시간 얻기

```javascript
date.getFullYear();  // 연도 반환
date.getMonth();  // 월 반환 (0부터 시작, 0이 1월)
date.getDate();  // 일 반환
date.getHours();  // 시간 반환
```

#### 3) Date 객체 출력하기

`toString`: 현재 날짜와 시간을 문자열로 반환

```javascript
date.toString();  // "Fri Oct 11 2024 10:00:00 GMT+0900"
```

`toLocaleDateString`: 지역화된 날짜 형식으로 반환
```javascript
date.toLocaleDateString();  // "2024-10-11"
```

***

### [6] 비동기 처리
비동기 처리는 시간이 오래 걸리는 작업을 처리하면서도 다른 작업을 동시에 수행할 수 있게 한다.

#### 1) 동기와 비동기
동기적 처리에서는 코드가 순서대로 실행되지만, 비동기적 처리에서는 특정 작업이 완료될 때까지 기다리지 않고 다른 작업을 실행할 수 있다.

##### (1) 동기: 순차적으로 코드 실행

```javascript
console.log("작업 1");
console.log("작업 2");  // 순서대로 실행
```

##### (2) 비동기: 특정 작업이 완료될 때까지 기다리지 않고 다른 작업을 실행
`setTimeout` 함수는 지정한 시간이 지나면 특정 코드를 실행하는 비동기 함수이다.
```javascript
setTimeout(() => {
    console.log("비동기 작업");
}, 1000);
console.log("동기 작업");
```

#### 2) 프로미스 객체를 이용한 비동기 처리

```javascript
let promise = new Promise(function(resolve, reject) {
    let 작업성공 = true;
    
    if (작업성공) {
        resolve("작업 성공!");
    } else {
        reject("작업 실패!");
    }
});

promise.then(function(result) {
    console.log(result);
}).catch(function(error) {
    console.log(error);
});
```

##### 💡 개념 요약:

비동기 처리는 오래 걸리는 작업이 있더라도 애플리케이션이 멈추지 않고 다른 작업을 동시에 수행할 수 있게 한다.
