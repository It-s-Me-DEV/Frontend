# CSS 심화

## 목차
- [1. 미디어 쿼리](#1-미디어-쿼리)
    * [1-1. 미디어 쿼리 사용법](#1-1-미디어-쿼리-사용법)
- [2. CSS의 다양한 기능](#2-css의-다양한-기능)
    * [2-1. 테두리 & 그림자](#2-1-테두리--그림자)
    * [2-2. 그라데이션](#2-2-그라데이션)
        - [2-2-1. linear-gradient](#2-2-1-linear-gradient)
        - [2-2-2. radial-gradient](#2-2-2-radial-gradient)
    * [2-3. transition](#2-3-transition)
    * [2-4. transform](#2-4-transform)
- [3. 프레임워크](#3-프레임워크)
- [4. 금주의 프로젝트](#4-금주의-프로젝트)

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

<b>border-radius</b> 속성은 박스의 테두리를 둥글게 만들어주는 속성입니다. 
```
.round-box { /* border-radius 없는 버전 */
  border-width: 2px;
  border-color: rgba(169, 169, 169, 0.216);
  border-style: solid;
  padding: 15px;
}
```
![image](https://github.com/user-attachments/assets/67809392-a2db-470b-b5a8-7960deee1b72)

```
.round-box {/* border-radius 있는 버전 */
  border-width: 2px;
  border-radius: 10px;
  border-color: rgba(169, 169, 169, 0.216);
  border-style: solid;
  padding: 15px;
}
```
이렇게 딱딱한 직사각형 모양인 박스에 border-radius를 10px만큼 추가해주겠습니다.

![image](https://github.com/user-attachments/assets/7f985983-2adb-4479-b8d3-d6622f9ed964)
border-radius를 추가했을 뿐인데 조금 더 예뻐졌습니다.

박스나 텍스트에 그림자를 넣을 수도 있습니다.
\
<b>box-shadow, text-shadow</b> 속성입니다.

```
<p style="text-shadow: 5px 5px 2px red">dsda</p>
/* text-shadow: 가로: 5px 세로: 5px 번짐정도: 2px 그림자색: red */
```
<p style="text-shadow: 5px 5px 2px red">실제 사용 예시입니다.</p>
가로 수치를 음수로 두면 그림자가 왼쪽으로, 세로 수치를 음수로 두면 그림자가 위로 생깁니다.

box-shadow도 똑같이 사용 가능합니다.

## 2-2. 그라데이션
그라데이션 효과는 <b>linear-gradient, radial-gradient, conic-gradient</b> 로 적용 가능합니다.\
이번에는 <b>linear-gradient, radial-gradient</b>만 알아보겠습니다.
### 2-2-1. linear-gradient
```
body{
    background: linear-gradient(green, yellow);
}
```
위에서 초록, 아래로 내려갈 수록 노란색이 나오는 그라데이션 배경색을 낼 수가 있습니다.

```
body{
    background: linear-gradient(to right, green, yellow);
}
```
이렇게 to right을 적게 되면 왼쪽에서부터 오른쪽으로 그라데이션 색이 적용됩니다.

to bottom right 같이 대각선 방향도 지정 가능합니다.
### 2-2-2. radial-gradient
```
body{
    background: radial-gradient(red, yellow, green);
    /* 색깔은 중심 → 내부 → 바깥쪽 순서입니다 */
}
```
radial-gradient는 원 모양으로 그라데이션을 지정할 수 있습니다.


![image](https://github.com/user-attachments/assets/c3d7a618-78dd-49a1-98be-5f7c26650d7d)
중심에서 red, 내부에서 yellow, 바깥쪽에서 green 색이 나타나는 것을 볼 수 있습니다.

```
body{
    background-image: radial-gradient(red 5%, yellow 15%, green 60%);
}
```
![image](https://github.com/user-attachments/assets/e9d59a19-9601-4e51-a9af-d2f0ae65bf59)
이렇게 비율 지정도 가능합니다.

## 2-3. transition
<b>transition</b> 속성은 어떤 속성에서 다른 속성으로 변화가 일어날 때 그 변환에 특징을 주는 속성으로, 예를 들어
```
p{
    width: 50%;
}
p:hover{
    width: 100%;
}
```
와 같은 CSS 시트가 있다고 생각해보겠습니다.

p 태그에 마우스를 올리면 넓이가 넓어지겠지만 갑자기 휙 변하는 것보단 넓어지는 애니메이션이 있으면 더 세련될 것 같습니다.
\
이럴 때 <b>transition</b> 속성을 추가해주면 됩니다.
```
p{
    width: 50%;
    transition: width 2s;
}
p:hover{
    width: 100%;
}
```
width가 변할 때 2초에 걸쳐 변화가 이루어진다는 의미입니다.
이는 아래 transform 속성과도 잘 어울립니다.

## 2-4. transform
<b>transform</b>은 대상을 움직이는 속성입니다. 이동시키거나,      회전시키거나, 크기를 키울 수 있습니다.

웹페이지에서 사용된 예시를 보여드리겠습니다.
```
.intro-li:hover {
  transform: scale(1.15);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: all 0.2s ease;
}
```
<b>transfrom: scale()</b> 속성을 이용하여 마우스를 올리면 엘리먼트의 크기가 커지게 만들었습니다.

![website](https://github.com/user-attachments/assets/48632e5a-2e66-470d-9c69-ca38bac34ba1)

이런 형태도 transform을 이용한 방식입니다.
## 3. 프레임워크
![image](https://github.com/user-attachments/assets/fadc8401-9576-49a1-950f-04b2a9ef9b4a)
최근에는 Bootstrap 말고도 수많은 CSS 프레임워크들이 출시되어 절찬리에 사용되고 있습니다.

특히 요즘에는 TailwindCSS가 강세를 보이고 있습니다.\
라이브러리들은 직접 다운로드 받을 필요도 없이 HTML에서 link 태그를 통해 불러올 수 있기 때문에 간편하게 사용할 수 있습니다.

이런 요소들을 활용한다면 힘들게 CSS를 모두 작성하지 않더라도 괜찮은 디자인을 사용할 수 있습니다.

![image](https://github.com/user-attachments/assets/b2624f80-eae8-439a-a17c-08a707ddac00)


## 4. 금주의 프로젝트
https://github.com/nowimseeingcashflow/Portfolio-Fe

Swiper 작업을 하였습니다.

https://nowimseeingcashflow.github.io/

또한 포트폴리오 페이지를 github.io를 이용하여 실제 접속할 수 있도록 호스트해두었습니다. ㅎㅎ
