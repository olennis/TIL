Query는 보통 데이터를 가져오는 ‘Read’의 역할을 담당하고 있다.

물론 쿼리문에 따라 Read의 역할만이 아닌 다른 용도로 사용할 수 있지만, 직관적인 사용을 위해서는 용도에 맞게 사용하는것이 중요하다.

그런 의미에서 Mutaiton은 ‘Update’의 역할을 수행하고 있다. 쿼리와 마찬가지로 뮤테이션 필드가 객체 타입을 반환하면 중첩 필드를 요청 할 수 있다.

```jsx
mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) {
  createReview(episode: $ep, review: $review) {
    stars
    commentary
  }
}

---

variables
{
  "ep": "JEDI",
  "review": {
    "stars": 5,
    "commentary": "This is a great movie!"
  }
}
```

위는 뮤테이션을 사용하는 예시코드이다. `createReview` 필드가 새로 생성된 리뷰의 `stars`와 `commentary` 필드를 반환하게 된다.

이렇게 하나의 요청으로 필드의 새 값을 변경하고 쿼리할 수 있기 때문에 기존데이터를 변경하는 경우에 유용하다.

또한 mutation이 update에서 사용 되는 만큼 useQuery의 경우 기본적으로 컴포넌트가 렌더링 될 때 실행이 되지만, useMutation의 경우 렌더링 시점이 아닌, 원하는 액션이 발생했을 때 실행하도록 되어있다.
