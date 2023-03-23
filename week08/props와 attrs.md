## props

styled-components에서 props를 사용하면 컴포넌트 내부의 스타일을 동적으로 변경할 수 있다.
이를 통해 다양한 상황에서 동일한 컴포넌트를 사용하면서도 다른 스타일을 적용할 수 있다.

예를 들어, 버튼 컴포넌트를 만들 때, props를 사용하여 버튼의 크기, 색상 등을 동적으로 변경할 수 있다.

```js
import styled from 'styled-components';

const Button = styled.button`
  background-color: ${(props) => props.color || 'white'};
  color: ${(props) => props.textColor || 'black'};
  font-size: ${(props) => props.fontSize || '14px'};
`;

<Button color="red" textColor="white" fontSize="16px">Click Me!</Button>
```

## attrs

속성 값을 동적으로 변경하는 데 사용된다.

```js
const Button = styled.button.attrs(props => ({
  type: props.type || "button",
  disabled: props.disabled || false
}))`
  color: ${props => props.color || "white"};
  background-color: ${props => props.bgColor || "blue"};
  font-size: ${props => props.fontSize || "16px"};
`;
```

이 예제에서, attrs는 버튼 요소에 대한 초기 속성을 정의한다.
이 속성들은 동적으로 변경될 수 있으며, 속성에 따라 버튼의 모양과 동작이 변경될 수 있다.
예를 들어, "disabled" 속성은 버튼이 비활성화된다.

attrs는 props 객체를 받아들이고, 이를 사용하여 동적으로 속성을 설정할 수 있다.
이는 컴포넌트에 전달되는 props를 기반으로 컴포넌트의 스타일을 유연하게 제어할 수 있게 한다.