# 호이스팅(Hoisting)

> [스코프](https://github.com/sunghyunjeonme/TIL/blob/master/JavaScript/execution-context.md)에 대한 개념을 알고 있어야 한다.

호이스팅이란 "끌어올린다"라는 뜻으로 변수 및 함수 선언문(식별자)이 스코프 내의 최상단으로 끌어올려지는 현상을 말한다. (조금 더 깊게 들어가면 이는 실행 컨텍스트의 LexicalEnvironment의 environmentRecord에 식별자 수집 과정을 추상화한 것이다.)

여기서 주의할 점은 `선언문`이라는 점이다. `대입문`은 끌어올려지지 않는다.

```js
console.log(a);
var a = 2;
```

자바스크립트 엔진은 크게 코드를 평가하는 과정과 실행하는 과정으로 나누어 처리한다.

- `var a`
- `a = 2`

코드를 평가하는 과정에서는 `var a` 선언문을 실행하고 코드를 실행하는 과정에서는 `a = 2` 대입문을 실행한다. 따라서, 평가 과정에서 변수 a가 호이스팅되고 아래와 같은 결과가 나온다.

```js
undefined;
```

여기서 `let` 키워드를 사용해서 변수를 선언했다면, `ReferenceError: a is not defined` 참조 에러가 출력될 것이다. `undefined`을 출력하는 이유는 `var` 키워드를 사용했기 때문이다.

- [참고 : 복습](https://github.com/sunghyunjeonme/TIL/blob/master/JavaScript/var-let-const.md)

## 함수 호이스팅에서 주의할 점

- **함수 선언문은 함수 전체가 호이스팅된다.**
  Why ? 런타임 이전에 함수 객체가 생성되어 있고 함수 이름과 동일한 식별자에 할당까지 완료된 상태이다.

```js
func();
function func() {
  console.log("함수 호이스팅");
}
```

```js
함수 호이스팅
```

- **함수 표현식은 호이스팅 되지 않는다.** Why ? 함수가 실행되는 시점에 평가되어 함수 객체가 된다.
- 여기서 `var sub`에 호이스팅이 발생해서 참조할 수는 있기 때문에 `ReferenceError`가 발생하지 않지만 그 값이 `undefined`이기 때문에 `TypeError`가 발생한다.
- 함수 표현식을 사용하면 함수 호이스팅이 발생하는 것이 아니라 변수 호이스팅이 발생한다.

```js
// 함수 참조
console.dir(add); // f add(x, y)
console.dir(sub); // undefined

// 함수 호출

console.log(add(2, 5)); // f add(x, y)
console.log(sub(2, 5)); // TypeError: sub is not a function

// 함수 선언문
function add(x, y) {
  return x + y;
}
// 함수 표현식
var sub = function (x, y) {
  return x - y;
};
```

## 변수 호이스팅과 함수(선언문) 호이스팅의 차이

변수 선언문과 함수 선언문은 런타임 이전에 자바스크립트 엔진에 의해 먼저 실행되어 식별자를 생성한다는 점은 동일하다. 하지만 `var` 키워드로 선언된 변수는 `undefined`로 초기화되고, 함수 선언문을 통해 암묵적으로 생성된 식별자는 함수 객체로 초기화된다.
