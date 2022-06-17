# Media Query

## Syntax

media query는 반응형 웹을 만드는 css 기술로, “어떤 조건에서 어떤 css를 적용하자” 라는 명령을 줄 때 쓴다. 특히 사용자의 화면이나 크기를 기반으로 다른 UI를 보여줄 수 있다.

미디어 쿼리는 선택 사항인 **미디어 유형**과, 자유로운 수의 **미디어 특성 표현식**으로 이루어지는데, 논리 연산자를 사용해 다수의 쿼리를 다양한 방법으로 결합할 수도 있다.

## 미디어 유형

- all

  모든 장치에 적합하다.

- print

  인쇄 결과물 및 출력 미리보기 화면에 표시중인 문서.

- screen

  주로 화면이 대상.

- speech

  음성 합성장치 대상.

## 미디어 특성 표현식

미디어 특성은 사용자 에이전트, 출력 장치, 환경 등의 특징을 나타냄.

미디어 특성 표현식은 선택 사항이며 특성의 존재 여부와 값을 판별.

각각의 미디어 특성 표현식은 괄호로 감싸야함.

- **with**: 스크롤바를 포함한 뷰포트 넓이
- **height**: 뷰포트의 넓이
- **aspect-ratio**: 뷰포트의 가로세로비

🧑🏻‍💻 Code

```css
@media only screen and (max-width: 480px) {
   body {
      font-size: 12px;
   }
}
```

**@media**

media 쿼리를 시작한다는 의미.

**only screen**

어떤 디바이스에서 적용하는지에 대한 의미.

**Ex**

- **only print**: 프린트를 하고싶을 때 작성
- **screen**: 어떤 디바이스에 상관없이, 화면에 보이는 스크린일 때 적용
- **and (max-width: 480px)**: media feature를 나타냄. 어떤 조건에서 코드를 적용할 지 나타냄

🧑🏻‍💻 Code

```html
<body>
  <div></div>
  <span>Plz flip your phone:( </span>
</body>
```

```css
body {
  display: flex;
  flex-direction: column;
  height: 100vh;
  aling-items: center;
  justify-content: center;
  font-family: sans-serif;
}
div {
  background-color: teal;
  width: 200px;
  height: 200px;
}
span {
  font-size: 40px;
}

# 300px 에서 900px 까지는 background-color를 tomato로 설정
@media screen and (min-width: 300px) and (max-width: 900px) {
   div {
     background-color: tomato;
   }
}

# 가로보기 모드일 경우 span이 보이지 않게 설정
@media screen and (orientation: landscape) {
   span {
     display: none;
   }
}
```

