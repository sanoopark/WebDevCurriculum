# Quest 08. 웹 API의 기초

## Introduction

- 이번 퀘스트에서는 웹 API 서버의 기초를 알아보겠습니다.

## Topics

- HTTP Method
- node.js `http` module
  - `req`와 `res` 객체

## Resources

- [MDN - Content-Type Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)
- [MDN - HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- [MDN - MIME Type](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type)
- [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop)
- [HTTP Node.js Manual & Documentation](https://nodejs.org/api/http.html)

## Checklist

- HTTP의 GET과 POST 메소드는 어떻게 다른가요?

  - GET은 서버에서 데이터를 가져오는 메서드이고, POST는 서버로 데이터를 전송하는 메서드입니다.

  - 다른 HTTP 메소드에는 무엇이 있나요?

    - HEAD : GET과 동일하지만 메시지 바디를 제외하고 반환합니다.
    - PUT : 목적 리소스를 현재 메시지의 값으로 생성하거나 만약 존재한다면 기존 리소스를 삭제하고 덮어씁니다.
      - PUT은 POST와 다르게 클라이언트가 리소스의 위치를 알고 URI를 지정해 주어야 합니다.
    - DELETE : 특정 리소스를 삭제합니다.
    - CONNECT : 목적 리소스로 식별되는 서버로의 터널을 맺습니다. (양방향 통신)
    - OPTIONS : 서버가 어떤 메서드를 지원하는지 알아볼 때 사용합니다. (CORS 상황에서는 먼저 OPTIONS 요청을 보내 테스트하고, 허용하면 실제 요청을 날립니다.)
    - TRACE : 목적 리소스의 경로를 따라 메시지 loop-back 테스트를 합니다. (핑퐁 테스트)
    - PATCH : 리소스를 부분적으로 변경합니다.

  - 각 메서드의 특성은 어떻게 다른가요? (+)

    ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FUOvbt%2FbtqThZBXamz%2FhkX1UreuXMvecjv1YkEtdK%2Fimg.png)

    - 안전(Safe) : 호출해도 리소스를 변경하지 않는 특성
    - 멱등성(Idempotent) : 동일한 요청을 여러 번 보내도 한 번 보내는 것과 같은 특성
    - 캐시 가능(Cacheable) : 응답 결과를 서버에 캐시 해서 사용해도 되는 메소드
      - GET, HEAD, POST, PATCH가 가능하지만 실무에서는 구현이 어렵기 때문에 GET, HEAD 정도만 캐시 하여 사용

- HTTP 서버에 GET과 POST를 통해 데이터를 보내려면 어떻게 해야 하나요?

  - GET은 쿼리스트링을 통해 POST는 바디를 통해 보냅니다.

  - HTTP 요청의 `Content-Type` 헤더는 무엇인가요?

    - 리소스의 형식을 명시하기 위해 헤더에 실리는 정보입니다.

  - Postman에서 POST 요청을 보내는 여러 가지 방법(`form-data`, `x-www-form-urlencoded`, `raw`, `binary`) 각각은 어떤 용도를 가지고 있나요?
    - `form-data` : non-ASCII text or large binary data
    - `x-www-form-urlencoded` : simple text/ ASCII data
    - `raw` : plain text or JSON or any other kind of string
    - `binary` : non-textual data (video/audio file, images...)

- node.js의 `http` 모듈을 통해 HTTP 요청을 처리할 때, `req`와 `res` 객체에는 어떤 정보가 담겨있을까요?

  - `req`는 브라우저인 클라이언트에 의해 전송되는 메시지고, `res`는 서버에서 응답으로 전송되는 메시지입니다.

  - GET과 POST에 대한 처리 형태가 달라지는 이유는 무엇인가요?
  
    - GET이 리소스를 read하기 위한 목적이라면, POST는 리소스를 기반으로 업데이트한 정보를 create하기 위한 목적이기 때문입니다.
    - GET은 read이므로 멱등성의 특징을 지닌 반면, POST는 그렇지 않기 때문에 이러한 부분들을 고려할 수 있습니다.

- 만약 API 엔드포인트(URL)가 아주 많다고 한다면, HTTP POST 요청의 `Content-Type` 헤더에 따라 다른 방식으로 동작하는 서버를 어떻게 정리하면 좋을까요? (?)

  - 그 밖에 서버가 요청들에 따라 공통적으로 처리하는 일에는 무엇이 있을까요? 이를 어떻게 정리하면 좋을까요?
    - http 모듈을 사용한다면 `res` 인자에 server 응답 정보가 담겨져 오는데, 이것을 파싱해서 클라이언트가 어떠한 가공된 정보를 받아야 하는지 결정하고 구현합니다.

## Quest

- 다음의 동작을 하는 서버를 만들어 보세요.
  - 브라우저의 주소창에 `http://localhost:8080`을 치면 `Hello World!`를 응답하여 브라우저에 출력합니다.
  - 서버의 `/foo` URL에 `bar` 변수로 임의의 문자열을 GET 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/foo` URL에 `bar` 키에 임의의 문자열 값을 갖는 JSON 객체를 POST 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/pic/upload` URL에 그림 파일을 POST 하면 서버에 보안상 적절한 방법으로 파일이 업로드 됩니다.
  - 서버의 `/pic/show` URL을 GET 하면 브라우저에 위에 업로드한 그림이 뜹니다.
  - 서버의 `/pic/download` URL을 GET 하면 브라우저에 위에 업로드한 그림이 `pic.jpg`라는 이름으로 다운로드 됩니다.
- expressJS와 같은 외부 프레임워크를 사용하지 않고, node.js의 기본 모듈만을 사용해서 만들어 보세요.
- 처리하는 요청의 종류에 따라 공통적으로 나타나는 코드를 정리해 보세요.

## Advanced

- 서버가 파일 업로드를 지원할 때 보안상 주의할 점에는 무엇이 있을까요?
