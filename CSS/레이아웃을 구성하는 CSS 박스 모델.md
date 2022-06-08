# 레이아웃을 구성하는 CSS 박스 모델

## 👞CSS와 박스 모델

1. **블록레벨 요소, 인라인 레벨 요소**
    - 블록 레벨 요소 : 태그를 사용해 요소를 삽입했을 때 혼자 한줄을 차지하는 것 ( h1, div, p )
    - 인라인 레벨 요소 : 블록 레벨 요소와 반대로 한줄을 차지하지 않는 것 ( span, img, strong )

<br>

2. **박스 모델의 기본 구성**
   ![gbgbgb](https://user-images.githubusercontent.com/48710889/172642513-6b1ed38b-710f-416c-93bd-17c0c387116d.png)

<br>

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

          - 박스 모델에 그림자 효과를 주는 속성

    <br><br>

## 👟테두리 스타일 지정하기
