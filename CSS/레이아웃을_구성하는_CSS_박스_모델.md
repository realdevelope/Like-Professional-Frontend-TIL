# 레이아웃을 구성하는 CSS 박스 모델

## 👞CSS와 박스 모델

1. **블록레벨 요소, 인라인 레벨 요소**
    - 블록 레벨 요소 : 태그를 사용해 요소를 삽입했을 때 혼자 한줄을 차지하는 것 ( h1, div, p )
    - 인라인 레벨 요소 : 블록 레벨 요소와 반대로 한줄을 차지하지 않는 것 ( span, img, strong )

<br>

2. **박스 모델의 기본 구성**

    ![gbgbgb](https://user-images.githubusercontent.com/48710889/172642513-6b1ed38b-710f-416c-93bd-17c0c387116d.png)

<br><br>

3. **width, height**
    ```html
    <style>
        .box1 {
            width: 400px; /*고정 너비*/
            height: 100px; /*고정 높이*/
        }
        .box2 {
            width: 50%; /*가변 너비 - 브라우저의 50%*/
            height: 100px; /*고정 높이*/
        }
    </style>
    ```
    - width 는 너비, height는 높이
    - 공통 속성값은 아래와 같습니다.
        - 크기 : px, em
        - 백분율 : 박스모델을 포함하는 부모요소를 기준으로 지정
        - auto : 너비값과 높이값이 콘텐츠에 따라 자동 정렬

<br>

4. **box-sizing**
    - 박스 모델의 너비와 높이를 어떻게 결정할 것인지 속성값인 border-box, content-box 중에서 선택가능

<br>

5.  **box-shadow**

    ```html
    <style>
        box-shadow: <수평거리> <수직거리> <흐림정도> <번짐정도><색상> insert;
    </style>
    ```

    ```html
    <style>
        .box1 {
            box-shadow: 2px -2px 5px 0px;
        } /* 오른쪽 윗부분에 그림자 */
        .box2 {
            box-shadow: 5px 5px 15px 5px blue;
        } /* 오른쪽 아랫부분에 파란색 그림자 */
    </style>
    ```

    -   박스 모델에 그림자 효과를 주는 속성

    <br><br>

## 👟테두리 스타일 지정하기

> top, right -> bottom -> left

1. **border-style**

    ```html
    <style>
        #box1 {
            border-style: solid;
        } /* 실선 */
        #box2 {
            border-style: dotted;
        } /* 점선 */
        #box3 {
            border-style: dashed;
        } /* 짧은 점선 */
    </style>
    ```

    - 테두리 스타일을 지정하는 속성
    - 속성값은 아래와 같습니다.
        - `hidden` : 테두리를 숨김
        - `solid` : 테두리를 실선으로 표시
        - `dotted` : 테두리를 점선으로 표시
        - `dashed` : 테두리를 짥은 직선으로 표시
        - `double` : 테두리를 이중선으로 표시
        - `groove` : 테두리를 창에 조각한 것처럼 표시
        - `ridge` : 테두리를 창에서 튀어나온 것 처럼 표시

<br>

2. **border-width**

    ```html
    border-width : <크기> | thin | medium | thick;
    ```

    ```html
    <style>
        #box1 {
            border-width: 2px; /* 네 방향 모두 2px */
        }
        #box2 {
            border-width: thick thin; /* top & bottom - thick, left & right - thin */
        }
        #box3 {
            border-width: thick thin thin; /* top - thick, right - thin, bottom - thin, left - thin */
        }
        #box4 {
            border-width: 10px 5px 5px 10px; /* top - 10px, right - 5px, bottom - 5px, left - 10px */
        }
    </style>
    ```

    - 테두리 두께를 지정하는 속성
    - 상하좌우 4개의 방향의 테두리 스타일을 한번에 지정할 수도, 2개나 3개, 4개를 각각 다르게 지정할 수 도 있다.

<br>

3. **border-color**

    ```html
    <style>
        #box1 {
            border-color: red;
        } /* 전체 테두리 - 빨강 */
        #box2 {
            border-top-color: blue; /* 위쪽 테두리 - 파랑 */
            border-left-color: red; /* 왼쪽 테두리 - 빨강 */
        }
    </style>
    ```

    - 테두리 색상을 지정하는 속성
    - 한번에 테두리색상을 지정할 수도, 하나씩 지정할수도 있다.

<br>

4. **border**

    ```html
    <style>
        p {
            padding: 10px;
            border: 3px dotted blue; /* 모든 테두리를 3px짜리 파란 점선 */
        }
    </style>
    ```

    - 태두리 스타일 묶어서 지정하는 속성
    - 테두리스타일, 두께, 색상을 한번에 표현 가능

<br>

5. **border-radius**

    ```html
    border-radius: <크기> | <백분율>
    ```

    ```html
    <style>
        #round {
            border-radius: 25px; /* 모든 꼭짓점을 둥글게 */
        }
    </style>
    ```

    - 둥근 테두리를 만드는 속성
    - 둥근 테두리는 물론 원 형태로도 가능
    - 또한 원하는 꼭지점만 둥근 테두리로도 설정 가능

<br>

## 🥾여백을 조절하는 속성

1. **margin**

    ```html
    margin: <크기> | <백분율>
    ```

    ```html
    <style>
        #margin1 {
            margin: 50px;
        }
        #margin2 {
            margin: 30px 50px;
        }
        #margin3 {
            margin: 30px 20px 50px;
        }
        #margin4 {
            margin: 30px 50px 30px 50px;
        }
        #margin5 {
            margin-right: 20px;
        }
    </style>
    ```

    - 요소 주변의 여백을 설정하는 속성( 테두리 바깥쪽의 여백)
    - margin 다음에 하이픈(-)을 넣고 top, right, bottom, left를 사용해서 특정방향에만 지정 가능
    - 마진 중첩
        - 요소를 세로로 배치할 경우 마진과 마진이 만나면 마진값이 큰쪽으로 겹쳐지는 문제로 이를 마진 중첩이라고 합니다.

<br>

2. **padding**

    ```html
    <style>
        #padding1 {
            padding: 20px 30px 40px 50px;
        }
        #padding2 {
            padding: 20px 30px;
        }
        #padding3 {
            padding: 20px;
        }
    </style>
    ```

    - 콘텐츠와 테두리 사이의 여백을 설정하는 속성 ( 테두리 안쪽의 여백)
    - padding 다음에 하이픈(-)을 넣고 top, right, bottom, left를 사용해서 특정방향에만 지정 가능

<br><br>

## 🥿웹 문서의 레이아웃 만들기

1. **display**
    ```html
    <style>
        nav ul li {
            display: inline-block; /* 인라인, 블록 모두 지정 */
            padding: 20px;
            margin: 0 20px;
            border: 1px solid #222;
        }
    </style>
    ```
    - 배치방법을 결정하는 속성
    - 블록 레벨 요소와 인라인 레벨 요소를 서로 바꿔서 사용가능
    - 주로 네비게이션, 혹은 가로로 배치할때 사용
    - 속성값은 아래와 같습니다.
        - block : 인라인 레벨 요소를 블록 레벨 요소로 만듬
        - inline : 블록 레벨 요소를 인라인 레벨 요소로 만듬
        - inline-block 인라인 레벨 요소와 블랙레벨요소의 속성을 모두 가지고 있으며 마진과 패딩을 지정가능

<br>

2. **float**

    ```html
    <style>
        img {
            float: left; /* 왼쪽에 떠 있게 */
            margin-right: 40px;
        }
    </style>
    ```

    - 왼쪽이나 오른쪽으로 배치하는 속성
    - 블록 태그를 사용시 나란히 옆에 두지 못할떄 사용
    - 속성값은 left, right 가 있습니다.

<br>

3. **clear**

    ```html
    <style>
        #box1 {
            background: #ffd800;
            float: left; /* 왼쪽으로 플로팅 */
        }
        #box4 {
            background: #a874ff;
            clear: left; /* 플로팅 해제 */
        }
    </style>
    ```

    - float 속성을 해제하는 속성
    - float 속성값은 left, right, 둘다 한번에 해제하는 both가 있습니다.

<br>

## 👠웹요소의 위치 지정하기

1. **left, right, top, bottom**

    ```html
    <style>
        #pos1 {
            position: absolute; /* 포지셔닝 - absolute */
            left: 50px; /* 왼쪽에서 50px 떨어지게 */
            top: 50px; /* 위쪽에서 50px 떨어지게 */
        }
    </style>
    ```

    - 웹 요소의 위치를 지정하는 속성
    - position으로 먼저 기준 위치를 정한 뒤 요소의 위치를 left, right, top, bottom 속성에서 선택하고 속성값을 지정

<br>

2. **position**
    ```html
    <style>
        #relative-2 {
            position: relative; /* 포지셔닝 - relative */
            left: 100px; /* 왼쪽에서 100px 떨어지게 */
            top: -50px; /* 위쪽에서 -50px 떨어지게 (위로 이동) */
        }
        #fixed {
            width: 100px;
            height: 100px;
            background-color: #222;
            position: fixed; /* 포지셔닝 - fixed */
            right: 30px; /* 오른쪽에서 30px 떨어지게 */
            top: 30px; /* 위쪽에서 30px 떨어지게 */
        }
    </style>
    ```
    - 텍스트나 이미지 요소를 나란히 배치하기도, 원하는 위치를 선택할 수도 있습니다.
    - 속성값은 아래와 같습니다.
        - static : 문서의 흐름에 맞춰 배치(기본값)
        - relative : static와 비슷하나 위치값을 지정할 수 있음
        - absolute : relative 값을 사용한 상위 요소를 기준으로 위치를 지정
        - fixed : 브라우저 창을 기준으로 위치를 지정

> position : absolute를 사용할때는 부모요소에 무적권!!! position: relative를 사용해줘야 된다!!!
