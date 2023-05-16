# ✔️객체

자바스크립트에서는 원시 값을 제외한 거의 모든 것이 객체다.

자바스크립트에서 객체는 0개 이상의 프로퍼티의 집합이며, 프로퍼티는 key와 value로 구성되어 있다.

```javascript
const person = {
	name: 'mingyo',
	age: 'secret',
};
```

자바스크립트에서 사용하는 모든 값이 프로퍼티의 value가 될 수 있다.

자바스크립트에서 함수 또한 객체(일급 객체)기 때문에 value로 사용할 수 있다.

함수가 프로퍼티 값으로 사용됐을 때 이 함수를 메서드라고 부른다.

결론적으로 객체는 0개 이상의 프로퍼티 집합이고, 프로퍼티의 값으로 함수도 사용할 수 있기 때문에

객체는 프로퍼티와 메서드의 집합으로 집합체, 이루어진 복합적인 자료구조라고 할 수 있다.

## 📌객체 생성

자바스크립트는 프로토타입 기반 객체지향 언어로서 클래스 기반 객체지향 언어와는 달리 다양한 객체 생성 방법을 지원한다.

- 객체 리터럴
- Object 생성자 함수
- 생성자 함수
- Object.create 메서드
- 클래스(ES6)

```javascript
// 객체 리터럴 방식
const person = {
	name: 'mingyo',
	sayHello: function () {
		console.log(`Hello! My name is ${this.name}.`);
	}
};

console.log(typeof person); // object
console.log(person); // {name: 'mingyo', sayHello: f}
```

중괄호 내에 0개 이상의 프로퍼티를 정의하여 객체를 생성한다. 중괄호는 블록을 의미하지 않는다.

변수에 할당되는 시점에 자바스크립트 엔진이 객체 리터럴을 해석해 객체를 생성한다.

## 📌프로퍼티

프로퍼티는 key와 value로 구성되어 있다고 했다.

JavaScript에서 거의 모든 값은 value로 사용될 수 있지만 key는 그렇지 않다.

key로 사용할 수 있는 값을 String 혹은 Symbol 값이다.

문자열 혹은 심볼 값 이외의 값을 key로 사용하면 암묵적 타입 변환을 통해 문자열로 변환된다.

생성한 객체에 프로퍼티를 동적으로 추가할 수 있다.

```javascript
let obj = {};
let key = 'hello';

obj[key] = 'world';
obj.hi = 'hi';

console.log(obj); //{hello: 'world', hi: 'hi'}
```

이미 존재하는 프로퍼티 키를 중복 선언하게 되면 존재하던 프로퍼티 키에 해당하는 값을 덮어쓴다.

```javascript
const obj = {
	name 'Jeong',
	name: 'Mingyo',
}
```

delete 연산자를 사용하면 프로퍼티를 삭제할 수 있다.

```javascript
const obj = {
	name: 'Mingyo',
	age: 'secret',
}
delete obj.age;
console.log(obj); // {name: 'Mingyo'}
```

## 📌메서드

앞에서도 이야기한 것처럼 함수도 객체(일급 객체)다.

따라서 프로퍼티 value로 쓸 수 있다. 그리고 얘를 일반 함수와 구분하기 위해 메서드라고 부른다.

메서드는 객체에 묶여있는 함수라고 생각하면 된다.

```javascript
const circle = {
	radius: 5,
	getDiameter: function () {
		return 2 * this.radius;
	}
};

console.log(circle.getDiameter()); // 10
```


## 📌프로퍼티 접근

프로퍼티 접근 방법은 두 가지다.

- 마침표 프로퍼티 접근 연산자
- 대괄호 프로퍼티 접근 연산자

```javascript
const person {
	name: 'Mingyo'
	1: 10
};

console.log(person.name); // Mingyo
console.log(person['name']); // Mingyo
console.log(person[1]); // 10 : person[1] -> person['1']
console.log(person['1']); // 10
```

대괄호 프로퍼티 접근 연산자를 사용하는 경우 연산자 내부에 키를 문자열로 적어줘야 한다.

위에서 이야기 했듯이 프로퍼티 키는 문자열 혹은 심볼 값만 가능하다.

숫자를 키로 하면 암묵적 타입 변환으로 인해 문자열 1로 변환된다.

대괄호 프로퍼티 접근 연산자를 사용할 때 숫자 key라면 문자열로 쓰지 않아도 접근이 가능하다.

