# Section 01 HTML 개요 및 기본 태그

## 01 HTML 개요
HTML( **HyperText Markup Language**)는 **웹 페이지**의 구조를 정의하는 표준 마크업 언어이다. <br/>
HTML은 텍스트, 이미지, 하이퍼링크 등을 웹 페이지에 표시할 수 있게 해준다. <br/>
웹 브라우저는 HTML을 해석하여 사용자가 볼 수 있는 웹 페이지로 변환한다.


## 02 HTML 기본 태그
HTML 태그는 **요소**를 정의하며, 보통 열림 태그와 닫힘 태그로 이루어져 있다. <br/>
일부 태그는 닫힘 태그 없이 **자체 닫힘** 형태로 사용할 수 있다.<br/>

<주요 기본 태그>
- **`<h1>` - `<h6>`**: 제목을 표시하는 태그로, `<h1>`이 가장 크고, `<h6>`이 가장 작다.
- **`<p>`**: 문단을 표시하는 태그이다.
- **`<a href="URL">`**: 하이퍼링크를 생성한다. 클릭하면 지정된 URL로 이동한다.
- **`<img src="image.jpg" alt="설명">`**: 이미지를 삽입한다.
- **`<ul>`, `<ol>`, `<li>`**: 순서 없는 리스트(`ul`), 순서 있는 리스트(`ol`), 그리고 리스트 항목(`li`)을 정의한다.

***
# Section 02 HTML5 문서 구조 및 주요 태그

## 01 HTML 문서 구조
HTML5 문서는 다음과 같은 기본 구조를 가진다:

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>페이지 제목</title>
  </head>
  <body>
    <h1>웹 페이지 제목</h1>
    <p>내용 작성</p>
  </body>
</html>
```


- `<!DOCTYPE html>`: HTML5 문서임을 선언
- `<html>`: 문서의 루트 요소로, 모든 HTML 태그를 포함
- `<head>` 문서의 메타데이터(예: 제목, 인코딩 등)를 정의
- `<body>`: 웹 페이지의 실제 내용을 포함하는 영역


## 02 HTML 주요 태그와 속성

HTML에는 다양한 태그와 속성을 활용할 수 있다. <br/>

### 주요 태그와 속성
* `<a href="URL" target="_blank">`: **다른 페이지로 연결**하는 링크를 만든다.
  -	href: 링크의 목적지 URL을 지정한다.
  -	target="_blank": 링크를 새 탭에서 연다.
* `<img src="image.jpg" alt="설명">`: **이미지를 삽입**할 때 사용한다.
  -	src: 이미지 파일의 경로를 지정한다.
  - alt: 이미지가 로드되지 않을 때 표시될 대체 텍스트를 설정한다.
* `<form>`: **사용자 입력을 받기 위한 폼**을 정의한다.
  -	action: 데이터를 제출할 서버의 URL을 지정한다.
  -	method: 데이터를 제출하는 방식(예: GET, POST)을 정의한다.
* 시맨틱 태그: HTML5에서 새로 추가된 시맨틱 태그는 페이지의 구조를 더 명확하게 나타낸다.
  -	`<header>`: 페이지나 섹션의 헤더를 정의한다.
  -	`<nav>`: 내비게이션 링크를 담는 섹션이다.
  -	`<article>`: 독립적인 콘텐츠를 나타낸다.
  -	`<footer>`: 페이지나 섹션의 푸터를 정의한다.
 
### GET과 POST의 차이
* GET: **데이터를 URL 파라미터로** 전달한다. 주로 데이터 조회에 사용되며, 보안이 필요한 정보 전달에는 적합하지 않다.
  - 예시: https://example.com/search?query=HTML
* POST: **데이터를 본문(body)에 담아 서버로** 전송한다. 주로 데이터 입력 또는 변경 작업에 사용되며, 보안이 필요한 정보 전달에 적합하다.
  - 예시:
    
    ```
    <form action="/login" method="POST">
      <input type="text" name="username" placeholder="아이디">
      <input type="password" name="password" placeholder="비밀번호">
      <input type="submit" value="로그인">
    </form>
    ```
