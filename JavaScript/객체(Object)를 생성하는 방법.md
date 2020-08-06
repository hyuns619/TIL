# 객체(Object)

자바스크립트의 객체는 이름(key)과 값(value)을 하나로 묶은 집합이다. 이러한 집합 하나 하나를 프로퍼티(property)라고 부른다. 값으로는 원시 타입(primitive)과 객체(object) 타입(배열, 함수, 정규식 등) 데이터 모두가 할당될 수 있다. 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해서 이를 메소드(method)라고 부른다. 즉, 메소드는 객체에 제한되어 있는 함수를 의미한다.
 
## 객체 리터럴(Literal)로 생성하기

객체 리터럴은 가장 기본적인 객체 생성 방식이다. 중괄호 (`{}`)를 사용하여 객체를 생성하며 {} 안에 `이름`과 `값`으로 이루어진 프로퍼티를 기술하면 해당 프로퍼티가 생성된다.

```javascript
let person = {
	name: 'jeon',
	gender: 'female',
};

let propertyName = 'name';

console.log(person); // {name: "jeon", gender: "female"}
console.log(person.name); // 마침표 (.) 연산자를 통해서 프로퍼티 값에 접근할 수 있으며
console.log(person[propertyName]); // 변수에 대입된 객체 안의 값을 읽을 때, 대괄호 ([]) 연산자를 통해서 프로퍼티 값에 접근할 수 있다.
```

객체를 정의하면 프로퍼티 값을 `추가`할 수 있으며 `수정`과 `제거`가 가능하다. <br> 객체 리터럴 안에 어떠한 프로퍼티도 작성하지 않으면 `빈 객체`를 생성할 수도 있다.

```javascript
// 빈 객체 생성
let person = {};
console.log(person); // {}
console.log(typeof person); // object

// 프로퍼티 추가
person.name = 'jeon';
console.log(person); // {name: "jeon"}

// 프로퍼티 수정
person.name = 'kim';
console.log(person); // {name: "kim"}

// 프로퍼티 제거
delete person.name;
console.log(person); // true
```
## 