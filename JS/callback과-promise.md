# Promise와 Callback

## 질문

1. Promise와 callback의 차이점을 설명해주세요.
2. 콜백 지옥을 해결하는 방법을 말씀해주세요.
3. async, await 사용 방법을 설명해주세요.
4. Promise를 사용한 비동기 통신과 async, await를 사용한 비동기통신의 차이를 설명해주세요.

### 1. Promise와 callback의 차이점을 설명해주세요.

callback을 사용하면 결과값을 처리하기 위해서는 콜백함수 안에서만 처리할 수 있기 때문에 계속 콜백함수의 깊이가 깊어진다는 단점이 있습니다. 하지만 Promise를 사용하면 비동기처리의 결과값을 프로미스 바깥에서 `then()`으로 받아서 처리할 수 있기 때문에 가독성이 좋고 편리하다는 장점이 있습니다.

### 2. 콜백 지옥을 해결하는 방법을 말씀해주세요.

- Promise나 async/await를 사용하면 됩니다.
- Promise를 사용하면 콜백의 결과를 바깥에서 `.then()`으로 이을 수 있기 때문에 가독성이 좋아지고, async/await를 사용하면 마치 동기함수처럼 비동기함수의 처리를 기다려주고 결과를 반환하기 때문에 콜백함수를 작성할 필요가 없습니다.

### 3. async, await 사용 방법을 설명해주세요.

- 비동기처리를 하는 함수 앞에 await를 붙이면 마치 동기함수처럼 그 함수의 처리를 기다려줍니다.
- await는 async 선언을 한 함수 안에서만 사용할 수 있으므로 await를 둘러싼 함수에게도 앞에 async를 붙여줍니다.
- 만약 전역스코프에서 await를 사용하려고 한다면 즉시실행 함수의 형태로 async 함수로 둘러싸야 사용할 수 있습니다.
  ```js
  (async () => {
    ... 코드1
    await promise();
    ... 코드2
  })();
  ```

### Promise를 사용한 비동기 통신과 async, await를 사용한 비동기통신의 차이를 설명해주세요.

- Promise와 async/await의 차이점은 첫번째로 에러 핸들링에 있습니다. Promise는 `.catch()` 메소드로 에러처리를 할 수 있지만 async/await는 에러처리를 할 수 있는 기능이 없어서 try~catch문을 사용해야 합니다.
- 두 번째는 코드 가독성입니다. Promise도 콜백함수보다는 가독성이 낫지만 그 이후에 해야 할 일이 계속 이어지면 then이 계속 늘어설 수 있습니다. 하지만 async/await는 동기 함수처럼 코드를 작성할 수 있기 때문에 가독성이 좀 더 좋습니다.

---

## Callback 함수란?

- 비동기처리방식은 순차적으로 처리되지 않아서 예상치 못한 결과가 발생할 수 있다는 단점이 있는데, 콜백함수는 그것을 보완하기 위한 방법이다.
- 비동기 처리를 하는 함수에게 그 함수가 끝난 뒤 실행해야 하는 작업을 함수로 넘기는데 넘기는 그 함수를 콜백함수라고 한다. 비동기처리를 하는 함수는 작업이 끝난 다음 내부에서 콜백함수를 호출한다.

## 콜백 지옥 (Callback hell)과 콜백 지옥을 해결하는 방법

콜백 함수 안에 다음에 실행할 콜백함수를 중첩해서 작성하는 것을 콜백 지옥이라고 한다.
이러면 가독성이 매우 떨어진다.
이것을 해결하기 위해

1. 중첩된 구조를 따로 함수로 분리해서 서로를 호출하도록 하거나 (근데 별로 추천 X)
2. Promise나 async/await를 사용한다.

## Promise 란?

Promise는 미래에 어떤 값을 반환하겠다는 약속을 가지는 객체이다. 대기 상태에서는 안의 작업을 처리하고, 완료가 되면 `.then()`이나 `.catch()`에 결과값을 넘겨서 그 다음 할 일을 처리할 수 있게 한다.

### Promise를 반환하는 함수 작성하는 법

1. Promise를 반환하는 함수는 1번처럼 유명함수로 작성해도 되고, 2번처럼 변수에 익명함수를 할당하는 식으로 작성해도 된다.
2. `new Promise()`를 생성하고, Promise의 인자로 resolve와 reject를 인자로 갖는 함수를 작성한다. resolve와 rejeect는 js 자체에서 제공하는 콜백 함수로, 성공 시에는 resolve를 에러를 던질때는 reject를, 적어도 하나는 반드시 호출해야 한다.
3. 정상적으로 처리가 되었을 때는 `resolve(반환할 값)`처럼 resolve를 호출해서 결과를 반환하고, 에러를 던저야 하는 상황이면 `reject(에러객체)`를 호출해 에러를 반환한다.
4. promise 함수를 호출하면 `.then()`을 통해서 resolve로 반환한 값을 참조하는 콜백함수를 작성할 수 있고, `.catch()`로는 에러처리를 할 수 있다. `.finally()`는 성공, 에러에 상관 없이 반드시 처리해야 하는 일을 이 안에 작성한다.

1번

```js
function getData() {
  return new Promise(function (resolve, reject) {
    // 작업을 처리해서 data를 받아옴
    resolve(data);
  });
}
```

2번

```js
let getData = function () {
  return new Promise(function (resolve, reject) {
    setTimeout(() => resolve('완료'), 1000);
  });
};
```

### promise 객체의 상태(state)와 result

`new Promise()`가 반환하는 promise 객체는 `state`와 `result` 프로퍼티를 갖는다.

state는 세 가지 상태를 갖는데,

- 처음에는 `pending (보류)` 였다가
- `resolve`가 호출되면 `fulfilled`,
- `reject`가 호출되면 `rejected`로 바뀐다.

result도

- 처음에는 `undefined` 였다가
- `resolve`가 호출되면 promise의 반환값인 `value`,
- `reject`가 호출되면 `error`로 바뀐다.

## async, await

- 함수 앞에 async를 붙이면 따로 Promise를 반환하지 않아도 Promise를 반환하는 함수로 만들어준다.
- 그리고 비동기처리를 하는 함수 앞에 await를 붙여주면 마치 동기함수처럼 그 작업의 처리를 기다려주고 결과값을 반환한다.
- await은 async 함수 안에서만 사용할 수 있다.
- then이나 catch로 에러처리를 할 수 없는 대신 try catch를 이용해 에러처리를 한다.

## Reference

- 모던 JavaScript 튜토리얼 - 프라미스와 async, await | https://ko.javascript.info/async
- 캡틴판교 - 자바스크립트 Promise 쉽게 이해하기 | https://joshua1988.github.io/web-development/javascript/promise-for-beginners/
- 동기방식 vs 비동기방식, 콜백함수와 Promise 까지 한번에 훑어보기! | https://mesonia.tistory.com/139
- 벨로퍼트와 함께하는 모던 자바스크립트 > 3장. 자바스크립트에서 비동기 처리 다루기 > 01. Promise | https://learnjs.vlpt.us/async/01-promise.html (Promise 함수 작성하는 법이 기술되어 있음)
- Promise와 async/await 차이점 | https://velog.io/@pilyeooong/Promise%EC%99%80-asyncawait-%EC%B0%A8%EC%9D%B4%EC%A0%90
