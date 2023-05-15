# ✔️Promise

프로미스: 내용이 실행은 되었지만 결과를 아직 반환하지 않은 객체

프로미스를 생성할 때 전달 인자로 전달하는 함수는 동기로 실행됨.

```javascript
const condition = true'
const promise = new Promise((resolve, reject) => {
	// 여기부터
	if (condition) {
		resolve('성공');
	} else {
		reject('실패');
	}
	//여까지는 동기로 실행 되는거임
})
```

프로미스에서 뭔가를 수행하고 그게 성공했으면 resolve를 호출, 실패했으면 reject를 호출

그럼 이제 수행 결과를 promise 변수에 가지고 있다가

promise 변수에 .then이나 .catch를 붙여서 수행 결과 값을 사용할 수 있음.

```javascript
//위 코드랑 이어지는 거임
// 밑에 코드를 쓰기 전 이 부분에 다른 코드를 실행할 수 있

promise
	.then((message) => {
		console.log(message); // 성공(resolve)한 경우 실행
	})
	.catch((error) => {
		console.log(error); // 실패(reject)한 경우 실
	})
```

Promise.resolve(성공리턴값): 바로 resolve하는 프로미스
Promise.reject(실패리턴값): 바로 reject하는 프로미스

```javascript
const promise1 = Promise.resolve('성공1');
const promise2 = Promise.resolve('성공2');
Promise.all([promise1, promise2])
	.then((result) => {
		console.log(result); //['성공1', '성공2']
	})
	.catch((error) => {
		console.error(error);
	});
```

Promise.all(배열): 여러 개의 프로미스를 동시에 실행
- 하나라도 실패하면 catch로 감
- 요즘엔 allSettled를 사용하고, 얘를 통해서 실패한 것만 추려낼 수 있음

프로미스로 사용하면 .then .then .then 이렇게 되기도 하는데 이것도 보기 싫음

## 📌async/await

async function을 도입해서 async/await을 사용해서 저 부분을 줄일 수 있음

변수 = await 프로미스; 인 경우 프로미스가 resolve된 값이 변수에 저

```javascript
async function findAndSaveUser(Users) {
	let user = await Users.findOne({});
	user.name = 'zero';
	user = await user.save();
	user = await Users.findOne({ gender: 'm'});
}
```

await이 then의 역할을 한다고 보면 됨.

await의 오른쪽에 있는 게 프로미스임

옛날에는 그냥 

```javascript
const result = await promise;
```

이렇게 쓰는게 안됐음. await은 항상 async function안에 존재하여야 했으며, async function을 따로 만들어서 이 함수를 실행해줘야 했음

근데 요즘은 탑레벨 await이 나와서 위 코드를 실행할 수 있음.

```javascript
const promise = new Promise();

async function main() {
	const result = await promise;
	return result;
}

main().then((name) => ....)
//혹은
const name = await main();
```

async 함수의 return값은 항상 then으로 받아야 함.

혹은 async도 프로미스기 때문에 await main() 으로 결과값을 받을 수도 있음.

단, async/await 을 쓸 때 주의할 점이 Promise가 실패했을 때 catch할 수 있는 부분이 없음

따라서 try-catch 문으로 묶어서 에러 처리를 진행해야 함.

화살표 함수도 async/await이 가능하다.

### 👉async 함수는 항상 Promise를 반환한다.

async 함수는 항상 Promise를 반환하기 때문에 then 혹은 await을 붙일 수 있다.

```javascript
async function findAndSaveUser(Users) {
	// 대충 코드~
}

findAndSaveUser().then(() => {
	//대충 코드
}); // 이렇게도 가능하고
//또는
async function other() {
	const result = await findAndSaveUser();
}
```

### 👉프로미스들의 배열을 가지고 반복문을 돌리는 for await 문법

```javascript
for await(변수 of 프로미스배열)
```

이런 식으로 프로미스들을 반복문을 돌릴 수 있음.

await이 then이니까, resolve된 프로미스가 변수에 담겨 나온다.

쉽게 각 요소들에 then이 붙어서 나온다고 생각하면 됨.

앞에서도 말했듯이 await은 async 함수 안에 존재할 수 있기 때문에 async 함수 안에서 for await을 사용할 수 있음.

```javascript
const promise1 = Promise.resolve('성공1');
const promise2 = Promise.resolve('성공2');
(async () => {
	for await (promise of [promise1, promise2]) }
		console.log(promise); // 여기 promise 변수에 resolve된 결과값이 들어있음.
})();
```