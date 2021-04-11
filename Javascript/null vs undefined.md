### null과 undefined

이 두 타입은 기본적으로 '값이 없음'을 나타낸다.

기본적으로 값이 할당되지 않은 변수는 undefined이며, undefined 타입은 변수 자체의 값 또한 undefined이다.

결론적으로 undefined는 데이터 타입이자, 값을 나타낸다.

```tsx
let something;
```

처럼 something이라는 변수를 선언하게 된다면 something이라는 변수에 undefined를 할당하게 된다. 변수의 초기값이 undefined가 되고 undefined라는 값을 가지게 된다.

그렇기 때문에 값이면서 데이터 타입이라고 볼 수 있다.

이에 반해 null타입 변수는 '값이 비어있다'를 나타내기 위해 사용한다.

동등연산자(==)를 사용하면 null과 undefined를 같은 값으로 처리하기 때문에 일치연산자(===)를 사용해야 한다.
