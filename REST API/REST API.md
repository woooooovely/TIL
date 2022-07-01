# REST API, HTTP Method

# REST?

“Representational State Transfer”의 약자.

웹에 존재하는 모든 자원(이미지, 동영상, DB) 에 고유한 URL을 부여하여 활용하는 것을 의미한다.

자원을 정의하고 자원에 대한 주소를 지정하는 방법론. 자원의 이름으로 구분해 해당 자원 상태를 주고 받는 모든 것을 의미한다.

# REST 구성요소

1. **자원(Resource), URL**

   모든 자원은 고유의 ID를 가지고 ID는 서버에 존재하고 클라이언트는 각 자원의 상태를 조작하기 위해 요청을

   보낸다. HTTP에서 이러한 자원을 구별하는 ID는 `student/1` 과 괕은 HTTP URL이다.

2. **행위(Verb), Method**

   클라이언트는 URL을 이용해 자원을 지정하고 자원을 조작하기 위해 Method를 사용한다. HTTP 프로토콜에

   서는 GET, POST, DELETE 같은 Method를 제공한다.

3. **표현(Respresentation)**

   클라이언트가 서버로 요청을 보냈을 때 응답 자원의 상태를 Representation이라고 한다. REST에서 하나의

   자원은 JSON, XML, RSS 등 여러 형태의 Respresentation으로 나타낼 수 있다.

# Why need REST?

REST API의 목적은 이해하기 쉽고 사용하기 쉬운 API를 제작으로 두고 있다

1. `GET /deleteUserInfo/id?=3`
2. `DELETE /users/3`

두 요청은 모두 특정 user의 정보를 삭제하는 API다. 하지만 1번 API는 restful 하지 못하다. 컨벤션 조차도 일관적이지 않을 수 있다. 이후 API의 이해도를 떨어뜨릴 수 있으며, 확장성도 없다.

REST API를 사용한다고 해서 성능이 향상되지는 않는다. 일관적인 컨벤션과 API의 이해도 및 호환성을 높이는 것이 REST API의 목적이다.

# REST 특징

1. **Uniform (유니폼 인터페이스)**

   Uniform Inteface는 URI로 지정한 리소스에 대한 조작을 통일되고 한정적인 인터페이스로 수행하는 아키텍처 스타일을 말한다.

2. **Stateless (무상태성)**

   REST는 무상태적인 성질을 갖는다. 다시말해 **작업을 위한 상태정보를 따로 저정하고 관리하지 않는다.**

   세션 정보나 쿠키정보를 별도로 저장하고 관리하지 않기 때문에 API 서버는 들어오는 요청만을 단순히 처리하

   면 된다. 이로 인해 서비스의 자유도가 높아지고 서버에서 불필요한 정보를 관리하지 않으므로 구현이 단순해

   진다.

3. **Cacheable (캐시 가능)**

   REST의 큰 특징 중 하나는 **HTTP라는 기존 웹 표준을 그대로 쓰기 때문에, 웹에서 사용하는 기존 인프라를 그**

   **대로 활용이 가능하다**. 그래서 HTTP가 가진 캐싱 기능이 적용 가능하다. HTTP 프로토콜 표준에서 사용하는

   Last-Modified 태그나 E-Tag를 이용하면 캐싱 구현이 가능하다.

4. **Self-descriptiveness (자체 표현 구조)**

   또 REST는 **REST API 메세지만 보고도 이를 쉽게 이해**할 수 있는 자체 표현 구조로 되어있다.

5. **Client - Server 구조**

   REST 서버는 API 제공, 클라이언트는 사용자 인증이나 컨텍스트(세션, 로그인정보) 등을 직접 관리하는 구조

   로 **각각의 역할이 확실히 구분**되기 때문에 **클라이언트와 서버에서 개발해야 할 내용이 명확**해지고 서로간에 의

   존성이 줄어든다.

