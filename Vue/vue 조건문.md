### vue's if?

조건문은 코드를 찍는 상황에서 마주하는 가장 작은 단위의 프로그램이라고 생각한다. 어떤 조건에서는 이런 것이, 다른 조건에서는 다른 것이 나와야 하기 때문에 컴퓨터적인 사고가 필요한 부분이다. react를 사용할 때는 상태와 삼항연산자의 조합으로 조건문을 표시했던 경우가 많은데, vue 같은 경우에는 html 태그에 직접 if문을 설정하는 것이 있었다.

```jsx
	<div
        v-if="!todo.edit"
        @dblclick="editTodo(todo)"
        class="title_todo"
        :class="{ title_todo_checked: todo.completed }"
   >
        {{ todo.title }}
   </div>
```

위의 div 태그는 투두리스트에서 사용했던 할 일을 표시해주는 역할을 수행한다. div태그의 속성으로 `v-if` 가 주어지고 `todo.edit` 이 falsy 한 값을 가질 때 보여지는 것을 의미한다. 만일 `todo.edit`의 값이 true 라면 이 div 태그는 유저들에게 보여지지 않을 것이다.

반대의 경우를 나타내고 싶다면 

```jsx
<input
        v-else
        type="text"
        v-model="todo.title"
        @keyup.enter="editTodo(todo)"
/>
```

위와 같이 v-else 혹은 v-else-if를 사용하면 된다. 나의 경우는 조건이 true or false의 단순한 조건문이었기 때문에 if가 아닌 경우를 전부 잡는 v-else를 사용했지만, 조건이 세분화 된다면 v-else-if 또한 사용해야 할 것이다.

다시 위의 div 태그로 돌아와서 본다면, class가 두개가 선언 되어 있는 것을 확인 할 수 있다.

투두리스트에서 사용되는 태그이다 보니 할 일을 완료하고 체크하게 되면 글자에 밑줄을 친다든지, 색을 변경하는 식으로 시각적인 효과를 주고 싶었다. 하지만 할 일을 완료하지 않은 상태에서는 원래대로의 효과가 있어야 했고, v-if 를 사용하자니 색깔만 바꾸기 위해서 다른 태그를 하나 더 만드는 것은 비효율적으로 느껴졌다.

그럴 때 사용할 수 있는 것이 class를 변경해서 class마다 효과를 지정해주는 것이다. 할 일을 완료하지 않은 상태에서는 `title_todo` class의 css 효과를 유지하고, 할 일을 완료한 상태가 된다면 `:class='{ title_todo_checked: todo.completed }'` 의 class가 추가된다. 여기에서의 조건문은 `todo.completed` 를 설정해서 todo.completed의 값에 따라 false인지 true인지를 판단하게 된다.
