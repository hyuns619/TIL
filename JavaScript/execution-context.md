# 실행 콘텍스트(Execution Context)

## 정의

실행 콘텍스트는 코드를 실행하는 데 필요한 환경을 제공하고 코드의 실행 결과를 관리하는 영역이다. 조금 추상적인 개념이지만, 실제 자바스크립트 엔진 내부에서 작동되고 있는 내부 메커니즘이다. 자바스크립트 엔진에 의해 생성되고 코드를 실행할 때 필요한 환경 정보를 담은 객체의 집합이라고 이해할 수 있다. 코드가 실행되는 것은 `실행 콘텍스트` 내부에서 실행되고 관리되고 있는 것이다.

자바스크립트 엔진은 코드를 실행하기 위해 아래와 같은 정보를 알고 있어야 한다.

- 변수 : 전역변수, 지역변수, 매개변수, 객체의 프로퍼티
- 함수의 선언
- 변수의 유효 범위
- this

실행 콘텍스트라는 개념을 `여권`에 빗대어 표현하면 보다 쉽게 이해할 수 있다. 여권에는 국적, 이름, 생년월일 등과 같은 정보(코드를 실행하는 데 필요한 정보)가 기재되어 있으며 여권(실행 콘텍스트)이 없으면 여행을 할 수 없다(모든 코드는 실행 콘텍스트 내부에서 실행). 여권을 통해서 입국 및 출국 심사를 진행하고 여권에 기재되어 있는 신상정보를 통해 여행자를 관리할 수 있다.

# 종류

자바스크립트 코드는 4가지 종류로 구분되어 있다. 전역 스코프에서 실행하는 전역 코드, 함수 스코프에서 실행하는 함수 코드, 많이 사용하지 않는 개념으로 여기서 다루진 않겠지만 `eval ()`로 실행되는 코드 그리고 모듈 스코프에서 실행되는 모듈 코드가 있다. 각각의 코드는 자신만의 `실행 콘텍스트`를 생성한다.

자바스크립트 엔진이 스크립트 파일을 실행하기 전에 가장 먼저 `전역 실행 콘텍스트(Global Execution Context, GEC)`가 생성되고, 함수를 호출할 때마다 `함수 실행 콘텍스트(Function Execution Context, FEX)`가 생성된다. 여기서 주의할 점은 전역 콘텍스트는 코드의 실행 이전에 생성되지만 함수 콘텍스트의 경우에는 함수를 호출할 때 생성된다는 점이다.

## 실행 콘텍스트 스택 (Execution Context Stack)

실행 콘텍스트 스택(=Call Stack)은 코드의 실행 순서를 관리한다. 코드가 평가되면 실행 콘텍스트가 생성되고 콜 스택의 최상위에 쌓인다. 콜 스택의 최상위에 존재하는 실행 콘텍스트는 언제나 현재 실행 중인 코드의 실행 콘텍스트이다.

```js
const x = 1;

function foo() {
  const y = 2;

  function bar() {
    const z = 3;
    console.log(x + y + z);
  }
  bar();
}
foo(); // 6
```

가장 첫 번째로 코드가 실행되기 전에 전역 실행 콘텍스트가 콜 스택에 쌓이고 이어서 `foo` 함수 실행 콘텍스트가 생성되고 콜 스택에 추가(push)되며 코드가 실행된다. 그리고 `bar` 함수에 대한 실행 콘텍스트가 생성되며 콜 스택에 추가되어 실행된다. 결과적으로 `6`이 출력되고 `bar` 함수는 종료된다. 이때 자바스크립트 엔진은 `bar` 함수 실행 콘텍스트를 콜 스택에서 제거(pop)한다. `foo` 함수는 더 이상 실행할 코드가 없으므로 종료되고 콜 스택에서 제거된다. 마지막으로 전역 코드가 남아있지 않으므로 전역 실행 콘텍스트도 콜 스택에서 제거된다. [GIF](https://miro.medium.com/max/1100/1*dUl6qPEaDJJTXWythQsEtQ.gif)를 통해서 더 쉽게 이해할 수있다.

##



- **VariableEnvironment**
  - environmentRecord (snapshot)
  - outerEnvironmentReference (snapshot)

- **LexicalEnvironment (어휘적/사전적 환경)**

  - environmentRecord (현재 콘텍스트의 식별자 정보, HOISTING)

    - 현재 실행 콘텍스트에 있는 식별자 정보를 수집해서 environmentRecord에 저장한다. 이를 HOISTING이라고 한다. 코드의 식별자 정보를 위로 끌어올린다.
    - 전역 실행 콘텍스트가 생성되고 실행될 때 가장 먼저 environmentRecord에 정보를 수집해서 저장한다. 현재 실행 콘텍스트에 선언되어 있는 식별자들이 무엇인지를 수집하고 저장하는 과정. 호이스팅이랑 같은 맥락.
    - inner에게 있어서 outerEnvironmentReference란 outer의 LexicalEnvironment
    - out의 outerEnvironmentReference란 전역의 lexicalEnvironment
      - 스코프는 실행 콘텍스트에 의해 결정되며 
      - outerEnvironmentReference에서 일어남 
- 
  - outerEnvironmentReference
    - 외부 환경에 대한 참조이다. 현재 실행 콘텍스트 외부의 식별자 정보(LexicalEnvironment)
    - SCOPE CHAIN 
    - 스코프는 실행 콘텍스트에 의해 결정된다.
    - 내부에서 외부로는 가능, 외부에서 내부로는 불가능. environmentRecord와 연관. why ? inner에서 선언한 변수는 lexicalEnvironment에 수집해 놓은 정보가 없기 때문에 외부에서 내부는 볼 수 없다
    - 전역에서 선언한 변수는 어디서 사용 가능, inner에서 사용한 변수는 inner에서만 사용 가능

inner 내부에서는 자신의 environmentRecord와 out의 LexicalEnvironment out의 outerEnvironmentReference에 의해 전역 컨텍스트에 있는 lexicalEnvironment에 접근 가능

그럼 스코프 체인은 무엇이냐 

이너에서 어떤 변수에 접근하려고 했는데 없다 -> 이너의 outEnvironmentReference를 타고 out의 LexicalEnvironment의 environmentRecord에서 찾는다 -> 여기서도 없다 그러면 또 outerEnvironmentReference를 타고 전역 LexicalEnvironment에 가서 찾는다

자기 자신과 가까운 곳에서부터 찾아가는 것


- ThisBinding


Execution Context

- Variable Environment
- Lexical Environment
  - environmentRecord : 현재 실행 중인 콘텍스트의 식별자를 수집한다. 이것이 호이스팅이라는 용어로 통용되고 있다.
  - outerEnvironmentReference : 현재 실행 중인 콘텍스트의 외부의 식별자 정보를 가져온다. 이것이 스코프 체인을 구성한다.