6. **계층형 구조**

   **REST 서버는 다중 계층으로 구성**될 수 있으며 보안, 로드 밸런싱, **암호화 계층을 추가해 구조상의 유연성**을 둘

   수 있고 PROXY, 게이트웨이 같은 네트워크 기반의 중간매체를 사용할 수 있게 한다.

# RESTful API 특징

- 확장성과 재사용성을 높여 유지보수 및 운용을 편리하게 한다.
- HTTP 표준을 기반으로 구현하므로, HTTP를 지원하는 프로그램 언어로 클라이언트, 서버를 구축할 수 있다.

# REST API Design Guide

1. URI는 정보의 자원을 표현해야 한다.

```markdown
GET /members/1
```

- resource는 동사보다 명사를, 대문자보다 소문자를 사용한다.
- resource의 도큐먼트 이름은 단수명사를 사용해야 한다.
- resource의 컬렉션 이름은 복수명사를 사용해야 한다.
- resource의 스토어 이름은 복수명사를 사용해야 한다.

1. 자원에 대한 동작은 HTTP Method (GET, POST, PUT, DELETE)로 표현한다.
2. URI에 HTTP 메소드가 들어가면 안된다.

```markdown
GET /books/delete/1 -> DELETE /books/1
```

1. URI에 동작에 대한 동사 표현이 들어가면 안된다. (즉, CRUD 기능을 나타내는 것은 URI에 쓰지 않음)

```markdown
GET /books/show/1 -> GET /books/1
GET /books/insert/2 -> POST /books/2
```

1. 경로 부분 중 변하는 부분은 유일한 값으로 대체한다. (즉, id는 하나의 특정 resource를 나타내는 고유값을 의미)

```markdown
book을 생성하는 URI: POST /students
id=10인 book을 삭제하는 URI: DELETE /students/10
```

1. 슬래시 구분자(/)는 계층 관계를 나타내는데 쓰인다.

```markdown
<http://edwith.org/courses/java>
```

1. URI 마지막 문자로 슬래시를 포함하지 않는다

```markdown
<http://edwith.org/cources/> (x)
```

# RESTful API를 위한 HTTP Methods

## 1. GET

**자원을 받아오기만 할 때 사용한다**.

어떠한 방식으로도 자원의 상태를 바꾸지 않으므로, safe method라고 불린다.

GET API는 멱등성을 가진다. 멱등성이란, **동일한 API를 여러번 호출 시 동일한 결과를 얻을 수 있음**을 의미한다.

## 2. POST

**새로운 자원을 추가할 때 사용한다**.

서버의 상태를 바꾸며, 비멱등성 성질을 가진다. 응답 코드로 `201(Created)` 를 받아야 정상적으로 서버에 추가되었음을 확인할 수 있다.

## 3. PUT

**존재하는 자원을 변경할 때 사용한다.**

만약 자원이 존재하지 않는 경우, API는 새로운 자원을 생성할 수 있게 해준다. 이 때 응답코드는 `201(Created)` 를 받게 된다.

존재하는 자원을 바꾼 경우 `200(OK)` 또는 `204(No Content)` 응답코드를 받게 된다.

### POST vs PUT

POST는 여러개의 자원에 수행되는 반면, PUT은 단일 자원에만 수행된다.

## 4. DELETE

**자원을 삭제할 때만 사용한다.**

DELETE는 멱등성을 가진다. DELETE 메소드를 요청하면 자원을 삭제하고, 반복적으로 DELETE를 호출한 경우 결과는 바뀌지 않는다. 하지만 제거되었으므로 `404(Not Found)` 를 반환받는다.

## 5. PATCH

**한 자원의 데이터를 부분적으로 변경할 때 사용한다.**

PUT도 마찬가지로 자원을 변경할 수 있지만, 조금 명확하게 존재하는 자원에 대해 부분적으로 업데이트를 위해서 PATCH를 사용한다. PUT은 자원을 완전히 대체하는 경우 사용한다.