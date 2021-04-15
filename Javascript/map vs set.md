### MAP

Map은 키가 있는 데이터를 저장한다는 점에서 객체와 유사하다. 다만, Map은 키 값에 다양한 자료형을 허용한다는 차이가 있다.

```jsx
let map = new Map();

map.set("1", "str1"); // 문자형 키
map.set(1, "num1"); // 숫자형 키
map.set(true, "bool1"); // 불린형 키

alert(map.get(1)); // 'num1'
alert(map.get("1")); // 'str1'

alert(map.size); // 3
```

map[key] = 2로 설정 하는 것 것 같이 map[key]를 사용 할 수 있긴 하지만, 이 방법은 map을 일반 객체로 취급하기 때문에 여러가지 제약이 생기게 된다. Map을 사용 할 때는 map 전용 메소드 set,get으 사용해야 한다.

또한 map은 키 값으로 객체를 사용 할 수 있다. 만약 일반적인 객체의 키로 객체를 할당한다면, 객체의 키는 문자열이어야 하기 때문에 변환되어 "[object object]"가 된다.

map은 삽입된 순서대로 순회를 실시한다. 객체가 순서를 기억하지 못하는 것과는 차이가 있다.

### SET

set은 중복을 허용하지 않는 값을 모아놓은 컬렉션이다. set에 키가 없는 값이 저장된다.

```jsx
let set = new Set();

let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

// 어떤 고객(john, mary)은 여러 번 방문할 수 있다.
set.add(john);
set.add(pete);
set.add(mary);
set.add(john);
set.add(mary);

// 셋에는 유일무이한 값만 저장된다.
alert(set.size); // 3

for (let user of set) {
  alert(user.name); // // John, Pete, Mary 순으로 출력됩니다.
}
```
