# Ajax

## Ajax란 무엇인가?

Ajax(Asynchoronous JavaScript and XML)란 자바스크립트를 사용하여 브라우저가 서버에게 비동기(Asynchronous) 방식으로 데이터를 요청하고, 서버가 응답한 데이터를 받아서 웹페이지를 동적으로 갱신하는 프로그래밍을 말한다.

## Ajax 이전

이전의 웹페이지는 html 태그로 시작해서 html 태그로 끝나는 완전한 HTML을 서버로부터 전송받아 웹페이지 전체를 처음부터 다시 렌더링하는 방식으로 동작했다. 따라서 화면이 전환되면 서버로부터 다시 새로운 HTML을 전송받아 웹페이지 전체를 렌더링했다. 이런 방식에는 아래와 같은 문제가 있다.

- 불필요한 데이터 통신 발생
- 화면 전환 시 순간적으로 깜박이는 현상이 발생
- 서버로부터 응답이 있을 때까지 다음 처리는 블로킹

## Ajax의 등장

Ajax의 등장 이전에는 동기적인 방식으로 브라우저와 서버 간의 통신을 했었다면 Ajax가 등장함으로써 비동기적인 통신이 가능하게 되었다. 즉, 서버로부터 웹페이지의 변경에 필요한 데이터만 비동기 방식으로 전송받아 웹페이지의 변경할 필요가 없는 부분은 다시 렌더링하지 않고, 변경할 부분만 한정적으로 렌더링하는 방식이 가능해진 것이다.

- Ajax(Asynchoronous JavaScript and XML)
  - XMLHttpRequest
  - Fetch API / ES6(ES2015)
  - JSON (data format)

## 어떻게 사용하는가?

## XMLHttpRequest

Wep API인 XMLHttpRequest 객체는 HTTP 통신을 위한 다양한 프로퍼티와 메서드를 제공한다.

XMLHttpRequest 생성자 함수를 호출하여 생성하고 `open()`, `send()` 등과 같은 메서드를 사용한다.

```js
const xhrRequest = new XMLHttpRequest();
xhrRequest.open(
  "GET",
  "https://learnwebcode.github.io/json-example/animals-1.json"
);
xhrRequest.onload = () => {
  const xhrRequest = JSON.parse(xhrRequest.responseText);
  console.log(xhrRequest[0]);
};
xhrRequest.send();
```

`open()`과 같은 요청 메서드와 URL을 설정하고, 모두 로드되었을 때 콜백함수를 초기화한다.

## Fetch API

기존의 `XMLHttpRequest` 객체를 이용한 Ajax는 사용성과 가독성 측면에서 부족했다. 그래서 등장한 것이 `Fetch API`로 ES6(ES2015)에서 표준이 되었다. IE를 지원하지 않는다는 점을 제외하고는 `XMLHttpRequest` 보다 훨씬 직관적이다. `fetch`는 Promise를 리턴한다.

```js
fetch("https://learnwebcode.github.io/json-example/animals-1.json")
  .then((res) => res.json())
  .then((resJson) => console.log(resJson));
```

`fetch()` 메서드는 URL을 인자로 받고 응답을 처리하기 위한 promise를 반환한다. 응답을 처리할 때는
