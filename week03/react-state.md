# React state란?

상태 변경을 통해 리렌더링을 다루기 위한 요소

조건

- 어플리케이션에서 변경이 되는 요소들을 state로 만들어야 함.
변경이 되지 않는 것을 state로 만들 이유가 없음
- 부모 컴포넌트가 props를 통해 전달한다면 state가 아님
- 다른 state나 props를 이용해 계산, 가공 가능하다면 state가 아님

## DRY 원칙

모든 형태의 정보 중복을 지양하는 원리로 다층 구조 시스템에서 유용하다.

## SSOT(Single Source of Truth)

모든 데이터요소들을 단일 출처에서만 생성 또는 편집하도록 하는 방법론
리액트에서 상태관리할때의 얘기를 하는 것 같다.

### DRY 원칙을 따르는 SSOT

react state를 만들 때 고민해야 하는 부분

## useState

state를 만들기 위해 사용하는 함수로 리액트 hook이다. 보통 함수 컴포넌트는 state가 없는 컴포넌트 인데 
hook이 생겨서 state를 함수형 컴포넌트에서 사용 가능하게 만들어 준다.
hook은 class에서는 동작하지 않아 요새 클래스 대신 함수형 컴포넌트를 사용하는 것 같다.

사용 예시

count 라는 state를 만들고 setCount라는 state를 변화시키는 함수를 같이 만든다.
그리고 useState의 인자로 count의 초기값을 받는다.
배열 구조 분해를 통해 2개의 값을 리턴하는 usestate의 값을 2가지로 바로 선언하는 것이 일반적이다.

```js
import React, { useState } from 'react';

function Example() {
   const [count, setCount] = useState(0);
 
   return (
     <div>
       <p>You clicked {count} times</p>
       <button onClick={() => setCount(count + 1)}>
     Click me
     </button>
    </div>
  );
}
```

### 1급 객체(first-class object)란?

자바스크립트에서 1급 객체의 조건은

1. 무명의 리터럴로 생성할 수 있다. 즉, 런타임에 생성이 가능하다.
2. 변수나 자료구조(객체, 배열 등)에 저장할 수 있다.
3. 함수의 매개변수에 전달할 수 있다. -> 여기선 이 부분을 활용한 것 같다.
4. 함수의 반환값으로 사용할 수 있다.

### Lifting State Up

React에서는 단방향 데이터 흐름이라는 원칙에 따라 상위 컴포넌트에서 하위 컴포넌트로 데이터의 방향이 흐른다.
이때 하위 컴포넌트에서 어떤 이벤트로 인해 상위 컴포넌트의 상태(state)가 바뀌는 것에 대하여
상위 컴포넌트의 `상태를 변경하는 함수` 그 자체를 하위 컴포넌트로 전달하고, 이 함수를 하위 컴포넌트가 실행한다. 
이것이 상태 끌어올리기로 단방향 데이터 흐름에 원칙에 어긋나지 않게 상태를 변경할 수 있게 해준다.
