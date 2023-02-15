# React Component

## 강의 정리

### REST란 무엇인가

- Representational State Transfer의 약자
- REST의 특징

  1. Client-server

     - 자원이 있는 쪽이 서버, 요청하는 쪽이 클라이언트
     - REST Server: API를 제공하고 비즈니스 로직 처리 및 저장을 담당
     - Client: 사용자 인증, context(세션, 로그인 정보) 등을 직접 관리하고 책임진다.

  2. Stateless

     - HTTP 프로토콜은 Stateless Protocol 이므로 REST 역시 무상태성을 갖는다.
     - client의 context를 server에 저장하지 않는다.
        - 즉, 세션과 쿠키와 같은 context 정보를 신경쓰지 않아도 되므로 구현이 단순해진다.

     - Server는 각각의 요청을 완전히 별개의 것으로 인식하고 처리한다.
     - 각 API 서버는 Client의 요청만을 단순 처리한다.
     - 즉, 이전 요청이 다음 요청의 처리에 연관되어서는 안된다.
     - 물론 이전 요청이 DB를 수정하여 DB에 의해 바뀌는 것은 허용한다.
     - Server의 처리 방식에 일관성을 부여하고 부담이 줄어들며, 서비스의 자유도가 높아진다.

  3. Cache

     - 웹 표준 HTTP 프로토콜을 그대로 사용하므로 웹에서 사용하는 기존의 인프라를 그대로 활용할 수 있다.
        - 즉, HTTP가 가진 가장 강력한 특징 중 하나인 캐싱 기능을 적용할 수 있다.
        - HTTP 프로토콜 표준에서 사용하는 Last-Modified 태스나 E-Tag를 이용하면 캐싱 구현이 가능하다.
     - 대량의 요청을 효율적으로 처리하기 위해 캐시가 요구된다.
     - 캐시 사용을 통해 응답시간이 빨리지고 REST Server 트랜잭션이 발생하지 않기 때문에 전체
     응답시간, 성능, 서버의 자원 이용률을 향상시킬 수 있다.

  4. Uniform Interface

     - 4가지 제약 조건이 있다.

       1. 자원에 대한 식별

          - 이름을 지닐 수 있는 모든 정보, 개념적인 대상 ex) 문서, 이미지 등
          - 자원은 객체, 상태는 변화가능하고, 변하지 않는 식별자가 필요하다!
            - 즉 URI를 통해 자원을 식별해야 한다.

       2. 표현을 통한 자원에 대한 조작
          - 표현: 특정한 상태의 자원에 대한 표현, ex) 문서, 파일, HTTP 메시지 entity 등
          - URI를 통해 특정한 상태의 자원을 서버와 클라이언트가 주고 받을 수 있다.
            - 즉, REpresentational State Transfer는 표현된 자원의 상태를 전송하는 것이라고 할 수 있다.
       3. 자기 서술적 메시지
          - 메시지는 스스로에 대해 설명해야 한다.
            - Host 헤더에 도메인명을 기재해야 한다.(HTTP/1.1 부터 Host 헤더 필수화)
              - ip주소 대신 도메인명이 필요한 이유는 하나의 ip주소에 복수의 도메인명이 존재 가능하기 때문
            - 캐쉬 관련 헤더를 통한 캐쉬 전략 지정
              - HTTP/1.1 : Cache-Control, Age, Etag, Vary
       4. HATEOAS
          더 알아보고 정리하자

  5. Layered System

     - Client는 REST API Server만 호출한다
     - REST Server는 다중 계층으로 구성될 수 있다.
     - Proxy, 게이트웨어 같은 네트워크 기반의 중간 매체를 사용할 수 있다.

  6. Code-On-Demand
     - Server로부터 스크립트를 받아서 Client에서 실행한다.
     - 반드시 충족할 필요는 없다.

### GraphQL은 왜 등장했는가?

- Graph Query Language의 약자, 데이터베이스 또는 데이터 관리 시스템에 접근하기 위한 언어
- 서버 API로 정보를 주고받는 것에 특화된 Query Language
- 만든 이유: 다양한 기기에서 필요한 정보의 형태가 조금씩 다른데 기존의 REST API로 구현하는 것이 어려웠다.
  정보를 요청하는 쪽에서 원하는 형태로 가져오고 수정할 수 있는 Query Language를 만들게 되었다

### GraphQL이란

- API를 위한 쿼리 언어
- 필요한 것을 정확하게 요청할 수 있는 기능을 제공하며 API를 쉽게 진화시키고 강력한 개발자 도구를 지원한다.
- 3가지 Operation type
  1. Query : 데이터 조회
  2. Mutation : 데이터 수정
  3. Subscription : 실시간 어플리케이션 구현을 위해 사용

