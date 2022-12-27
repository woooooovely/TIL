# ES6 문법

# 📌 ES6?

ES는 ECMAScript의 약자이며 **자바스크립트의 표준, 규격을 나타내는 용어**

뒤 숫자는 버전을 뜻하고 ES5는 2009년에, ES6는 2015년에 출시

# ✅ let, const 키워드

블록스코프를 가지고 재선언이 불가했지만, **재할당 가능**한 `let` 변수 선언 키워드와 **재할당과 재선언이 불가한** 상수 선언 키워드인 `const` 가 추가

기존 `var` 키워드 보다 예측 가능한 코드를 작성이 가능해짐

# ✅ 템플릿 리터럴

`${}` 중괄호 앞에 달러 표시를 이용해 자바스크립트 표현식이 가능하다.

```jsx
//ES5
var str1 = ', ';
var str2 = 'World!';
var str3 = 'Hello' + str1 + str2;

//ES6
let str1 = ', ';
let str2 = 'World!';
let str3 = `Hello ${str1} ${str2}`;
```

# ✅ 화살표 함수

함수 표현식을 화살표 함수로 표현할 수 있다.

화살표 함수가 추가되어 함수를 간결히 나타낼 수 있어 **가독성 및 유지 보수성이 증가**

`return` 문에서 소괄호 사용 가능

```jsx
// ES5
function plusFn(a, b) {
	return a + b;
}

// ES6
// 함수 표현식 -> 화살표 함수
const plusFn = (a, b) => {
	return a + b;
}
// 함수 표현식 -> 화살표 함수(생략)
const plusFn = (a, b) => a + b;
```

# ✅ ****구조 분해 할당****

펼치다라는 뜻으로, 객체나 배열에서 사용하며 **값을 해체한 후 각 값을 변수에 새로 할당**하는 과정

```jsx
// 배열
const arr = [1, 2, 3];
const [one, two, three] = arr;

console.log(one) // 1
console.log(two); // 2
console.log(three); // 3

// 객체
const obj = {
	firstName: '조',
	lastName: '우상',

const { firstName, lastName } = obj;

console.log(firstName); // 조
console.log(lastName); // 우상 
```

# ✅ Promise

자바스크립트에서 비동기 처리를 위해 기존에는 콜백 함수, 콜백 패턴을 이용했다.

하지만 결과로 **콜백헬**을 발생시켰다.

그래서 해결책으로 `Promise` 가 도입되고 **후속처리 메소드로 에러처리를 효과적으로 할 수 있게 됬다.**