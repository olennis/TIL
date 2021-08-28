## lineheight

line-height 속성을 선언할 때는 다음과 같은 방식들이 있다.

```jsx
line-height:10px
line-height:1
line-height:1em

```

이런 방식으로 선언 할 때에, 몇몇 특별한 경우를 제외하고는 lineheight 값을 고정값으로 주지 않는다. -> 폰트의 사이즈가 변 할 수 있기 때문이다.

두번째 방식 같은 경우에는 폰트의 사이즈가 변할 때 line-height 값도 변하기 때문에 주어진 영역보다 폰트 사이즈가 크더라도 화면이 깨지지 않는다.

em을 사용하는 방식은 폰트 크기에 따라 line-height 값도 변하게 된다. 예를 들어

```jsx
font-size:20px;
line-height : 2em;
```

이라는 코드가 있을 때, line-height 값은 해당요소의 폰트의 두배 크기를 갖게 된다. (1em인 경우 20px)

```jsx
.parent{
	font-size:20px;
	line-height:1em;
}
.child-1{
	fost-size:30px;
}
.child-2{
	font-size:40px;
}
```

와 같은 구성이 있을 때는 line-height는 parent 요소에서 선언이 됐기 때문에 parent의 font-size를 가지게 된다. 즉, 밑에 있는 자식요소들은 지정된 영역보다 폰트의 사이즈가 더 큰 상황이다. 이런 경우에도 화면이 깨지게 된다.
