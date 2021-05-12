# var, let, const 차이점

모두 변수를 선언하는 키워드라는 것은 동일하다. ES5까지 `var` 키워드를 사용했다. ES6에서 왜 `let`과 `const`가 도입되었을까.

# 스코프 규칙

> 자세한 내용은 [스코프](https://github.com/sunghyunjeonme/TIL/blob/master/JavaScript/scope.md)를 참고

- `var`는 함수 스코프를 갖는다.
- `let`, `const`는 블록 스코프를 갖는다.

```js
var x = 1;
if (true) {
  var x = 10;
}
console.log(x); // 10
```

`var` 키워드로 선언한 변수는 함수의 스코프 블록만을 지역 스코프로 인정한다. 따라서, 코드 블록 내에 선언해도 모두 전역 변수가 된다.

```js
let foo = 1;
{
  let foo = 2;
  let bar = 3;
}
console.log(foo); // 1
console.log(bar); // ReferenceError: bar is not defined
```

`let`과 `const` 키워드로 선언한 변수는 블록 내에 선언된 변수를 지역 변수로 인정한다. 따라서, `bar`를 출력하면 ReferenceError가 발생하는 것이다.

# 호이스팅

- `var`은 함수 스코프의 최상단으로 호이스팅되고 선언과 동시에 `undefined`로 초기화된다.
- `let`과 `const`는 블록 스코프의 최상단으로 호이스팅되지만 값이 할당되기 전까지 어떤 값으로도 초기화되지 않는다. (변수 선언문을 만나면 초기화 단계가 이루어지긴 하지만, 대부분 할당이 이루어지기 때문에)

```js
function foo() {
  console.log(foo); // undefined
  var foo = "Foo";
  console.log(foo); // Foo
}
foo();
```

따라서, 선언 전에 출력하면 `undefined`가 출력된다.

```js
//
function checkHosting() {
  console.log(foo); // ReferenceError
  let foo = "Foo";
  console.log(foo); // Foo
}
checkHosting();
```

반면에, `let`과 `const`의 경우는 호이스팅이 되지만 어떤 어떤 값도 가지지 않기 때문에 ReferenceError가 발생한다. 이를 **TDZ(Temporal Dead Zone)**이라고 한다. 즉, 선언은 되었지만 참조할 수 없는 사각지대를 갖는 셈이다.

![TDZ](../images/let-lifecycle.png)

호이스팅이 이루어지지만, ReferenceError가 뜨는 이유는 TDZ 때문이다.

## 전역 객체로의 바인딩

strict mode가 아니라는 가정하에,

- `var`는 전역 스코프에서 선언되었을 경우 전역 객체에 바인딩 된다.
- `let`과 `const`는 전역 스코프에서 선언되었을 경우 글로벌 객체에 바인딩되지 않는다.

```js
var foo = "Foo"; // 전역 스코프
let bar = "Bar"; // 전역 스코프
console.log(window.foo); // Foo
console.log(window.bar; // undefined
```

브라우저 환경에서 전역 객체는 `window`이다. `var` 경우 바인딩이 되었지만 `let`의 경우 바인딩되지 않았다.

# 재선언

- `var`는 재선언이 가능하다.
- `let`과 `const`는 재선언이 불가능하다.

```js
var foo = 123;
var foo = 234; // 재선언 가능

let bar = 456;
let bar = 789; // SyntaxError: Identifier 'bar' has already been declared
```

## let vs const

- `var`와 `let`은 재할당이 가능하다.
- `const`는 선언과 초기화가 반드시 동시에 일어나야 하며 재할당이 불가능하다. 즉, 고정값을 선언할 때 사용하는 키워드이다.

## 정리하며

- ES6를 사용한다면 `var` 키워드를 사용하지 않는다.
- 변수 선언에는 기본적으로 `const`를 사용하고 `let`은 재할당이 필요한 경우에 한정해서 사용하자.
- `const`를 사용하면 불필요한 재할당을 줄일 수 있기 때문이다.
