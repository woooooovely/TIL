# animation 넣기

## 📌 styled-components에 animation 넣기

- **CSS와 같은 방법으로 쓰인다.**
    - styled-components에서 트랜지션을 사용할 때에는 `keyframes` 라는 유틸을 사용한다.

```jsx
import styled, { keyframes } from 'styled-components'

const easeIn = keyframes`
	0% {
				transform: translateX(20px);
				opacity: 0;
		 }

	100% {
					opacity: 1;
					transform: none;
			 }
`;

const Box = styled.div`
	width: 100px;
	height: 100px;
	animation: ${easeIn} 1s ease-in;
`

export default function App() {
	return (
			<Box>
				<span>Hello, world!</span>
			</Box>
	)
}
```