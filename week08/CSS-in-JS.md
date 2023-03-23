## 라우터란?

클라이언트가 웹 페이지에서 특정 url경로로 이동할 때, 이를 처리할 수 있는 서버나 핸들러를 연결해주는 것

보통 웹 프레임워크나 라이브러리에서 제공된다.

만약 '/user' 경로로 요청이 들어온 경우, 해당 경로를 처리하는 서버 측 코드나 핸들러를 실행하여 사용자 정ㅊ보를 조회하거나 등록하는 등의 작업을 수행한다.

## React Router

리액트에서 라우팅을 구현하기 위해 `react-router-dom` 라이브러리를 사용한다.

### Browser Router

HTML의 history api를 사용해 클라이언트 측 라우팅을 처리한다.
리액트에서 react-router-dom을 사용하려면 BrowserRouter 컴포넌트로 감싸줘야 한다.
그러면 페이지 전환을 감지하고, url 경로를 업데이트하여 해당 경로에 매칭되는 컴포넌트를 렌더링 시킬 수 잇게 된다

```js
import { BrowserRouter, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Route path="/" exact component={Home} />
      <Route path="/about" component={About} />
      <Route path="/contact" component={Contact} />
    </BrowserRouter>
  );
}
```

### Route

url 경로와 매칭되는 컴포넌트를 렌더링 하는 역할을 한다.
path 속성과 component 속성을 가지는데
path는 url경로를 지정하고 component는 해당 url에 매칭되어 렌더링 될 컴포넌트를 지정한다.

### Memory Router

브라우저의 url을 변경하지 않고, 메모리 내에서 라우팅을 처리한다.

테스트나 서버 사이드 렌더링에서 유용하게 사용되는데
테스트에서는 브라우저가 없어도 동작하는 메모리 내 라우팅을 사용하여 더 쉽게 테스트할 수 있다.

```js
import { MemoryRouter, Route } from 'react-router-dom';

function App() {
  return (
    <MemoryRouter>
      <Route path="/" exact component={Home} />
      <Route path="/about" component={About} />
      <Route path="/contact" component={Contact} />
    </MemoryRouter>
  );
}
```

BrowserRouter와 동일한 방식으로 사용된다.