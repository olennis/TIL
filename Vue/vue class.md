# vue class

vue를 사용하다 보면 클래스를 더 추가 해줘야 할 필요가 있었다.

data와 html 태그가 다음과 같이 주어 질 때,

```jsx
//case 1
<div v-bind:class="{ active: isActive }"></div>

// case 2
<div
  class="static"
  v-bind:class="{ active: isActive, 'text-danger': hasError }"
></div>

data: {
  isActive: true,
  hasError: false
}
```

아래와 같이 렌더링 된다.

```jsx
<div class="static active"></div>
```

반드시 인라인일 필요는 없으며, 아래와 같을 때도 같은 결과로 렌더링 된다.

```jsx
<div v-bind:class="classObject"></div>

data: {
  classObject: {
    isActive: true,
    'text-danger': false
  }
}
```
