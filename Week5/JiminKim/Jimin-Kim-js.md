# JavaScript

## 목차
- [1. Javascript란?](#1-javascript란)
- [2. Javascript 사용법](#2-javascript-사용법)
    - [2-1. Javascript 기초 문법](#2-1-javascript-기초-문법)
    - [2-2. EC6 문법](#2-2-es6-문법)
- [3. JavaScript의 주요 활용 예시](#3-javascript의-주요-활용-예시)
- [4. 금주의 프로젝트](#4-금주의-프로젝트)

## 1. JavaScript란?

[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)\
JavaScript는 웹 상에서 브라우저가 웹 페이지를 제어하고 동적인 변화를 제어하기 위하여 만들어진 스크립트 언어입니다.

원래 웹 브라우저에서만 쓰기 위해 개발되었으나, Node.js의 발명으로 웹 브라우저 외부에서 서버 사이드 개발도 가능해졌고 여러 가지 프로그램을 제작하는 데에 무궁무진한 활용을 할 수 있게 되었습니다.

![js_thanks](https://github.com/user-attachments/assets/9a939748-23b6-4af6-a5ed-ee7e5d67919d)
그러나 이 언어 자체가 필요에 의해 굉장히 급조된 성격을 지녀서 위의 짤처럼 이해할 수 없는 문법, 보안 문제 등이 화두가 되기도 합니다.\
개발자들 사이에서 농담 반 진담 반으로 최악의 언어라는 별명을 붙이기도 합니다.

이러한 단점들로 인해 현재는 JavaScript의 단점을 보완한 TypeScript를 사용하는 경향이 있습니다.

https://aierse.tistory.com/16\
TypeScript 또한 사장될 거라는 재미있는 의견도 발견해서 들고 와봤습니다.
## 2. JavaScript 사용법
JavaScript(이하 JS)는 HTML 문서 내에서 직접적으로 <b>\<script></b> 태그를 사용하여 작성하거나 따로 .js 파일을 작성 후 HTML 파일에서 호출하는 방식으로 쓸 수 있습니다.

### 2-1. JavaScript 기초 문법
https://ko.javascript.info/javascript-specials\
JS 문법은 자료형이 지정하지 않는다는 것을 제외하면 C언어와 유사합니다.

### 2-2. ES6 문법
JS는 시간이 갈 수록 버전이 업데이트되며 더 많은 기능들이 추가됩니다. ESMAScript 6 버전은 가장 모던한 방식의 문법입니다.\
더 세련된 문법을 여러 개 소개해보겠습니다.

- Arrow function

    원래 JS에서는 함수를 선언할 때
    ```
    const func = function(x){
        console.log(x);
    }
    ```
    `function()`을 쓰는데, 이제는 그렇게 할 필요 없이
    ```
    const func = (x) => {
        console.log(x);
    }
    ```
    Arrow function 기능을 쓰면 더 멋있게 함수를 선언할 수 있습니다.\
    개인적으로 JS에서는 함수에서 변수로 함수를 부르는 경우가 많은데, 이럴 때 사용하기 좋은 것 같습니다.

- let과 const 선언
    
    원래 JS에서는 변수를 생성할 때 var을 사용했었는데, 이제는 여러 기술적 이슈로 인하여 let과 const를 사용하여 변수를 선언합니다.
    ```
    var x = 3; // old style

    let y = 3;
    const z = 3; //ES6 style
    ```
    기본적인 특징으로는 let과 const는 재선언이 불가능해서 더 안전하고 block scope를 가진다고 합니다.

    장점만 있는 것은 아닌데, var은 Hoisting이라고 하는 기법인 위에서 값 초기화 없이 선언만 해두고 나중에 할당하는 방식을 지원합니다... 표준 문법은 var은 안 쓰는 걸 추천한다고 합니다.

- async / await

    JS에서 가장 특징적인 기능인 `promise()`와 `callback`을 가장 세련되게 쓰는 방법 `async`, 그리고 `await`입니다.
    JS가 의도와는 다르게 실행 속도 차이로 인하여 코드 아랫줄이 윗줄보다 먼저 실행되는 상황과 같은 일을 피하기 위해 사용될 수 있습니다.

## 3. JavaScript의 주요 활용 예시
JavaScript가 보통 어떨 때 쓰이는지 제 코드에서 활용 예시를 가져와봤습니다.

```
const gnbOpener = document.querySelector("#gnb-opener");
const gnbMenu = document.querySelector(".gnb-menu");
const menu = document.querySelector(".menu");

gnbOpener.addEventListener("click", ()=> {
    gnbMenu.classList.toggle('show');
    menu.classList.toggle('show');
});
```
`document.querySelector()` 함수는 현재 HTML 페이지에서 () 안에 든 내용을 찾아서 지정해줍니다.\
지금 코드에서는 gnb-opener이라는 id를 가진 엘리먼트를 찾아 gnbOpener에 담아주었습니다.

그리고 밑에 `.addEventListener("event", function)`를 통해 엘리먼트를 클릭하는 이벤트가 발생시에 function을 실행해주도록 코드를 작성하였습니다.\
여기서 2-2에서 소개해드렸던 Arrow Function을 활용해보았습니다.

## 4. 금주의 프로젝트
https://nowimseeingcashflow.github.io/

https://github.com/nowimseeingcashflow/Portfolio-Fe

이제 내용적으로 부족한 부분들을 제외하면 거의 완성입니다.
