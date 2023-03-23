## Reset CSS

리셋 CSS(reset CSS)는 브라우저의 기본 스타일을 모두 초기화하고, 모든 요소에 대해 동일한 기본 스타일을 적용하는 CSS 파일.
리셋 CSS는 다양한 브라우저에서 동일한 모양으로 웹사이트를 보여주기 위해 사용된다.
이는 브라우저마다 기본적으로 적용되는 스타일은 차이가 있기 때문이다.

리셋 CSS는 웹 디자인을 시작할 때 가장 먼저 적용되는 CSS 파일 중 하나이며, 주로 다음과 같은 방법 중 하나로 사용됩니다.

### normalize.css

normalize.css는 브라우저의 기본 스타일을 재정의하지 않으며, 모든 스타일이 일관성 있게 적용되도록 조정한다.
가능한 한 브라우저의 내장 스타일을 최대한 건들지 앟는 선에서 브라우저간에 상이한 부분만 스타일을 통시켜준다.
이는 기존 CSS 코드를 normalize.css와 함께 사용하더라도 기존 스타일이 변경되지 않도록 보장한다.


## `box-sizing` 속성

요소의 크기를 계산하는 방법을 결정한다.

기본적으로, box-sizing의 값은 `content-box`로 설정되어 있다.
이 경우에는 요소의 width와 height 속성값에는 해당 요소의 내용(content)의 크기만 포함된다.
즉, 테두리(border)와 안쪽 여백(padding)의 크기는 width와 height 값에 포함되지 않는다.

box-sizing 속성값을 `border-box`로 설정하면, 요소의 width와 height 속성값에는 테두리와 안쪽 여백의 크기까지 포함된다.
이렇게 하면 요소의 전체 크기를 정확하게 제어할 수 있다.

예를 들어, 다음과 같은 CSS 코드를 적용하면 box-sizing 속성값이 border-box로 설정되어 있기 때문에, .box 클래스의 너비와 높이에는 테두리와 안쪽 여백의 크기도 포함된다.


```css
.box {
  box-sizing: border-box;
  width: 200px;
  height: 200px;
  padding: 20px;
  border: 10px solid black;
}

```

## `word-break` 속성
## Theme
## ThemeProvider