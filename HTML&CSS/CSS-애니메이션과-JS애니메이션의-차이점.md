# CSS 애니메이션과 JS 애니메이션의 차이점

- css는 선언형이기 때문에 좀 더 직관적이다.
- 반면 JS는 어떻게 해야 한다는 동작을 일일이 지시해야 한다.(명령형) 그래서 더 세밀한 작업을 할 수 있기도 하다.

## CSS 애니메이션

- top, left처럼 레이아웃 계산을 다시 하게 만드는 요소로 애니메이션을 구현했다면 리렌더링이 많이 되기 때문에 비효율적이지만,
- translate처럼 composite 레이어를 생성해서 따로 관리하는 애니메이션의 경우, GPU에서 별도의 스레드(컴포지터 스레드)로 처리하기 때문에 더 효율적이다.

## JS 애니메이션

- top, left처럼 레이아웃 계산을 다시 하게 만드는 요소와 setInterval()을 조합해서 만든 애니메이션이라면, 레이아웃 계산을 하느라 1초당 필요한 프레임을 만족시키지 못할 경우 화면이 끊겨보인다.
- 1초당 필요한 프레임이 보통 60fps인데, `requestAnimationFrame()`이라는 메소드를 이용하면 메인 스레드가 안정적으로 애니메이션을 생성할 수 있다.

## Reference

- https://d2.naver.com/helloworld/5237120 | 최신 브라우저의 내부 살펴보기 3 - 렌더러 프로세스의 내부 동작
- https://wit.nts-corp.com/2020/06/05/6134 | CSS 애니메이션의 성능 아는 만큼 좋아져요!
- https://brunch.co.kr/@99-life/2#comment | CSS Animation
  어떻게 사용하고계신가요?
- https://sculove.github.io/post/animation-for-performance/ | 애니메이션 성능을 높이는 방법
- https://simsimjae.tistory.com/402 | 자바스크립트 애니메이션 - requestAnimationFrame 활용하기
