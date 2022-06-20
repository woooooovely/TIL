# React Lifecycle

# React Lifecycle

React에서 라이프사이클은 크게 **‘마운트', ‘업데이트', ‘언마운트'**로 구분한다. 세 카테고리의 순서는 아래랑 같다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f5703731-3f17-4925-be69-3ea5de13f7bb/Untitled.png)

라이프사이클 함수들 중에 ‘Will’ 접두사가 붙은 메소드는 어떤 작업을 작동하기 전에 실행되는 메소드이고, ‘Did’ 접두사가 붙은 메소드는 어떤 작업이 작동한 후 실행되는 메소드다.

# Mount

DOM이 생성되고 웹 브라우저 상에 나타나는 것을 마운트(Mount) 라고 한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e180d910-1316-494a-bcd5-aafe79b64274/Untitled.png)

# Update

update가 되는 경우는 네 가지 경우가 있다.

1. **props가 바뀔 때**
2. **state가 바뀔 때**
3. **부모 컴포넌트가 리렌더링 될 때**
4. **this.forceUpdate로 강제로 렌더링을 트리거할 때**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0ca79885-51c4-401f-9807-7cb6a9982184/Untitled.png)

1, 2, 3번 경우 화면 갱신 단계의 첫 번째로 이루어지지만, `forceUpdate` 함수를 강제로 트리거 했을 경우에는 이전 단계 없이 바로 `render` 함수를 실행한다.

여기서 `shouldComponentUpdate` 함수는 리렌더링을 할지 말지 결정하는 함수고, 리턴값은 true 또는 false다. 리턴값이 true일 경우에만 `render` 함수를 수행하고, false일 경우 리렌더링을 종료한다.

# Unmount

언마운트(Unmount)의 경우에 컴포넌트가 웹 브라우저 상에 사라지기 전에 호출하는 메소드인 `componentWillUnmount` 만 호출하고 종료된다.

# Lifecycle Method

## render()

컴포넌트의 모양새를 정리하며 라이프사이클 메소드 중 유일하게 필수인 메소드.

메소드 안에서 `this.props` 와 `this.state` 에 접근 가능하고, 리액트 요소를 반환.

아무것도 보여주고 싶지 않을 때는 `null` 또는 `false` 를 반환.

메소드 안에 이벤트 설정이 아닌 곳에서 `setState` 를 쓰면 안되며, 브라우저의 DOM에 접근해서도 안된다.

## constructor

컴포넌트를 만들 때 처음 실행되고, 초기 `state` 를 정의할 수 있다.

## getDerivedStateFormProps

부모 컴포넌트로부터 받은 `props` 를 `state` 에 동기화 하기 위해 사용.

## componentDidMount

렌더링을 마친 후 사용된다.

다른 자바스크립트 라이브러리 또는 프레임워크 함수를 호출하거나 이벤트 등록, `setTimeout` , `setInterval` , 네트워크 요청같은 비동기 작업을 처리한다.

## shouldComponentUpdate

Update가 발생했을 경우, 리렌더링을 시작할지 결정하는 메소드.

이 메소드는 무조건 `true` 또는 `false` 를 반환해야 한다.

## getSnapshotBeforeUpdate

`render` 에서 만들어진 결과물이 브라우저에서 실제로 반영되기 전에 호출된다.

`componentDidMount` 에서 세 번째 파라미터인 `snapshot` 으로 전달받을 수 있다.

주로 스크롤바 위치 유지 등과 같이 업데이트하기 직전의 값을 참고할 일이 있을 때 활용.

## componentDidUpdate

리렌더링이 완료된 후 실행.

Update가 끝난 직후이기 때문에, DOM 관련 처리를 해도 된다.

`prevProps` 또는 `prevState` 를 사용하여 컴포넌트가 이전에 가졌던 데이터 접근이 가능.

`getSnapshotBeforeUpdate` 에서 반환한 값을 `snapshot` 으로 전달받을 수 있다.

## componentWillUnmount

컴포넌트를 DOM에서 제거할 때 실행되고, 등록한 이벤트, 타이머, 직접 생성한 DOM이 있다면 제거.

## componentDidCatch

컴포넌트 렌더링 중 에러가 발생할 경우 애플리케이션이 먹통이 되지 않고 오류 UI를 보여줄 수 있게 해준다.



![post-thumbnail](https://velog.velcdn.com/images/st2702/post/adbd06c3-50ad-4251-a374-57622e21bc12/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-10-22%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2011.12.17.png)