computed 속성은 템플릿 내에 표현식을 사용할 때 활용된다.

아래와 같은 코드가 있다고 할 때,

```jsx
<template>
	<div id="example">
  {{ message.split('').reverse().join('') }}
	</div>
</template>
```

message를 활용해서 연산을 하는 코드라는 것은 알지만, 이 코드가 더 복잡해 진다면 쉽게 알아볼 수 없다.

이런 부분을 방지하기 위해

```jsx
computed : {
	function : function(){
		return
	}
}
```

와 같이 computed 속성을 활용한다.

### computed vs method

method 속성에서도 함수를 만들어 사용 할 수 있고, computed에서도 동일하다. 당장 눈으로 보이는 차이점은 템플렛 안에서 사용 할 때, 중괄호 안에서 소괄호를 사용하냐 사용하지 않냐 정도의 차이가 있다.

```jsx
<template>
	<div id="example">
  {{ method() }}
	{{ computed }}
	</div>
</template>
```

### why use computed?

그렇다면 왜 computed 속성을 따로 구분해서 사용 해야 할까?

가장 큰 이유는 computed 속성은 종속 대상을 따라 저장 된다는 것이다. computed 속성은 해당 속성이 종속된 대상이 변경 될 때만 함수를 실행한다.

method 같은 경우

```jsx
<template>
	<div id="example">
  {{ method() }}
	{{ method() }}
	{{ method() }}
	</div>
</template>
```

위와 같은 코드가 있을 때, 총 세번의 method가 실행되고 결과값이 렌더링 된다.

이와 달리

computed 속성의 경우

```jsx
<template>
	<div id="example">
  {{ computed() }}
	{{ computed() }}
	{{ computed() }}
	</div>
</template>
```

이와 같은 코드가 있을 때, computed 속성이 여러번 있더라도 계산 되어 있던 값을 한 번만 리턴하게 된다. 작은 데이터에서는 큰 차이가 없겠지만, 많이 사용하게 된다면 이런 부분에서 캐싱을 하는 것이 도움이 된다.
