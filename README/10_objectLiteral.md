# 객체 리터럴
- 원시 타입은 단 하나의 값만 나타내지만 객체 타입은 다양한 타입의 값을 하나의 단위로 구성한 복합적인 자료구조다.
- 원시타입의 값은 변경이 불가능하지만 객체 타입의 값, 즉 객체는 변경 가능한 값이다.
- 객체는 0개이상의 프로퍼티로 구성된 집합이며, 프로퍼티는 키 와 값으로 구성된다.
- 자바스크립트에서 사용할 수 있는 모든 값은 프로퍼티 값이 될 수 있다.
- 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 메서드라 부른다.

```javascript
var counter = {
  num : 0, // 프로퍼티
  increase : function(){ // 메서드
    this.num++
  }
}
```
- 프로퍼티 : 객체의 상태를 나타내는 값
- 메서드 : 프로퍼티를 참조하고 조작할 수 있는 동작

## 객체 리터럴에 의한 객체 생성
- 자바스크립트는 프로토타입 기반 객체지향 언어로서 클래스 기반 객체지향 언어와는 달리 다양한 객체 생성 방법을 지원한다
  - 객체 리터럴
  - Object 생성자 함수
  - 생성자 함수
  - Object.create 메서드
  - 클랜스(ES6)
- 대부분의 중괄호는 코드블록을 의미하지만 객체 리터럴의 중괄호는 코드 블록을 의미하지 않는다. 따라서 값으로 평가되기 때문에 중괄호 뒤에 세미콜론을 붙인다.

## 프로퍼티
- 객체는 프로퍼티의 집합이며, 프로퍼티는 키와 값으로 구성된다.
- 프로퍼티 키 : 빈 문자열을 포함하는 모든 문자열 또는 심벌 값
- 프로퍼티 값 : 자바스크립트에서 사용할 수 있는 모든 값
- 포로퍼티 키는 자바스크립트에서 사용 가능한 요효한 이름인 경우 따옴표를 생략할 수 있다.
- 즉, 식별자 네이밍 규칙을 따르지 않는 이름에는 반드시 따옴표를 사용해야한다.

```JAVASCRIPT
var person = {
  firstName : "song", // 식별자 네이밍 규칙을 준수하는 키
  last-name : 'Yu' // 식별자 네이밍 규칙을 준수하지 않는 키 에러
} 
```
- 자바스크립트 엔진에서 -을 연산자로 해석하기 때문에 위코드가 오류가 나는 것이다.

- 문자열 또는 문자열로 평가할 수 있는 표현식을 사용해 프로퍼티 키를 동적으로 생성할 수도 있다. 이 경우 프로퍼티 키로 사용할 표현식을 대괄호[...]로 묶어야한다.

```javascript
var obj = {}
var key = 'hello'
var test = "world"

obj.key = test
console.log(obj) // key : world

obj[key] = test
console.log(obj) // hello : world
```

- 프로퍼티 키는 문자열이나 심벌 값 외의 값을 사용하면 암묵적 타입 변환을 통해 문자열이 된다.

## 프로퍼티 접근
- 프로퍼티 접근하는 방법은 두 가지가 있다.
  - 마침표 프로퍼티 접근 연산자(`.`)를 사용하는 마침표 표기법
  - 대괄호 프로퍼티 접근 연산자(`[...]`)를 사용하는 대괄호 표기법
- 프로퍼티 키가 식별자 네이밍 규칙을 준수하는 이름, 즉 자바스크립트에서 사용 가능한 유요한 이름이면 마침표 표기법과 대괄호 표기법을 모두 사용할 수 있다.
- 대괄호 표기법을 사용하는 경우 대괄포 프로퍼티 접근 연산자 내부에 지정하는 프로퍼티 키는 반드시 따옴표로 감싼 문자열이어야한다.
  - 따옴로 감싸지 않으면 자바스크립트 엔진은 식별자로 해석하기 때문이다.
- 객체에 존재하지 않는 프로퍼티에 접근하면 undefined를 반환한다. 오류가 발생하지 않는데 주의해야 한다.
```javascript
let person = {
  name : 'song'

console.log(person['name']) // song
console.log(person[name]) // ReferenceError 발생
console.log(person.name) // song
console.log(person.age) // undefined
}
```

## ES6에서 추가된 객체 리터럴의 확장 기능
- 프로퍼티 값으로 변수를 사용하는 경우 변수 이름과 프로퍼티 키가 동일한 이름일 때 프로퍼티 키를 생략할 수 있다. 
```javascript
var x = 1, y = 2

var obj = {
  x : x,
  y : y
}
// 위 코드와 아래 코드는 같은 내용을 출력한다.
var x = 1, y = 2
var obj = {x, y}

```

- 표현식을 사용해 프로퍼티 키를 동적으로 생성 할 수도 있다.
- 단, 프로퍼티 키로 사용할 표현식을 대괄호로 묶어야 한다.
- 이른 계산된 프로퍼티 이름이라 한다.

```javascript
var prefix = 'prop'
var i = 0
var obj = {}
obj[prefix + '-' + ++i] = i
obj[prefix + '-' + ++i] = i
obj[prefix + '-' + ++i] = i

console.log(obj)  // {prop-1 : 1, prop-2 : 2, prop-3 : 3}
```
