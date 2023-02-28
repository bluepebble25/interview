# this

## this

- this는 객체 내부에서 메서드가 객체에 접근하기 위한 방식이다.
- this는 어디서 호출되는지의 맥락과 함수 호출 방식에 따라 this가 가리키는 대상이 달라진다.

### 상황별 this가 가리키는 것

- 객체의 메서드: 메서드를 호출한 객체
- 앞에 객체 없이 함수 호출: 전역객체(window)를 가리킨다. 'use strict'으로 strict 모드를 설정하면 undefined가 된다.
- 객체의 메서드 안에 정의된 내부함수: 전역객체
- 객체 내부의 메서드를 별도의 변수로 분리해서 호출: 전역객체
- 콜백함수: 전역객체, <객체 내부의 메서드를 별도의 변수로 분리해서 호출>하는 경우가 되버리기 때문.
- 생성자 함수를 new 연산자 사용하면 인스턴스, 사용 안하면 전역객체. 그래서 new로 생성 안하면 `this.name = name` 같은 경우 전역객체에 프로퍼티가 할당된다.

## 화살표 함수

- 화살표 함수는 ES6에서 새로 추가된 함수 선언 방식이다. 익명 함수이며 변수에 할당해서 사용할 수도 있다.
- 함수의 내용이 return문밖에 없다면 중괄호와 return을 생략할 수 있다.

### this

- 화살표함수에서의 this는 자신이 속한 스코프가 가리키는 this를 가리키게 된다.
- 이유는 화살표 함수에는 this가 아예 존재하지 않아서 상위 스코프를 타고 올라가서 this를 찾게 되고, 만약 어떤 함수 안에서 선언되었다면 상위 스코프를, 객체 안이나 글로벌로 선언되었다면 전역객체를 가리킨다.

## Reference

- 메서드와 this | https://ko.javascript.info/object-methods
- 함수 호출 방식에 의해 결정되는 this | https://poiemaweb.com/js-this
- [JavaScript] 화살표 함수와 this 바인딩 | https://velog.io/@padoling/JavaScript-%ED%99%94%EC%82%B4%ED%91%9C-%ED%95%A8%EC%88%98%EC%99%80-this-%EB%B0%94%EC%9D%B8%EB%94%A9
- [JS] this 바인딩 (콜백함수에서의 this) | https://velog.io/@colki/JS-this-%EB%B0%94%EC%9D%B8%EB%94%A9-%EC%BD%9C%EB%B0%B1%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C%EC%9D%98-this
