# 네이티브 객체 vs 호스트 객체

## ECMAScript

ECMAScript는 자바스크립트 표준 사양이다. 프로그래밍 언어의 값, 타입, 객체와 프로퍼티, 함수, 표준 빌트인 객체 등 핵심 문법을 규정한다.

**각 브라우저 제조사는 ECMAScript 사양을 준수해서 브라우저에 내장되는 자바스크립트 엔진을 구현한다.**

자바스크립트는 일반적으로 프로그래밍 언어로 기본 뼈대(코어)를 이루는 ECMAScript와 브라우저가 별도로 지원하는 클라이언트 사이드 Web API 뜽을 아우르는 개념이다.

## 네이티브 객체(Native Object)

ECMAScript 명세에서 공식적으로 정의된 객체를 말한다.

- `Object`
- `String`
- `Number`
- `Function`
- `Array`
- `RegExp`
- `...`

## 호스트 객체 (Host Object)

자바스크립트를 실행하는 환경에 따라서 종속된 객체를 말한다. 예를 들어, 브라우저에서 제공하는 Wep API가 있다.

- `window`
- `document`
- `location`
- `XMLHttpRequest`
- `querySelector`
- `...`

## 참고

- [Stackoverflow, What is the difference between native objects and host objects?](https://stackoverflow.com/questions/7614317/what-is-the-difference-between-native-objects-and-host-objects)
- [Poiemaweb, 빌트인 객체](https://poiemaweb.com/js-built-in-object)
