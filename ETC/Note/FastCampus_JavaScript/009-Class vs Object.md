# 클래스와 오브젝트

> 드림코딩 강의로 선회하여 강의 노트를 정리

**클래스란**

> 조금 더 연관있는 데이터를 한 곳에 묶어 놓은 컨테이너

```js
class Person {
  name; // name과 age라는 프로퍼티가 있다. (속성/field)
  age;
  speak(); // 말하는 function이 존재한다. (행동/method)
 }
```

클래스 안에 메서드가 없고, 데이터만 존재할 때가 있는데 이를 가리켜 데이터 클래스라고 한다.

**캡슐화**<br>

캡슐화를 통해 내부적으로 보여지는 변수와 외부에서 볼 수 있는 변수를 나누어서 관리하는 것을 캡슐화라고 부른다.

**상속과 다양성**

클래스를 이용해서 특정 객체가 다른 객체로부터 기능을 이어받을 수 있다. 자바스크립트의 상속은 **프로토타입 체인**이라고 부르는 객체의 자료 구조로 구현되어 있으며 프로토타입 **상속**이라고 부른다.

자바스크립트는 프로토타입 상속에 기반을 둔 객체 지향 언어라고 볼 수도 있는데, 객체지향 언어로 프로그래밍을 잘하는 것은 풀어야 하는 문제, 구현해야 하는 기능들을 객체로 잘 정의할 수 있는 것이다. **주변의 모든 물건을 보면서 클래스로 정의하는 연습을 해 보자.**

## 클래스와 오브젝트의 차이

**Class (붕어빵 틀)**

- template
- declare once
- no data

**Object (붕어빵)**

- instance of a class
- created many times
- data in

즉,

> Class : template<br>
> Object : instance of a class

JavaScript classes

- introduced in **ES6**
- syntactical sugar over **prototype-based** inheritance

---

**Class declarations**

```js
class Person {
  // constructor
  constructor(name, age) {
    // fields
    this.name = name;
    this.age = age;
  }
  // methods
  speak() {
    console.log(`${this.name}: hello!`);
  }
}

const hyun = new Person("hyun", 27);
console.log(hyun.name);
console.log(hyun.age);
hyun.speak(); // 'hyun' // 27 // hyun: hello!
```

**Getter and setters**

```js
class User {
  constructor(firstName, lastName, age) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
  }
  get age() {
    return this._age;
  }
  set age(value) {
    this._age = value < 0 ? 0 : value;
  }
}

const user1 = new User("Steve", "Job", -1);
console.log(user1.age); // 0
```

**상속과 다양성**

```js
class Shape {
  constructor(width, height, color) {
    this.width = width;
    this.height = height;
    this.color = color;
  }

  draw() {
    console.log(`drawing ${this.color} color of!`);
  }

  getArea() {
    return this.width * this.height;
  }
}

class Rectangle extends Shape {
  // extends 키워드를 통한 상속
}
class Triangle extends Shape {
  // 원하는 함수만을 가져와서 사용하는 것 (오버라이딩 / 이는 클래스의 다양성)
  draw() {
    super.draw(); // super 키워드를 사용하면 모두 호출할 수 있다.
    console.log("🔺"); // draw 함수를 오버라이딩하면 Shape에 정의된 함수는 호출되지 않는다.
  }
  getArea() {
    return (this.width * this.height) / 2; // 삼각형이기 때문에, 원하는 함수만(오버라이딩) 가져와서 2로 나누었다.
  }
}
const rectangle = new Rectangle(20, 20, "blue");
rectangle.draw(); // drawing blue color of!
console.log(rectangle.getArea()); // 400
const triangle = new Triangle(20, 20, "red"); // drawing red color of!
console.log(triangle.getArea()); // 200
```

**클래스 확인 : instanceOf**

```js
console.log(rectangle instanceof Rectangle); // true
console.log(triangle instanceof Rectangle); // false
console.log(triangle instanceof Triangle); // true
console.log(triangle instanceof Shape); // true
console.log(triangle instanceof Object); // true
```
