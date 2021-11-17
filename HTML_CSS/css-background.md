#css background

이미지를 다룰 일이 많은데, 항상 이미지 반응형이 문제였다. 크기를 맞추면 비율이 깨지고 비율을 맞추면 뭔가가 틀어지는 등 항상 반응형에 많은 노력을 쏟던 와중에 background 속성을 줘서 하는것이 그나마 많은 도움이 된다는 것을 느꼈다.

background 속성을 주게 되면 영역 전체에 이미지를 깨지지 않게 줄 수 있게 되는데, 배경을 감싸고 있는 영역만 신경을쓰면 되는것 같았다.

```jsx
background-image: url(url 경로);

background-position: center center;

background-repeat:  no-repeat;
//background : url() no-repeat center center 과 같이
//한 줄로도 사용 가능

background-attachment: fixed;

background-size:  cover;
```

이런식으로 속성을 주게 되면 이미지가 고정이 되면서 감싸고 있는 크기만 줄어들게 된다.

예시 블로그 : [https://yuja-kong.tistory.com/entry/CSS-background-url-이미지-웹-모바일-크기-동시에-맞추기](https://yuja-kong.tistory.com/entry/CSS-background-url-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%9B%B9-%EB%AA%A8%EB%B0%94%EC%9D%BC-%ED%81%AC%EA%B8%B0-%EB%8F%99%EC%8B%9C%EC%97%90-%EB%A7%9E%EC%B6%94%EA%B8%B0)

이미지 때문에 골치아플 때 참고!
