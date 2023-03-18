## Web APIs - History

브라우저의 세션 히스토리에 접근할 수 있는 api이다.
브라우저 세션 히스토리를 조작하고 페이지의 url을 변경할 수 있다.

History API는 다음과 같은 메서드와 속성을 제공한다.

back(): 이전 페이지로 이동합니다.
forward(): 다음 페이지로 이동합니다.
go(): 상대적으로 이동할 페이지 수를 인자로 받아 해당 페이지로 이동합니다.
pushState(): 새로운 세션 히스토리 항목을 추가합니다.
replaceState(): 현재 페이지의 세션 히스토리 항목을 대체합니다.
state: 현재 페이지의 상태 객체를 가져옵니다.

## React Router - NavLink, Link, Navigate, useNavigate

History API를 리액트에서 쉽게 사용할 수 있게 제공해주는 기능들이다.

### NavLink

NavLink는 현재 위치와 링크의 경로가 일치하는 경우에 활성화 스타일을 적용하는 컴포넌트.
해당 링크를 클릭하면 class에 active가 들어가며
이를 통해 현재 위치를 나타내는 네비게이션 링크에 스타일을 적용할 수 있다.

```js
import { NavLink } from 'react-router-dom';

<NavLink to="/about" activeClassName="active">About</NavLink>
```

### Link

Link는 클릭 시 해당 경로로 이동하는 컴포넌트.
a 태그와 같은 역할을 하지만, 페이지 전체를 새로 불러오지 않고 React Router를 이용해 페이지 전환을 시켜준다.

```js
import { Link } from 'react-router-dom';

<Link to="/about">About</Link>
```

### Navigate

Navigate는 주어진 경로로 즉시 이동하는 컴포넌트.
렌더링이 필요없는 로그아웃 같은 역할을 수행할때 적합함.

```js
import { Navigate } from 'react-router-dom';

<Navigate to="/" />
```

### useNavigate

useNavigate는 Navigate 컴포넌트와 비슷한 역할을 하는 훅.
이 훅을 사용하면 함수 내에서 페이지 전환을 할 수 있다.

```js
import { useNavigate } from 'react-router-dom';

function About() {
  const navigate = useNavigate();

  const handleClick = () => {
    navigate('/home');
  }

  return (
    <div>
      <button onClick={handleClick}>Go to Home</button>
    </div>
  );
}
```
