# CSS

## 목차
- [1. CSS 개요](#1-css-개요)
- [2. CSS 주요 속성](#2-css-주요-속성)
    * [2-1. Box Model 지정](#2-1-box-model-지정)
    * [2-2. Text 지정](#2-2-위치-지정)
    * [2-3. 가시성 지정](#2-3-가시성-지정)
    * [2-4. Font 지정](#2-4-font-지정)
- [3. 금주의 프로젝트](#3-금주의-프로젝트)


## 1. CSS 개요
CSS는 캐스캐이딩 스타일시트(Cascading Style Sheets)의 약자로 HTML 태그를 화면 상에 어떻게 표현할지를 설정합니다.

기본적으로 CSS가 없으면 밋밋한 HTML 페이지를 ↓
![image](https://github.com/user-attachments/assets/ad7cbb60-fa37-4444-9523-3105f4a6419c)


이런 식으로 생기를 불어넣어줍니다. ↓

또한 PC, 휴대폰, 태블릿 등 다양한 기기와 그에 따른 다양한 디스플레이에 맞춰 화면을 표시하기 위하여 웹 페이지의 스타일을 정의하는 데에 사용합니다.

기본적으로 html 태그 내에 style 속성을 사용하여 작성하거나, \<style> 태그를 사용, 또는 .css 파일을 작성 또는 Bootstrap과 같은 외부 css 프레임워크를 \<link> 태그를 통해 불러와 사용하는 방법이 있습니다.

## 2. CSS 주요 속성
### 2-1. Box Model 지정

각각의 박스(Element)들은 Margin > Border > Padding > Content 순으로 둘러싸여 있습니다.\
기본적으로 내용을 담고 있는 부분인 Content를 제외한 나머지 부분들에 대하여 알아봅니다.

- Margin

    CSS에서 margin은 박스 밖의 공간을 나타냅니다. 위, 오른쪽, 아래쪽, 왼쪽 (시계 방향) 4방향의 속성을 가집니다. margin은 기본적으로 0의 값을 가지고 있습니다.

    table—caption, table , inline—table 등의 테이블 관련 태그들을 제외한 모든 태그에 적용이 가능합니다.

    ```
    p{
        margin-top: 10px;
        margin-left: 20px;
    }
    ```
    위 코드는 어떤 박스에 대하여 위에 10px만큼, 왼쪽에 20px만큼의 border을 갖게 합니다.

    ```
    p{
        margin: 10em 20em 10em 20em;
    }
    ```
    각각 margin-(방향) 으로 작성할 필요없이 한꺼번에 margin: 으로 묶어 작성 가능합니다.

    margin: 뒤에 속성값을 몇 개 적느냐에 따라 특정 방향은 생략이 가능합니다.

    예를 들어 속성값을 10px라고 1개만 적는다면 4방향 모두 10px의 margin을 갖게 됩니다.
    ```
    p{
        margin: 10px 20px; /*상하 10px, 오른쪽 왼쪽 20px 가짐*/
    }
    ```
    2개를 적는다면 top과 bottom, left와 right가 같은 값을 가집니다.

     ```
    p{
        margin: 10px 20px 30px; /*top 10px, 오른쪽 왼쪽 20px, bottom 30px 가짐*/
    }
    ```
    3개를 적는다면 right과 left가 같은 값을 가지게 됩니다.\
    보이시다시피 기술 순서는 시계 방향입니다.\
    이 순서는 다른 영역에도 똑같이 적용됩니다.

- Border

    border은 말 그대로 테두리입니다. 테두리 두께나 스타일을 지정할 수 있습니다. 

    margin과 마찬가지로 시계방향대로 스타일을 적용할 수 있습니다.

    ```
    p {
        border-top-style: dotted;
        border-right-style: solid;
        border-bottom-style: dotted;
        border-left-style: solid;
    }
    ```
    이는 아래와 같이 표현 가능합니다.
    ```
    p{
        border-style: dotted solid;
    }
    ```
    스타일에는 'none', 'hidden', 'dotted', 'dashed’, 'solid', 'double', 'groove', 'ridge', 'inset', ’outset' 등이 있습니다.


    테두리 두께는 border-width 속성을 통해 적용할 수 있습니다.

    ```
    .round-box {
        border-width: 2px; /* 두께가 2px이 됨 */
        border-radius: 10px;
        border-color: rgba(169, 169, 169, 0.216);
        border-style: solid;
    }
    ```

    위와 같이 테두리 색이나 테두리 모양도 설정할 수 있습니다.

    아예 간편화해서 border 속성으로 작성도 가능한데,

    ```
    p{
        border: 5px solid #ccc;
    }
    ```
    이러면 작성이 끝입니다!

- Padding

    padding은 테두리 내부에서 여백을 주는 방식입니다.\
    사실상 작성 방식은 margin과 같아 건너뛰겠습니다.
    ```
    padding: - - - -;
    ``` 
    이런 식으로 작성하면 되겠습니다.

### 2-2. 위치 지정

HTML 문서를 처음으로 작성할 때, 모든 엘리먼트가 기본적으로 왼쪽 맞춤되어 보기 싫은 상황이 있을 것입니다. 이럴 때 이런저런 배치를 하는 방법을 공부해보겠습니다.

- Text 배치

    텍스트는 기본적으로 왼쪽 맞춤되어 있는데, text-align 속성을 통해 배치를 할 수가 있습니다.

    ```
    p{
        text-align: center;
    }
    ```
    이렇게 텍스트를 가운데에 정렬할 수 있습니다.

- Element 배치

    엘리먼트들을 배치하는 방법은 여러 가지 방법이 있습니다.\
    기본적으로 엘리먼트를 가로로 두고 싶다면 여러 가지 방법이 있겠지만 display를 변경할 수 있습니다.

    ```
    div{
        display: inline-block;
    }
    ```

    div들은 기본적으로 block 형태, 즉 서로 세로로 쌓이는 형태로 배치됩니다. 하지만 CSS를 통해 display 형식을 변경하는 방법으로 서로 가로로 배치될 수 있습니다.

    ```
    div{
        float: left;
    }
    ```
    또는 float 속성을 이용하여 왼쪽으로 붙도록 속성을 줄 수 있습니다.

    ```
    .header {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        z-index: 999;
    }
    ```
    또한 position 속성을 통해 특정 위치에 엘리먼트가 위치하도록 할 수 있습니다. 제가 만들고 있는 웹 페이지에서 header가 항상 화면 제일 위에 보여지게 하도록 설정한 방식입니다.

    z-index는 다른 엘리먼트들과 겹쳤을 때 어떤 엘리먼트가 위에 표시될 것인지 정해주는 속성입니다. (z-index 수치가 높을 수록 위에 표시)

### 2-3. 가시성 지정

엘리먼트를 선택적으로 보여주고 싶을 때 가시성 속성을 지정해줄 수 있습니다. 예를 들어 버튼을 눌러야만 글자가 보이게 하고 싶다면 버튼을 누르기 전에는 엘리먼트를 숨겨놓을 수 있을 것입니다.

- visibility
    ```
    div{
        visibility: hidden;
    }
    ```
    이런 식으로 visibility를 hidden으로 설정하게 되면 div가 보이지 않게 됩니다.\
    보이게 하려면 visibility: visible; 을 사용합니다.

- display: none

    ```
    div{
        display: none;
    }
    ```
    visibility: hidden; 은 엘리먼트를 보이지 않게 해주지만 엘리먼트가 있는 영역은 그대로 표시가 됩니다.

    이 영역까지 숨기고 싶다면 display: none; 을 고려할 수 있습니다.

### 2-4. Font 지정

- font-family

    font-family 속성으로 엘리먼트에 설정할 폰트 종류를 지정합니다.
     'Gill’, 'Helvetica’. serif, 'sans-serif, 'cursive', 'fantasy','monospace' 등 중에서 설정 가능합니다.

- font-style

    font-style 속성을 통해 이탈릭체, 글꼴 굵게 설정 등을 할 수 있습니다.

- @font-face

    ```
    @font-face {
        font-family: 'GmarketSansMedium';
        src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/GmarketSansMedium.woff') format('woff');
        font-weight: normal;
        font-style: normal;
    }
    ```
    이런 식으로 외부에서 폰트를 받아와서 설정을 할 수도 있습니다.\
    이렇게 폰트를 받아와서 태그 속성에 font-family: 'GmarketSansMedium'; 속성을 주면 폰트를 적용할 수 있습니다.

### 3. 금주의 프로젝트

https://github.com/nowimseeingcashflow/Portfolio-Fe
