useQuery는 콜백함수 안에서 사용할 수 없다.

useQuery는 컴포넌트가 마운트, 렌더 될 때, 아폴로 클라이언트가 자동으로 실행한다.

useLazyQuery는 컴포넌트가 렌더 될 때가 아닌 이벤트에 대해 query를 실행해준다.

---

참고 블로그 : [https://hyojin96.tistory.com/entry/GraphQL-useQuery-useLazyQuery](https://hyojin96.tistory.com/entry/GraphQL-useQuery-useLazyQuery)
