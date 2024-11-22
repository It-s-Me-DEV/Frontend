# Next.js

## 목차
- [1.TypeScript](#1-typescript)
- [2. Next.js](#2-nextjs)
    - [2-1. 환경 설정](#2-1-환경-설정)
    - [2-2. 파일 구조와 라우팅](#2-2-파일-구조와-라우팅)
- [3. 프로젝트](#3-프로젝트)

## 1. TypeScript
### 타입스크립트를 사용하고 싶다면
```
npx create-react-app my-app --template typescript

또는

tsc --init
```
CRA로 리액트 앱을 만들 때 TypeScript를 사용하겠다고 명시해주거나 이미 만든 프로젝트에서 initialize 해주고 `tsconfig.json` 파일이 생깁니다.

### Type
타입스크립트에서 타입 지정은 정말 중요한데요, 사용법은 이렇습니다.

`const num : number = 3`

변수명에 : type 을 지정해줍니다.

```
function isHungry ( food : string ) : boolean {
        ...
    }  
```
함수에도 적용 가능합니다.

```
type State =
	| {
			type: 'idle';
	  }
	| {
			type: 'dragging';
	  };

```
이런 식으로 여러 타입을 가질 수 있는 아예 새로운 타입을 만드는 것도 유효하며, 이 방식을 Union이라고 합니다..

### 예외 처리
TypeScript는 엄격한 언어이기 때문에 null, undefined 등이 들어가면 안 되는 곳에 들어갈 상황을 발견하면 컴파일 중에 에러를 냅니다.

이런 예외 상황들을 잘 처리해야 오류 없는 코드를 작성할 수 있습니다.

다음과 같은 방법이 있습니다:

**1. if문 사용**
```
const dividerRef = useRef<HTMLDivElement | null>(null);
if (!dividerRef){
    ...
}
```
간단하게 ! 처리하면 에러 없이 실행할 수 있습니다.
하지만 매번 if문을 쓰는 게 번거로울 수 있다는 문제가 있을 수 있습니다.

예외 처리를 간단하게 만들어주는 이런 라이브러리도 있습니다.\
[`tiny-invariant`](https://github.com/alexreardon/tiny-invariant?tab=readme-ov-file)

**2. Optional Chaining**

`?.` 이라는 문법이 있습니다.

.으로 이어지는 체인의 각 참조가 유효한지 명시적으로 검증할 필요 없이, 연결된 객체가 nullish (null 또는 undefined)이라면, 에러가 발생하는 것 대신에 표현식의 값은 undefined가 됩니다. 

이런 방식을 이용하면 더 깔끔한 코드를 작성할 수 있습니다.

```
contentRef.current?.style.removeProperty('--local-resizing-width');
```
제가 이번에 사용한 코드입니다.

contentRef.current의 style이 없다면 자동으로 뒤의 함수는 실행되지 않을 것입니다.

## 2. Next.js
### 2-1. 환경 설정
https://nextjs.org/learn 과 [생활코딩 Next.js 강의](https://www.youtube.com/watch?v=9KOaR6QMb9A&list=PLuHgQVnccGMCwxXsQuEoG-JJ7RlwtNdwJ)를 참고하였습니다.

다만 영상 강의가 13버전 기반인데, Next.js는 지난 달 15 버전으로 업데이트가 되었습니다. 호환성 문제가 있을 수 있습니다.

터미널에서 `npx create-next-app@latest [폴더명]` 을 실행하는 것으로 next.js 앱을 바로 만들 수 있습니다.

![image](https://github.com/user-attachments/assets/74831b55-0137-47f3-9929-c3d272993a6b)

자동으로 TypeScript, ESLint, Tailwind CSS 등등을 사용할 것인지 물어봐줍니다. 굉장히 편리합니다.

### 2-2. 파일 구조와 라우팅
기본적으로 Next.js에서는 `page.tsx`, `layout.tsx`에서 페이지를 보여줍니다. (js, jsx, ts 지원)

```
// layout.tsx

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```
```
// pages.tsx
export default function Page() {
  return (
    <main className="flex min-h-screen flex-col p-6">
      ...
    </main>
  );
}
```

page.tsx에서 export한 `Page()`를 layout.tsx에서 `children`으로 받아 페이지를 표시합니다.

![image](https://github.com/user-attachments/assets/d47b79c4-5bf0-4dd2-b214-99d2aaf2506a)
라우팅도 간단하게 진행되는데, url path가 /id라 하면,\
app 폴더 내에 /id 폴더를 생성하고 또 다른 layout.tsx와 page.tsx를 만들면 됩니다.

## 3. 프로젝트

pragmatic-drap-and-drop 이라는 라이브러리를 사용하여 사이드바의 넓이를 드래그로 조정할 수 있는 기능을 만들어보았습니다.
공식 문서에 있는 예제를 참고하여서 만들었습니다!

![img](https://github.com/user-attachments/assets/a3f3d809-a5fd-4754-a70d-ae550b0778de)

https://jimmin.tistory.com/1

세부적인 내용은 블로그에 작성해두었습니다.
