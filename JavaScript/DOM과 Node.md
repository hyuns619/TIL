> [210202_TIL](<https://github.com/sunghyunjeonme/TIL/blob/master/TIL%20(Today%20I%20Learned)/%20February/210202_TIL.md>)의 내용을 토대로 이해가 미흡했던 부분을 다시 정리하는 글이다.

## DOM과 Node

[앞에서](<https://github.com/sunghyunjeonme/TIL/blob/master/JavaScript/%EB%AC%B8%EC%84%9C%20%EA%B0%9D%EC%B2%B4%20%EB%AA%A8%EB%8D%B8(Document%20Object%20Model).md>) 정리한 문서 객체 모델(DOM)은 모든 요소, 속성, 텍스트를 자바스크립트가 이해할 수 있도록 객체로 변환하는 역할을 했다.

간단한 문서를 통해 DOM 구조와 Node의 개념에 대해 자세히 이해하자.

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
  </head>

  <body>
    <h1>DOM이란</h1>
    <p><strong>Document Object Model</strong>의 줄임말입니다.</p>
  </body>
</html>
```

DOM 트리의 최상단에는 `document` 객체가 존재하는데 해당 객체는 DOM에 접근하기 위한 `진입점`의 역할을 한다. `document` 객체는 JavaScript가 DOM의 세계로 들어올 수 있도록 두 팔 벌려 환영하고 있는 셈이다.

`document.body`는 `<body>` 태그를 객체로 나타낸 것이고 이 객체는 DOM 트리를 구성

왜 굳이 객체화할까? 왜 DOM을 만들었을까?

모든 콘텐츠를 객체화한다면, 단연 자바스크립트가 해당 콘텐츠에 접근할 수 있게 되고 그에 따른 다양한 조작을 할 수 있을 것이다.

DOM은 자바스크립트가 모든 콘텐츠에 접근해서 interactive 할 수 있도록 다양한 인터페이스를 제공한다. [DOM은 다음과 같은 API를 제공한다.](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model#dom_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4)

DOM tree의 상단에는 `document` 객체가 존재하고 이 객체는 DOM에 접근하기 위한 `진입점`과 같다. document 객체는 JavaScript가 DOM의 세계로 들어올 수 있도록 두 팔 벌려 환영하고 있는 셈이다. 이 진입점(document)을 통과하면 어떤 `노드`에도 접근할 수 있다.

## DOM과 Node

브라우저는 HTML코드를 해석해서 트리 형태로 구조화된 Node들을 가지고 있는 문서(DOM)을 생성한다.

즉 DOM은 자바스크립트 Node 개체의 계층화된 트리이다.

![node](../images/web_node_tree.png)

위의 그림처럼

```js
for (let key in Node) {
  console.log(key, " = " + Node[key]);
}
ELEMENT_NODE = 1;
ATTRIBUTE_NODE = 2;
TEXT_NODE = 3;
CDATA_SECTION_NODE = 4;
ENTITY_REFERENCE_NODE = 5;
ENTITY_NODE = 6;
PROCESSING_INSTRUCTION_NODE = 7;
COMMENT_NODE = 8;
DOCUMENT_NODE = 9;
DOCUMENT_TYPE_NODE = 10;
DOCUMENT_FRAGMENT_NODE = 11;
NOTATION_NODE = 12;
```

`console.dir(document.body)`로 `<body>` 개체를 살펴보면 아래와 같은 결과를 확인할 수 있다.

```js
console.dir(document.body);
nodeType: 1;
__proto__: HTMLBodyElement;
```
