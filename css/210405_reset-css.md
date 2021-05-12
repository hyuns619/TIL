# CSS Reset

크롬, 파이어폭스, IE 등 브라우저마다 HTML 요소의 기본 스타일을 가지고 있다. 이와 같은 부분은 CSS로 스타일링을 할 때 동일한 스타일 적용을 방해하기 때문에 이를 방지하기 위해서 사전에 스타일 초기화를 진행한다. 스타일 초기화 전략은 크게 `CSS Reset`과 `CSS Normalize`가 있다.

## Reset.css vs Normalize.css

모든 브라우저 내장 스타일을 없애는 기법으로, 어떤 스타일도 적용되어 있지 않은 상태에서 스타일링을 시작할 수 있다. `h1`~`h6`, `p`, `em` 등 각 태그에 적용된 스타일을 모두 없앤다. 많은 초기화 방법이 있지만, 그중에서도 [Eric Mayer](https://cdnjs.com/libraries/meyer-reset)의 Reset CSS를 많이 사용하고 있다.

## Normalize.css

모든 브라우저의 스타일을 동일하게 하는 기법으로, 모든 기본 스타일을 없애는 `Reset CSS`와는 기본 스타일을 최대한 보존하면서 그에 대한 버그를 줄이는 방향으로 스타일을 재지정하는 방법이다. [necolas](https://github.com/necolas/normalize.css/)의 `Normalize CSS`를 많이 사용하고 있다.

## 차이점

- `Reset CSS`의 경우에 모든 것을 초기화하기 때문에 스타일을 처음부터 적용해 나가는 것이 힘들 수 있으며 브라우저의 버그를 고치는 것이 아니기 때문에 브라우저마다 다른 버그를 발생시킬 수 있다. **완전히 초기화하는 것이기 때문에 업데이트를 할 필요가 없다.**

- `Normalize CSS`의 경우에는 브라우저가 업데이트 되어서 새로운 내장 스타일이 적용되었을 때마다 각 브라우저의 다른 점을 파악해서 스타일을 업데이트해야 하기 때문에 끊임없는 버전 업데이트가 있어야 최신 스타일을 유지할 수 있다. 하지만, **브라우저의 버그를 고치기 때문에 버그가 발생할 걱정을 덜면서 기본 스타일을 어느 정도는 유지하기 때문에 스타일링에 힘을 덜 쏟을 수 있다.**

각각의 장단점이 있기 때문에 상황에 맞게 적용해서 사용하면 될 것 같다.

## 참고

- [CSS reset 과 CSS normalize 쉽게 이해하기](http://hleecaster.com/css-reset-normalize/)
- [Normalize.css - CSS 초기화](https://webdir.tistory.com/455)
