컴포넌트가 있고, state가 있기 때문에 vue 에서도 state관리가 필요하다. state를 차례대로 내리는것이 아니라 모든 컴포넌트에서 접근이 가능하게 도와주는것이 vuex인데, 기존에 react에서 사용했었던 redux와는 조금 다른느낌으로 vue에 더 잘 맞는 느낌이었다. 개인적으로 느끼기에는 더 직관적이었고 (action과 mutation의 구분이 어렵기는 하지만) 직접 사용하기에도 더 쉬웠다.

우선 root에 store.js를 만들어준다. (redux의 store와 같은 기능을 수행한다고 이해했다.)

```jsx
//store.js
import Vue from "vue";
import Vuex from "vuex";

Vue.use(Vuex);

export default new Vuex.Store({
  state: {
    countNum: 0,
  },
  getters: {},

  mutations: {
    addNum: (state) => {
      state.countNum += 1;
    },
    minusNum: (state) => {
      state.countNum -= 1;
    },
    add5Num: (state) => {
      state.countNum += 5;
    },
  },
  actions: {},
});
```

위의 코드에서 state는 vue 컴포넌트에서의 data 역할을 수행한다. state는 mutation에 의해서만 변화 되는데, mutations과 actions의 차이는 공부가 조금 더 필요한 부분인 것 같다.

공식문서에 따르면

- 상태를 변이시키는 대신 액션으로 변이에 대한 커밋을 합니다.
- 작업에는 임의의 비동기 작업이 포함 될 수 있습니다.

라고 되어 있다.
//20211031
