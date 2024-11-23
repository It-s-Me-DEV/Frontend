
## HTML5  
**HTML(HyperText Markup Language)**: 웹페이지의 내용과 구조를 기술하는 마크업 언어  

```html
<!DOCTYPE html>
<html>
    <head></head>
    <body></body>
</html>
```

#### 주요 특징  
- `<p></p>`: 요소를 나타냄  
- HTML은 웹페이지의 **내용**과 **구조**를 담당  
- 스타일 및 디자인은 CSS로 처리  

#### 스타일 적용 예시  
```html
<!DOCTYPE html>
<html>
    <head>
        <style>
            body {
                background-color: yellow;
            }
        </style>
    </head>
    <body>
        <p>안녕하세요!</p>
    </body>
</html>
```

#### 주요 태그  
- **텍스트 강조**  
  ```html
  <b>굵은 글씨</b>
  <strong>의미 강조</strong>
  <del>취소선</del>
  ```
- **이미지 삽입**  
  ```html
  <img src="이미지링크" width="300" height="200">
  ```

---

### CSS  
**CSS(Cascading Style Sheets)**: HTML 요소의 스타일(디자인)을 정의  

#### 기본 구조  
```css
셀렉터 {
    프로퍼티: 값;
}
```

#### HTML에 CSS 연결  
- 내부 스타일: `<style>` 태그 사용  
  ```html
  <style>
      body {
          background-color: lightblue;
      }
  </style>
  ```
- 외부 파일 연결  
  ```html
  <link rel="stylesheet" href="style.css">
  ```

#### 주요 셀렉터  
```css
* { 전체 }
태그명 { 태그 }
.class { 클래스 }
[attribute] { 속성 }
[attribute="value"] { 특정 값 선택 }
부모 > 자식 { 자식 }
```

#### 주요 프로퍼티  
```css
/* 레이아웃 */
width: 
height: 
margin:
padding: 
border: 

/* 폰트 */
font-size: 
font-family: 
font-weight: 

/* 위치 */
position: 
top: 
left: 

/* 정렬 */
float: 
text-align:
```

---

### JavaScript  
**JavaScript(JS)**: 동적 웹 동작을 위한 프로그래밍 언어  

#### 기본 구조  
```javascript
console.log('Hello, World!'); 
```

#### 변수 선언  
```javascript
var 변수명;
변수명 = '값';
```

#### 조건문과 반복문  
```javascript
if (조건) {
} else if (조건) {
} else {
}

for (let i = 0; i < 10; i++) {
    console.log(i);
}
```

#### 함수 정의  
```javascript
function 함수명(매개변수) {
}
```

#### switch 문  
```javascript
switch (조건) {
    case '값1':
        break;
    case '값2':
        break;
    default:
}
```

#### 데이터 변환  
```javascript
String(3); // 숫자를 문자열로 변환
Number('42'); // 문자열을 숫자로 변환
```

#### 객체와 프로퍼티  
```javascript
let obj = { key: 'value' };
obj.newKey = 'newValue'; // 프로퍼티 추가
delete obj.key; // 프로퍼티 삭제
```
