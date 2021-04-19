## event.preventDefault

preventDefault는 기본적으로 정의된 이벤트를 작동하지 못하게 하는 메서드이다.

예를 들어 a태그는 적용된 href 링크값으로 페이지 이동을 해주는 기본 적인 기능을 가지고 있다. a태그를 클릭 했을 때 preventDefault() 메서드를 실행시켜 주면 페이지 이동을 하는 기본 기능을 막게 된다.

```html
**<a href="[http://naver.com](http://naver.com/)" id="link"></a>
<script>
  	document.querySelector('#link').addEventListener('click', function( e ){		e.preventDefault();	});
  *// a 태그 클릭 시 링크값이 있어도 이동하지 않는다.*
</script>
**
```

preventDefault() 메서드는 이벤트가 전파되는것(버블링이나 캡처 단계)를 중지시키지는 않는다.
