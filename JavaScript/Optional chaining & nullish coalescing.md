# ✔️옵셔널 체이닝과 널 병합 연산자

이전 포스팅에서는 단축 평가(short-circuit evaluation)에 대해서 살펴보았다.

단축 평가를 이용해 논리 연산의 결과를 결정 짓는 피연산자를 그대로 반환하는 특징을 이용해 if 문을 대체하거나 혹은 객체가 null 혹은 undefined인 경우에 발생할 수 있는 널 참조 에러를 막기도 하였다.

## 📌옵셔널 체이닝(?.)

옵셔널 체이닝 연산자는 ES11(ECMAScript2020)에서 도입되었다.

옵셔널 체이닝 연산자를 통해 참조하려는 객체가 null인지 혹은 undefined인지 확인할 수 있다.

만약 참조하려는 객체가 null 또는 undefined라면 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.

```javascript
let elem = null;

let value = elem?.value;
console.log(value); // undefined
```

## 📌널 병합 연산자(??)

널 병합 연산자 또한 ES11(ECMAScript2020)에서 도입되었다.

널 병합 연산자는 좌항의 피연산자가 null 또는 undefined라면 우항의 연산자를 반환하고, 그렇지 않은 경우에는 좌항의 피연산자를 반환한다.

```javascript
const foo = null ?? 'default string';
console.log(foo); // default string
```

# 🔚

그 동안 참조하려는 값이 null 혹은 undefined인지 판단하는 경우에 단축 평가를 많이 사용했는데

falsy값 중 빈 문자열('')과 숫자은 객체로 평가될 때도 있다고 한다. 따라서 의도치 않은 결과가 나올때도 있다고 하니

명시적으로 이해하기 쉬운 널 병합 연산자나 옵셔널 체이닝을 적극 활용해보자.