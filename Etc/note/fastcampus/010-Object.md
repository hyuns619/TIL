# Object 객체

> 드림코딩 강의로 선회하여 강의 노트를 정리

- 자바스크립트의 데이터 타입 중 하나이다.
- 오브젝트는 key와 value로 구성된다.
- 관련 데이터 또는 기능을 묶어 놓은 모음.
- 자바스크립트에 있는 거의 모든 객체는 Object의 인스턴트이다.

## 객체를 생성 방법

**1. Object literal syntax**

```js
const hyun = { name: "hyun", age: 27 };
console.log(hyun.name, hyun.age); // hyun, 27

hyun.hasJob = true;
console.log(hyun); // { name: 'hyun', age: 27, hasJob: true }
```

자바스크립트는 **동적으로 타입**이 런타임 때 결정되는 언어이므로 위와 같이 뒤늦게 하나의 프로퍼티를 추가할 수 있다. 하지만, 유지 보수가 힘들기 때문에 이런 행위는 지양하자.

**2. Object constructor syntax**

```js
const obj2 = new Object();
```

### 계산된 프로퍼티

```js
// dot - 보통의 경우
console.log(hyun.name);
// computed - 실시간으로 원하는 키의 값을 받아 오고 싶을 때
console.log(hyun["name"]);
hyun["hasJob"] = true;
```

### 단축 프로퍼티

```js
function makeUser(name, age) {
  return {
    name, // name: name 과 같음
    age, // age: age 와 같음
    // ...
  };
}
```

이름과 값이 변수의 이름과 같을 때, `name:name` 대신 `name`만 적어주어도 프로퍼티를 설정할 수 있다.

```js
let user = {
  name, // name: name 과 같음
  age: 30,
};
```

한 객체에서 일반 프로퍼티와 단축 프로퍼티를 함께 사용할 수도 있다.

## 생성자 함수

> 객체 리터럴로 객체를 생성하면 동일한 키와 값을 반복해서 작성해야 하는 불편함이 있다. 하지만, **생성자**를 사용하면 이름이 같은 메서드와 프로퍼티를 가진 객체 여러 개를 효율적으로 생성할 수 있다.

```js
const person = new Person("hyun", 27);

function Person(name, age) {
  // 생성자 함수의 이름은 대문자로 기입해야 한다.
  // 생성자 함수 문법을 사용하면 자바스크립트 엔진이 오브젝트를 생성해준다.
  // this = {};
  // 1. 새로운 오브젝트를 만들어서, this에다가 name과 age라는 새로운 프로퍼티를 넣고
  this.name = name;
  this.age = age;
  // return this;
  // 결국은 this를 리턴하는 함수이다.
}

console.log(person); // Person {name:'hyun', age:27}
```

생성자 함수는 결국 클래스와 같은 붕어빵 틀 역할을 하는 템플릿이다. `person`은 생성자 함수가 찍어내는 붕어빵, 즉 객체이다.

### in 연산자

in 연산자를 통해 해당하는 옵젝트 안에 키가 존재하는지 확인할 수 있다.

```js
let user = { name: "John", age: 30 };
console.log("name" in user); // true
console.log("none" in user); // false
```

### for in / for of

**for i**

```js
const hyun = { name: "hyun", age: 27, hasJob: true };

for (key in hyun) {
  console.log(key);
}
// name
// age
// hasJob
```

모든 key를 받아와서 처리하고 싶을 때 사용할 수 있음.

**for of**

데이터를 순서대로 나열할 때 사용할 수 있다.

```js
const array = [1, 2, 3, 4, 5];
// 기존의 for문
// for(let i = 0; i < array.length; i++){
//     console.log(array[i])
// }
for (value of array) {
  console.log(value);
}
// 결과는 동일하다.
// 1
// 2
// 3
// 4
// 5
```

### 객체 복사 비교

```js
const user = { name: "hyun", age: 20 };
const user2 = user;
user2.name = "coder";
console.log(user); // {name:corder, age:20}
```

[여기](<https://github.com/sunghyunjeonme/TIL/blob/master/JavaScript/%EC%BD%94%EC%96%B4%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8(%EB%8D%B0%EC%9D%B4%ED%84%B0%20%ED%83%80%EC%9E%85).md#%EB%B6%88%EB%B3%80-%EA%B0%9D%EC%B2%B4>)의 내용처럼 객체는 변경 불가능한 값이 아니므로 객체 user2는 변경된다. 그런데 변경하지 않은 객체 user1 또한 동시에 변경된다. user1과 user2는 같은 주소를 참조하고 있기 때문인데, 객체를 불변 객체로 만들어서 프로퍼티의 변경을 방지할 수 있다.

**Object.assign**

```js
const fruit1 = { color: "red" };
const fruit2 = { color: "blue", size: "big" };
const mixed = Object.assign({}, fruit1, fruit2);
console.log(mixed.color);
console.log(mixed.size); // blue // big
```
