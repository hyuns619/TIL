# 실행 콘텍스트(Execution Context)

실행 콘텍스트란 실행 가능한 코드를 형상화해서 구분하는 추상적인 개념이다.

실행 콘텍스트란 함수를 실행할 때 필요한 환경정보를 담은 객체를 얘기한다.

- 추상적인 개념과 해당 정보를 담고 있는 객체를 지칭할 때 모두 통용한다.

## Execution Context

- **VariableEnvironment**
  - environmentRecord
  - outerEnvironmentReference
- **LexicalEnvironment (어휘적/사전적 환경)**

  - environmentRecord (현재 콘텍스트의 식별자 정보, HOISTING)

    - 현재 문맥에 있는 식별자 정보르 수집해서 environmentRecord에 남기는데, 이런 정보 수집 과정을 HOISTING이라고 함.

  - outerEnvironmentReference

- ThisBinding
