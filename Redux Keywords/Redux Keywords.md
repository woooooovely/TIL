## 액션(Action)

상태에 변화가 필요할 때 발생시킨다. 액션은 하나의 객체로 표현한다.

```jsx
{
  type: "TOGGLE_VALUE"
}
```

액션 객체는 `type` 필드를 필수적으로 가지고 있어야 하고 그 외의 값들은 개발자 마음대로 넣을 수 있다.

```jsx
{
  type: "ADD_TODO",
  data: {
    id: 0,
    text: "리덕스 배우기"
  }
}
{
  type: "CHANGE_INPUT",
  text: "안녕하세요"
}
```

## 액션 생성함수 (Action Creator)

컴포넌트에서 더욱 쉽게 액션을 발생시키기 위한 것이다. 필수는 아니다.

```jsx
export function addTodo(data) {
  return {
    type: "ADD_TODO",
    data
  };
}

// 화살표 함수로도 만들 수 있다.
export const changeInput = text => ({ 
  type: "CHANGE_INPUT",
  text
});
```

## 리듀서 (Reducer)

변화를 일으키는 함수. 현재의 상태와 액션을 참조하여 새로운 상태로 반환

```jsx
function reducer(state, action) {
  // 상태 업데이트 로직
  return alteredState;
}
```

만약 카운터를 위한 리듀서를 작성한다면 이런 방식으로 작성할 수 있다.

```jsx
function counter(state, action) {
  switch (action.type) {
    case 'INCREASE':
      return state + 1;
    case 'DECREASE':
      return state - 1;
    default:
      return state;
  }
}
```

## 스토어 (Store)

한 애플리케이션 당 하나의 스토어를 이용할 수 있다. 현재의 앱 상태와, 리듀서, 내장함수를 포함하여 저장시키는 함수다.

## 디스패치 (Dispatch)

스토어의 내장함수 중 하나. 액션을 발생시킨다라고 이해하면 된다.

## 구독 (Subscribe)

스토어의 내장함수 중 하나. subscribe 함수에 특정 함수를 전달해주면, 액션이 디스패치 되었을 때 마다 전달해준 함수가 호출된다. 리액트에서는 `connect` 함수 또는 `useSelector` Hook을 사용한다.