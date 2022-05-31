# URI & URL

## URI

URI는 특정 리소스를 식별하는 통합 지원 식별자(Uniform Resource Identifier)를 의미한다. 웹 기술에서 사용하는 논리적 또는 물리적인 리소스를 식별하는 고유한 문자열 시퀀스다.

## URL

URL은 흔히 웹 주소라고도 하며, 컴퓨터 네트워크 상에서 리소스가 어디있는지 알려주기 위한 규약이다. URI의 서브셋이다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d4695a40-ae1a-4e1a-a49e-6d3c8cbe34dd/Untitled.png)

비록 URL은 URI의 서브셋이지만 URI와 URL의 결정적인 차이점은 아래와 같음.

> ***URI는 식별하고, URL은 위치를 가르킨다.***

현실과 비교해 예시를 두 가지를 들어보면

1. **“Woosang”**은 나의 이름이며 **식별자(Identifier)**다. 이는 URI와 비슷하지만 내 위치나 연락처에 대한 정보가 없으므로 URL이 될 수 없다.
2. **“서울특별시 용산구 한남동 한남대로 7”**은 주소다. **주소는 특정 위치를 가르킨다.** URL 및 URI와 비슷하며 간접적으로 내가 있는 장소로 식별한다.

## URI의 구조

일반 URI는 다음과 같은 형태를 나타낸다.

```markdown
scheme:[//[user[:password]@]host[:port]][/path][?query][#fragment]
```

1. **scheme** : 사용할 프로토콜을 뜻하며 웹에서는 http 또는 https를 사용
2. **user & password** : 서버에 있는 데이터에 접근하기 위한 사용자의 이름과 비밀번호
3. **host & port** : 접근할 대상의 호스트명과 포트번호
4. **path** : 접근할 대상의 경로에 대한 상세 정보
5. **query** : 접근할 대상에 전달하는 추가적인 정보 (파라미터)
6. **fragment** : 메인 리소스 내에 존재하는 서브 리소스에 접근할 때 이를 식별하기 위한 정보