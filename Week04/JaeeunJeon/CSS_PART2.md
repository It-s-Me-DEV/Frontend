# Section 04: Advanced CSS (CSS3)의 추가 기능
## (1) Advanced CSS 개요
현재의 Advanced CSS는 “기존의 CSS + CSS3(추가된 신기능)”으로 Advanced CSS는 실렉터, 박스 모델, 배경과 테두리, 이미지 관련, 텍스트 효과, 2D/3D 트랜스폼, 애니메이션, 폰트, 다단 기능 등을 제공한다.
## (2) 이미지 스타일
### (1) 썸네일 이미지 (thumbnail image)
이미지를 클릭하면 원본 이미지가 별도의 창(또는 탭)에 표시된다.
주로 쇼핑몰 사이트에서 활용
```css
.thumbnail { 
width: 150px; 
height: 150px; 
object-fit: cover; 
}
```
### (2) 반응형 이미지 (Responsive Images)
화면의 크기에 따라 자동으로 이미지의 크기와 배치를 바꿀 수 있다.
반응형 이미지를 구현하려면 이미지의 가로 너비를 100%로 지저한다.
```css
img {
  max-width: 100%;
  height: auto;
}
```

## (3) 웹 폰트 : @font-face
웹 폰트는 Advanced CSS에 추가된 것으로, 사용자의 컴퓨터상에 폰트를 다운로드 하지 않아도 해당 폰트를 사용할 수 있다.
무료로 폰트를 제공하는 사이트에는 구글폰트가 있다.
```css
@font-face { /*1. 웹 폰트 정의*/
  font-family: 'CustomFont'; /*폰트명 정의*/
  src: url('CustomFont.woff2'); /*사용할 폰트 파일명*/
}
p {
  font-family: 'CustomFont', sans-serif; /*사용할 폰트명*/
}
```
