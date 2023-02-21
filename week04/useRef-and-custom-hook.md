# useRef

[블로그에 정리해 두었다.](https://yodoree.github.io/react/2023/02/16/useRef.html)

## Custom Hook

use로 시작하는 camelCase로 이름이 붙은 함수로 만들면 된다.
로직을 재사용하기 위해 나만의 hook을 만들면 좋다.

### Hook의 규칙

hook은 호출 규칙이 있는다.

1. Function Component 바로 안쪽, 즉 함수의 최상위 실행컨텍스트에서 사용해야 한다.
2. Function Component 또는 Custom Hook에서만 사용해야 한다.
    콜백 함수나 조건문 안에서 hook을 호출하면 안된다.

## 아직 이해하지 못했거나 더 알아봐야할 개념

- [x] hook의 규칙을 좀 더 나만의 언어로 이해해보자.
- [x] custom hook을 만들어보고 다시 정리하자.
