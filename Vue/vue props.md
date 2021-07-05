리액트에서 쓰던 props의 개념이 vue에서도 있었다. 컴포넌트로 구성되어 있는 vue이기 때문에, 상위 컴포넌트에서 하위 컴포넌트로 데이터를 내려주고 하위 컴포넌트로부터 이벤트를 받아 오는 과정이 필요했다.

```jsx
// 상위 컴포넌트
<template>
  <div id="app">
    <하위컴포넌트
      v-on:isChange="changeSidebarStatus"
      :데이터="데이터"
    ></Header>
  </div>
</template>

<script>
import 하위컴포넌트 from "./components/하위컴포넌트.vue";

export default {
  name: "App",
  data: function() {
    return {
      데이터: true,
    };
  },
  methods: {
    changeStatus: function() {
      this.데이터 = !this.데이터;
    },
  },
  components: {
    하위컴포넌트
  },
};
</script>
```

상위 컴포넌트가 위와 같이 구성되어 있을 때, <하위컴포넌트 />에서는 '데이터'의 값을 받을 수 있게 된다.

```jsx
//하위 컴포넌트
<template lang="">
  <div>
    <a href="#" @click="isChange">

    </a>
  </div>
</template>
<script>
export default {

  methods: {
    isChange: function() {
      this.$emit("isChange");
      console.log(!this.데이터);//false or true
      return !this.데이터;
    },
  },
  props: ["데이터"],
};
</script>
```

이렇게 됐을 때 하위 컴포넌트에서 '데이터'의 값을 받아 사용 할 수 있게 되고, $emit 을 통해 상위 컴포넌트에 이벤트를 전달 할 수 있게 된다. 상위 컴포넌트에서는 'isChange'라는 이벤트를 받게 되고, isChange라는 이벤트가 발생 할 때마다, changeStatus 메소드를 실행 하게 된다.
