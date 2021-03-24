# 스코프(Scope)

## 정의

스코프는 자바스크립트 엔진이 `식별자(Identifier)`를 검색할 때 사용하는 규칙이다. 자바스크립트 엔진은 이 규칙대로 식별자를 찾는다.

> 식별자(Identifier) : 변수, 함수의 이름과 같이 어떤 대상을 다른 대상과 구분하여 식별할 수 있는 유일한 이름

## 스코프가 없다면?

스코프가 없다면 어떻게 될까를 생각해 보면 그에 대한 효용을 알 수가 있다. 스코프가 없다면, 한 코드 내에서 같은 식별자 이름을 사용하는 것은 충돌을 일으킬 수 있으므로 프로그램 전체에서 하나밖에 사용할 수 없을 것이다.

예를 들어, 내 PC의 폴더를 생각해 보자. 새로운 폴더를 만들 수 없었다면 같은 이름을 갖는 파일을 하나밖에 만들 수 없었을 것이다.

스코프는 위와 같은 `폴더` 역할을 하는 셈이다. **즉, 스코프는 식별자 간의 충돌을 방지하기 위해 식별자에 대한 유효 범위를 정해 놓은 규칙이라고 이해할 수 있다.**

## 스코프 체인

현재 스코프에서 식별자를 검색할 때 상위 스코프를 연쇄적으로 찾아 나가는 방식을 말한다. 실행 컨텍스트가 생성되면서 `LexicalEnvironment`가 만들어지고 내부 구성으로 `outerEnvironmentReference` 가 있는데 바로 이 outer 참조 값이 상위 스코프의 LexicalEnvironment를 가리키기 때문에 이를 통해 체인처럼 연결되는 것이다.

외부에서 선언한 변수는 내부에서 접근할 수 있지만, 내부에 선언한 변수에 외부에서 접근할 수 없다는 것이 위와 같은 이유에서다. (하위 컨텍스트의 outerEnvironmentReference를 통해 상위 컨텍스트까지 연쇄적으로 탐색하여 나가기 때문임. 즉, 상위 컨텍스트의 LexicalEnvironment에는 outerEnvironmentReference가 없는 것이다.)

다음과 같은 과정으로 스코프 체인을 검색한다.

1. 현재 실행 컨텍스트의 LexicalEnvironment의 environmentRecord에서 식별자를 검색한다.
2. 식별자 정보가 없으면 outerEnvironmentReference를 통해 상위 컨텍스트의 environmentRecord에서 식별자를 검색한다.
3. 위와 같은 과정을 전역 컨텍스트의 LexicalEnvironment까지 탐색해도 해당 식별자 정보를 찾지 못하면 undefined 및 에러를 반환한다. (undefined와 Reference error는 var, let 키워드와 연관이 있음.)

## Reference

- [You-Dont-Know-JS](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch1.md)
- [PoiemaWeb, 스코프](https://poiemaweb.com/js-scope)
