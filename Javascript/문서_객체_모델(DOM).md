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

1.  **DOM 요소에 합수 직접 연결하기**

    -   함수가 간단할시 직접연결

        ```javascript
        var cup = document.querySelector('#cup'); // id = cup인 요소를 가져옴 ( 접근 )
        cup.onclick = function () {
            alert('이미지를 클릭했습니다.');
        };
        ```

    <br>

2.  **함수 이름을 사용해 연결하기**

    -   함수를 따로 정의해 놓았을때 함수이름을 이용해 사용
    -   단, 함수표시 () 괄호를 작성하지 않고 이름만 작성

        ```javascript
        var cup = document.querySelector('#cup'); // id = cup인 요소를 가져옴 ( 접근 )
        cup.onclick = changeImg;

        function changeImg() {
            cup.src = 'images/cup-2.png';
        }
        ```

    <br>

3.  **DOM의 event 객체 알아보기**
    -   이벤트 정보를 저장하는 event 객체
        ```javascript
        var cup = document.querySelector('#cup'); // id = cup인 요소를 가져옴
        cup.onclick = function (event) {
            alert('이벤트 유형: ' + event.type + ', 이벤트 발생 위치 : ' + event.pageX + ',' + event.pageY);
        };
        ```
    -   event 객체에는 이벤트 정보만 들어있기 때문에 이벤트가 발생한 대상에 접근하려면 this를 사용해야함
        ```javascript
        var cup = document.getElementById('cup');
        cup.onclick = function (event) {
            alert('클릭한 이미지 파일 : ' + this.src);
        };
        ```

<br>

4. **addEventListener() 메서드 사용하기**

    - 이벤트 객체를 사용해 이벤트 처리기 연결
    - 위의 3가지와는 달리 한 요소에 여러 이벤트 처리가 가능

    ```html
    요소.addEventListener(이벤트, 함수, 캡쳐여부);
    ```

    - 이벤트 : 이벤트 유형을 지정 ( on을 붙이지 않고 사용)
    - 함수 : 이벤트가 발생하면 실행할 명령이나 함수를 지정 (함수 정의시 event객체를 인수로 받음)
    - 캡처여부 : 이벤트를 캡쳐하는지 여부를 지정하며, true이면 캡처링, false이면 버블링

        > 캡처링: DOM의 부모노드에서 자식노드로 전달되는 것<br>
        > 버블링 : DOM의 자식 노드에서 부모 노드로 전달 되는 것

        ```javascript
        var cover = document.getElementById('cover');

        cover.addEventListener('mouseover', changeImg);
        cover.addEventListener('mouseout', originImg);

        function changeImg() {
            cover.src = 'images/easys-2.jpg';
        }
        function originImg() {
            cover.src = 'images/easys-1.jpg';
        }
        ```

<br>

5. **CSS 속성에 접근하기**

    - 스타일 속성값을 가져와서 그값을 원하는 대로 수정
    - 속성명 중 - 가 있는 속성은 카멜표기법으로 변경

    ```html
    document.요소명.style.속성명
    ```

    ```javascript
    //id가 desc인 요소의 글자색 변경
    document.getElementById('desc').style.color = 'blue';
    ```

    ```javascript
    // 메서드 안에서 함수 선언해서 보기쉽게 작성 - 도형의 테두리,배경 변경
    var myRect = document.querySelector('#rect');

    myRect.addEventListener('mouseover', function () {
        // mouseover 이벤트 처리
        myRect.style.backgroundColor = 'green'; // myRect 요소의 배경색
        myRect.style.borderRadius = '50%'; // myRect 요소의 테두리 둥글게 처리
    });
    myRect.addEventListener('mouseout', function () {
        // mouseout 이벤트 처리
        myRect.style.backgroundColor = ''; // myRect 요소의 배경색 지우기
        myRect.style.borderRadius = ''; // myRect 요소의 테두리 둥글게 처리 안 함
    });
    ```

<br><br>

## DOM에서 노드 추가/삭제 하기

1. **노드 리스트**

    - DOM에서 새로운 노드를 만들어 추가하거나 삭제하려면 노드리스트를 사용해야한다
    - querySelectorAll() 메서드를 사용하여 노드를 한번에 여러개 가져옴
    - 배열과 비슷한 형태여서 인덱스 번호로 특정 위치의 노드에 접근할 수 있음

    ```html
    <h1>Web Programming</h1>
    <ul id="itemList">
        <li>HTML</li>
        <li>CSS</li>
        <li>Javascript</li>
    </ul>
    ```

    ```javascript
    document.querySelectorAll('li');
    document.querySelectorAll('li')[1];
    ```

<br>

