## async 그리고, await

async와 await은 Promise를 조금 더 간결하게 그리고 동기적으로 실행되는 것처럼 보이도록 만들어줌.

Promise와 changing 과 같이 난잡해진 코드 위에 사용하면, 순서대로 코드를 작성하는 것처럼  간편하게 만들 수 있음.

이렇게 기존에 존재하는 것 위에 간편하게 쓸 수 있는 API를 제공하는 것을 📌 **syntatic sugar 라고 함.**

## async

promise로 만든 것을 async로 작성

```jsx
// Promise
function fetchUser() {
    return new Promise((resolve, reject) => {
          resolve('yura');
      })
 }

// async
async function fetchUser() {
     return 'yura';
  }

const user = fetchUser();
user.then(console.log);
console.log(user);
```

## await

```javascript
function delay(ms) {
     // 정해진 시간 ms가 지나면 resolve를 호출하는 Promise를 반환
     return new Promise(resolve => setTimeout(resolve, ms));
}

async function getApple() {
    // await은 이 delay가 끝날 때까지 3초 기다려준다.
    await delay(3000);
    return '🍎';
}

async function getBanana() {
     await delay(3000);
     return '🍌';
}

function pickFruits() {
    return getApple().then(apple => {
        return getBanana().then(banana => `${apple} + ${banana}`);
    }):
}

// -> 위의 pickFruits 함수를 async로
async function pickFruits() {
    const apple = await getApple();
    const banana = await getBanana();
    return `${apple} + ${banana}`;
}

pickFruits().then(console.log); // 6초 뒤 🍎 + 🍌 출력
```