## pull 취소

풀을 받고 취소하고 싶은 경우

```jsx
$git reset --hard ORIG_HEAD

```

ORIG_HEAD는 이전에 작업한 곳의 헤드를 나타내는 표현이다. pull 혹은 merge를 잘못하게 되면 이것을 이용한다.
