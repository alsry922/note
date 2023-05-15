# ✔️Map

일반 객체 리터럴과 비슷함

보통 key-value 구조의 객체를 Map이라고 함.

JavaScript에서의 Map이 독특한 점은

객체를 key 사용할 수 있으며, 심지어 객체를 value로 사용할 수도 있다.

일반 객체 리터럴에서 우리가 사용할 때 key는 무조건 String 혹은 Symbol만 사용할 수 있었음.

#### 🌟객체를 key로 사용할 때의 주의점

```javascript
const m = new Map();

m.set('a', 'b');
m.set('c', 'd');
// 이러면 m 은 {'a' => 'b'}, {'c' => 'd'} 이렇게 나오겠지

// get 메서드로 key의 value를 가져올 수 있
m.get('a'); // 'b'
```

앞에서 객체를 key 와 value로 사용할 수 있다고 했음

```javascript
m.set({a: 'b'}, {c: 'd'});
//그럼 이제 m은
//{"a" => "b"}
//{"c" => "d"}
//{Object => Object}
// 요렇게 된다.
```

그럼 저 키에 해당하는 value를 어떻게 불러올까?

```javascript
m.get({a: 'b'});
```

이렇게 하면 될까? No!

m.set() 메서드에서 key로 사용한 객체와 m.get() 메서드에서 key로 사용한 객체와의 무슨 차이가 있을까?

바로 참조값이 다르다는 것이다.

모양은 똑같지만 서로 다른 객체인 것이다.

따라서 객체를 key로 사용하고 싶다면

```javascript
const d = {};

m.set(d, 'e');

m.get(d);
```

이렇게 객체를 미리 변수에 할당해 놓아야 한다.

## 📌주로 쓰는 프로퍼티와 메서드

```javascript
m.size; // 맵의 속성 갯수

for (const [k, v] of m) {
	console.log(k, v); // 반복문에 바로 넣어 사용이 가능
}

m.forEach((v, k) => {
	console.log(k, v); // 배열도 아닌데 forEach가 가
});

m.delete(key); // 해당 key-value 쌍 삭제
m.has(key); // 해당 키가 있는지 확인, 불리언 값 return
m.clear(); // 맵 비우
```

size로 속성 개수를 조회할 수 있다.

# ✔️Set

일반 배열 리터럴과 비슷함

하지만 set은 중복을 허용하지 않음

배열은 중복을 허용하기 때문에 기존 배열에서 중복을 제거하고 싶을 때 Set을 사용하기도 한다.

API는 Map과 비슷하지만 Map에서 set이 Set에서는 add인 점 정도가 다르다.

# ✔️WeakMap

Map가 다른 점은 없는데 garbage collecting이 잘 된다.

```javascript
let user = {name: 'mingyo', age: 29};
user.married = false; // 이렇게 user 객체에 부가적인 정보를 추가로 넣을 수 있음
```

그런데 만약 user 객체를 건들기는 싫고 저런 부가적인 정보를 갖고는 싶어!

그러면 여러 방법이 있는데 간단하게는

```javascript
const userObj = {
	user,
	married: false,
}
```

이렇게 새로운 객체를 만들어서 user 객체는 건드리지 않고, married라는 부수적인 정보를 추가로 갖게 할 수 있음.

근데 이걸 WeakMap을 사용하면 가비지 컬렉팅을 쉽게할 수 있다.

```javascript
const wm = new WeakMap();
wm.set(user, {married: false});
user = null;
```

이런식으로도 가능하다. user 객체를 건들지 않으면서(수정하지 않으면) married라는 부가적인 정보를 추가로 갖게 되었으며,

나중에 user를 null로 할당해서 가비지 컬렉팅이 되었으면, value인 {married: false}도 가비지 컬렉팅 되어 메모리에서 제거된다.

그니까 이 둘은 하나로 묶여있어서 하나가 날라가면 나머지 하나도 날라가게 되는 것이다.