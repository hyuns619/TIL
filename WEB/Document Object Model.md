# DOM(Document Object Model)

> DOM(문서 객체 모델 : Document Object Model)

텍스트 파일로 만들어져 있는 웹 문서를 브라우저에 렌더링하려면 웹 문서를 브라우저가 이해할 수 있는 구조로 메모리에 올려야 한다. 브라우저의 렌더링 엔진은 웹 문서를 로드한 후, 파싱하여 웹 문서를 브라우저가 이해할 수 있는 구조로 구성하여 메모리에 적재하는 데 이를 DOM이라고 한다. 즉, **모든 요소와 요소의 속성, 텍스트를 각각의 객체로 만들고 이들 객체를 부모 관계로 표현할 수 있는 트리 구조로 구성한 것이 DOM이다.** DOM은 자바스크립트를 통해 동적으로 변경할 수 있으며 변경된 DOM은 렌더링에 반영된다.

<center>

![dom](../images/web_dom.png)
<small>브라우저는 웹 문서(HTML, XML, SVG)를 로드한 후, 파싱하여 DOM을 생성한다.</small>

</center>

DOM은 자바스크립트가 자신에게 접근해서 수정하는 방법을 제공하는데 이를 DOM API(Application Programming Interface)라고 부른다. 이 말인즉슨 정적인 웹 페이지에 접근하여 동적으로 웹 페이지를 변경하기 위한 방법은 메모리 상에 존재하는 DOM을 변경하는 것이고, 이때 필요한 것이 DOM에 접근하고 변경하는 프로퍼티와 메서드의 집합인 DOM API이다.

<center>

DOM은 HTML과 JavaScript를 이어주는 진입점과 같은 역할을 한다.

![dom-sceond](..images/../../images/web_dom2.png)

</center>

# DOM tree

![dom-tree](../images/web_dom_tree.png)

DOM tree는 브라우저가 HTML 문서를 로드한 후 파싱하여 생성하는 모델을 의미한다. 계층 간의 구조가 나무가 뿌리를 내리듯이 위에서 아래로 뻗는 형태로 되어 있는데 이것을 나무에 비유해서 DOM tree라고 표현한다.

DOM에서 모든 요소, 속성, 텍스트는 하나의 객체이며 각각의 객체를 노드(Node)라고 칭한다. 모든 노드는 document 객체의 자식이다. 또한 각 노드 간의 위치 관계를 `부모 노드(parent node), 자식 노드(child node), 형제 노드(sibling node)`로 표현할 수 있다.

- document
  - parent node
    - child node
    - sibling node

DOM tree는 대표적으로 네 종류의 노드로 구성된다.

- 문서 노드 (Document Node) : DOM tree의 최상위 노드

  - 각각의 요소, 속성, 텍스트 노드에 접근하려면 문서 노드를 통해야 함.

- 요소 노드 (Element Node) : HTML 태그를 표현하는 노드

  - ex. `<body>, <h1>, <p>` 등과 같은 각종 tags

- 어트리뷰트 노드(Attribute Node) : HTML 요소의 속성을 표현하는 노드

  - 해당 요소 노드를 찾아 접근하면 속성을 수정할 수 있다.

- 텍스트 노드 (Text Node) : 문자를 표현하는 노드
  - ex. `<h1> tag 내부의 안녕하세요` 와 같은 문자
  - 요소 노드의 자식 요소가 되며 따로 자식 노드를 가질 수 없다.
  - 이를 나무의 잎사귀에 비유해서 leaf node라고 부르기도 한다.

## 접근 메서드

id 속성으로 노드 선택하기

```js
document.getElementById("id");
// 하나의 id tag를 선택할 때 사용된다.
```

class 속성으로 노드 선택하기

```js
document.getElementsByClassName("class");
// 여러 tag를 한 번에 선택할 때 사용된다.
```

css 선택자로 노드 선택하기

```js
document.querySelector("(#, .) css selector");
// 하나의 요소 선택
document.querySelectorAll("(#, .) css selector");
// 여러 개의 요소 선택
```

## DOM 이동 시 활용 가능한 탐색 프로퍼티

탐색 프로퍼티를 사용하면 이웃 노드로 바로 이동할 수 있다.

- 모든 노드에 적용 가능

  |       프로퍼티       |   유형    |                       결과                       |
  | :------------------: | :-------: | :----------------------------------------------: |
  |   node.childNodes    | 자식 노드 |         node의 자식 노드 모음(NodeList)          |
  |   node.firstChild    | 자식 노드 |          node의 첫 번째 자식 노드 하나           |
  |    node.lastChild    | 자식 노드 |           node의 마지막 자식 노드 하나           |
  |   node.parentNode    | 부모 노드 |              node의 부모 요소 하나               |
  | node.previousSibling | 형제 노드 | node의 이전(previous) 혹은 좌측에 있는 노드 하나 |
  |   node.nextSibling   | 형제 노드 |   node의 다음(next) 혹은 우측에 있는 노드 하나   |

- 요소 노드에만 적용 가능
  | 프로퍼티 | 유형 | 결과 |
  | :----------------------------: | :------------: | :-------------------------------------------------: | --- |
  | element.children | 자식 요소 노드 | element의 자식 요소 모음(HTMLCollection) |
  | element.firstElementChild | 자식 요소 노드 | element의 첫 번째 자식 요소 하나 | |
  | element.lastElementChild | 자식 요소 노드 | element의 마지막 자식 요소 하나 | |
  | element.parentElement | 부모 요소 노드 | element의 부모 요소 하나 | |
  | element.previousElementSibling | 형제 요소 노드 | element의 이전(previous) 혹은 좌측에 있는 요소 하나 | |
  | element.nextElementSibling | 형제 요소 노드 | element의 다음(next) 혹은 우측에 있는 요소 하나 |
  | |

## HTML 콘텐츠 조작

HTML 문서를 객체로 표현한 DOM의 각 노드들은 다양한 프로퍼티를 갖고 있다. HTML 콘텐츠를 조작하기 위해 아래와 같은 메서드를 사용할 수 있다.

innerHTML 프로퍼티

```js
const myTag = document.querySelector("#list-1");
myTag.innerHTML = "value";
```

- 요소 노드 내부의 HTML 코드를 문자열로 리턴해준다.
- 마크업도 포함된다.

outerHTML 프로퍼티

```js
const myTag = document.querySelector("#list-1");
myTag.outerHTML = "value";
```

- 해당 요소를 포함한 전체의 요소를 HTML 코드를 문자열로 리턴해준다.

textContent 프로퍼티

```js
const myTag = document.querySelector("#list-1");
myTag.textContent = "value";
```

- 요소의 텍스트를 변경한다. textContent를 통해 새로운 텍스트를 할당하면 텍스트를 변경할 수 있다.
- 마크업을 포함하면 문자열로 인식되어 그대로 출력된다.
