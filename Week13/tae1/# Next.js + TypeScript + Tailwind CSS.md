
# Next.js + TypeScript + Tailwind CSS 프로젝트 가이드

이 문서는 Next.js를 사용하여 TypeScript와 Tailwind CSS를 함께 활용하는 방법에 대해 다룹니다. Next.js 프로젝트 설정과 디렉토리 구조에 대해 자세히 설명합니다.

---

## 📖 목차
1. [Next.js란 무엇인가?](#1-nextjs란-무엇인가)
   - [Server-side Rendering (SSR)](#server-side-rendering-ssr)
   - [Static Site Generation (SSG)](#static-site-generation-ssg)
2. [Next.js와 React의 차이점](#2-nextjs와-react의-차이점)
3. [프로젝트 초기 설정](#3-프로젝트-초기-설정)
   - [Node.js 설치 확인](#nodejs-설치-확인)
   - [Next.js 프로젝트 생성](#nextjs-프로젝트-생성)
4. [Tailwind CSS 설정](#4-tailwind-css-설정)
   - [Tailwind CSS 설치](#tailwind-css-설치)
   - [Tailwind 설정 파일 수정](#tailwind-설정-파일-수정)
   - [글로벌 CSS 추가](#글로벌-css-추가)
5. [디렉토리 구조](#5-디렉토리-구조)
   - [전체 구조](#전체-구조)
   - [디렉토리별 상세 설명](#디렉토리별-상세-설명)

---

## 1. Next.js란 무엇인가?

Next.js는 React를 기반으로 한 웹 프레임워크로, 다음과 같은 기능을 제공합니다:

- **서버사이드 렌더링 (SSR)**: 각 요청마다 서버에서 HTML을 생성합니다.
- **정적 사이트 생성 (SSG)**: 빌드 시 HTML을 생성하여 정적 파일로 배포합니다.
- **SEO 최적화**: SSR과 SSG를 통해 검색 엔진 친화적인 페이지를 제공합니다.

### Server-side Rendering (SSR)
- 요청 시 데이터를 서버에서 가져와 HTML을 생성합니다.
- **사용 예:** 사용자 맞춤 데이터를 표시하는 대시보드.

### Static Site Generation (SSG)
- 빌드 시 HTML을 생성해 정적 파일로 제공.
- **사용 예:** 자주 변경되지 않는 블로그나 문서 페이지.

---

## 2. Next.js와 React의 차이점

| **기능**             | **React**                      | **Next.js**                                 |
|-----------------------|--------------------------------|---------------------------------------------|
| **렌더링 방식**      | 클라이언트 사이드 렌더링(CSR) | SSR, SSG, CSR 모두 지원                    |
| **라우팅**           | React Router 필요             | 파일 기반 라우팅 제공                      |
| **SEO**              | 직접 구현 필요                | 기본적으로 SEO 최적화                      |
| **데이터 Fetching**  | `useEffect`로 구현            | `getStaticProps`, `getServerSideProps` 제공 |
| **배포**             | 추가 설정 필요                | Vercel과 같은 간단한 배포 옵션 지원        |

---

## 3. 프로젝트 초기 설정

### Node.js 설치 확인
터미널에서 Node.js 설치 여부를 확인합니다:

```bash
node -v
```

설치되어 있지 않다면 [Node.js 공식 사이트](https://nodejs.org/)에서 **LTS 버전**을 다운로드하세요.

### Next.js 프로젝트 생성
터미널에서 아래 명령어를 실행하여 프로젝트를 생성합니다:

```bash
npx create-next-app@latest my-next-app --typescript
```

생성 후 디렉토리 구조는 다음과 같습니다:

---

## 4. Tailwind CSS 설정

### Tailwind CSS 설치
다음 명령어로 Tailwind CSS와 관련 패키지를 설치합니다:

```bash
npm install tailwindcss postcss autoprefixer
npx tailwindcss init
```

### Tailwind 설정 파일 수정
`tailwind.config.js` 파일을 열고 아래 내용을 추가합니다:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/pages/**/*.{js,ts,jsx,tsx}",
    "./src/components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

### 글로벌 CSS 추가
`src/styles/globals.css` 파일에 Tailwind 기본 스타일을 추가합니다:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## 5. 디렉토리 구조

### 전체 구조

```
my-next-app/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   ├── styles/
├── tsconfig.json
├── tailwind.config.js
├── next.config.js
├── package.json
└── README.md
```

---

### 디렉토리별 상세 설명

#### **`public/`**
- 정적 파일(이미지, 폰트 등)을 저장하는 폴더입니다.
- `public/` 폴더에 있는 파일은 URL 경로로 직접 접근할 수 있습니다.  
  예를 들어, `public/images/logo.png` 파일은 `/images/logo.png`로 접근 가능합니다.
- **Tip:** 모든 정적 파일은 이곳에 저장하세요.

---

#### **`src/`**
소스 코드를 저장하는 루트 폴더로, 일반적으로 **`components/`**, **`pages/`**, **`styles/`** 폴더를 포함합니다.







![image](https://github.com/user-attachments/assets/5506c22e-5b32-467a-83d1-869a554165da)


![image](https://github.com/user-attachments/assets/10ea99d2-922b-49fb-a353-7070e600d8ee)

---

##### **`src/components/`**
- 재사용 가능한 UI 컴포넌트를 저장하는 폴더입니다.
- **예:**  
  - **`Header.tsx`**: 헤더 UI 컴포넌트
    
   ![image](https://github.com/user-attachments/assets/9510b6b1-a8f5-4487-8295-9f3fa45ed27e)

  - **`Footer.tsx`**: 푸터 UI 컴포넌트
    
   ![image](https://github.com/user-attachments/assets/286f3835-2484-4ac6-8489-1a80a9bb8fb9)

- **Tip:** 컴포넌트를 파일 단위로 분리하면 유지보수가 용이합니다.

  
![image](https://github.com/user-attachments/assets/a949736e-3d90-4b44-86d7-a6d01cf3d6b4)

![image](https://github.com/user-attachments/assets/52c96f15-c13a-4d79-99d0-26574e8a0d85)

![image](https://github.com/user-attachments/assets/cf3ac650-e9ec-4ae0-b189-ce6d9ca62bde)

![image](https://github.com/user-attachments/assets/18ee551f-654c-4a39-b10a-53e8757847fa)


---

##### **`src/pages/`**
- 페이지와 라우팅을 관리하는 폴더입니다.
- 각 파일은 자동으로 라우팅됩니다.  
  **예:**
  - `index.tsx` → `/`
  - `about.tsx` → `/about`
  - `api/hello.ts` → `/api/hello` (API 라우트)
- **폴더 구조:**
  ```
  pages/
  ├── index.tsx       # 메인 페이지
  ├── about.tsx       # About 페이지
  └── api/            # API 엔드포인트
      └── hello.ts    # 간단한 API 예제
  ```

---

##### **`src/styles/`**
- CSS 스타일 파일을 저장하는 폴더입니다.
- **주요 파일:**
  - **`globals.css`**: 글로벌 스타일 정의.
  - **컴포넌트 스타일**: 컴포넌트별로 CSS 파일을 모듈화하여 작성합니다.
- **Tip:** Tailwind CSS와 함께 사용하면 유틸리티 클래스로 스타일을 빠르게 작성할 수 있습니다.

---

#### **`tsconfig.json`**
- TypeScript 설정 파일로, 프로젝트의 타입스크립트 관련 규칙을 정의합니다.
- 예: 경로 별칭 설정, 엄격한 타입 검사.

---

#### **`tailwind.config.js`**
- Tailwind CSS 설정 파일입니다.
- `content` 옵션을 통해 Tailwind가 적용될 파일 경로를 지정합니다.

---

#### **`next.config.js`**
- Next.js의 설정 파일입니다.
- 특정 기능(이미지 최적화, 환경 변수 등)을 활성화하거나 사용자 정의 설정을 추가할 수 있습니다.

---

#### **`package.json`**
- 프로젝트의 메타 정보를 담고 있으며, 의존성 및 실행 스크립트를 정의합니다.

---

#### **`README.md`**
- 프로젝트에 대한 설명 파일로, 프로젝트를 소개하거나 사용 방법을 문서화합니다.

---

