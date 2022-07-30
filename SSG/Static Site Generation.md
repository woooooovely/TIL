# Next.js Page Rendering

# Static Site Generation (정적 페이지 생성)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/993dd819-036b-4e5c-b260-ced60e9dd5c4/Untitled.png)

SSG는 1990년대의 웹에서 많이 쓰였고, 지금은 변경되지 않은 웹(이용 약관 페이지)등에 많이 쓰인다.

## 장점

80번 포트로 들어오는 HTTP 요청만 처리하면 되기 때문에 웹 서버가 가볍다.

## 단점

HTML에 변경 사항이 있으면 **다시 빌드해 웹 서버에 업로드** 해야 한다.

## In Next.js

Next에서는 `getStaticProps` 함수를 통해 HTML 파일에 들어갈 데이터를 빌드 시점에 넣어줄 수 있다.