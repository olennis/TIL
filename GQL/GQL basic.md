# Graph Query Language

해야지 해야지 하고 생각만하다가 계속 뒤로 밀려버린 graphql을 이제는 조금 건드려봐야 할 때가 됐다. graph ql이 뭐다~ 정도만 들었어서 그런지 굉장히 하드할것이라고 생각이 되지만 써보고 싶었던 스택이기 때문에 기대가 되는 부분이 더 크다.

### GraphQL?

facebook이 만든 새로운 api 표준, 데이터 주고 받기 기능, Graph Query Language

우선 리액트를 만든 페이스북이 만들었기 때문에 리액트와 굉장히 잘 맞는다고 들었다. (어떤 부분이 잘 맞는지는 아직은 잘 모르겠다.)

그래프큐엘은 하나의 endpoint에서 받아오기 때문에 모바일 기기 사용이 증대하는 요즘에 효과적인 데이터 로딩이 가능하다. 또한 프론트단에서 필요한 데이터에 보다 손쉽게 접근이 가능하다.

### GraphQL vs REST

블로그를 사용하는 유저가 블로그에 글을 쓰는 상황에서 REST API라면 3가지의 엔드포인트가 필요하다. 어떤 유저인지를 파악할 수 있는 엔드포인트와 어떤 글을 작성하는지, 그리고 어떤 사람들에게 노출이 될 것인지(팔로우)가 그것인데, GQL은 하나의 endpoint로 한 번의 호출만 처리하게 된다.

```jsx
query{
User (id:!@$#@#%@#$%@#)
name
posts
.
.
.
}
```

위와 같은 형식의 요청을 보내게 된다. GQL 요청이 어떤식으로 이루어지는지 아직은 잘 모르겠지만, REST와 비교해 더 간단해 보이는것은 맞는것 같다.
또한 GQL을 사용하게 되면 쿼리를 통하여 딱 필요한 데이터만 fetching 해주기 때문에 overfetch 혹은 underfetch에 대한 걱정을 할 필요가 없다.

### Graphql 사용 예

```jsx
{
  "accounts": [
    {
      "id": "1",
      "username": "velopert",
      "email": "public.velopert@gmail.com",
      "friends": [
        "2",
        "3"
      ],
      "first_name": "Minjun",
      "last_name": "Kim"
    },
    {
      "id": "2",
      "username": "jn4kim",
      "email": "jn4kim@gmail.com",
      "friends": [
        "1",
        "4"
      ],
      "first_name": "Jayna",
      "last_name": "Kim"
    },
    {
      "id": "3",
      "username": "abet",
      "email": "abet@gmail.com",
      "friends": [
        "4"
      ],
      "first_name": "Abet",
      "last_name": "Bane"
    },
    {
      "id": "4",
      "username": "Betty",
      "email": "betty@gmail.com",
      "friends": [
        "1",
        "3"
      ],
      "first_name": "Betty",
      "last_name": "Cain"
    }
  ]
}

///
query {
    account(id: "1") {
        username
        email
        firstName
        lastName
        friends {
            firstName
            username
        }
    }
}
```

### 결과

```jsx
{
  "data": {
    "account": {
      "username": "velopert",
      "email": "public.velopert@gmail.com",
      "firstName": "Minjun",
      "lastName": "Kim",
      "friends": [
        {
          "firstName": "Jayna",
          "username": "jn4kim"
        },
        {
          "firstName": "Abet",
          "username": "abet"
        }
      ]
    }
  }
}
```

아직 기초 개념만 훑어본 정도기 때문에 실제로 사용까지 해보는것은 무리가 있지만, 조금 더 시간을 쏟아서 GQL도 제대로 다룰 수 있도록 하자.
