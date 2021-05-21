# CSS 애니메이션(Animation)

## animation 속성

`@keyframes` 규칙을 통해서 애니메이션을 사용한다. (단축 속성)

| 값                          | 의미                      |  기본값   |
| --------------------------- | ------------------------- | :-------: |
| `animation-name`            | @keyframes 이름을 지정    |  `none`   |
| `animation-duration`        | 애니메이션 지속 시간 설정 |   `0s`    |
| `animation-timing-function` | 타이밍 함수 지정          |  `ease`   |
| `animation-delay`           | 대기 시간 설정            |   `0s`    |
| `animation-iteration-count` | 반복 횟수 설정            |    `1`    |
| `animation-direction`       | 반복 방향 설정            | `normal`  |
| `animation-fill-mode`       | 전후 상태 설정            |  `none`   |
| `animation-play-state`      | 재생과 정지               | `running` |

## 사용법

```css
animation: 애니메이션 이름(keyframes) 지속시간 [타이밍 함수, 대기 시간,
  반복횟수, 전후상태, 재생/정지];
```

```css
.box {
  width: 100px;
  height: 100px;
  background: tomato;
}
/* mouse를 hover했을 때 키프레임 발동 */
.box:hover {
  animation: first-animation 2s infinite alternate;
}
/* keyframes 규칙 */
@keyframes first-animation {
  0% {
    width: 100px;
  }
  100% {
    width: 500px;
  }
}
```

## @keyframes 규칙

- 2개 이상의 애니메이션 중간 프레임을 지정하는 역할

```css
@keyframes name {
  0& {
    속성: 값;
  }
  50& {
    속성: 값;
  }
  100& {
    속성: 값;
  }
}
```

```css
@keyframes move-box {
  0% {
    left: 100px;
  }
  100% {
    top: 200px;
  }
}
```

- [예제 보기](https://codepen.io/hyuns619/pen/LYxoLRx)
