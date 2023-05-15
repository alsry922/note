# ✔️단축 평가

쉽게 이야기하면 앞에만 보고도 판단할 수 있으면 굳이 뒤까지 보지 않겠다는 의미이다.

이 개념은 JavaScript에만 존재하는 것은 아니다.

용어가 익숙하지 않아도 예시만 보면 경험을 통해서 다들 이해하는 것이다.

```javascript
true || false // -> true
true || true // -> true
false || false // -> false
```

OR 연산은 둘 중 하나만 true가 되면 true 평가된다.

즉 앞에 내용이 true면 뒷 내용은 볼 필요도 없이 true로 단정지으면 된다.

실제로 앞이 true면 뒷 내용은 보지도 않고 true로 결론내린다.

```javaScript
true && true // -> true
true && false // -> false
false && false // -> false
```

AND 연산은 둘 다 true가 되어야 true로 평가된다.

즉 앞에 내용이 false면 뒷 내용은 볼 필요도 없이 false로 단정지으면 된다.

실제로 앞 내용이 false면 뒷 내용은 보지도 않고 false로 결론내린다.

## 📌단축 평가를 이용하여 if문을 대체

논리곱(&&) 또는 논리합(||) 연산자 표현식의 평가 결과는 항상 boolean이 아닐 수 있다.

JavaScript는 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환한다. 

그래서 두 논리 연산자의 표현식은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다.

(무슨 소리인지 이해 안가도 괜찮다. 뒤에 설명할 것이다.)

### 👉논리곱(&&)의 단축 평가

```javascript
let done = true;
let message = '';

if (done) message = '완료';

message = done && '완료';

console.log(message); // -> 완료
```

보기에는 좀 이상하지만 가능하다.

위 if문은 살펴보면 명료하다. done이 true로 평가된다면 message에 '완료'를 할당하겠다는 의미이다.

그 밑에 문장은 조금 이상한데 대입 연산자 뒤부터 살펴보자

done은 ture이다. AND 연산자는 둘 다 true여야 true로 평가되기 때문에 뒷 내용도 봐야한다.

즉 논리 연산의 결과를 결정하는 것은 뒷 내용(두 번째 피연산자)이 된다.

그래서 AND 연산자는 뒷 내용(두 번째 피연산자)을 그대로 반환한다.

그래서 message에 '완료'가 할당되는 것이다.

만약 여기서 done이 false였다면 message가 false였을 것이다.

이미 done이 논리 연산의 결과를 결정지었기 때문이다.

### 👉논리합(||)의 단축 평가

```javascript
let done = false;
let message = '';

if (!done) message = '미완료';

message = done || '미완료';

console.log(message); // -> 완료
```

여기서 done은 false다. OR 연산자는 둘 중 하나만 true면 true로 평가되기 때문에 뒷 내용도 봐야한다.

즉 논리 연산의 결과를 결정하는 것의 뒷 내용(두 번째 피연산자)이 된다.

그래서 OR 연산자는 뒷 내용을 그대로 반환하고, message에는 '미완료'가 할단되는 것이다.

# ✔️단축 평가 정리

JavaScript에서 단축 평가는

단축 평가를 통해서 평가 결과가 확정된 경우 나머지 평가 과정을 생략하고 

평가 결과를 결정지은 피연산자를 boolean 값으로 변환하지 않고 그대로 변환하는 것을 의미한다.

```javascript
'Cat' || 'Dog' // 'Cat'
false || 'Dog' // 'Dog'
'Cat' || false // 'Cat'

'Cat' && 'Dog' // 'Dog'
false && 'Dog' // false
'Cat' && false // false
```

오타 혹은 틀린 내용 피드백 해주시면 빠르게 반영하겠습니다 감사합니다.