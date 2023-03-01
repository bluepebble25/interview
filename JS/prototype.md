# prototype

## 프로토타입에 대해 설명해주세요

- 메소드나 프로퍼티를 담고 있는 객체이며, 상속을 가능하게 해주는 객체이다.
- 더 정확히 말하면 프로토타입 객체와 프로토타입 링크가 있는데, 어떤 객체를 상속하려면 프로토타입 링크로 원본 객체의 프로토타입이나 원본 객체를 참조하면 된다.
- 그래서 어떤 프로퍼티를 참조하라는 명력을 받았을 때 자신에게 없다면 부모 객체의 프로퍼티에 링크를 타고 올라가서 참조를 할 수 있고, 상속이 된 것처럼 부모의 것을 자신의 것처럼 사용할 수 있다. 이것이 바로 프로토타입 체인이라는 개념이다.

<br>

+) 부정확할수도 있는 추가 개념  
[[Prototype]]이 참조하는 객체를 '프로토타입’이라고 한다. `__proto__` 는 getter, setter와 같은 접근자의 역할을 한다.
직접 `__proto__`로 접근하는 대신 `Object.getPrototypeOf`, `Object.setPrototypeOf`로 getter, setter처럼 프로토타입을 얻고, 설정할 수 있다.

## Reference

- 프로토타입 상속 | https://ko.javascript.info/prototype-inheritance
- 프로토타입 | https://poiemaweb.com/js-prototype
- [JavaScript] 프로토타입과 프로토타입 체인 | https://hanamon.kr/javascript-%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85%EA%B3%BC-%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85%EC%B2%B4%EC%9D%B8/
