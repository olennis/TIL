# Subscriptions : **Get real-time updates from your GraphQL server**

쿼리 및 뮤테이션 외에도 GraphQL은 Subscriptions라는 세번째 작업 유형을 지원한다.

쿼리와 비슷하게 subscription 또한 데이터를 가져올 수 있지만 시간이 지남에 따라 결과를 변경 할 수 있게 오래 지속되는 작업을 가져온다. (GraphQL 서버에 대한 활성 연결을 유지하여 서버가 subscription 결과에 대한 업데이트를 푸시 할 수 있게 함.)

### subscription을 사용하는 경우

대부분의 경우 클라이언트는 백엔드를 최신 상태로 유지하기 위해 subscription를 사용해서는 안된다. 대신 쿼리로 간헐적으로 폴링하거나 사용자가 요청시 쿼리를 다시 실행해야 한다. 

다음과 같은 경우에는 subscription을 사용해야 하는데, 

- 큰 개체가 점진적으로 변할 때
- 대기 시간이 짧은 실시간 업데이트일 때

### subscription 프로토콜 선택

Graph QL 사양은 subscription요청을 보내는 특정 방법을 정의하지는 않는다. 때문에 라이브러리를 사용 해야 하는데, 크게 두 가지의 라이브러리(graphql-ws 및 subscriptions-transport-ws )가 있다. 두 라이브러리는 동일한 프로토콜을 사용하지 않으므로 서버와 클라이언트가 모두 동일한 것을 사용하는지 확인이 필요하다.