
# **Next.js + TypeScript + Tailwind CSS OT 자료**

---

## **1. Next.js란?**
Next.js는 **React 기반의 풀스택 프레임워크**로, 서버사이드 렌더링(SSR), 정적 사이트 생성(SSG), Incremental Static Regeneration(ISR) 등의 다양한 렌더링 방식을 제공합니다. SEO 최적화와 성능 향상을 지원하며, 개발자가 복잡한 설정 없이 효율적으로 웹 애플리케이션을 개발할 수 있도록 돕습니다.

---

## **2. Next.js + TypeScript + Tailwind CSS 사용 이유**

### **1. Next.js의 주요 장점**
- **파일 기반 라우팅**: 폴더 구조에 따라 URL이 자동으로 생성.
- **SSR/SSG 지원**: 페이지 요청 시 서버에서 HTML을 생성하거나, 사전에 정적 HTML 생성.
- **API Routes**: 백엔드와의 통합이 쉬움.
- **SEO 최적화**: SSR과 메타 태그 관리로 검색 엔진 친화적.
- **성능 최적화**: 코드 분할, 이미지 최적화 등의 기능.

---

### **2. TypeScript 사용 이유**
- **타입 안전성 제공**: 런타임 오류를 줄이고 코드의 가독성과 유지보수성을 높임.
- **IDE 지원 강화**: 자동완성, 타입 추론, 실시간 오류 감지.
- **대규모 프로젝트에 적합**: 코드의 일관성과 안정성을 유지.

---

### **3. Tailwind CSS 사용 이유**
- **유틸리티 클래스 기반**: HTML 내에서 CSS를 바로 작성 가능.
- **빠른 스타일링**: 사전 정의된 클래스만으로 복잡한 UI 생성.
- **반응형 디자인 간편**: `sm`, `md`, `lg` 등의 접두사를 사용해 다양한 화면 크기 대응.
- **커스터마이징 용이**: `tailwind.config.js`를 통해 테마를 쉽게 수정.

---

## **3. Next.js 설치 및 폴더 구조**

### **1. Next.js + TypeScript + Tailwind 설치**

#### **1) Next.js + TypeScript 설치**
```bash
npx create-next-app@latest my-next-app --typescript
cd my-next-app
npm run dev
```

#### **2) Tailwind CSS 설치**
```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
```

---

### **2. Next.js 폴더 구조**
```bash
my-next-app/
├── node_modules/
├── public/
├── pages/
│   ├── api/
│   │   └── hello.ts   # API 라우트
│   ├── _app.tsx       # 공통 레이아웃
│   ├── _document.tsx  # HTML 구조 수정
│   ├── index.tsx      # 메인 페이지
│   ├── about.tsx      # '/about' 페이지
│   └── post/
│       └── [id].tsx   # 동적 라우팅
├── components/        # UI 컴포넌트
├── styles/            # CSS 파일
│   ├── globals.css    # 전역 스타일
│   └── Home.module.css
├── utils/             # 유틸리티 함수
├── hooks/             # 커스텀 훅
├── context/           # 전역 상태 관리
├── tailwind.config.js # Tailwind 설정
├── tsconfig.json      # TypeScript 설정
└── package.json       # 프로젝트 설정
```

---

## **4. Next.js + TypeScript 주요 기능**

### **1. 파일 기반 라우팅**
- `pages` 폴더 내 파일로 URL 생성.
```typescript
// pages/about.tsx
export default function About() {
  return <h1>About Page</h1>;
}
```

### **2. 동적 라우팅**
- 대괄호(`[]`)로 동적 URL 처리.
```typescript
// pages/post/[id].tsx
export default function Post({ id }: { id: string }) {
  return <h1>Post ID: {id}</h1>;
}

export async function getServerSideProps({ params }: any) {
  return { props: { id: params.id } };
}
```

---

### **3. 데이터 페칭**
#### (1) **SSG**: 정적 사이트 생성
```typescript
export async function getStaticProps() {
  return { props: { message: "Static Data" } };
}

export default function Home({ message }: { message: string }) {
  return <h1>{message}</h1>;
}
```

#### (2) **SSR**: 서버사이드 렌더링
```typescript
export async function getServerSideProps() {
  return { props: { message: "Server-Side Data" } };
}
```

#### (3) **ISR**: 점진적 정적 재생성
```typescript
export async function getStaticProps() {
  return {
    props: { message: "ISR Data" },
    revalidate: 10, // 10초마다 재생성
  };
}
```

