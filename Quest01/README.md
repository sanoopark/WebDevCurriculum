# Quest 01. HTML과 웹의 기초

## Introduction

- HTML은 HyperText Markup Language의 약자로, 웹 브라우저에 내용을 표시하기 위한 가장 기본적인 언어입니다. 이번 퀘스트를 통해 HTML에 관한 기초적인 사항들을 알아볼 예정입니다.

## Topics

- HTML의 역사
  - HTML 4.01, XHTML 1.0, XHTML 1.1
  - XHTML 2.0과 HTML5의 대립
  - HTML5와 현재
- 브라우저의 역사
  - Mosaic와 Netscape
  - Internet Explorer의 독점시대
  - Firefox와 Chrome의 등장
  - iOS Safari와 모바일 환경의 브라우저
  - Edge와 Whale 등의 최근의 Chromium 계열 브라우저
- HTML 문서의 구조
  - `<html>`, `<head>`와 `<body>` 등의 HTML 문서의 기본 구조
  - 시맨틱 엘리먼트
  - 블록 엘리먼트와 인라인 엘리먼트의 차이

## Resources

- [MDN - HTML](https://developer.mozilla.org/ko/docs/Web/HTML)
- [HTML For Beginners](https://html.com/)
- [History of the web browser](https://en.wikipedia.org/wiki/History_of_the_web_browser)
- [History of HTML](https://en.wikipedia.org/wiki/HTML)
- [StatCounter](https://gs.statcounter.com/)

## Checklist

- HTML 표준의 역사는 어떻게 될까요?

  - HTML 표준을 지키는 것은 왜 중요할까요?

    - HTML 표준을 지키는 것이 곧 웹 표준을 지키는 것이기 때문입니다. 웹 표준에 따라 개발된 브라우저 간에는 크로스 브라우징 이슈가 적기 때문에 웹 애플리케이션을 개발할 때 더 효율적으로 작업할 수 있습니다.
    - [HTML5 TEST](https://html5test.com/)에서 현재 사용하는 브라우저와 기타 다른 브라우저가 HTML5 표준을 얼마나 서포트하고 있는지 자세한 항목들과 함께 살펴볼 수 있습니다.

  - XHTML 2.0은 왜 세상에 나오지 못하게 되었을까요? (-)

  - HTML5 표준은 어떤 과정을 통해 정해질까요?

    - W3C의 HTML5 표준 5.3은 개발 중단되어 WHATWG HTML Living Standard로 통합되었습니다.
    - 현재는 애플, 모질라, 구글, 마이크로소프트를 핵심으로 하는 WHATWG에서 논의하고 발표합니다.
    - [HTML: The Living Standard A technical specification for Web developers](https://developers.whatwg.org/)

- 브라우저의 역사는 어떻게 될까요?

  - Internet Explorer가 브라우저 시장을 독점하면서 어떤 문제가 일어났고, 이 문제는 어떻게 해결되었을까요?

    - IE의 독점으로 기술 발전이 이뤄지지 않아 5년 간 기능 개선이 거의 없었습니다. 모질라에서 파이어폭스를 지속적으로 개발했고, 결정적으로 구글에서 크롬을 개발해 점유율을 가져올 수 있었습니다.

  - 현재 시점에 브라우저별 점유율은 어떻게 될까요? 이 브라우저별 점유율을 알아보는 것은 왜 중요할까요?

    - 우리나라는 크롬 1위, 사파리 · 삼성인터넷 2위, 엣지 · 웨일 3위, IE 4위 순으로 점유율이 높습니다.
    - 점유율이 중요한 이유는 브라우저마다 렌더링 엔진이 달라 크로스 브라우징이 필요한데, 점유율이 높은 브라우저를 우선으로 작업하기 때문입니다.

  - 브라우저 엔진(렌더링 엔진)이란 무엇일까요? 어떤 브라우저들이 어떤 엔진을 쓸까요?

    - 렌더링 엔진은 HTML과 CSS를 파싱해서 DOM과 CSSOM을 생성하고, 둘을 결합해 렌더 트리를 생성하는 브라우저의 구성 요소입니다.
    - Firefox - Gecko
    - Chrome - Blink (Webkit에서 파생된 엔진)
    - Edge - Blink
    - IE - Trident
    - Safari - Webkit

  - 모바일 시대 이후, 최근에 출시된 브라우저들은 어떤 특징을 가지고 있을까요? (-)

- HTML 문서는 어떤 구조로 이루어져 있나요?

  - `<head>`에 자주 들어가는 엘리먼트들은 어떤 것이 있고, 어떤 역할을 할까요?

    - `head`는 `title`, `link`, `meta` 등을 포함합니다.
    - `meta`는 인코딩 설정, 저자와 설명 등을 나타낼 수 있습니다.
    - `link`는 아이콘, CSS 등을 연결할 수 있습니다.

  - 시맨틱 태그는 무엇일까요?

    - 시맨틱 엘리먼트를 사용하면 어떤 점이 좋을까요?

      - SEO를 향상시킵니다.
      - 시각 장애인의 사용성을 높입니다.
      - `div`를 찾는 것보다, 의미있는 코드 블록을 찾는 것이 훨씬 쉽습니다.
      - 다른 개발자에게 해당 엘리먼트 안에 채워질 데이터 유형을 알립니다.

    - `<header>`, `<footer>`, `<article>`, `<section>`, `<div>` 엘리먼트의 차이점은 무엇인가요?

      - `<header>` : 소개 및 탐색에 도움을 주는 콘텐츠를 나타냅니다. 제목, 로고, 검색 폼, 작성자 이름 등을 포함합니다.
      - `<footer>` : `<article>`, `<aside>`, `<nav>`, `<seciton>`의 footer를 나타냅니다. 해당 섹션의 저자, 저작권 정보, 관련 문서 등을 포함합니다.
      - `<article>` : 독립적으로 구분해 배포하거나 재사용할 수 있는 구획을 나타냅니다. 게시판과 블로그 글, 매거진이나 뉴스 기사 등에 사용할 수 있습니다. `<article>`이 중첩되어 있을 때, 안쪽에 있는 요소는 바깥쪽에 있는 요소와 관련된 글을 나타냅니다. 예를 들어 `<article>` 블로그 글은 `<article>` 댓글을 포함합니다.
      - `<section>` : 독립적인 구획을 나타내며, 더 적합한 의미를 가진 요소가 없을 때 사용합니다. 요소의 콘텐츠를 외부와 구분하여 단독으로 묶어야 한다면 `<article>`이 더 좋은 선택입니다.
      - `<div>` : CSS로 꾸미기 전에는 콘텐츠나 레이아웃에 어떤 영향도 주지 않는 컨테이너입니다.

  - 블록 레벨 엘리먼트와 인라인 엘리먼트는 어떤 차이가 있을까요?
    - 블록 레벨 엘리먼트는 새로운 줄에서 100% width를 차지합니다.
    - 인라인 엘리먼트는 새로운 줄을 만들지 않으며 필요한 width만 차지합니다.

## Quest (-)

- [이 화면](screen.png)의 정보를 HTML 문서로 표현해 보세요. 다만 CSS를 전혀 사용하지 않고, 문서의 구조가 어떻게 되어 있는지를 파악하여 구현해 보세요.
  - [CSS Naked Day](https://css-naked-day.github.io/)는 매년 4월 9일에 CSS 없는 웹 페이지를 공개하여 내용과 마크업에 집중한 HTML 구조의 중요성을 강조하는 행사입니다.
- 폴더에 있는 `skeleton.html` 파일을 바탕으로 작업해 보시면 됩니다.
  - 화면을 구성하는 큰 요소들을 어떻게 처리하면 좋을까요?
  - HTML 문서상에서 같은 층위에 비슷한 요소들이 반복될 때는 어떤 식으로 처리하는 것이 좋을까요?

## Advanced

- XML은 어떤 표준일까요? 어떤 식으로 발전해 왔을까요?

  - XML(eXtensible Markup Language)은 W3C에서 개발된 마크업 언어입니다. XML은 HTML처럼 데이터를 보여주는 목적이 아닌, 데이터를 저장하고 전달할 목적으로 만들어졌습니다.

- JSON과는 어떤 차이가 있을까요? (+)

  - XML 문서는 DOM을 이용하여 접근해야 합니다. 하지만 JSON은 문자열을 전송받은 후에 바로 파싱하므로, XML보다 더 빠른 처리 속도를 보여줍니다. 따라서 JSON은 HTML과 JS가 연동되어 빠른 응답이 필요한 웹 환경에서 많이 사용되고 있습니다. 하지만 전송받은 데이터의 무결성을 사용자가 직접 검증해야 합니다. 따라서 데이터의 검증이 필요한 곳에서는 스키마를 사용하여 데이터의 무결성을 검증할 수 있는 XML이 아직도 많이 사용되고 있습니다.

- YML, Markdown 등 다른 마크업 언어들은 어떤 특징을 가지고 있고, 어떤 용도로 쓰일까요?
  - YML은 JSON의 불편함을 해소하기 위해 만들어진 상위 호환 언어입니다. JSON보다 이해하기 쉬운 형태로 쓰여집니다.
