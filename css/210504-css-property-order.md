# CSS 속성 순서 컨벤션

CSS 속성을 작성할 때 조금 더 일관성 있게 통일해서 작성하면 좋을 것 같다는 생각을 하게 되었다. 관련된 포스트를 검색하다가 같은 생각을 하는 사람들이 많았으며 이는 컨벤션으로 이어졌다. 한눈에 보기 쉽게 할 수 있도록 컨벤션을 지정해 놓고 넘어가야겠다.

아래와 같이 다양한 CSS 프로퍼티 순서에 대한 고찰이 있었고 다양한 컨벤션이 존재했다.

## Outside In

[“Outside In” — Ordering CSS Properties by Importance](https://webdesign.tutsplus.com/articles/outside-in-ordering-css-properties-by-importance--cms-21685) **해당 컨벤션에 맞추어 CSS 속성 순서를 작성하자.**

**Outside In** 즉, 큰 범위의 속성부터 작은 범위의 속성 순으로 작성하는 것이다. 예를 들어서 `display`, `float`, `position` 속성은 기존의 흐름을 벗어나게 하고 주변 요소의 흐름에도 영향을 주기 때문에 큰 범주에 포함되는 속성이라고 할 수 있다. `cusor`, `overflow`, `z-index`은 부가적인 속성으로 보고 가장 마지막에 작성한다.

### 순서

- 레이아웃 속성 ( position, float, clear, display)
- 상자 모델 속성 ( width, height, margin, padding)
- 시각적 속성 ( color, background, border, box-shadow)
- 타이포그래피 속성 ( font-size, font-family, text-align, text-transform)
- 기타 속성 ( cursor, overflow, z-index)

### 예시

1. 큰 범위의 속성부터 작은 범위의 속성 순서로 작성한다.
2. 필요에 따라 가독성을 위해 각 속성의 블럭마다 줄바꿈을 해준다.

```css
.button {
  display: inline-block;
  margin: 1em 0;
  padding: 1em 4em;

  color: #fff;
  background: #196e76;
  border: 0.25em solid #196e76;
  box-shadow: inset 0.25em 0.25em 0.5em rgba(0, 0, 0, 0.3), 0.5em 0.5em 0 #444;

  font-size: 3em;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  text-transform: uppercase;
  text-decoration: none;
}
```

## Mozilla

> 모질라에서 권장한 CSS 속성 기술 문서

1. display --객체의 노출여부/표현방식--
2. list-style
3. position --위치/좌표--
4. float
5. clear
6. width / height --크기/여백--
7. padding / margin
8. border / background --윤곽/배경--
9. color / font --글자/정렬--
10. text-decoration
11. text-align / vertical-align
12. white-space
13. other text
14. content --내용--

- `위치` > `윤곽` > `외곽` > `채색` > `타이포` 와 같이 밖에서부터 안쪽으로의 흐름이다.

## Naver

1. display(표시)
2. overflow(넘침)
3. float(흐름)
4. position(위치)
5. width/height(크기)
6. padding/margin(간격)
7. border(테두리)
8. background(배경)
9. color/font(글꼴)
10. animation
11. 기타

## 참고

- [
  “Outside In” — Ordering CSS Properties by Importance](https://webdesign.tutsplus.com/articles/outside-in-ordering-css-properties-by-importance--cms-21685)