---

### **4. API Routes**
```typescript
// pages/api/hello.ts
import { NextApiRequest, NextApiResponse } from "next";

export default function handler(req: NextApiRequest, res: NextApiResponse) {
  res.status(200).json({ message: "Hello from API" });
}
```

---

## **5. Tailwind CSS 설정 및 사용법**

### **1. Tailwind CSS 설정**
#### **1) `tailwind.config.js` 설정**
```javascript
module.exports = {
  content: ["./pages/**/*.{js,ts,jsx,tsx}", "./components/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

#### **2) `globals.css`에 Tailwind 지시문 추가**
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

### **2. Tailwind CSS 기본 사용법**

#### **1) 유틸리티 클래스**
- Tailwind는 사전 정의된 클래스를 조합하여 스타일을 적용.
```typescript
export default function Home() {
  return (
    <div className="flex justify-center items-center h-screen bg-gray-100">
      <h1 className="text-4xl font-bold text-blue-500">Hello Tailwind CSS!</h1>
    </div>
  );
}
```

#### **2) 반응형 디자인**
- `sm`, `md`, `lg`, `xl` 접두사를 사용.
```html
<div class="text-sm md:text-lg lg:text-xl">Responsive Text</div>
```

#### **3) 상태 스타일링**
- Hover, Focus, Active 상태 스타일.
```html
<button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
  Hover Me
</button>
```

#### **4) 다크 모드**
- 다크 모드를 위한 `dark` 클래스 지원.
```html
<div class="bg-white dark:bg-black text-black dark:text-white">Dark Mode</div>
```

---

### **3. Tailwind CSS + TypeScript 예제**

#### **1) 프로젝트 파일 구조**
```bash
my-next-app/
├── components/
│   └── Button.tsx      # 재사용 가능한 버튼 컴포넌트
├── pages/
│   └── index.tsx       # 메인 페이지
├── styles/
│   └── globals.css     # 전역 스타일
└── tailwind.config.js  # Tailwind 설정
```

#### **2) Button 컴포넌트**
```typescript
// components/Button.tsx
interface ButtonProps {
  label: string;
  onClick: () => void;
}

export default function Button({ label, onClick }: ButtonProps) {
  return (
    <button
      onClick={onClick}
      className="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
    >
      {label}
    </button>
  );
}
```

#### **3) 메인 페이지**
```typescript
// pages/index.tsx
import Button from "../components/Button";

