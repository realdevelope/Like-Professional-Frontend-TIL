# CSS 고급 선택자

## 🌌연결선택자

1. **하위 선택자**

    ```html
    상위요소 하위요소
    ```

    ```html
    <style>
        section p {
            /* section 요소의 모든 하위 p 요소에 적용 */
            color: blue; /* 글자색을 파란색으로 */
        }
    </style>
    <section>
        <h1>예약 방법 & 사용 요금</h1>
        <p>아직 온라인 예약 신청이 준비되어 있지 않습니다. <br />전화(xxx-xxxx-xxxx)로 문의 바랍니다.</p>
        <div>
            <p>가족실(2~4인) : 60,000원/일</p>
            <p>도미토리(4인 공용) : 25,000원/일</p>
        </div>
    </section>
    ```

    - 하위 요소에 스타일을 적용
    - 하위선택자를 사용하면 부모요소에 포함된 하위 요소를 모두 선택하며 자손선택자라고도 합니다.
    - 고로 위의 예제에선 p태그 전체가 적용된다

<br>

2. **자식 선택자**

    ```html
    부모요소 > 자식요소
    ```

    ```html
    <style>
        section > p {
            /* section 요소의 자식 p 요소에 적용 */
            color: blue; /* 글자색을 파란색으로 */
        }
    </style>
    <section>
        <h1>예약 방법 & 사용 요금</h1>
        <p>아직 온라인 예약 신청이 준비되어 있지 않습니다. <br>전화(xxx-xxxx-xxxx)로 문의 바랍니다.</p>
        <div>
        <p>가족실(2~4인) : 60,000원/일</p>
        <p>도미토리(4인 공용) : 25,000원/일</p>
    </section>

    ```

    - 하위선택자와는 다르게 자식요소에만 적용
    - 고로 위의 예제에선 section의 작식 p 태그만 적용된다.

<br>

3. 인접 형제 선택자

    ```html
    요소1 + 요소2
    ```

    ```html
    <style>
        h1 + p {
            /* h1 요소의 형제 요소 중 첫번째 p 요소에 적용 */
            background-color: #222; /* 배경은 검은색으로 */
            color: #fff; /* 글자는 흰색으로 */
        }
    </style>
    <section>
        <h1>예약 방법 & 이용 요금</h1>
        <p>아직 온라인 예약 신청이 준비되어 있지 않습니다. <br />전화(xxx-xxxx-xxxx)로 문의 바랍니다.</p>
        <p>가족실(2~4인) : 60,000원/일</p>
        <p>도미토리(4인 공용) : 25,000원/일</p>
    </section>
    ```

    - 형제요소중에서 첫번쨰 요소만 적용
    - 고로 위의 예제에서는 h1 의 첫번째 형제인 p 태그만 적용

<br>

4. 형제 선택자

    ```html
    요소1 ~ 요소2
    ```

    ```html
    <style>
        h1 ~ p {
            /* h1 요소와 형제인 모든 p 요소에 적용 */
            background-color: #222; /* 배경은 검은색으로 */
            color: #fff; /* 글자는 흰색으로 */
        }
    </style>
    <section>
        <h1>예약 방법 & 이용 요금</h1>
        <p>아직 온라인 예약 신청이 준비되어 있지 않습니다. <br />전화(xxx-xxxx-xxxx)로 문의 바랍니다.</p>
        <p>가족실(2~4인) : 60,000원/일</p>
        <p>도미토리(4인 공용) : 25,000원/일</p>
    </section>
    ```

    - 인접 형제 선택자와 다르게 모든 형제에 적용
    - 고로 위의 예제에서는 h1의 형제인 p태그 모두 적용

<br><br>

## 🪐속성 선택자

1.  **[속성]**

    ```html
    <style>
        a[href] {
            background: yellow;
            border: 1px solid #ccc;
            font-weight: normal;
        }
    </style>
    <ul>
        <li><a>메인 메뉴 : </a></li>
        <li><a href="#">메뉴 1</a></li>
        <li><a href="#">메뉴 2</a></li>
        <li><a href="#">메뉴 3</a></li>
        <li><a href="#">메뉴 4</a></li>
    </ul>
    ```

    -   특정 속성이 있는 요소를 선택하는 선택자
    -   href속성이 있는 요소를 입력한 예제
    -   고로 위의 예제에서는 a요소중 href가 있는 요소만 적용

    <br>

