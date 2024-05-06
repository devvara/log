
# 프로미스 Promise

초기 자바스클비트는 비동기 작업을 수행할 수 있는 기본적인 도구를 제공했지만, 시간이 지남에 따라 이러한 기능들은 더욱 진화되었으며 ES6(2015)에 Promise가 공식적으로 도입되었고, 이후 ES2017에서 async/await 구문이 추가되어 비동기 코드의 작성이 더욱 간편하고 지관적이게 되었다.

## 싱글 스레드

자바스크립트는 싱글 스레드 환경에서 실행된다. 한 번에 하나의 작업만 처리할 수 있다. 모든 코드가 동기적으로 실행되면 하나의 긴 작업이 진행되는 동안 나머지 모든 작업들은 대기를 해야 한다. 이는 서버에 데이터를 요청하고 응답을 기다리는 동안 사용자는 아무런 상호작용을 할 수 없어 마치 동작이 멈춤 것처럼 보여진다.

자바스크립트는 비동기 작업을 통해 파일 읽기, 네트워크 요청 등 시간이 많이 걸리는 작업을 백그라운드에서 처리할 수 있게 하여 메인 스레드가 사용자 인터페이스를 방해하지 않고 계속해서 응답할 수 있게 해준다.

## Promise 기본 구조

Promise는 비동기 작업의 최종 성공과 실패 그리고 결과값을 나타내는 객체이다. 비동기 프로그래밍을 쉽게 깔금하게 처리할 수 있으며, 콜백 지옥(callback hell) 문제를 해결하는데 도움을 준다.

Promise의 상태
1. Pending(대기중): 비동기 처리 로직이 아직 완료되지 않은 상태
2. Fulfilled(이행됨): 비동기 처리가 성공적으로 완료되어 프로미스가 결과 값을 반환한 상태
3. Rejected(거부됨): 비동기 처리가 실패하거나 오류가 발생한 상태

````javascript
let promise = new Promise(function(resolve, reject) {
  // 비동기를 수행하는 코드

  if (/*코드가 성공적으로 수행된 경우*/) {
    resolve(value) // resolve를 호출하여 프로미스를 이행 상태로 변경
  } else {
    reject(error) // reject를 호출하여 프로미스를 거부 상태로 변경
  }
})
````

## Promise 사용

Promise 객체는 `then`, `catch`, `finally` 메소드를 사용하여 결과나 오류를 처리한다.

- then(): Promise가 성공적으로 완료되었을 때 실행될 함수
- catch(): Promise가 실패했ㅇ르 때 실핼될 함수
- finally(): Promise의 성공/실패 여부에 관계없이 실행되는 함수, 리소스를 정리하느 코드를 넣는다.
  
````javascript
promise
  .then(function(result) {
    console.log('성공:', result);
  })
  .catch(function(error) {
    .console.error('실패:', error);
  })
  .finally(function() {
    console.log('작업 완료');
  });
````

## Promise 체이닝

Promise 객체는 `then` 메소드에서 다른 Promise를 반환할 수 있어 여러 비동기 작업을 순차적으로 실행할 수 있다. 리를 통해 비동기 작업을 체이닝 할 수 있다.

````javascript
doSomething()
  .then(function(result) {
    return doSomethingElse(result);
  })
  .then(function(newResult) {
    return doThirdThing(newResult);
  })
  .then(function(finalResult) {
    console.log('최종 결과:', finalResult);
  })
  .catch(failureCallback);
````

`catch`를 통해 `then` 호출에서 걸쳐 발행할 수 있는 어떤 에러도 처리할 수 있다.

## Promise 정적 메소드

- Promise.all(): 여러 Promise들을 병렬로 실행하고 모든 Promise들이 완료될 때까지 기다린다. 모든 Promise들이 성공적으로 완료되면, 각 Promise의 결과값들을 배열로 반환한다.
- Promise.race(): 여러 Promise 중 가장 먼저 완료되는 Promise의 결과값 또는 에러를 반환한다.
- Promise.resolve()와 Promise.reject(): 각각 즉시 이행 또는 거부되는 Promise 객체를 생성한다.

````javascript
Promise.all([promise1, promise2, promise 3])
  .then(results => {
    console.log(results);
  })
  .catch(error => {
    console.error(error);
  });
````
