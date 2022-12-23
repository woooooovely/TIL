# AJAX(Asynchronous Javascript And XML)

# 📌 AJAX?

Asynchronous Javascript And Xml (비동기 자바스크립트와 XML)의 약자.

**자바스크립트를 이용해 서버와 브라우저가 비동기 방식**으로 데이터를 교환할 수 있는 통신기능

브라우저가 소유하고 있는 `XMLHttpRequest` 객체를 이용해 페이지를 새로 고치지 않아도 데이터를 불러오는 기법이다.

<aside>
💡 즉, **자바스크립트를 통해 서버에 데이터를 비동기 방식으로 요청하는 것.**

</aside>

# 🔧 비동기 방식

**웹페이지를 리로드 하지 않고 데이터를 불러오는 방식**이며 Ajax를 통해서 서버에 요청하고 멈춰있는 것이 아니라 그 프로그램은 계속 돌아간다는 의미가 포함되어있다.

![Untitled](AJAX(Asynchronous%20Javascript%20And%20XML)%20f400e19cc72942ffa2715ed180d6fd12/Untitled.png)

## 장점

페이지를 다시 불러올 경우 전체 리소스를 다시 불러와야해서 불필요한 리소스 낭비가 발생하지만, 비동기 방식을 이용하면 **필요한 부분만 불러와 사용할 수 있으므로** 매우 큰 장점이 있다.

# 📎 AJAX를 사용 가능하게 하는 요소들

1. **HTML**
2. **DOM**
3. **JavaScript**
4. **XMLHttpRequest**
5. 기타

## 할 수 있는 것

AJAX를 이용하여 **클라이언트에서 서버로 데이터를 요청**하고 그에 대한 **결과를 돌려받을 수 있다.**

# ❓ AJAX를 쓰는 이유

기본적으로 HTTP는 클라이언트 측에서 Request를 보내고 서버 측에서 Response를 받으면 **이어졌던 연결이 끊어지게 된다**. 그래서 내용을 갱신하기 위해 다시 Request를 보내고 Response를 받으려면 **엄청난 자원의 손해와 시간낭비를 초래한다.**

AJAX는 `XMLHttpRequest` 를 통해 서버에 Request 한다. 그래서 JSON이나 XML 형태로 필요한 데이터만 받아 갱신하기 때문에 자원과 시간을 절약할 수 있다.

# ✅ 장단점

## 장점

1. 웹 페이지의 속도 향상
2. 서버의 처리가 완료될 때 까지 대기하지 않고 처리가능
3. 서버에서 Data만 전송이 가능해서 코딩의 양이 감소

## 단점

1. 히스토리 관리가 되지 않음
2. 페이지 이동이 없는 통신으로 보안의 문제가 있음
3. `XMLHttpRequest` 사용 시 유저에게 아무런 진행 정보가 제공되지 않음
4. HTTP 클라이언트 기능이 한정적

# ⚡ 진행 과정

1. `XMLHttpRequest` Object 생성
2. callback 함수 생성
3. Open a request
4. Send the request

# 🧑‍💻 예시 코드

```jsx
function reqListener(e) {
	console.log(e.currentTarget.response);
} // callback 함수

var requset = new XMLHttpRequest(); //XMLHttpRequest 객체 생성
var serverURL = ''; // 서버측 url

request.addEventListener("load", reqListener);
request.open("GET", serverURL); // Open request
request.send(); // Send request
```