## 메타데이터 및 타이틀 변경
pages/_app.js 또는 app/layout.js 파일에서 <title> 태그 수정.

## 라우팅
- Next.js는 파일 기반 라우팅을 사용
- pages 디렉토리 안에 파일을 생성하면 URL 경로로 매핑

## Single Page Application (SPA)
- Next.js는 기본적으로 CSR과 SSR 모두 지원
- useEffect를 활용하면 클라이언트 측 데이터 로딩 가능
- public 폴더에 파일을 넣으면 정적 파일로 제공
- URL로 /파일명 접근 가능.

## CSS
- 글로벌 스타일은 styles/globals.css에서 관리
- 컴포넌트별 CSS는 모듈 파일(.module.css)로 분리 가능

## 백엔드 통신
- pages/api 디렉토리에서 API 라우트 생성 가능

## 글 목록 가져오기
- 백엔드 API를 호출해 데이터 가져오기

## 글 읽기
- 동적 라우트(pages/posts/[id].js)를 사용하여 특정 글 ID로 페이지 생성

## 글 생성
- useState와 onSubmit 이벤트로 폼 데이터 처리
- API를 통해 새로운 글 저장 요청

## 캐시 처리
- getStaticProps로 정적 생성 후 리빌드 타이밍(revalidate) 설정
- 클라이언트에서는 SWR 라이브러리로 데이터 캐싱 관리 가능

## 글 수정
- 기존 데이터를 가져와 폼에 미리 채운 뒤 수정 요청을 API로 전송

## 글 삭제
삭제 버튼을 눌렀을 때 API 요청으로 데이터 삭제 처리
삭제 후 목록을 재요청하거나 상태 업데이트

## 업데이트 & 삭제 버튼 구현
- 각 글 목록 옆에 "수정" 및 "삭제" 버튼 추가
- 클릭 이벤트로 적절한 API 요청 수행
