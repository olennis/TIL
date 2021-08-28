## css-margin

margin을 간단하게 생각했었다. 그래서 위치를 잡고, 정렬시키는데에 margin을 아무 생각없이 썼다.

```jsx
<div class='first'></div>
<div class='second'></div>
```

와 같은 html이 있을 때,

```jsx
.first{
	margin :
	100px auto;

}
.second {
	margin : 90px auto
}
```

위와 같이 margin 값을 주게 되면, 처음 내 생각은 first에서 아래로 100px의 마진을 받게 되고, second에서 위로 90px의 마진을 받게 된다고 생각해서 first와 second사이의 여백은 190px로 생각했었다. 근데 실제로 저 요소들 사이의 공간은 100px이었고, 이유는 margin의 값이 중첩될 때는, 큰 값의 값만 적용되기 때문이다. 사이 공간을 190px로 하고 싶다면, margin-bottom이나 margin-top 속성을 활용해야 한다. (혹은 패딩)
