# vue 기본 문법

cli를 통해 vue 프로젝트를 만들고 나니 이게 뭔지.. 이걸 어찌 써야 하는지.. 아무것도 알지 못하는 나를 발견하게 됐다. 언제까지 모른채로 있을 수는 없으니 유튜브를 통해 vue todolist 강의를 들으면서 기본적인 개념들 혹은 기본적인 문법을 사용해 봤다.

## 기본 템플릿 구성

vue 프로젝트를 만들게 되면 기본적인 태그를 가지고 만들게 된다.

```jsx
<template /> // 서비스의 웹 구조를 만들게 된다. html 태그를 적게 되고, 어떤식의 구성을 가지고 있는지 알 수 있다.
<script /> // 서비스의 스크립트 코드를 가지게 된다.
<style /> // 서비스의 스타일링, css 코드를 작성하게 된다.

태그를 통해 vue가 동작하게 된다.
```

위의 세가지 기본 태그 중 <template>, <style> 태그는 기존의 html,css 코드와 구성이 비슷하기 때문에 어떤 식으로 구성이 되어있는지만 파악한다면 사용하기 어렵지 않았다.

문제는 <script> 태그였다. js 코드이기 때문에 이게 뭐고 저게 뭐고 하는 것은 알았지만 이 태그 안에서 리턴되는 값의 키 값이 어떤 근거로 생겨나는지 알 수 없었다. 대충 파악하기로는 name은 컴포넌트의 이름, components는 이 컴포넌트가 포함하고 있는 컴포넌트(들로 혼자만의 생각을 했다.)

구조분해할당과 this가 들어가기 때문에 익숙하지 않아 하나씩 탐색하는 것에 애먹기는 했다. 

todo를 만들기 위해 컴포넌트를 하나 만들고 이 컴포넌트에 연습을 했지만, 컴포넌트 구조가 복잡해진다면 살짝 머리가 아플것 같기도 하다.

```jsx
<template lang="">
    <div>
        <div>
            <input
                type="text"
                class="todo_input"
                placeholder="enter todo"
                v-model="titleForNew"
                @keyup.enter="addTodo"
            />
            <button class="button_input" @click="addTodo">add</button>
        </div>
        <div class="container">
            <div
                v-for="(todo, index) in todos"
                :key="todo.id"
                class="todo_item"
            >
                <input type="checkbox" />
                {{ todo.title }}

                <span>
                    <button>edit</button>
                    <button @click="delTodo(index)">delete</button>
                </span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "todo-list",
    data() {
        return {
            titleForNew: "",
            idForNew: 0,
            todos: [],
        };
    },
    methods: {
        addTodo() {
            if (this.titleForNew === "") return;
            this.todos.push({
                id: this.idForNew,
                title: this.titleForNew,
                completed: false,
            });
            this.titleForNew = "";
            this.idForNew++;
        },
        delTodo(index) {
            this.todos.splice(index, 1);
        },
    },
};
</script>
<style>
	...
</style>
```

## jsx와는 다른..

vue를 사용해서 todolist를 만들다보니 몇가지 낯 익지 않은 문법들을 사용했어야 했다.

```jsx
@keyup, @click :key, v-for, v-model
```

@같은 경우는 이벤트의 앞에서 사용 되는 v-on:의 축약형으로 되어 있고, v-for는 vue에서의 for문과 react jsx 에서의 map 과 같은 기능을 하는 것으로 이해했다. v-model 같은 경우는 지정한 값을 자동으로 렌더해줘서 데이터의 변화를 쉽게 체크 할 수 있다.(==⇒ onchange + state 합친 느낌?) :key같은 경우는 vue 문법상 변수 = ''와 같이 작성해야 하는 경우가 많은데, 이렇게 작성한다면 변수를 스트링으로 처리해버린다. 이런 것을 방지하기 위해 :key같이 콜론을 표시해(v-bind)준다.
