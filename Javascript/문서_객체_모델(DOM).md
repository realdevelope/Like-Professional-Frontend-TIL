# 문서 객체 모델 (DOM)

## 💎문서 객체 모델

1. **문서 객체 모델**
    - 자바스크립트를 이용하여 웹 문서에 접근하고 제어할 수 있도록 객체를 사용해 웹 문서를 체계적으로 정리하는 방법
    - 웹 문서와 그 안의 모든 요소를 객체로 인식하고 처리함(웹문서 전체는 document 객체, 삽입한 이미지는 image 객체)

<br>

2. **요소의 계층 관계**
   ![mjbgvfvf](https://user-images.githubusercontent.com/48710889/175802089-8091a551-e34d-4abd-a7b5-53b537ef22ff.PNG)
    ```javascript
       //html 요소 관계 알아보기
       <!DOCTYPE html>
       <html lang="ko">
       <head>
       <title>DOM Tree 알아보기</title>
       </head>
       <body>
       <h1>DOM을 공부합시다</h1>
       <img src="images/easys-3.jpg" alt="">
       </body>
       </html>
    ```

<br>

3. **DOM 트리**
    - 웹 문서에 있는 요소들 간의 부모, 자식 관계를 계층 구조로 표시
    - 트리 형태가 되기 때문에 DOM 트리라고 함
    - 노드 : DOM 트리에서 가지가 갈려져 나간 항목
    - 루트노드 : DOM 트리의 시작 부분(최상단)

<br>

4. **DOM을 구성하는 원칙**
    - 모든 HTML 태그는 요소(element)노드
    - 웹 문서의 텍스트 내용은 요소 노드의 자식 노드인 텍스트(text) 노드
    - 태그의 속성은 요소노드의 자식노드인 속성(attribute)노드
    - 주석은 주석(comment)노드

<br><br>

## 💍DOM 요소에 접근하고 속성 가져오기

1. **DOM 요소에 접근**

    - 웹문서에서 원하는 요소를 찾아가는 것을 접근한다(access)라고 함
    - `getElementById()` 메서드
        ```html
        요소명.getElementById("id명");
        <!-- 반환값이 1개 -->
        ```
    - `getElementByClassName()` 메서드
        ```html
        요소명.getElementByClassName("class명");
        <!-- 반환값이 2개 이상, HTMLCollection 객체에 저장 -->
        ```
    - `getElementByTagName()` 메서드
        ```html
        요소명.getElementByTagName("태그명");
        <!-- 반환값이 2개 이상, HTMLCollection 객체에 저장 -->
        ```
    - `querySelector() `메서드, `querySelectorAll()`

        ```html
        노드.querySelector(선택자)
        <!-- 반환값이 1개 -->
        노드.querySelectorAll(선택자/태그)

        <!-- 반환값이 여러개일 때 모두 반환, 노드리스트로 저장 -->
        ```

        -> id, class, 태그 상관없이 다 가능하며, id는 이름앞에 #를, class는 이름앞에 .를, 태그는 기호없이 태그명을 사용<br><br>

    - `getAttribute()` 메서드, `setAttribute()` 메서드

        ```html
        getAttribute("속성명");
        <!-- 속성 노드의 값을 가져옴 -->

        setAttribute("속성명", "바꿀값");
        <!-- 속성 노드의 값을 바꿈 -->
        ```

        ```html
        function displaySrc() { var cup = document.querySelector("#cup"); alert("이미지 소스 : " + cup.getAttribute("src")); }
        <!-- getAttribute 로 이미지소스 출력 -->
        ```

<br><br>

## 💍DOM에서 이벤트 처리하기

1. addEventListener() 메서드 사용
    - 이벤트 객체를 사용해 이벤트 처리기 연결
    ```html
    요소.addEventListener(이벤트, 함수, 캡쳐여부);
    ```
    - 이벤트 : 이벤트 유형을 지정 ( on을 붙이지 않고 사용)
    - 함수 : 이벤트가 발생하면 실행할 명령이나 함수를 지정 (함수 정의시 event객체를 인수로 받음)
    - 캡처여부 : 이벤트를 캡쳐하는지 여부를 지정하며, true이면 캡처링, false이면 버블링

        > 캡처링: DOM의 부모노드에서 자식노드로 전달되는 것<br>
        > 버블링 : DOM의 자식 노드에서 부모 노드로 전달 되는 것