### REST API vs GraphQL

| 비교 내용                                | REST API    | GraphQL           |
| ---------------------------------------- | ----------- | ----------------- |
| 자원에 대한 형태 정의와 데이터 요청 방법 | 연결        | 분리              |
| Resource의 크기와 형태                   | 서버가 결정 | 클라이언트가 결정 |
| Resource를 나타내는 Method               | URI         | GraphQL Schema    |
| 여러 Resource에 접근                     | 여러번      | 1번               |

- REST API 방식
  - URI를 통해 HTTP Method로 요청하고 데이터를 검색한다.
  - 자원의 타입 또는 형태와 리소스를 가져오는 방식이 연결되어 있음
  - GET `/books/1`

```json
{
  "title": "Romance of the Three Kingdoms",
  "author": {
    "firstName": "Luo",
    "lastName": "Guanzhong"
  }
}
```

    - 장점
        기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍쳐 스타일이다.
        HTTP 프로토콜을 따르는 모든 플랫폼에서 호환되고(범용성) REST API 사용을 위한 인프라 구축이 따로 필요없다.
    - 단점
        표준이 존재하지 않는다.
        사용할 수 있는 메소드가 4가지 밖에 없다.
        구형 브라우저가 지원하지 못하는 부분이 존재한다.

- GraphQL 방식

  - 자원의 타입 또는 형태와 리소스를 가져오는 방식이 분리되어 있음
  - 데이터에 대한 타입을 정의하고 데이터에 접근할 수 있는 `Query` 타입이 필요

  ```js
  type Book {
    id: ID
    title: String
    author: Author
  }
  type Author {
    id: ID
    firstName: String
    lastName: String
    books: [Book]
  }

  type Query {
    book(id: ID!): Book
    author(id: ID!): Author
  }
  ```

  - `/graphql?query={ book(id: "1") { title, author { firstName }}}`

  ```json
  {
    "title": "Black Hole Blues",
    "author": {
      "firstName": "Janna"
    }
  }
  ```

        - 장점
        HTTP 요청의 횟수를 줄일 수 있다. 원하는 정보를 하나의 query에 모두 담아 요청하는 것이 가능하기 때문이다.
        HTTP response의 size를 줄일 수 있다. 위 내용과 연결된다.

        - 단점
        파일 전송 등 Text만으로 하기 힘든 내용들을 처리하기 복잡하다.
        고정된 요청과 응답만 필요한 경우 query로 인해 요청의 크기가 rest api보다 커질 수 있다.
        재귀적인 query가 불가능하다.(결과에 따라 응답의 깊이가 얼마든지 깊어질 수 있는 api를 만들 수 없다.)

### REST API 정리

우선은 REST API란 REST 아키텍쳐 스타일을 준수하는 것이다.
간단하게는 HTTP URI를 통해 자원을 식별하고,
HTTP Method(post, get, put, delete)를 통해 해당자원에 대한 CRUD Operation을 적용하는 것을 얘기하곤 한다.
하지만 Roy Fielding(rest 개념 도입자)에 의하면 자신의 논문 어디에도 CRUD는 언급하지 않았다고 한다.
그래서 우리가 흔히 쓰는 방식은 주로 REST 스타일을 어느 정도 준수하는 HTTP API를 사용한다 라는 말이 좀 더 명확한 것 같다.

또 RESTful 하다라는 것은 REST API의 설계의도를 명확하게 지켜주는 것이다.
REST의 특징을 모두 이해해서 다시 작성하면 좋을 것 같다.

여기까지가 내가 이해한 내용이다. 추후에 더 정리하면서 이해가 되는대로 재정리가 필요하다.

### API 설계의 방향성

그래서 API를 설계할때 다음 3개의 장단점을 비교하고 프로젝트에 맞는 API를 설계하려는 자세가 필요할 것 같다.

1. REST API
2. REST 스타일의 API (HTTP API)
3. 다른 API 표준 (GraphQL API)

### JSON

JSON이란 JavaScript Object Notation의 약자이다. 직역하면 자바스크립트 객체표기법이다.
클라이언트가 사용하는 언어에 관계 없이 통일된 데이터를 주고 받을 수 있도록 서버에서 클라이언트로 데이터를 보낼 때 사용하는 양식이다.
과거 웹 초기 시절부터 사용되어 온 XML은 헤더와 태그 등의 여러 요소로 가독성이 떨어지고,
쓸데없이 용량을 잡아먹는 다는 단점이 지적되어왔는데 이를 대신해 간결하고 통일된 양식으로 사용하는 것이 JSON 이다.

