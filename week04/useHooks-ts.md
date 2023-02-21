# usehooks-ts

[usehooks-ts](https://usehooks-ts.com/)
다양한 hook이 있는 라이브러리다.
hook이 어떻게 만들어져 있는지 코드가 다 공개되어 있어서
custom hook을 만들때 참고해도 되고, 유용한 hook을 가져다 써도 된다.

```shell
npm i usehooks-ts
```

## usehooks에서 사용하는 것들

### useBoolean

true/false를 명확하게 toggle 형식으로 다룰때 유용하다.

```js
{ value, toggle } = useBoolean(); 

// 원하는 곳에서 사용!
toggle(); 
```

### useEffectOnce

useEffect를 한번만 실행시킬 때 사용한다.
useEffect로도 의존성 배열을 통해 한번만 실행하게 제어할 수 있지만 좀 더 함수 이름으로 명확하게 가독성 좋게 하기 위해 사용 하는 것 같다.

### useFetch

fetch를 반복해서 사용할때 유용하다.
정해진 url로 원하는 데이터를 얻어온다.
정말 간단히 사용할때만 좋다.
몇가지 기능이 더 있는 useFetch 라이브러리가 따로 있다.

### useInterval

만약 리액트에서 setInterval을 사용해야하는 일이 생기면
useInterval을 사용해야 한다.

## swr

데이터를 가져오기 위한 react-hooks
캐시로부터 데이터를 반환한 후, fetch 요청을 하고, 최종적으로 최신화된 데이터를 가져오는 전략이라고 설명하고 있다.
이 말을 해석하면, 캐시에 담겨져 있는 데이터로 먼저 빠르게 그리고, fetch된 데이터로 최신화를 시킨다.
그래서 빠르게 반응한다. 라고 이해했다.

## 아직 이해하지 못했거나 더 알아봐야할 개념

- [x] usehook-ts의 hooks의 예제들을 사용해보고 장단점 파악하기
- [x] setInterval을 사용하면 문제가 발생하는 이유
- [x] react-query
- [x] swr
