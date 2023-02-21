# React Hook 이란

리액트에서 16.8버전부터 추가된 새로운 요소
hook을 사용하면 class component를 만들지 않아도 state나 여러 react의 기능을 사용할 수 있다.
그래서 hook이 나오고나서 class component는 더이상 사용하지 않는다.

## Hooks

### useState

state를 만들 수 있게 해준다.

다음과 같이 만들며 이름은 원하는 대로 변경 할 수 있다.

```js
const [state, setState] = useState('초기값');
```

### useEffect

렌더링 될때마다 실행된다.

다음과 같이 사용하며, 두번째 인자인 의존성 배열을 통해, 언제 실행을 할지 결정할 수 있다.

```js
useEffect(() => {
	
}, []);
```

### useContext

Context를 이용하면 컴포넌트마다 props를 넘겨 주지 않아도 컴포넌트 전체에 데이터를 넘겨줄 수 있다.
state를 관리하기 위해 사용하는데 보통 이것보다 외부라이브러리를 사용해 state를 관리하는 것 같다.

### useRef

- [블로그에 정리해 두었다.](https://yodoree.github.io/react/2023/02/16/useRef.html)

### useLayoutEffect

컴포넌트들이 render되고 그려지기 전에 실행된다.
useEffect는 그려지고 나서 실행된다.
따라서 그려지기 전에 변화하는 것들이 있다면 useEffect보다 useLayoutEffect를 사용하는 것이 적합하다.

## React StrictMode 란

React StrictMode로 실행하며 코드를 두번씩 실행해서 비교한다.
코드를 좀더 엄격히 판단하기 위해 사용하는 것 같고 그래서 리액트 작업할때 콘솔이 두번씩 나온다.
이걸 처음 알았다.

## 아직 이해하지 못했거나 더 알아봐야할 개념

- [x] URI
- [x] [useEffect 완벽 가이드](https://overreacted.io/ko/a-complete-guide-to-useeffect/)
- [x] useContext
- [x] 리액트 라이프사이클
- [x] React StrictMode