자바스크립트에서 JSON객체는 두가지 메서드를 제공한다.

1. JSON.parse()

   - JSON 문자열의 구문을 분석하고 그 값을 JavaScript 값으로 변환시켜 줌

   ```js
   const json = '{"result":true, "count":42}';
   const obj = JSON.parse(json);
   console.log(obj.count);
   // Expected output: 42
   console.log(obj.result);
   // Expected output: true
   ```

2. JSON.stringify() - js값이나 객체를 JSON 문자열로 변환한다.

   ```js
   console.log(JSON.stringify({ x: 5, y: 6 }));
   // Expected output: "{"x":5,"y":6}"

   console.log(JSON.stringify([new Number(3), new String('false'), new Boolean(false)]));
   // Expected output: "[3,"false",false]"

   console.log(JSON.stringify({ x: [10, undefined, function () {}, Symbol('')] }));
   // Expected output: "{"x":[10,null,null,null]}"

   console.log(JSON.stringify(new Date(2006, 0, 2, 15, 4, 5)));
   // Expected output: ""2006-01-02T15:04:05.000Z""
   ```

### DSL(Domain-Specific Language)

특정 도메인에 특화된 언어를 말한다.
완전하지 않거나, 특수목적에 한정된 언어이다.
내가 아는 언어중에만 예시를 들어보면 `CSS` 뿐이다. 어떤 특수 목적으로만 사용 가능한 언어를 말하는 것 같다.
강의 내용에 React는 선언형(HTML과 유사한 모양의 DSL을 사용)을 사용한다고 하는데 템플릿 형식에 뷰를 위한 목적만 가지고 있기 때문에
DSL이라고 표현하는 것이 아닌가 싶다.

### 선언형 프로그래밍

선언형은 프로그램이 무엇을 해야 할지를 나타내는 경우이다. 예를 들면 어떤 웹페이지를 만들때 어떻게 페이지를 만드는지 보다,
무엇을 페이지에 보여지게 만들 것인지 고민하는 것이다.

