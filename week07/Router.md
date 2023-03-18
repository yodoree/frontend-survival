# ReactRouter - RouterProvider

React Router v6.4에서 다시 지원하는 RouterProvider 컴포넌트는
React Router의 context를 제공하는 컴포넌트다.
이를 통해 Link, Route, Navigate 등의 React Router 컴포넌트 들을 사용할 수 있다.

```js
import { RouterProvider, createBrowserRoute } from 'react-router-dom';

const routes = [
	{
		element: <Layout />,
		children: [
			{ path: '/', element: <HomePage /> },
			{ path: '/about', element: <AboutPage /> },
		],
	},
];

const router = createBrowserRouter(routes);

root.render((
	<React.StrictMode>
		<RouterProvider router={router} />
	</React.StrictMode>
));
```