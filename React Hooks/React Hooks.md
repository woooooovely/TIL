# React Hooks

# Hooks

함수형 컴포넌트가 클래스형 컴포넌트의 기능을 사용할 수 있도록 해주는 기능

# Hook을 쓰는 이유

Hook을 사용해 함수형 컴포넌트에서도 state와 생명주기를 다룰 수 있기에 클래스형 컴포넌트에서만 가능하던 상태관리를 더 손쉽게 할 수 있어 필요하다.

# Hook의 규칙

1. **최상위에서만 Hook을 호출**

- React 함수(컴포넌트)의 최상위에서만 Hook을 호출할 것
- 반복문, 조건문, 중첩된 함수 등에서 호출 X

1. **React 함수에서만 Hook을 호출**

- Custom Hook에서는 호출 가능
- 일반적인 Javascript 함수에서는 호출 X

1. **Hook을 만들 때 앞에 use 붙이기**

- 이렇게 하면 한눈에 봐도 Hook 규칙이 적용되는 지 파악할 수 있음

1. **React는 Hook이 호출되는 순서에 의존**

- 한 컴포넌트에 여러 개의 Hook이 사용되는 경우
- Hook은 위에서부터 아래로 순서에 맞게 동작

🧑🏻‍💻 Code

```jsx
function Form() {
   // 1. name이라는 state 변수를 사용
   const [name, setName] = useState('Mary');

   // 2. Effect를 사용해 폼 데이터 저장
   useEffect(function persistForm() {
      localStorage.setItem('formData', name);
   });

   // 3. surname이라는 state 변수를 사용
   const [surname, setSurname] = useState('Poppins');
   
   // 4. Effect를 사용해 제목을 업데이트
   useEffect(function updateTitle() {
      document.title = name + ' ' + surname;
   });

   // ...
};
```

Hook에 호출 순서에 따른 결과

```jsx
// -----------
// 첫 번째 렌더링
//------------
useState('Mary')  // 1. 'Mary'라는 name state 변수 선언
useEffect(persistForm)   // 2. 폼 데이터를 저장하기 위한 effect를 추가
useState('Poppins')   // 3. 'Poppins'라는 surname state 변수 선언
useEffect(updateTitle)   // 4. 제목을 업데이트하기 위한 effect를 추가

// -----------
// 두 번째 렌더링
// -----------
useState('Mary')   // 1. name state 변수를 읽음 (인자는 무시됨)
useEffect(persistForm)   // 2. 폼 데이터를 저장하기 위한 effect가 대체
useState('Poppins')   // 3. surname state 변수를 읽음 (인자는 무시됨)
useEffect(updateTitle)   // 4. 제목을 업데이트하기 위한 effect가 대체
```

# Hook의 장점

1. **함수형 컴포넌트로 코드 통일 가능**

- 이전에는 state 유무로 있으면 클래스형이 없으면 함수형으로 분리해서 작업했음

1. **useEffect로 클래스형 LifeCycle에 흩어져 있는 로직을 묶음**

- hook은 LifeCycle과 달리 여러번 선언 가능해 코드가 무엇을 하는지에 따라 hook 별로 분기가 가능

1. **Custom Hook을 이용해 손쉽게 로직 재사용 가능**

- 클래스형 컴포넌트에서 로직을 재사용하기 위해 썼던 HOC나 render-props 같은 패턴이 가져오는 컴포넌트 트리의 불필요한 중첩을 없애줌

# Hook 종류

## 기본 Hooks

1. useState (동적 상태 관리)
2. useEffect (side effect 수행 - mount / unmount / update)
3. useContext (컴포넌트를 중첩하지 않아도 전역 값 쉽게 관리)

## 추가 Hooks

1. useReducer (복잡한 컴포넌트들의 state를 관리/분리)
2. useCallback (특정 함수 재사용)
3. useMemo (연산한 값 재사용)
4. useRef (DOM 선택, 컴포넌트 안에서 조회/수정 할 수 있는 변수 관리)