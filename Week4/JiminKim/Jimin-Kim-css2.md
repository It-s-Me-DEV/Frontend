# CSS 심화

## 목차
- [1. 미디어 쿼리](#1-미디어-쿼리)
    * [1-1. 미디어 쿼리 사용법](#1-1-미디어-쿼리-사용법)
- [2. CSS의 다양한 기능](#2-css의-다양한-기능)
    * [2-1. 테두리 & 그림자]()
    * [2-2. Text 지정](#2-2-위치-지정)
    * [2-3. 가시성 지정](#2-3-가시성-지정)
    * [2-4. Font 지정](#2-4-font-지정)
- [3. 금주의 프로젝트](#3-금주의-프로젝트)

## 1. 미디어 쿼리
미디어 쿼리는 다양한 디스플레이에 맞춰서 웹사이트를 어떻게 표현할 것인지를 지정해줄 수 있는 기능입니다.

예를 들어 우리가 웹사이트를 제작할 때 PC와 모바일 버전을 따로 제작할 수도 있겠지만, 서버 자원을 아끼기 위해서 또는 그 외의 이유로 똑같은 페이지를 켜더라도 기기에 맞는 다른 모양의 페이지를 보여주도록 제작할 수 있습니다.

이를 가능하게 하는 것이 미디어 쿼리 <b>@media</b> 기능입니다.

### 1-1. 미디어 쿼리 사용법
사용법은 간단합니다.
```
@media screen and (화면 조건)
```
Java의 애노테이션, 또는 전 주에 살펴보았던 <b>@font-face</b>에서도 볼 수 있는 형태입니다.

HTML에서 CSS 파일을 불러올 때
```
<link rel="stylesheet" href="css.css" media="screen and (max-width : 1000px)">
```
속성을 주어도 되고 위에서 보이다시피
```
@media screen and (max-width)
```
.css 파일에서 이렇게 선언해주어도 괜찮습니다.

```
 @media screen and (min-width : 320px) and (max—width : 550px) {
    .header {
        display: none;
    }
 }

 @media screen and (min-width : 550px) {
    .header {
        display: block;
    }
 }
```
사용 예시를 보겠습니다. 이렇게 지정하면 320px ~ 550px의 화면에서는 header 클래스를 가진 엘리먼트가 안 보일 것이고, 550px가 넘는 화면에선 보이게 될 것입니다.


## 2. CSS의 다양한 기능
CSS3 버전이 되면서 이런저런 기능들이 생겨났습니다.\
괜찮은 기능들을 몇 개 소개해보겠습니다.

## 2-1. 테두리 & 그림자
화면을 표현하는 데에 있어서 조금 더 예쁘게 보이게 할 수 있는 속성입니다.

![image](https://github.com/user-attachments/assets/67809392-a2db-470b-b5a8-7960deee1b72)

![image](https://github.com/user-attachments/assets/7f985983-2adb-4479-b8d3-d6622f9ed964)

## 3. 금주의 프로젝트
https://github.com/nowimseeingcashflow/Portfolio-Fe

Swiper 작업을 하였습니다.

https://nowimseeingcashflow.github.io/

또한 포트폴리오 페이지를 github.io를 이용하여 실제 접속할 수 있도록 호스트해두었습니다. ㅎㅎ

