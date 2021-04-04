## 블록 (block)

- 사용 가능한 최대 너비를 사용한다.
- 크기를 지정할 수 있다.
- `width:100%;` `height:0;` 으로 시작한다.
- 수직 정렬 형태이다.
- `margin`과 `padding`의 `top, bottom, left, right` 값을 모두 사용할 수 있다.
- 기본 너비가 부모 요소의 넓이다.
- `<div>`, `<p>`, `<h1>` 태그 등이 있다.

## 인라인 (Inline)

- 필요한만큼의 너비를 사용한다.
- 크기를 지정할 수 없다.
- `width:0;` `height:0;` 으로 시작한다.
- 수평 정렬 형태이다.
- `margin`과 `padding`의 `top, bottom`은 사용할 수 없다.
- `<span>`, `<img>` 태그 등이 있다.

## 인라인 블록 (Inline Block)

- `display` 속성이 `inline-block` 으로 지정된 요소는 기본적으로 인라인 요소처럼 수평으로 정렬된다. 블록 요소에만 지정할 수 있었던 `width`와 `height` 그리고 `margin`과 `padding` 속성의 상하 간격 또한 지정할 수 있게 된다.
- `<button>`, `<select>` 태그 등이 있다.

## 정리

- 블록 요소는 레이아웃을 구성할 때 사용한다.
- 인라인 요소는 텍스트를 다룰 때 사용한다.
- `width`와 `height`를 별도로 설정하지 않았을 경우에는 자동적으로 브라우저에서 기본 값 `auto`를 설정한다. `auto` 값은 블럭 요소와 인라인 요소에 따라서 다르게 동작한다.

## 참고

[Codepen](https://codepen.io/hyuns619/pen/bGgRbGw)을 통해서 요소 간의 특징을 조금 더 명확하게 파악할 수 있다.
