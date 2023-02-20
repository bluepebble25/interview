# Virtual DOM 관련 질문

## Virtual DOM은 무엇인가? / Virtual DOM의 원리

- 가상 돔은 실제 DOM을 추상화한 Javascript 객체이며 메모리에만 존재하는 개념이다.
- 사용자가 state를 바꾸면 Virtual DOM으로 먼저 렌더링을 해보고 이전 Virtual DOM과 비교해서 달라진 부분만 실제 DOM에 반영하는 방식으로 작동한다. Virtual DOM이 변했다고 DOM이 바로 변하는 건 아니고 한꺼번에 변화를 모아서(batch) 반영하기 때문에 직접 DOM을 조작할 때보다 렌더링 과정이 단축된다.
- DOM의 변화를 비교하는데 사용되는 알고리즘: diffing 알고리즘

## key props를 사용하는 이유는 무엇인가요?

- 예를 들어서 리스트의 앞에 새로운 요소가 추가되면 이전에 있던 것들은 뒤로 밀리게 되는데, 그 때 React는 전부 새로운 요소라고 생각하게 된다. 그래서 리렌더링을 방지하고자 원래 있던 것인지 아닌지 식별하기 위해 key를 붙인다.

### key 유의할 점

- key 값으로 index 값은 지양하고 변하지 않는 값을 주자.
- 형제들 사이에서 고유한 값이어야 한다.
- key값은 자식 컴포넌트가 읽을 수 없다. key 값이 필요하다면 다른 이름의 props로 따로 전달하자.

## Reference

- [Virtual DOM and Internals](https://reactjs.org/docs/faq-internals.html#gatsby-focus-wrapper)
- [리스트와 Key](https://ko.reactjs.org/docs/lists-and-keys.html#keys)