2.  **[속성 = 속성값]**

    ```html
    <style>
        a[target='_blank'] {
            padding-right: 30px;
            background: url(images/newwindow.png) no-repeat center right;
        }
    </style>
    <ul>
        <li><a href="hhttps://html.spec.whatwg.org" target="_blank">HTML</a></li>
        <li><a href="https://www.w3.org/TR/selectors">CSS Selector Level 3</a></li>
        <li><a href="https://www.w3.org/TR/css3-mediaqueries">미디어쿼리</a></li>
    </ul>
    ```

    -   특정 속성값이 있는 요소를 선택하는 선택자
    -   target속성값이 \_blank 인 요소만만 선택하는 예제
    -   고로 위의 예제에선 첫번째 링크에만 적용

    <br>

3.  **[속성 ~= 속성값]**

    ```html
    <style>
        a[class~='button'] {
            box-shadow: rgba(0, 0, 0, 0.5) 4px 4px; /* 그림자 지정 */
            border-radius: 5px; /* 테두리를 둥글게 */
            border: 1px solid #222;
        }
    </style>
    <ul>
        <li><a href="#" class="flat">메뉴 1</a></li>
        <li><a href="#" class="flat">메뉴 2</a></li>
        <li><a href="#" class="button">메뉴 3</a></li>
        <li><a href="#" class="flat button">메뉴 4</a></li>
    </ul>
    ```

    -   여러개 값 중에서 특정 속성값이 포함된 속성 요소를 선택하는 선택자
    -   button스타일이 있는 요소를 찾는 예제
    -   고로 위의 예제에서는 메뉴3, 4에 적용

<br>

4. **[속성 |= 속성값]**

    ```html
    <style>
        a[title|='us'] {
            /* 속성값이 "us"이거나 "us-"로 시작하는 요소를 찾는 선택자 */
            background: url(images/us.png) no-repeat left center;
        }
        a[title|='jap'] {
            /* 속성값이 "jap"이거나 "jap-"로 시작하는 요소를 찾는 선택자 */
            background: url(images/jp.png) no-repeat left center;
        }
        a[title|='chn'] {
            /* 속성값이 "chn"이거나 "chn-"로 시작하는 요소를 찾는 선택자 */
            background: url(images/ch.png) no-repeat left center;
        }
    </style>
    <ul>
        <li>외국어 서비스 :</li>
        <li><a href="#" title="us-english">영어</a></li>
        <li><a href="#" title="ja">일본어</a></li>
        <li><a href="#" title="chn">중국어</a></li>
    </ul>
    ```

    - 특정 속성값이 포함된 요소를 선택하는 선택자
    - title속성값에 각 조건에 맞는 a 요소를 찾는 예제
    - 고로 위의 예제에서는 영어, 중국어에 적용

<br>

5. **[속성 ^= 속성값]**

    ```html
    <style>
        a[title^='eng'] {
            /* 속성값이 "eng"로 시작하는 요소를 찾는 선택자 */
            background: url(images/us.png) no-repeat left center;
            padding: 5px 25px;
        }
        a[title^='jap'] {
            /* 속성값이 "jap"로 시작하는 요소를 찾는 선택자 */
            background: url(images/jp.png) no-repeat left center;
            padding: 5px 25px;
        }
        a[title^='chin'] {
            /* 속성값이 "chn"로 시작하는 요소를 찾는 선택자 */
            background: url(images/ch.png) no-repeat left center;
            padding: 5px 25px;
        }
    </style>
    <ul>
        <li>외국어 서비스 :</li>
        <li><a href="#" title="english">영어</a></li>
        <li><a href="#" title="japanese">일본어</a></li>
        <li><a href="#" title="chinese">중국어</a></li>
    </ul>
    ```

    - 특정 속성값으로 시작하는 속성 요소를 선택하는 선택자
    - 고로 위의 예제에서는 모두 부합하기에 전부 적용

