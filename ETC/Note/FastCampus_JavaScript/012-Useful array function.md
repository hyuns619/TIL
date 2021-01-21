# 유용한 배열 메서드

> 드림코딩 강의로 선회하여 강의 노트를 정리

## 1. make a string out of an array

> **join**

- 배열을 String으로 변환해준다.

```js
{
  const fruits = ["apple", "banana", "orange"];
  const result = fruits.join("|");
  console.log(result); // apple|banana|orange
}
// join의 APIs를 확인하면 separator?처럼 물음표가 있는데 이건 전달해도 되고, 전달하지 않아도 된다는 뜻.
// 인수로 구분자를 받기도 함.
```

## 2. make an array out of a string

> **split**

- String을 배열로 변환해준다.

```js
{
  const fruits = "🍎, 🥝, 🍌, 🍒";
  const result = fruits.split(",");
  console.log(result); // ["🍎", " 🥝", " 🍌", " 🍒"]
}
// 인수로 구분자와 옵션인 limit을 전달 받는다.
// 구분자는 꼭 전달해서 사용해야 한다.
```

## 3. make this array look like this: [5, 4, 3, 2, 1]

> **reverse**

- 배열 안에 들어있는 요소의 순서를 거꾸로 만들어준다.

```js
{
  const array = [1, 2, 3, 4, 5];
  const result = array.reverse();
  console.log(result); // [ 5, 4, 3, 2, 1 ]
  console.log(array); // [ 5, 4, 3, 2, 1 ]
  // reverse는 배열 자체를 변화시키고, 변화된 배열 자체를 리턴하는 걸 확인할 수 있다.
}
```

## 4. make new array without the first two elements

> **slice**

- 주어진 배열에서 첫 번째와 두 번째 요소를 제외한 새로운 배열을 만들어 준다.

```js
{
  //slice
  const array = [1, 2, 3, 4, 5];
  const result = array.slice(2, 5);
  console.log(result); // [3, 4, 5]
  console.log(array); // [1, 2, 3, 4, 5]

  //splice
  const array = [1, 2, 3, 4, 5];
  const result = array.splice(2, 5);
  console.log(result); // [3, 4, 5]
  console.log(array); // [1, 2]

  //slice -  기존의 배경되지 않음. 원하는 부분만 리턴해서 받아오고 싶을 때 사용.
  //splice - 배열 자체가 변경된다.
}
```

```js
class Student {
  constructor(name, age, enrolled, score) {
    this.name = name;
    this.age = age;
    this.enrolled = enrolled;
    this.score = score;
  }
}
const students = [
  new Student("A", 29, true, 45),
  new Student("B", 28, false, 80),
  new Student("C", 30, true, 90),
  new Student("D", 40, false, 66),
  new Student("E", 18, true, 88),
];
```

## 5. find a student with the score 90

> **find**

- true가 나오면 배열을 return한다.

```js
{
 const result = students.find((student) => student.score ===90);
 console.log(result);
  // Student {
  // name: 'C',
  //age: 30,
  //enrolled: true,
  //score: 90 }
}

  // 화살표 함수에서 한 문장이면 괄호가 생략이 가능하고, 리턴과 세미콜론이 생략 가능하다.

  // 배열에 있는 find라는 함수를 호출할 때, 콜백 함수(화살표 함수)를 전달해 주었고

  // 배열의 요소마다 호출이 되고 각 student를 받아 왔을 때, 학생의 점수가 90점이면 true

  // 아니면 false를 return한다. find는 ture가 나오면 배열을 리턴해주는 APIS.
}
```

- `find()` 내부에 불려지는 함수가 `콜백 함수`이고
- 이 콜백 함수는 배열의 있는 `요소`마다 `순차적`으로 실행이 된다.
- 첫 번째와 두 번째 요소에서는 조건이 충족이 안 되어서 콜백 함수가 안 불려지고
- 세 번째에서 충족되는 조건을 있으므로 콜백 함수가 불려진다.

## 6. make an array of enrolled students

> **filter**

- 단어 뜻 그대로 필터 역할을 한다.
- 콜백 함수를 전달하고 true인 값을 모아서 새로운 값을 전달해준다.
- filter를 이용하면 원하는 값만 받아올 수 있다.

