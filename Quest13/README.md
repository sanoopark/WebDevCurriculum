# Quest 13. 웹 API의 응용과 GraphQL

## Introduction

- 이번 퀘스트에서는 차세대 웹 API의 대세로 각광받고 있는 GraphQL에 대해 알아보겠습니다.

## Topics

- GraphQL
  - Schema
  - Resolver
  - DataLoader
- Apollo

## Resources

- [GraphQL](https://graphql.org/)
- [GraphQL.js](http://graphql.org/graphql-js/)
- [DataLoader](https://github.com/facebook/dataloader)
- [Apollo](https://www.apollographql.com/)

## Checklist

- GraphQL API는 무엇인가요? REST의 어떤 단점을 보완해 주나요?

  - GraphQL은 클라이언트가 서버로부터 데이터를 효율적으로 가져오기 위해 사용하는 쿼리 언어입니다.
  - GraphQL API는 이러한 GQL로 만들어진 API입니다.
  - GQL은 가져오는 데이터의 종류를 쿼리 조합을 통해서 결정하기 때문에 여러 번 네트워크를 호출할 필요 없이, 한 번만 호출하면 됩니다.
  - 그렇기에 받아야 하는 항목들이 많고 딱 정해진 경우에 유용합니다.
  - 그러나 GraphQL은 요청복잡도가 높고, REST API는 응답복잡도가 높으므로 누구에게 어떤 정보를 제공하느냐에 따라 선택하는 것이 좋습니다.

- GraphQL 스키마는 어떤 역할을 하며 어떤 식으로 정의되나요?

  - 스키마는 데이터 타입의 집합으로 API 문서 역할을 합니다.
  - API를 설계할 때 스키마를 통해 어떤 종류의 객체를 반환할지, 내가 받을 수 있는 자원은 어떤 종류인지, 어떠한 자원을 인자로 받는지 등을 정의합니다.

- GraphQL 리졸버는 어떤 역할을 하며 어떤 식으로 정의되나요?

  - 클라이언트로부터 요청된 Query 혹은 Mutation에 대해 반환할 결과를 생성하는 로직입니다.
  - GraphQL 서버가 리졸버를 찾아 Query와 Mutation에 해당하는 함수를 실행하게 됩니다.

  - GraphQL 리졸버의 성능 향상을 위한 DataLoader는 무엇이고 어떻게 쓰나요? (-)

- 클라이언트 상에서 GraphQL 요청을 보내려면 어떻게 해야 할까요?

  - Relay, Apollo 등과 같은 클라이언트 라이브러리를 사용합니다.

  - Apollo 프레임워크(서버/클라이언트)의 장점은 무엇일까요? (-)
  
  - Apollo Client를 쓰지 않고 Vanilla JavaScript로 GraphQL 요청을 보내려면 어떻게 해야 할까요?
    - https://graphql.org/code/#javascript

- GraphQL 기반의 API를 만들 때 에러처리와 HTTP 상태코드 등은 어떻게 하는게 좋을까요?

## Quest

- 메모장의 서버와 클라이언트 부분을 GraphQL API로 수정해 보세요.

## Advanced

- GraphQL이 아직 제대로 수행하지 못하거나 불가능한 요구사항에는 어떤 것이 있을까요?
- GraphQL의 경쟁자에는 어떤 것이 있을까요?