<br>

6. **[속성 $= 속성값]**

    ```html
    <style>
        a[href$='hwp'] {
            /* 연결한 파일의 확장자가 hwp인 링크 */
            background: url(images/hwp_icon.gif) center right no-repeat; /* 배경으로 hwp 아이콘 표시 */
            padding-right: 25px; /* 아이콘을 표시할 수 있도록 오른쪽에 25px 여백 */
        }

        a[href$='xls'] {
            /* 연결한 파일의 확장자가 hwp인 링크 */
            background: url(images/excel_icon.gif) center right no-repeat; /* 배경으로 hwp 아이콘 표시 */
            padding-right: 25px; /* 아이콘을 표시할 수 있도록 오른쪽에 25px 여백 */
        }
    </style>
    <h3>회사 소개 파일 다운 받기</h3>
    <ul>
        <li><a href="intro.hwp">hwp 파일</a></li>
        <li><a href="intro.xls">엑셀 파일</a></li>
    </ul>
    ```

    - 특정한 값으로 끝나는 속성의 요소를 선택하는 선택자
    - href에 링크된 파일의 확장자에 따라 아이콘 다르게 표시하는 예제
    - 고로 위의 예제에서는 모두 부합하므로 전부 적용

<br>

7. <b>[속성 *= 속성값]</b>

    ```html
    <style>
        a[href*='w3'] {
            /* href 속성값 중에 w3가 있는 a 요소를 찾는 선택자 */
            background: blue;
            color: white;
        }
    </style>
    <h1>HTML5 참고 사이트</h1>
    <p>(아래 링크 중 파란색 배경의 링크는 W3C 사이트로 연결됩니다.)</p>
    <ul>
        <li><a href="https://html.spec.whatwg.org/">HTML 표준안 사이트</a></li>
        <li><a href="https://caniuse.com/">HTML 지원 여부 체크</a></li>
        <li><a href="https://www.w3.org/TR/css3-mediaqueries">미디어쿼리</a></li>
    </ul>
    ```

    - 일부 속성값이 일치하는 요소를 선택하는 선택자
    - w3가 포함된 요소를 href를 이용해서 찾는 속성
    - 고로 위의 예제는 3번째 미디어쿼리에 적용

<br><br>

## 🌍가상 클래스와 가상 요소

1.  **사용자 동작에 반응하는 가상 클래스**

    ```html
    <!--적용 순서-->
    link > visited > hover > active
    ```

    ```html
    <style>
        .navi ul li {
            float: left;
            width: 150px;
            padding: 10px;
        }
        .navi a:link,
        .navi a:visited {
            display: block;
            font-size: 14px;
            color: #000;
            padding: 10px;
            text-decoration: none; /* 밑줄 없앰 */
            text-align: center;
        }
        .navi a:hover,
        .navi a:focus {
            background-color: #222; /* 배경 색 */
            color: #fff; /* 글자 색 */
        }
        .navi a:active {
            background-color: #f00; /* 배경 색 */
        }
    </style>
    <div class="container">
        <nav class="navi">
            <ul>
                <li><a href="#">이용 안내</a></li>
                <li><a href="#">객실 소개</a></li>
                <li><a href="#">예약 방법 및 요금</a></li>
                <li><a href="#">예약하기</a></li>
            </ul>
        </nav>
    </div>
    ```

    -   :link
        -   방문하지 않은 링크에 스타일을 적용
        -   기본값은 파란글자와 밑줄
    -   :visited
        -   방문한 링크에 스타일을 적용
        -   기본값은 보라색글자와 밑줄
    -   :hover
        -   특정 요소에 마우스를 올려놓으면 스타일적용
    -   :active
        -   웹 요소를 활성화했을 때 스타일 적용
        -   주로 이미지, 링크 등을 클릭했을때
    -   :focus

        -   웹 요소에 초점이 맞추어 있을때 스타일 적용
        -   예로 텍스트 필드 안에 포인터 올려놓거나 할때

    <br>

    -> 고로 위의 예제에서는 마우스 포인터 올렸을때, 클릭했을때 적용

<br>

