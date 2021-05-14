# CSS 미디어 쿼리를 이용한 반응형 작업

반응형 작업이란 특정 디바이스의 사이즈에 맞춰서 그에 따라 화면을 재구성하는 작업이다. CSS 미디어 쿼리를 이용해서 특정 뷰포트의 사이즈일 때, 화면에 변화를 주는 형식으로 반응형 디자인을 할 수 있다.

> 기본 규칙

```css
@media media-type and (media-feature-rule) {
  /* CSS code here */
}
```

**미디어 타입**

지정할 수 있는 미디어 타입은 아래와 같다.

| 타입     | 의미                              | 기본값 |
| -------- | --------------------------------- | ------ |
| `all`    | 모든 미디어 타입에 적용           | `all`  |
| `screen` | 컴퓨터 화면, 타블렛, 스마트 폰 등 |        |
| `print`  | 인쇄 전용                         |        |

**미디어 규칙**

| 특성          | 의미                                |
| ------------- | ----------------------------------- |
| `width`       | 뷰포트 가로 너비                    |
| `max-width`   | 뷰포트 최대 가로 너비(이하)         |
| `min-width`   | 뷰포트 최소 가로 너비(이하)         |
| `height`      | 뷰포트 세로 너비                    |
| `max-height`  | 뷰포트 최대 세로 너비(이하)         |
| `min-height`  | 뷰포트 최소 세로 너비(이상))        |
| `orientation` | 뷰포트 방향(`portrait`,`landscape`) |

> 예시

```css
@media screen and (max-width: 1200px) {
  body {
    color: red;
  }
}
```

뷰포트(`screen`)의 최대 가로 너비가 1200px 이하일 때, body 태그의 글자 색상을 red로 지정하겠다. 기본 규칙의 미디어 특성(`media-feature-rule`)의 조건이 맞을 때만 아래의 코드가 실행된다. 일종의 조건문처럼 이해할 수 있다.

결과는 [코드펜](https://codepen.io/hyuns619/pen/ZEeWJzB)에서 확인할 수 있다.

## 미디어(그리드) 옵션

> 디바이스 종류에 따른 단위는 반응형 대안은 기획 및 디자인 단계에서 결정하는 것이 효과적이다. 아래의 약속은 언제든지 유동적으로 변동될 수 있다.

|        종류         |      디바이스      |  단위(px)   |
| :-----------------: | :----------------: | :---------: |
|    Large Devices    |      Desktops      | 1201px 이상 |
|   Medium Devices    | Desktops + Tablets | 1200px 이하 |
|    Small Devices    |      Tablets       | 992px 이하  |
| Extra Small Devices |       Phones       | 768px 이하  |
