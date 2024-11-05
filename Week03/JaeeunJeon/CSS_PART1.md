# Section 01 CSS 개요 및 CSS 기본 사용법

## (1) CSS 개요
CSS( **Cascading Style Sheets** )는 HTML 요소의 **스타일(디자인)** 을 지정하는 스타일 언어이다. <br/>
CSS는 색상, 폰트, 레이아웃 등을 설정하여 웹 페이지를 시각적으로 아름답게 만들 수 있다. <br/>
HTML은 구조를 담당하고, CSS는 스타일을 적용하여 사용자에게 더 나은 사용자 경험을 제공한다.

## (2) CSS 기본 사용법
CSS는 세 가지 방식으로 적용할 수 있다.

- **인라인(inline) 스타일**: HTML 요소의 `style` 속성을 사용하여 직접 스타일을 적용.

```html
<p style="color: red;">이 문장은 빨간색이다.</p>
```

- **내부(internal) 스타일**: HTML 문서의 `<head>` 내에 `<style>` 태그를 사용하여 스타일을 정의.

```html
<style>
  p { color: blue; }
</style>
```

- **외부(external) 스타일**: 별도의 CSS 파일을 링크하여 스타일을 적용. 가장 일반적인 방식.

```html
<link rel="stylesheet" href="styles.css">
```

***

# Section 02 CSS의 주요 속성과 값

## (1) 색상과 배경(Colors and Backgrounds) 지정
- 색상(Color): color 속성으로 텍스트의 색상을 지정.

```css
p { color: green; }
```

- 배경색(Backgound Color): `backgound-color` 속성으로 요소의 배경색을 지정.

```css
div { background-color: yellow; }
```

## (2) 폰트(Fonts) 지정
- 폰트 설정: `font-family` 속성으로 텍스트에 사용할 폰트를 지정.

```css
p { font-family: Arial, sans-serif; }
```

- 폰트 크기: `font-size` 속성으로 텍스트의 크기를 지정.

```css
h1 { font-size: 24px }
```

## (3) 텍스트(Text) 지정
- 텍스트 정렬: `text-align` 속성으로 텍스트의 정렬 방식을 지정.

```css
p { text-align: center; }
```

- 텍스트 장식: `text-decoration` 속성으로 텍스트에 밑줄, 취소선 등을 지정.

```css
a { text-decoration: none; }
```

## (4) 테이블(Table) 지정
- 테이블 경계선: `border` 속성으로 테이블에 경계선을 추가.

```css
table { border: 1px solid black; }
```

## (5) 테두리(Border) 지정
- 테두리 스타일: `border` 속성으로 요소의 테두리를 지정.

```css
div { border: 1px solid red; }
```

- 테두리 반경: `border-radius` 속성으로 테두리의 모서리를 둥글게 설정.

```css
div { border-radius: 10px; }
```

## (6) 박스 모델(Box model) 지정
- 패딩(Padding): `padding` 속성으로 내용과 테두리 사이의 간격을 설정.

```css
div { padding: 20px; }
```

- 마진(Margin): `margin` 속성으로 요소의 외부 간격을 설정.

```css
div { margin: 15px; }
```


- ### Margin가 Padding의 차이점
`margin`과 `padding`은 CSS에서 요소와 주변 공간을 다루는 속성이다. 이 두 속성은 모두 **공간을 정의**하는 역할을 하지만, 적용되는 위치와 목적이 다르다.

#### 1. Margin (마진)

`margin`은 **요소의 바깥쪽**에 존재하는 **외부 여백**을 정의한다. 즉, 한 요소와 다른 요소 사이의 간격을 설정할 때 사용한다.  
마진은 네 방향(상, 하, 좌, 우)으로 설정할 수 있으며, 부모 요소나 형제 요소와의 거리를 조정하는 데 유용하다.

##### 마진 특징
- **여백이 요소 밖에 적용**되며, 다른 요소와의 간격을 조정한다.
- 마진은 요소 간의 **겹침 현상**(margin collapsing)이 발생할 수 있다. 이는 인접한 요소들 간에 마진이 합쳐지면서 최댓값이 적용되는 경우를 말한다.
- 마진은 배경색이나 테두리와는 **관련이 없다**.

##### 마진 설정 예시
```css
div {
  margin-top: 20px;   /* 위쪽 마진 */
  margin-right: 15px; /* 오른쪽 마진 */
  margin-bottom: 20px;/* 아래쪽 마진 */
  margin-left: 15px;  /* 왼쪽 마진 */
}

/* 축약형 */
div {
  margin: 20px 15px;  /* 상하 20px, 좌우 15px */
}
```

#### 2. Padding (패딩)

`padding`은 요소의 내부 여백을 정의하며, 콘텐츠와 요소의 경계(테두리) 사이의 간격을 조정한다.
즉, 요소 내부에서 텍스트나 이미지 같은 콘텐츠와 테두리 사이의 공간을 설정할 때 사용된다.

##### 패딩 특징
- **여백이 요소 내부** 에 적용되며, 콘텐츠와 요소의 경계(테두리) 사이의 간격을 조정한다.
- 패딩은 배경색, 이미지, 테두리의 **영향을 받는다**. 배경색은 패딩 영역까지 확장된다.
- 마진과 달리 **겹침 현상이 발생하지 않는다**.

##### 패딩 설정 예시
```css
div {
  padding-top: 10px;   /* 위쪽 패딩 */
  padding-right: 20px; /* 오른쪽 패딩 */
  padding-bottom: 10px;/* 아래쪽 패딩 */
  padding-left: 20px;  /* 왼쪽 패딩 */
}

/* 축약형 */
div {
  padding: 10px 20px;  /* 상하 10px, 좌우 20px */
}
```

## (7) 가시성(Visibility)과 위치(Positioning) 지정
- 가시성(Visibility): `visibility` 속성으로 요소의 표시 여부를 지정.

```css
div { visibility: hidden; }
```

***

# Section 03 미디어 쿼리(Media Query)

## (1) 미디어 쿼리의 개요
미디어 쿼리는 화면의 **크기**나 **디바이스 종류**에 따라 다른 스타일을 적용할 수 있게 한다. <br/> 
반응형 웹 디자인을 구현할 때 자주 사용된다.

## (2) 미디어 쿼리 사용 방법
미디어 쿼리는 `@media` 규칙을 사용하여 특정 조건에서만 스타일을 적용한다.

```css
@media screen and (max-width: 600px) {
  div { background-color: blue; }
}
```