2. **요소 상태에 따른 가상 클래스**

    - :target

        - 앵커 대상에 스타일을 적용
        - 같은 문서 안에서 다른 위치로 이동시 앵커 이용 하는데 이 앵커에 해당 선택자를 사용

    - :enabled, :disabled

        - 요소의 사용 여부에 따라 스타일을 적용
        - 사용할 수 있는 상태 - :enabled, 사용할 수 없는 상태 - :disabled

    - :checked

        - 선택한 항목의 스타일을 적용
        - form의 라디오 박스나 체크박스에서 선택된 경우에 checked속성 추가되는데 이를 이용

    - :not
        - 특정 요소를 제외하고 스타일을 적용
        - 스타일을 적용하려고 하는 필드 보다 적용하지 않는 필드가 더 많을때 유용

<br>

3.  **구조 가상 클래스**

    -   특정위치의 자식요소 선택하기
        <br>(class, id 사용하지 않고도 가능)

        ```html
        <style>
            .contents :nth-child(3) {
                background-color: #ffff00;
            }
            .contents p:nth-of-type(3) {
                background-color: #00b900;
            }
        </style>
        <div class="contents">
            <h2>이용안내</h2>
            <p>Excepteur....</p>
            <p>Qui magna....</p>
            <h2>객실 소개</h2>
            <p>Irure....</p>
            <h2>예약 방법 및 요금</h2>
            <p>Fugiat....</p>
        </div>
        ```

        -   `:only-child` : 부모안에 자식요소가 하나일떄 자식요소 선택
        -   `A:only-type-of` : 부모안에 A 요소가 하나뿐일때 선택
        -   `:fist-child` : 부모안에 있는 첫번째 자식요소 선택
        -   `:last-child` : 부모안에 있는 요소중 마지막 자식요소 선택
        -   `A:first-of-type` : 부모안에 있는 A 요소 중 첫번째 요소 선택
        -   `A:last-of-type` : 부모안에 있는 A 요소 중 마지막 요소 선택
        -   `:nth-child` : 부모안에 있는 모든 요소중 n번째 자식 요소 선택
        -   `:nth-last-child(n)` : 부모안에 있는 모든 요소 중에서 끝에서 n번쨰 자식요소 선택
        -   `A:nth-of-type(n)` : 부모안에 있는 A요소중에 n번째 요소 선택
        -   `A:nth-last-of-type(n)` : 부모안에 있는 A요소중 끝에서 n번째 요소 선택

    -   수식을 사용해 위치 지정하기

        ```html
        <style>
            table tr:nth-of-type(2n + 1) {
                /* 홀수 번째 열에만 스타일 적용 */
                background: lightgray;
                color: black;
            }
        </style>
        ```

        -   위치를 지정할떄 계속 일정하게 바뀐다면 규칙을 찾아 an+1 처럼 수식을 사용가능
        -   n값은 0부터 시작
        -   홀수는 :nth-child(odd), 짝수는 :nth-child(even)을 사용하여 스타일 적용

    -   가상요소

        ```html
        <style>
            li.new::after {
                content: 'NEW!!';
                font-size: x-small;
                padding: 2px 4px;
                margin: 0 10px;
                border-radius: 2px;
                background: #f00;
                color: #fff;
            }
        </style>
        <div class="container">
            <h1>제품 목록</h1>
            <ul>
                <li class="new">제품 A</li>
                <li>제품 B</li>
                <li>제품 C</li>
                <li class="new">제품 D</li>
            </ul>
        </div>
        ```

        -   ::first-line, ::first-letter

            -   각 첫번째줄, 첫번째글자에 스타일을 적용
            -   단, 첫번째글자는 첫번째 줄에 있어야함 (br태그 등으로 띄워져있으면 적용x)

        -   ::before, ::after
            -   각 내용 앞뒤에 콘텐츠(텍스트, 이미지 등)를 추가
            -   부트스트랩의 라벨 과 같은 기능으로 많이 사용 ( ex) NEW 제품 )

> 꿀팁!!!! <br>
> ' : ' 이거든 ' :: ' 이거든 속성이 앞에 있을떄 띄워쓰면 적용되지 않으므로 붙여서 쓸 것!!!
