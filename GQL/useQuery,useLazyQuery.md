## useQuery

```js
function Dogs({ onDogSelected }) {
  const { loading, error, data } = useQuery(GET_DOGS);

  if (loading) return "Loading...";
  if (error) return `Error! ${error.message}`;

  return (
    <select name="dog" onChange={onDogSelected}>
      {data.dogs.map((dog) => (
        <option key={dog.id} value={dog.breed}>
          {dog.breed}
        </option>
      ))}
    </select>
  );
}
```

useQuery는 콜백함수 안에서 사용할 수 없다.
useQuery를 사용하려면 graphQL 쿼리 문자열을 호출하고 전달한다. 구성 요소가 렌더링 되면 ui를 렌더링하는데 사용할 수 있는 apollo client의 개체를 반환한다.
loading은 쿼리가 아직 진행 중임을 나타낸다.
loading이 false이고 error가 없으면 쿼리가 완료됨을 나타낸다.

apollo client는 서버에서 쿼리 결과를 가져올 때마다 자동으로 해당 결과를 로컬로 캐시한다. 이것은 동일한 쿼리의 후속 실행을 빠르게 만드는 결과를 낸다.

useQuery는 컴포넌트가 마운트, 렌더 될 때, 아폴로 클라이언트가 자동으로 실행한다.

220415 추가

- refetch를 통해 데이터를 업데이트 하고 새로고침 하는것 같은 결과를 가져 올 수 있다.
- refetch === 캐시 이후의 데이터를 가져옴
- useQuery에서의 refetch, useLazyQuery에서의 refetch..?

## useLazyQuery

useLazyQuery는 컴포넌트가 렌더 될 때가 아닌 이벤트에 대해 query를 실행해준다.

---

참고 블로그 : [https://hyojin96.tistory.com/entry/GraphQL-useQuery-useLazyQuery](https://hyojin96.tistory.com/entry/GraphQL-useQuery-useLazyQuery)
