# Redux

# 리덕스(Redux)?

가장 많이 사용하는 **리액트 상태관리 라이브러리.**

리덕스를 사용하면 **컴포넌트의 상태 업데이트 관련 로직을 다른 파일로 분리**시켜 더 효율적으로 관리할 수 있다.

# 리덕스 키워드

## 액션

상태에 어떤 변화가 필요하면 action이 필요하다.

이는 하나의 **객체로 표현**하고, **type 필드 즉, action의 이름을 가지고 있어야 한다**.

액션의 이름은 문자열 형태로, 주로 대문자로 작성하고 **액션의 이름은 고유해야 한다**.

```jsx
{
    type: 'TOGGLE_VALUE',
}
```

### 액션 타입 지정

액션 타입은 대문자로 정의하고, 문자열 내용은 **‘모듈이름/액션이름'과 같은 형태**로 작성한다.

```jsx
	const INCREASE = 'couter/INCREASE';
```

## 액션 생성 함수

액션 생성함수(action creater)는 액션 객체를 만들어주는 함수다.

export 키워드를 사용함으로써 이 함수를 다른 파일에서 불러와 사용하는 것이 가능하다.

```jsx
export const changeInput = text =>({
     type: 'CHANGE_INPUT',
     text
})
```

## 리듀서

리듀서(reducer)는 **변화를 일으키는 함수**다.

액션을 만들어서 발생시키면 리듀서가 **현재 상태(state)와 전달 받은 객체(action)를 파라미터로 받아** 두 값을 참고하여 새로운 상태를 만들어 반환한다.

```jsx
const initialState ={
    counter: 1
};

function reducer(state = initialState, action) {
      switch(action.type) {
           case INCREMENT:
               return {
                   counter: state.counter + 1
                };
           default:
               return state;
    }
}
```

### 루트 리듀서

리듀서를 여러개 만든 경우 `createStore` 함수를 사용해 **최종적으로 스토어를 만들 때 리듀서를 하나만 사용**해야 한다.

리듀서를 하나로 합치는 작업은 리덕스에서 제공하는 `combineReducer` 라는 유틸함수를 사용하면 쉽게 처리 가능하다.

```jsx
const rootReducer = combineReducer({
        reducer1,
        reducer2
})
```

## 스토어

프로젝트에 리덕스를 적용하기 위해 스토어를 만든다. **한 개의 프로젝트는 단 하나의 스토어만 가질 수 있다.**

스토어를 만들 때 `createStore` 함수를 사용한다. **함수의 파라미터에는 리듀서 함수를 넣어야 한다.**

스토어에는 여러가지 내장 함수가 포함되어 있다.

```jsx
import { createStore } from 'redux';

(...)

const store = createStore(reducer);
```

## 디스패치

디스패치(dispatch)는 스토어의 내장함수 중 하나이다. **액션 객체를 파라미터로 넣어 호출해 액션을 발생**시킴.

디스패치가 호출되면 **스토어는 리듀서 함수를 실행시켜 새로운 상태를 만들어준다.**

```jsx
dispatch(action);
```

## 구독

구독(subscribe)는 스토어의 내장함수중 하나이다. `subscribe` 함수 안에 **리스너 함수를 파라미터로 넣어서 호출하면 리스너 함수가 액션이 디스패치 되어 상태가 업데이트 될 때마다 호출된다.**

```jsx
const listener = () => {
      console.log('상태가 업데이트 됨');
}
const unsubscribe = store.subscribe(listener);
```