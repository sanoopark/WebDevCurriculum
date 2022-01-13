# Quest 09. 서버와 클라이언트의 대화

## Introduction

- 이번 퀘스트에서는 서버와 클라이언트의 연동, 그리고 웹 API의 설계 방법론 중 하나인 REST에 대해 알아보겠습니다.

## Topics

- expressJS, fastify
- AJAX, `XMLHttpRequest`, `fetch()`
- REST, CRUD
- CORS

## Resources

- [Express Framework](http://expressjs.com/)
- [Fastify Framework](https://www.fastify.io/)
- [MDN - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN - XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
- [REST API Tutorial](https://restfulapi.net/)
- [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete)
- [MDN - CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

## Checklist

- 비동기 프로그래밍이란 무엇인가요?

  - 블로킹을 방지하기 위해 현재 실행 중인 태스크가 종료되지 않아도 다음 태스크를 바로 실행하는 프로그래밍 기법

  - 콜백을 통해 비동기적 작업을 할 때의 불편한 점은 무엇인가요? 콜백지옥이란 무엇인가요?

    - 불편한 점

      - 가독성이 좋지 않습니다.
      - 비동기 처리 중 발생한 에러의 처치가 곤란합니다.
      - 여러 개의 비동기 처리를 한 번에 처리하는 데에 한계가 있습니다.

    - 콜백 지옥

      - 콜백 함수 호출이 중첩되어 코드의 복잡도가 높아지는 현상

  - 자바스크립트의 Promise는 어떤 객체이고 어떤 일을 하나요?

    - 비동기 처리 상태와 처리 결과를 관리하는 객체입니다.
    - then, catch, finally와 같은 후속 처리 메서드를 통해 콜백 지옥을 해결합니다.

  - 자바스크립트의 `async`와 `await` 키워드는 어떤 역할을 하며 그 정체는 무엇일까요?

    - 프로미스 기반이자만 후속 처리 메서드 없이 동기 처리처럼 프로미스가 처리 결과를 반환하도록 합니다.

- 브라우저 내 스크립트에서 외부 리소스를 가져오려면 어떻게 해야 할까요?

  - HTML이 아닌 자바스크립트를 사용해서 HTTP 요청을 전송하려면 XMLHttpRequest 객체를 사용해야 합니다.

  - 브라우저의 `XMLHttpRequest` 객체는 무엇이고 어떻게 동작하나요?

    - 비동기 방식으로 서버에 데이터를 요청하고 응답받아 동적으로 웹페이지를 갱신하는 AJAX를 구현한 객체입니다.
    - HTTP 요청 전송과 응답 수신을 위한 메서드와 프로퍼티를 제공합니다.
    - [AJAX의 동작 원리](http://www.tcpschool.com/ajax/ajax_intro_works)

  - `fetch` API는 무엇이고 어떻게 동작하나요?

    - AJAX를 구현한 인터페이스이며, 프로미스를 사용해 XHR보다 좋은 가독성을 제공합니다.
    - 브라우저에 내장된 Web API 입니다.

    - 동작 과정

      - fetch 요청
      - `Promise<Response>` 반환
      - `Response` 꺼냄 (promise, async/await)
      - `Response` 의 json 메서드 실행
      - `Promise<data>` 반환
      - `data` 꺼냄

    - 개발 배경

      - XHR은 입력, 출력, 그리고 상태 모두를 하나의 객체로 관리해야 했습니다.
      - XHR의 상태 값은 이벤트를 통해 추적해야 했습니다.
      - 이벤트 기반 모델은 Promise 기반 비동기 프로그래밍 방식과 잘 어울리지 않습니다.

    - XHR과의 차이점

      - 프로미스를 사용해 가독성이 조금 더 좋습니다.
      - Headers, Request, Response 같은 객체를 직접 다룰 수 있어 유연합니다.
      - fetch는 요청 취소를 공식적으로 지원하지 않습니다. (`AbortController.abort()`는 실험 단계)

- REST는 무엇인가요?

  - REST

    - Representational State Transfer
    - 웹에 존재하는 모든 리소스에 고유한 URI를 부여해 활용하는 것
    - 리소스를 정의하고 리소스에 대한 주소를 지정하는 방법론
    - HTTP 인프라를 최대한 활용할 수 있게 설계된 아키텍처 스타일

  - REST API는 어떤 목적을 달성하기 위해 나왔고 어떤 장점을 가지고 있나요?

    - 구성 요소

      - Resource (URI) : 클라이언트에서 자원의 상태를 조작하는 요청을 보내기 위해 필요한 ID (`movies/1`)
      - Verb (Method) : 클라이언트가 URI를 이용해 자원을 지정하고 조작하기 위한 메서드 (HTTP 메서드)
      - Representation : 클라이언트에서 서버로 요청을 보냈을 때 서버가 응답하는 자원의 상태 (JSON, XML 등)

    - RESTful

      - 클라이언트 / 서버 구조 (Client-Server)
        자원이 있는 Server , 자원을 요청하는 Client의 구조를 가진다.

      - 무상태 (Stateless)
        HTTP는 Stateless 프로토콜 이므로 REST 역시 무상태성을 가진다. 클라이언트의 Context 를 서버에 저장하지 않는다.

      - 캐시 처리 가능 (Cachealble)
        웹 표준 HTTP 프로토콜을 그대로 사용하므로 , 웹에서 사용하는 기존의 인프라를 그대로 활용 가능하다.

      - 계층화
        API 서버는 순수 비즈니스 로직을 수행하고 그 앞단에 사용자 인증 , 암호화 , 로드밸런싱 등을 하는 계층을 추가하여 구조상의 유연성을 줄 수 있다.

      - 인터페이스 일관성(Uniform Interface)
        URI로 지정한 자원에 대한 조작을 통일되고 한정적인 인터페이스로 수행한다. HTTP 표준에만 따른다면 모든 플랫폼에 사용이 가능하다.

      - 자체 표현 구조
        동사(Method) + 명사(URI) 로 이루어져있어 어떤 메서드에 무슨 행위를 하는지 알 수 있으며 REST API 자체가 매우 쉬워서 API 메세지 자체만 보고도 API를 이해할 수 있다

  - RESTful한 API 설계의 단점은 무엇인가요?

    - 메소드의 한계 : REST는 HTTP 메소드를 이용하여 URI를 표현합니다. 이러한 표현은 쉬운 사용이 가능하다는 장점이 있지만 반대로 메소드 형태가 제한적인 단점이 있습니다.
    - 표준의 부재 : REST는 설계 가이드로, 명확한 표준이 없습니다.

- CORS란 무엇인가요? 이러한 기능이 왜 필요할까요? CORS는 어떻게 구현될까요?

  - [CORS](https://ko.javascript.info/fetch-crossorigin)

## Quest

- 이번 퀘스트는 Midterm에 해당하는 과제입니다. 분량이 제법 많으니 한 번 기능별로 세부 일정을 정해 보고, 과제 완수 후에 그 일정이 얼마나 지켜졌는지 스스로 한 번 돌아보세요.
  - 이번 퀘스트부터는 skeleton을 제공하지 않습니다!
- Quest 05에서 만든 메모장 시스템을 서버와 연동하는 어플리케이션으로 만들어 보겠습니다.
  - 클라이언트는 `fetch` API를 통해 서버와 통신합니다.
  - 서버는 8000번 포트에 REST API를 엔드포인트로 제공하여, 클라이언트의 요청에 응답합니다.
  - 클라이언트로부터 온 새 파일 저장, 삭제, 다른 이름으로 저장 등의 요청을 받아 서버의 로컬 파일시스템을 통해 저장되어야 합니다.
    - 서버에 어떤 식으로 저장하는 것이 좋을까요?
  - API 서버 외에, 클라이언트를 띄우기 위한 서버가 3000번 포트로 따로 떠서 API 서버와 서로 통신할 수 있어야 합니다.
  - Express나 Fastify 등의 프레임워크를 사용해도 무방합니다.
- 클라이언트 프로젝트와 서버 프로젝트 모두 `npm i`만으로 디펜던시를 설치하고 바로 실행될 수 있게 제출되어야 합니다.
- 이번 퀘스트부터는 앞의 퀘스트의 결과물에 의존적인 경우가 많습니다. 제출 폴더를 직접 만들어 제출해 보세요!

## Advanced

- `fetch` API는 구현할 수 없지만 `XMLHttpRequest`로는 구현할 수 있는 기능이 있을까요?
- REST 이전에는 HTTP API에 어떤 패러다임들이 있었을까요? REST의 대안으로는 어떤 것들이 제시되고 있을까요?
  - [GraphQL 개념잡기](https://tech.kakao.com/2019/08/01/graphql-basic/)
