# Routing

웹사이트는 어떤 주소로 접속하느냐에 따라 다른 내용이 나오는데
그렇게 요구된 사항에 따라 다른 데이터를 보여줄 수 있게 하는 것을 라우팅이라고 한다.

좀 더 정확하게 어떤 네트워크 안에서 통신 데이터를 보낼 때 최적의 경로를 선택하는 과정이다.

리액트에서는 `react-router-dom`을 사용하여 이 과정을 제어할 수 있다.
주소로 접속했을 때 주소와 관련있는 컴포넌트를 지정하여 보여줄 수 있다.

## HTML DOM API

자바스크립트를 사용하여 HTML 요소들에 접근하고 조작할 수 있도록 해주는 것
특정 요소를 변경하거나 추가, 제거 할 수 있다.

모든 최신 브라우저에서 지원된다.

### Location

현재 문저의 URL을 나타내는 객체이며 `window`객체의 프로퍼티로 가져올 수 있다.

### pathname

현재 url에서 호스트와 쿼리 문자열을 제외한 경로 부분만을 나타내는 `location`객체의 프로퍼티다.

예를 들어,
https://www.example.com/path/to/page.html?param1=value1&param2=value2와 
같은 URL이 있다면, location.pathname은 /path/to/page.html을 반환한다.