수업에 등록된 학생들만(true) 찾아서

```js
{
  const result = students.filter((student) => student.enrolled);
  console.log(result); // student.enrolled가 true인 것들만 반환
}
```

## 7. make an array containing only the students' scores

> **map**

- 배열 안의 요소 하나하나를 다른 값으로 변경해준다.
  - 지정된 콜백 함수를 호출하면서 각각의 요소들을 `함수`를 거쳐서 `새로운 값`으로 변경한다.

```js
// result should be: [45, 80, 90, 66, 88]

{
  const result = students.map((student) => student.score);
  console.log(result); // [ 45, 80, 90, 66, 88 ]
}
```

- `map()`은 배열 안에 들어있는 모든 요소들을 전달해준 콜백 함수를 통해 호출하면서
- 콜백 함수에서 가공되어 return 되어진 값으로 대체한다.
- ex ) 점수를 2배로 변경하고자 하면
  - `const result = students.map((studnet) => student.score * 2);`
- 콜백 함수로 전달되는 인자는 최대한 이해하기 쉽게 기재해야 한다.
  - value가 아닌, student처럼!

## 8. check if there is a student with the score lower than 50

> **some**

- some 누군가에게 만족되는 조건이 있는지, 없는지를 확인한다.

학생들 중 점수가 50점보다 낮은 학생이 있는지. (true가 return)

```js
//some
{
  const result = students.some((student) => student.score < 50);
  console.log(result); // true
  //every
  const result2 = students.every((studnet) => students.score < 50);
  console.log(result2); // false
}
```

- 배열에서 하나라도 충족되는 요소가 있으면 true가 리턴이 된다.
- `some`은 배열의 요소 중에서 콜백 함수의 return이 true가 있는지 없는지를 확인한다.
- 반대로 `every`는 모든 요소가 조건에 충족이 되면 true가 리턴이 된다.

## 09. compute students' average score

> **reduce**

- 원하는 `시작점`부터 모든 배열을 돌면서, 어떤 값을 `누적`할 때 사용한다.
- 콜백 함수를 전달할 수 있고, 이니셜 value를 전달한다.
- 배열 안에 들어있는 모든 요소마다 호출이 되고
- 콜백 함수에서 리턴되는 값은 누적된 결과 값을 리턴한다.

```js
{
  const result = students.reduce((prev, curr) => prev + curr.score, 0);
  console.log(result / students.length); // 73.8
  // prev에는 이 전의 콜백 함수에서 리턴된 값이 전달되어 오고
  // curr에는 배열의 아이템을 순차적으로 전달 받는다.
  // initial 값, 0부터 시작
}
```

## 10. make a string containing all the scores

학생들의 모든 점수를 String으로

```js
// result should be: '45, 80, 90, 66, 88'
{
  const result = students.map((student) => student.score).join();
  console.log(result); // '45,80,90,66,88'

  // 학생들의 배열을 점수로 변환해야 한다. (map)
  // map을 이용하게 되면 새로운 배열이 리턴된다.
  // 리턴된 배열에 join을 사용하면 string으로 변경할 수 있다.
  // map은 새로운 배열 자체를 리턴한다.

  const result2 = students
    .map((student) => student.score)
    .filter((score) => score >= 50)
    .join();
  console.log(result2);
}
```

11 . sorted in ascending order

> **sort**

점수를 정렬하고 낮은 점수가 먼저 나오게 해서 String으로 변환

```js
// result should be: '45, 66, 80, 88, 90'
{
  const result = students
    .map((student) => student.score)
    .sort((a, b) => a - b)

    .join(); // 스트링으로 변환
  console.log(result);
}
```

- map을 이용해서 score로 맵핑
- sort를 이용해서 정렬하는데
- sort의 콜백 함수에는 a, b (이전 값과 현재 값)이 전달이 되며 만약 `-` 값을 리턴하게 되면 첫 번째가 뒤에 값보다 작다고 간주되어 정렬이 된다.
- 높은순부터 나오게 하고 싶으면 (b-a)로 변경하면 된다.
