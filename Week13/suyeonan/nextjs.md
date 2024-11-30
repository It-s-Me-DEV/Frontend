## nextjs
### SSR(서버 사이드 렌더링)이란?
#### 서버에서 먼저 완전한 HTML을 생성하고 이를 클라이언트로 전송하는 방식
#### <-> CSR(클라이언트 사이드 렌더링) : 클라이언트 측에서 HTML을 생성해 페이지 렌더링
### SSR 장점
#### 1. 빠른 로딩 시간
##### 클라이언트가 HTML을 최초 로드하는 시간이 줄어들어 바로 컨텐츠 확인 가능
#### 2. SEO(검색 엔진 최적화)
##### 검색 엔진(ex. Googel)이 사이트를 더 잘 이해하고 인덱싱할 수 있게 만드는 기술
##### 완전한 HTML 문서가 검색 엔진에 전달되기에 JavaScript를 실행하지 않고도 인덱싱 가능
### SSR 구현
##### getServerSideProps 함수 사용
```js
// pages/example.js

export async function getServerSideProps() {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts'); //fetch를 사용해 데이터 가져옴
  const posts = await res.json(); //텍스트 형식의 JSON 데이터를 JavaScript 객체로 변환

  return { props: { posts } }; //데이터 전달
}

//전달받은 데이터 렌더링
export default function ExamplePage({ posts }) {
  return (
    <ul>
      {posts.map(({ id, title, body }) => (
        <li key={id}>
          <h2>{title}</h2>
          <p>{body}</p>
        </li>
      ))}
    </ul>
  );
}

```