또 프로그램이 함수형, 논리형, 제한형 프로그래밍 언어 등으로 작성된 경우에 선언형이라고 한다.
[참고자료](https://ko.wikipedia.org/wiki/%EC%84%A0%EC%96%B8%ED%98%95_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)

### 명령형 프로그래밍

쉽게 설명하면 컴퓨터가 수행할 명령들을 순서대로 써 놓은 것이라고 볼 수 있다.
이런 프로그래밍은 `how to solve it`, 즉 어떻게 그것을 해결할 것인가에 주목한다.
그래서 알고리즘 문제등을 풀때 주로 사용하는 것 같다.
주로 컴퓨터 하드웨어가 명령형으로 구현된다.

### 명령형 vs 선언형

명령형은 무엇을 어떻게(how) 할 것인지가 중요하고, 선언형은 무엇을(what) 할 것인가가 중요하다.
이 말은 잘 이해가 가지 않으므로 현실적인 예를 들어보자.

1. 첫번째 예시

당신은 애인과 함께 근사한 레스토랑에 가서 식사를 하기로 결정했다. 즐거운 기분으로 레스토랑에 도착한 뒤 안내 데스크에 다가가 이렇게 말한다.

명령형 방식 : "저기 창가 쪽 자리가 비었네요. 저 자리로 걸어가서 앉을게요"
선언형 방식 : "두 명 앉을 자리 부탁해요"

2. 두 번째 예시

낯선 사람이 당신에게 OO호텔이 어디 있는지를 묻는다. 당신은 그곳이 어디 있는지 잘 안다. 이때 당신은 이렇게 말한다.

명령형 방식 : "여기서 쭉 직진하시다가 롯데리아가 보이시면 우회전 하세요. 직진하다가 두 번째 신호등에서 좌회전하세요. OO호텔이 보일 겁니다"
선언형 방식 : "OO 호텔은 xxx동 xxx로 xx길 10에 있습니다.

자바스크립트 코드로 차이를 살펴보자

```js
// 배열을 파라미터로 받고 각 요소들의 값에 2를 곱하는 함수

// 명령형 방식
function double(arr) {
  let results = [];
  for (let i = 0; i < arr.length; i++) {
    results.push(arr[i] * 2);
  }
  return results;
}

// 선언형 방식
function double(arr) {
  return arr.map((item) => item * 2);
}
```

명령형 방식을 보면 어떻게 배열에 있는 요소들에 2를 곱할지 설명하고 있고
선영형 방식을 보면 자바스크립트 내장함수 map을 이용해 무엇을 할지만 작성되어 있다.
두가지 방식은 비슷하게 작동하지만 가독성 측면에서 명령형보다 선언형 방식의 가독성이 보다 좋다.
마치 네비게이션에게 100m 직진해서 우회전 하고 또 100M직진해서 다시 우회전해줘 라고 명령하는 것보다
어디 주소로 안내해줘 라고 선언하는 것이 편리하고 가독성이 좋은 것과 같다.

### SRP(단일 책임 원칙)

단일 책임 원칙이란 Single Responsibility Principle의 약자로 객체는 단 하나의 책임만 가져야 한다는 원칙을 말한다.
여기서 책임이라는 의미는 하나의 기능을 담당한다고 생각하면 된다.

단일 책임 원칙 준수 유무에 따른 가장 큰 파급효과는 기능 변경이 일어났을때 이다.
한 객체에 책임, 즉 기능이 많아질수록 객체 내부에서 서로 다른 기능을 하는 코드에 변화가 일어났을때 충돌을 일으킬 가능성이 높다.
즉 SRP 원칙을 잘 따르면 한 책임의 변경으로부터 다른 책임의 변경으로의 연쇄작용에서 자유로울 수 있게 된다.
뿐만 아니라 기능을 적절히 분배하므로 코드의 가독성 향상 및 유지보수가 용이하다.

React에서도 컴포넌트 규모가 커지면 너무 많은 기능을 감당할 수 있기 때문에 이를 최소 단위로 최대한 쪼개서 관리하는 것이 중요하다.

### Atomic Design

아토믹 디자인은 react나 vue 등의 라이브러리에서 컴포넌트 단위로 개발을 진행할 때
앞서 말한 SRP원칙으로 컴포넌트를 최소단위로 쪼개 코드의 재사용성을 높일때 효과적인 인터페이스 시스템을 만든다.
원자(atoms), 분자(Molecules), 유기체(Organisms), 템플릿(Templates), 페이지(pages) 로 이어지는 형식이다.

- Atoms(원자)

  - 가장 작은 단위의 컴포넌트이다. (디자인과 기능의 최소 단위)
  - 다양한 state 즉 상태, 색상, 폰트, 애니메이션과 같은 추상적인 요소가 포함될 수 있다.
  - 대표적인 컴포넌트는 버튼(Button), 텍스트(Text), 아이콘(Icon) 등이 있다.

- 분자(Molecules)

  - 2개 이상의 원자로 구성되어 있다.
  - 하나의 단위로 함께 동작하는 UI 컴포넌트들의 단순한 그룹이다.
  - 대표적인 컴포넌트는 입력 폼(Input Form), 내비게이션(Navigation), 카드(Card) 등이 있다.

- Organism(유기체)

  - 분자들을 결합하여 유기체를 형성 (분자가 되지 않은 원자도 포함)
  - 인터페이스가 어떻게 보이는지 시작하는 단계
  - 대표적인 컴포넌트는 입력 폼과 함께 헤더를 감싸거나, 카드를 관리하는 그리드 등이 있다.

- 템플릿(Templetes)

  - 여러 유기체의 집합
  - 디자인을 확인하고 레이아웃이 실제로 구동하는지 확인하는 단계
  - 대표적인 컴포넌트는 여러 카드와 그리드를 묶는 템플릿(헤더, 메인, 푸터) 등이 있다.

- Page(페이지)

  - 템플릿을 이용해서 배치를 통해 컴포넌트를 그려서 디스플레이한다.
  - 완성된 하나의 페이지이다.

              장점

              디자인 시스템 구성에 있어서 가이드라인으로 활용할 수 있다.
              애플리케이션과 분리하여 컴포넌트를 개발하고 테스트할 수 있다.

    컴포넌트 재사용성이 극대화된다.

### React component 와 props

React Component 는 다음과 같이 작성한다
함수에 이름 첫글자에 대문자를 사용하고 html을 리턴한다.
es6의 클래스를 사용해서 작성할 수도 있으나 현재는 주로 함수형으로 작성한다.

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

컴포넌트는 합성이 가능하다.

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}
```

Props는 읽기 전용이다.
모든 react 컴포넌트는 props를 다룰 때 반드시 순수 함수처럼 동작해야 한다.
순수 함수란 자신에게 할당된 입력값 즉, argument를 변경하지 않는 것이다.
