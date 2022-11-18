# React Query

## React Query 사용하기

---

React Query를 사용하기 위해 

1. `QueryClientProvider` 를 **하위 컴포넌트들을 감싸준다**
2. `new QueryClient` **인스턴스를 client props로 전달해준다**

App.js

```jsx
const queryClient = new QueryClient();

export default function App() {
	return (
		<QueryClientProvider client={queryClient}>
			...childComponents
		</QueryClientProvider>
	);
};
```

## useQuery 사용하기

---

**useQuery는 비동기 데이터를 요청할 때 사용하는 Hook이다.**

useQuery는 **2개의 Argument(인수)를 사용한다.**

1. 첫 번째 인수는 유일무이한 **문자열로 입력**해준다. (해당 문자열은 이후 **캐싱된 값을 찾기 위한 key**로 사용된다.)
2. 두 번째 인수는 **Promise를 반환하는 Callback 함수를 입력해준다.**

         **→ Callback 함수 내부에서 비동기 데이터 요청을 처리한다.**

```jsx
const result = useQuery('super-heores', () => {
	return axios.get('https://localhost:4000/superheroes');
});

console.log(result);
```

**Query에 대한 정보들이 반환된다.**

![Untitled](React%20Query%20bbf4a458105f4ff38cad313a36d91950/Untitled.png)

**가장 기본적으로 사용되는 값들은?**

- **isLoading : 데이터를 요청 중임을 알려주는 값으로 Boolean이 나온다.**
- **data : Server에 요청한 데이터가 이곳에 담긴다.**

**isLoading, data를 이용한 예제코드**

```jsx
import axios from 'axios';
import useQuery from 'react-query';

const fetchSuperHeroes = () => {
	return axios.get('http://localhost:4000/superheroes');
};

export const RQSuperHeroes = () => {
	const { isLoading, data } = useQuery('super-heroes', fetchSuperHeroes);

	if(isLoading) {
		return (
			<div>로딩중...</div>
	)};
	
	return (
		<h2>
			{data?.data.map((hero) => (
				<div key={hero.id}>{hero.name}</div>
			)))}
		</h2>
	);
}; 
```

위와 같이 **데이터를 요청하는 데에 있어 굉장히 짧고 쉽게 구현이 가능하다.**

**useQuery 내부에 내장되어 있는 기능들이 있기 때문에 매우 편리하고 효율적이다.**

## Error 처리하기

---

기존에 error를 추적하고 사용하기 위해 state를 사용했다.

**useQuery는 내장되어 있는 값을 통해 error를 쉽게 처리할 수 있다.**

**예제코드)**

```jsx
import axios from 'axios';
import useQuery from 'react-query';

const FetchSuperHeroes = () => {
	return axios.get('http://localhost:4000/superheroes');
}

const RQSuperHeroes = () => {
	const { isLoading, isError, data, error } = useQuery('super-heroes', FetchSuperHeroes);
	
	if(isLoading) {
		return <h2>로딩중...</h2>
	}

	if(isError) {
		return <h2>{error.message}</h2>
	}

	return (
		<h2>
			{data?.data.map((hero) => (
				<div key={hero.id}>{hero.name}</div>
			)))}
		</h2>
	);
}
```

**위의 예제 코드에서 isError, error가 추가되었다.**

- **isError : error가 발생했는지에 대한 Boolean 값이 반환된다.**
- **error : error에 대한 정보가 반환된다.**