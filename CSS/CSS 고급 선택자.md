# CSS 고급 선택자

## 🌌연결선택자

1. **하위 선택자**

```html
상위요소 하위요소
```

```html
<style>
    section {
        width: 600px;
        margin: 20px auto;
    }
    p {
        width: 500px;
        padding: 10px;
        background-color: #fff;
        border: 1px solid #ccc;
        line-height: 2;
    }
    section p {
        /* section 요소의 모든 하위 p 요소에 적용 */
        color: blue; /* 글자색을 파란색으로 */
    }
</style>
```

-   하위 요소에 스타일을 적용
-   하위선택자를 사용하면 부모요소에 포함된 하위 요소를 모두 선택하며 자손선택자라고도 합니다.

<br>

2. **자식 선택자**

```html
부모요소 > 자식요소
```

```html
<style>
    section {
        width: 600px;
        margin: 20px auto;
    }
    p {
        width: 500px;
        padding: 10px;
        background-color: #fff;
        border: 1px solid #ccc;
        line-height: 2;
    }
    section > p {
        /* section 요소의 자식 p 요소에 적용 */
        color: blue; /* 글자색을 파란색으로 */
    }
</style>
```

3. 인접 형제 선택자

```html
요소1 + 요소2
```

```html
<style>
    section {
        width: 600px;
        margin: 20px auto;
    }
    p {
        width: 500px;
        padding: 10px;
        background-color: #fff;
        border: 1px solid #ccc;
        line-height: 2;
    }
    h1 + p {
        /* h1 요소의 형제 요소 중 첫번째 p 요소에 적용 */
        background-color: #222; /* 배경은 검은색으로 */
        color: #fff; /* 글자는 흰색으로 */
    }
</style>
```

<br>

4. 형제 선택자

```html
요소1 ~ 요소2
```

```html
<style>
    section {
        width: 600px;
        margin: 20px auto;
    }
    p {
        width: 500px;
        padding: 10px;
        background-color: #fff;
        border: 1px solid #ccc;
        line-height: 2;
    }
    h1 ~ p {
        /* h1 요소와 형제인 모든 p 요소에 적용 */
        background-color: #222; /* 배경은 검은색으로 */
        color: #fff; /* 글자는 흰색으로 */
    }
</style>
```

<br><br>

## 🪐속성 선택자

1. **[속성]**

```html
<style>
    a[href] {
        background: yellow;
        border: 1px solid #ccc;
        font-weight: normal;
    }
</style>
```

-   특정 속성이 있는 요소를 선택하는 선택자
-   href속성이 있는 요소를 입력한 예제
    <br>

2. **[속성 = 속성값]**

```html
<style>
    a[target='_blank'] {
        padding-right: 30px;
        background: url(images/newwindow.png) no-repeat center right;
    }
</style>
```

-   특정 속성값이 있는 요소를 선택하는 선택자
-   target속성값이 \_blank만 선택하는 예제

<br>

3. **[속성 ~= 속성값]**

```html
<style>
    a[class~='button'] {
        box-shadow: rgba(0, 0, 0, 0.5) 4px 4px; /* 그림자 지정 */
        border-radius: 5px; /* 테두리를 둥글게 */
        border: 1px solid #222;
    }
</style>
```

-   여러개 값 중에서 특정 속성값이 포함된 속성 요소를 선택하는 선 택자
-   button스타일이 있는 요소를 찾는 예제

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
```

-   특정 속성값이 포함된 요소를 선택하는 선택자
-   title속성값에 us나 us-로 연결된 속성값이 있는 a 요소를 찾는 예제

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
```

-   특정 속성값으로 시작하는 속성 요소를 선택하는 선택자

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
```

-   특정한 값으로 끝나는 속성의 요소를 선택하는 선택자
-   href에 링크된 파일의 확장자에 따라 아이콘 다르게 표시하는 예제

<br>

7. **[속성 *= 속성값]**

```html
<style>
    a[href*='w3'] {
        /* href 속성값 중에 w3가 있는 a 요소를 찾는 선택자 */
        background: blue;
        color: white;
    }
</style>
```

-   일부 속성값이 일치하는 요소를 선택하는 선택자
-   w3가 포함된 요소를 href를 이용해서 찾는 속성

<br><br>

## 🌍가상 클래스와 가상 요소
