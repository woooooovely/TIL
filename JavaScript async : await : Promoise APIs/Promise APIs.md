## Promise APIs

## all

- Promise 배열을 전달하여 병렬적으로 다 받을 때까지 모아준다.
- getApple 과 getBanana는 서로 연관이 없기 때문에 각 3초라는 시간 즉, 총 6초를 기다려야 할 필요가 없다. 이 때 , all을 이용하여 병렬로 실행하면 3초만 기다리면 된다.

```js
function pickAllFruits() {
    return Promise.all([getApple(), getBanana()]
    .then(fruits => fruits.join(' + '));
}
pickAllFruits().then(console.log); // 3초 뒤 🍎 + 🍌 출력
```

## race

- 어떤 것이든 상관없이 먼저 반환되는 첫 번째 값만 받아오고 싶을 때

```js
function pickOnlyOne() {
    return Promise.race([getApple(), getBanana()])
}
pickOnlyOne().then(console.log);
```