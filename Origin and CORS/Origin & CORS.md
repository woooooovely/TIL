# Origin & CORS

# 📌 Origin

오리진(origin)과 비슷한 개념으로는 도메인(Domain)이 있다. 

<aside>
💡 1. **도메인(domain)**: naver.com
2. **오리진(origin)**: https://www.naver.com/PORT

</aside>

위와 같이 도메인과 오리진의 차이는 프로토콜과 포트번호의 포함 여부이다.

# 📌 CORS

교차 출처 리소스 공유의 약어로 어떠한 오리진에서 작동하고 있는 웹 어플리케이션이 다른 **오리진 서버로의 액세스를 오리진 사이의 HTTP 요청에 의해 허가**를 할 수 있는 체계

체계적으로는 **서버에서 응답 헤더에 리소스를 공유하기 위해** **헤더를 추가하여 허가하는 형태**

![Untitled](Origin%20&%20CORS%20bcf2d069e8d04a0fb770e8f7c0d94819/Untitled.png)

# ⭐ CORS의 필요성

## Same-Origin Policy

웹 시큐리티의 중요한 정책 중 하나인 Same-Origin Policy가 존재한다. 

**오리진 사이의 리소스 공유에 제한을 거는 것**으로 XSS와 CSRF를 막는 것을 목적으로 한다.

1. **XSS(Corss Site Scripting**)
    
    유저가 웹 사이트에 접속하는 것으로 **정상적이지 않은 요청이 클라이언트에 실행되는 것을 나타냄**
    
2. **CSRF(Cross-Site Request Forgeries)**
    
    웹 애플리케이션 유저가 의도치 않은 처리를 웹에서 실행되는 것