# CSS 기본 선택자 정리

## <mark>기본 문법

선택자로 검색한 대상에 각 속성과 값을 삽입해서 스타일을 지정한다.

## <mark>CSS 선언 방식

### 인라인(In-line)</mark>

- HTML 태그에 직접 스타일 속성값을 지정하는 방법이다.

```html
<div style="color:red; font-size:20px; font-weight:bold;">HELLO</div>
```

### 내장(Embedded)

- head 태그 안에 style tag를 선언하여 HTML 내부에서 사용하는 방법이다.

```html
<head>
  <style>
    div {
      color: red;
      font-size: 20px;
      font-weight: bold;
    }
  </style>
  <body>
    <div>HELLO</div>
  </body>
</head>
```

### 외부 (External)

- CSS 스타일 파일을 따로 저장해서 페이지에 링크를 거는 방법이다. 여러 개의 파일을 링크할 수 있다.

```html
<head>
  <link rel="stylesheet" href="css/common.css" />
</head>
<body>
  <div>HELLO</div>
</body>
```

```css
/* <!-- common.css -- >  */
div {
  color: red;
  font-size: 20px;
  font-weight: bold;
}
```

### `@import` 방식 (at 규칙)

- 외부 방식으로 링크된 CSS 안에 또 다른 CSS를 불러오는 방법이다.
- 페이지가 모두 로딩되어야만 이미지가 로딩되는 이슈로 인해서 적절한 상황에 맞게 사용해야 한다.

```html
<head>
  <link rel="stylesheet" href="css/common.css" />
</head>
<body>
  <div>HELLO</div>
</body>
```

```css
/* common.css */
@import url("./common2.css");
```

```css
/* common2.css */
div {
  color: red;
  font-size: 20px;
  font-weight: bold;
}
```

## <mark>기본 선택자

- 전체 선택자 `*`
- 태그 선택자 `E`
- 클래스 선택자 `.E`
- 아이디 선택자 `#E`

class 선택자를 지향해야 하는 이유

1. 우선 순위 문제
2. 일관된 규칙성
3. 재사용

## <mark>복합 선택자

- 일치 선택자 `EF`
  - small>`E`와 `F`를 동시에 만족하는 요소 선택</small>
- 자식 선택자 `E` > **`F`**
- 후손(하위) 선택자 `E` **`F`**
- 인접 형제 선택자 `E` + **`F`**
  - <small> `E`의 다음 형제 요소 `F` 하나만 선택</small>
- 일반 형제 선택자 `E` ~ **`F`**
  - <small> `E`의 다음 형제 요소 `F` 모두 선택</small>

## <mark>가상 클래스 선택자

요소 앞에 콜론`:`을 붙여 사용한다.

- hover

```css
e: hover; /* 요소에 마우스가 올라가 있는 동안에만 요소 선택 */
```

- active

```css
e: active; /* 요소를 마우스로 클릭하는 동안에만 요소 선택 */
```

- focus

```css
e: focus; /* 요소가 포커스된 동안에만 요소 선택, 대화용 콘텐츠에서 사용 가능 */
```

`hover`, `active`, `focus`는 동작을 나타내는 선택자이다. 자바스크립트 이벤트와는 관련이 없지만, 특별하게 움직임을 나타내는 선택자이기 때문에 따로 알고 있도록 하자.

- first-child
- last-child

```css
e: first-child; /* 요소가 형제 요소 중 첫 번째 요소라면 선택 */
e: last-child; /* 요소가 형제 요소 중 마지막 요소라면 선택 */
```

```css
.fruits li:first-child {
  color: red;
}
```

```html
<ul class="fruits">
  <li>딸기</li>
  <li>사과</li>
  <li>오렌지</li>
  <li>망고</li>
</ul>
```

1. `fruits`라는 클래스를 가진 요소를 선택했다.
2. `fruits` 뒤에 공백이 있는데 이는 후손 선택자
3. `fruits` 요소의 후손 중 `li` 태그를 찾아라.
4. `first-child` 가상 클래스 선택자, 첫 번째 자식 요소를 찾아라.
5. 결과는 `<li>딸기</li>` 선택

- nth-child

```css
e: nth-child(n);
/* 요소가 형제 요소 중 n번째 요소라면 선택*/
/* n 키워드 사용시 0부터 해석*/
```

- nth-of-type

```css
e: nth-of-type(n);
/* 요소의 태그 이름과 동일한 형제 요소 중 요소가 n번째 요소라면 선택  */
```

- not

```cs
E:not(s)
```

- [예제1](https://codepen.io/hyuns619/pen/QWdOWXx) / [예제2](https://codepen.io/hyuns619/pen/jOyaWvo)

### 뒤에서부터 앞으로 해석하면 이해하기 더 쉽다.

## <mark>가상 요소 선택자

CSS를 통해서 HTML에 가상의 요소를 생성할 수 있다.

요소 앞에 콜론`::`을 붙여 사용한다.

- before
- after

```css
e::before
/* 요소 내부의 앞에 내용(content)을 삽입 */
e::after
/* 요소 내부의 뒤에 내용(content)을 삽입 */
```

- [예제](https://codepen.io/hyuns619/pen/poRdbEW)

## <mark> 속성 선택자

- [attr]
- [arrt=value]
- [attr^=value]
- [attr$=value]
- [예제1](https://codepen.io/hyuns619/pen/BapmLPO) / [예제 2](https://codepen.io/hyuns619/pen/zYNPKbB)

## <mark> 상속(Inheritance)

글자를 다루는 속성은 상속이 된다. 그 외의 상속되지 않는 속성(값)도 `inherit`이라는 값을 사용하여 부모에서 자식으로 강제 상속시킬 수 있다. 단, 모든 속성이 강제 상속을 사용할 수 있는 것은 아니다.

## <mark> 우선 순위

같은 요소가 여러 선언의 대상이 될 경우, 어떤 선언의 CSS 속성을 우선해서 적용할지 결정하는 방법이다.

1. `!important`
2. 인라인 선언 방식
3. 아이디 선택자
4. 클래스 선택자
5. 태그 선택자
6. 전체 선택자
7. 상속

## CSS 단위

- **`px`**
  - 해상도에 따라 픽셀 값은 변함
  - 절대적인 값을 고정할 때 사용
- **`%`**
  - 부모 요소의 사이즈에 영향을 받음
- **`em`**
  - 현재 자기 자신의 `font-size`에 영향을 받음
  - 폰트는 상속이 되기 때문에 후손 단위로 사이즈가 넘어가는 형태
  - 특정한 상위 요소에 절대적인 값을 지정하고 하위 요소는 그 값에 맞게 변형되게끔 사용함
- **`rem`**
  - 최상위 `html` 요소에 지정된 `font-size`의 영향을 받음
  - `html` 요소에 지정된 `font-size` 상속을 무시하려면 하위 요소에 `font-size` 값을 지정
- [예제](https://codepen.io/hyuns619/pen/NWdwBVw?editors=1100)

- **`vw`**, **`vh`**

  - `viewport`를 기준으로 가로, 세로를 지정
  - `100%`가 최대 값이고 백분율을 기준으로 사이즈 조절

- **`vmin`**, **`vmax`**
  - `vmax`는 너비 중 더 긴 쪽을 백분율로 계산
  - `vmin`은 너비 중 더 짧은 쪽을 백분율로 계산