2. **텍스트 노드를 사용하는 새로운 요소 추가하기**

    - 요소 노드 만들기 - createElement()
        - 노드를 만들뿐, 노드를 추가한 것 은 아님, p 태그에 해당하는 텍스트 노드도 만들어야함
        ```html
        document.createElement(노드명)
        ```
        ```javascript
        var newp = document.createElement('p');
        ```
    - 텍스트 노드 만들기 - createTextNode()
        - 내용을 담는 텍스트 노드를 자식노드로 만들어 연결
        ```html
        document.createTextNode(텍스트);
        ```
        ```javascript
        var txtNode = document.createTextNode('DOM은 document object model 의 줄임말입니다.');
        ```
    - 자식 노드 연결하기 - appendChile()
        - 텍스트노드나 속성노드를 만든 후 요소 노드에 연결할 떄 사용
        - 자식 노드중에 가장 끝에 추가됨
        ```html
        부모노드.aapendChild(자식노드)
        ```
        ```javascript
        newP.appendChild(txtNode);
        document.getElementById('info').appendChild(newP);
        ```
    - 전체 소스 코드 완성하기

        ```javascript
        <div id="container">
            <h1>DOM을 공부합시다</h1>
            <a href="#" onclick="addP(); this.onclick='';">
                더 보기
            </a>
            <div id="info"></div>
        </div>;

        function addP() {
            var newP = document.createElement('p');
            var txtNode = document.createTextNode('DOM은 Document Object Model의 줄임말입니다.');
            newP.appendChild(txtNode);
            document.getElementById('info').appendChild(newP);
        }
        ```

<br>

3. **속성값이 있는 새로운 요소 추가하기**

    - 요소 노드 만들기 - createElement()
        - 텍스트 노드와 동일하게 이미지노드 만듬
        ```javascript
        // 이미지 노드 추가하기
        var newImg = document.createElement('img');
        ```
    - 속성 노드 만들기 - createAttribute()

        - 이미지요소는 src속성을 사용해서 파일의 경로를 지정해야 이미지 보여줄 수 있기 때문에 createAttribute() 를 꼭 사용해야함

        ```javascript
        // 속성 노드 만ㄷ르기
        document.createAttribute(속성명);
        ```

        ```javascript
        // 이미지의 src 속성 만들고 지정
        var srcNode = document.createAttribute('src');

        srcNode.value = 'images/dom.jpg'; //src 속성값 지정
        ```

    - 속성 노드 연결하기 - setAttributeNode()
        - 속성노드는 요소노드의 자식으로 연결해야하고, 새로만든 노드를 추가하려면 setAttributeNode()를 사용
            ```javascript
            // 요소 노드의 자식으로 속성 노드 연결
            요소명.setAttributeNode(속성노드);
            ```
            ```javascript
            // 이미지의 src 속성노드연결
            newImg.setAttributeNode(srcNode);
            ```
    - 자식 노드 연결하기 - appendChild()
        - 속성노드까지는 연결했지만 이미지요소는 만들기만 했기때문에 appendChild()를 사용해서 자식노드로 추가해야함
            ```javascript
            // info 위치에 img 요소를 자식요소로 추가
            document.getelementById('info').appendChild(newImg);
            ```
    - 전체 소스 코드 완성하기

        ```javascript
        // 링크 클릭시 텍스트와 이미지 표시
        <div id="container">
            <h1>DOM을 공부합시다</h1>
            <a href="#" onclick="addContents(); this.onclick='';">
                더 보기
            </a>
            <div id="info"></div>
        </div>;

        function addContents() {
            var newP = document.createElement('p');
            var txtNode = document.createTextNode('DOM은 Document Object Model의 줄임말입니다.');
            newP.appendChild(txtNode);

            var newImg = document.createElement('img');
            var srcNode = document.createAttribute('src');
            var altNode = document.createAttribute('alt');
            srcNode.value = 'images/dom.jpg';
            altNode.value = '돔 트리 예제 이미지';
            newImg.setAttributeNode(srcNode);
            newImg.setAttributeNode(altNode);

            document.getElementById('info').appendChild(newP);
            document.getElementById('info').appendChild(newImg);
        }
        ```

<br>

4. **노드 삭제하기**

    - parentNode 프로퍼티

        - DOM 트리의 노드는 바로 삭제할 수 없기때문에 부모노드에 접근해야함
        - 현재 노드의 부모 노드에 접근해서 부모노드의 요소노드를 반환
            ```javascript
            노드.parentNode;
            ```
            ```javascript
            document.querySelectorAll('li')[1].parentNode;
            ```

    - removeChild() 메서드
        - 자식노드를 삭제하는 역할
        - 부모노드만 찾으면 간단
        ```javascript
        부모노드.removeChild(자식노드);
        ```
        ```javascript
        li.parentNode.removeChild(li);
        ```
