# HTML

포트폴리오 웹사이트 제작을 위한 프론트엔드 - HTML 부분입니다.\
학교 웹사이트 페이지를 레퍼런스 삼아서 모양을 잡아보려고 합니다.

https://youtu.be/Yoly5scwhdY?si=Rf9Pv4c00o_oNpc6

마침 홍익대학교 홈페이지 모작하는 영상을 찾아 참고하였습니다.\
홈페이지 모작 외에도 이런저런 도움이 되는 영상들이 많이 있어 참고하시면 좋을 것 같습니다.

## HTML 기본 구조

HTML은 기본적으로 다양한 tag들로 이루어져 있습니다.

<b>\<html></b>

  - \<head>\
인코딩. 키워드, 뷰포트 등의 문서에 대한 정보를 제공합니다.\
meta 태그로 인코딩 정보 (보통 한국에선 한글의 표현을 위해 UTF-8로 인코딩하는 경우가 많은 것으로 보입니다)에 대한 정보를 제공하거나, 뷰포트 정보를 제공하고, CSS 파일 등을 불러오는 장소로 쓰입니다.

  - \<body>\
기본적으로 우리 눈에 보여질 각종 버튼, 메뉴, 문자 등이 표현되는 곳입니다.

    - \<div> , \<nav>\
 \<div> 태그는 주로 문서를 구역 별로 나누거나, 스타일시트를 적용할 그룹 영역으로 사용하거나 문서 전체에 스타일시트 적용을 초기화할 때 사용합니다. \<nav> 태그는 사이트의 내비게이션(메뉴) 항목을 표시할 때 사용합니다.

    - \<main> , \<section>\, \<header>\
문서의 내용을 표시하는 태그로. 주로 문서의 영역적인 의미로 사용됩니다.\
문서의 내용을 표시할 때 \<article>, \<section>, \<div> 중에 아무거나 사용해도 된다고 합니다.

    - \<a>\
링크를 이용해서 다른 페이지로 이동하는 데에 쓰입니다. href 속성을 이용하여 이동하고 싶은 페이지를 작성할 수 있습니다.\
target 속성에서 "_blank"를 사용하면 이동할 페이지를 새 탭에 표시해줍니다.

    - \<ul>, \<li>\
Unordered list, 순서가 지정되지 않고 bullet point로만 리스트를 나열합니다. 순번을 붙이는 리스트를 사용하고 싶다면 ol 태그를 고려할 수 있습니다.

<b>Class, Id</b>


HTML에는 글로벌 속성이라고 불리는 class와 id가 있습니다. \
태그 안에 class="", id="" 와 같은 방식으로 작성하여 태그에 이름을 붙여주는 성격을 지녔으며, \
이를 통해 CSS나 자바스크립트를 제어할 때 특정 엘리먼트를 검색할 수 있게 해줍니다.



### VSCode 작성 미세팁

이미 다들 아실 거라고 생각하지만 분량 이슈로 적어봅니다. 

![image](https://github.com/user-attachments/assets/f1e1ee65-3567-494e-ba0e-f425c8854de1)
불편한 띄어쓰기, 들여쓰기.. 그리고 깔끔하지 않은 배치를 어떻게 정리할까요?\
VSCode Prettier Extention 설치 후

![image](https://github.com/user-attachments/assets/39e275df-cfa5-4ca5-8daf-a0204dcb2e4a) 

Ctrl + Shift + P 누르고 Format Document를 해주면?

![image](https://github.com/user-attachments/assets/3b7fa10c-7280-4fe3-ad65-3200e8e04ace) 

깔끔하게 정리해줍니다.

### emmet 작성법

emmet은 HTML 작성 속도를 크게 향상시켜주는 플러그인입니다.\
HTML을 작성할 때 일일이 <>와 속성 등을 작성할 필요없이 요소 이름만 간단하게 적으면 tag 형태로 만들어줍니다.

ex.)
```
a.search
```
↓
```
<a class="search"></a>
```
ex.)
```
div.swiper>ul>(li.swiper-slide>a)*5
```
↓
```
<div class="swiper">
    <ul>
        <li class="swiper-slide"><a href=""></a></li>
        <li class="swiper-slide"><a href=""></a></li>
        <li class="swiper-slide"><a href=""></a></li>
        <li class="swiper-slide"><a href=""></a></li>
        <li class="swiper-slide"><a href=""></a></li>
    </ul>
</div>
```