export default function Home() {
  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100">
      <h1 className="text-4xl font-bold text-blue-600 mb-4">Welcome to Next.js + Tailwind</h1>
      <Button label="Click Me" onClick={() => alert("Button Clicked!")} />
    </div>
  );
}
```

---

#### **4)폴더 구조**


```bash
my-next-app/
├── node_modules/
├── public/
├── pages/
├── styles/
├── components/
├── .next/
├── utils/
├── hooks/
├── context/
├── services/
├── tailwind.config.js
├── tsconfig.json
├── next.config.js
├── package.json
└── README.md
```

| 폴더/파일          | 설명                                                                                 |
|--------------------|--------------------------------------------------------------------------------------|
| **node_modules/**  | 프로젝트 의존성 패키지가 저장되는 폴더. 사용자가 직접 수정하지 않음.                   |
| **public/**        | 정적 파일(이미지, 폰트, favicon 등)을 저장. 이 폴더 안의 파일은 `/` 경로로 접근 가능. |
| **pages/**         | Next.js의 핵심 폴더로, 라우팅을 관리하며 SSR, SSG, API Routes 등을 구현.              |
| **styles/**        | CSS 파일을 관리. Tailwind CSS 또는 CSS Modules를 사용할 때 사용.                     |
| **components/**    | 재사용 가능한 React 컴포넌트를 저장. UI 요소를 모듈화하여 유지보수성 향상.           |
| **.next/**         | Next.js가 빌드 과정에서 생성하는 캐시 폴더. 배포 및 서버에서 사용되며 직접 수정하지 않음.|
| **utils/**         | 프로젝트 전반에서 사용되는 유틸리티 함수 저장.                                       |
| **hooks/**         | 커스텀 React 훅을 저장.                                                              |
| **context/**       | 전역 상태 관리 컨텍스트를 저장.                                                      |
| **services/**      | API 호출 로직과 서비스 계층 로직을 저장.                                             |
| **tailwind.config.js** | Tailwind CSS 설정 파일.                                                          |
| **tsconfig.json**  | TypeScript 설정 파일.                                                               |
| **next.config.js** | Next.js 설정 파일로, 이미지 최적화, 리다이렉션, 환경 변수 등을 설정.                  |
| **package.json**   | 프로젝트의 의존성 및 실행 스크립트를 정의.                                           |
| **README.md**      | 프로젝트 설명 문서.                                                                 |

---

#### **2. pages/** 폴더 구조

`pages/` 폴더는 Next.js의 가장 중요한 폴더로, 모든 페이지와 API 라우트가 여기서 정의됩니다.

```bash
pages/
├── api/
│   └── hello.ts       # API 엔드포인트
├── _app.tsx           # 공통 레이아웃
├── _document.tsx      # HTML 구조 수정
├── index.tsx          # 메인 페이지 ('/')
├── about.tsx          # 정적 페이지 ('/about')
├── post/
│   ├── [id].tsx       # 동적 라우팅 ('/post/:id')
│   └── create.tsx     # 새로운 게시물 작성 페이지
└── 404.tsx            # 커스텀 404 페이지
```

| 파일            | 설명                                                                                 |
|-----------------|--------------------------------------------------------------------------------------|
| **_app.tsx**    | 모든 페이지에서 공통으로 사용되는 컴포넌트와 레이아웃 정의.                           |
| **_document.tsx** | HTML `<head>`와 `<body>` 태그를 수정하고, 전역 구조를 설정.                         |
| **index.tsx**   | 애플리케이션의 기본 루트 경로 페이지.                                                 |
| **404.tsx**     | 없는 페이지 요청 시 표시될 커스텀 에러 페이지.                                        |
| **api/**        | API 라우트를 관리하는 폴더. 서버리스(Serverless) 함수를 작성 가능.                     |

---

#### **3. components/** 폴더 구조

```bash
components/
├── layout/
│   ├── Header.tsx      # 헤더 컴포넌트
│   ├── Footer.tsx      # 푸터 컴포넌트
│   └── Sidebar.tsx     # 사이드바 컴포넌트
├── ui/
│   ├── Button.tsx      # 재사용 가능한 버튼 컴포넌트
│   └── Card.tsx        # 카드 컴포넌트
├── forms/
│   ├── Input.tsx       # 입력 필드 컴포넌트
│   └── TextArea.tsx    # 텍스트 영역 컴포넌트
└── pages/
    └── PostList.tsx    # 게시물 리스트 컴포넌트
```

| 폴더/파일      | 설명                                                 |
|----------------|----------------------------------------------------|
| **layout/**    | 레이아웃 관련 컴포넌트 저장. Header, Footer 등.        |
| **ui/**        | 재사용 가능한 UI 컴포넌트(Button, Card 등).           |
| **forms/**     | 폼과 관련된 입력 필드, 텍스트 영역 컴포넌트 저장.       |
| **pages/**     | 특정 페이지에서만 사용하는 컴포넌트 저장.              |

---

#### **4. styles/** 폴더 구조

```bash
styles/
├── globals.css        # 전역 스타일
├── Home.module.css    # Home 컴포넌트 전용 스타일
└── theme.css          # Tailwind 커스텀 테마 설정
```

| 파일            | 설명                                  |
|----------------|-------------------------------------|
| **globals.css**| 모든 페이지에 적용되는 전역 스타일.      |
| **module.css** | CSS Modules로 컴포넌트 단위 스타일 정의.|
| **theme.css**  | Tailwind의 커스텀 테마 설정.           |

---

#### **5. 기타 폴더**
- **utils/**: 공통으로 사용하는 유틸리티 함수 저장.
- **hooks/**: 커스텀 React 훅 저장.
- **context/**: 전역 상태 관리를 위한 Context API 파일 저장.
- **services/**: API 호출 및 서비스 계층 로직 파일 저장.

---

### **폴더 구조 요약**
1. **pages/**: 라우팅과 SSR/SSG/API Routes 관리.
2. **components/**: UI와 레이아웃 컴포넌트 관리.
3. **styles/**: CSS 파일 관리.
4. **utils/**: 공통 함수 관리.
5. **hooks/**: 커스텀 훅 관리.
6. **context/**: 전역 상태 관리.
7. **services/**: API 호출 및 서비스 로직 관리.


```
