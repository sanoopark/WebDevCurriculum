# Quest 02. CSS의 기초와 응용

## Introduction

- CSS는 Cascading StyleSheet의 약자입니다. 웹브라우저에 표시되는 HTML 문서의 스타일을 지정하는 (거의) 유일하지만 다루기 쉽지 않은 언어입니다. 이번 퀘스트를 통해 CSS의 기초적인 레이아웃 작성법을 알아볼 예정입니다.

## Topics

- CSS의 기초 문법과 적용 방법
  - Inline, `<style>`, `<link rel="stylesheet" href="...">`
- CSS 규칙의 우선순위
- 박스 모델과 레이아웃 요소
  - 박스 모델: `width`, `height`, `margin`, `padding`, `border`, `box-sizing`
  - `position`, `left`, `top`, `display`
  - CSS Flexbox와 Grid
- CSS 표준의 역사
- 브라우저별 Developer tools

## Resources

- [MDN - CSS](https://developer.mozilla.org/ko/docs/Web/CSS)
- [Centering in CSS: A Complete Guide](https://css-tricks.com/centering-css-complete-guide/)
- [A complete guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [그리드 레이아웃과 다른 레이아웃 방법과의 관계](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Grid_Layout/%EA%B7%B8%EB%A6%AC%EB%93%9C_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83%EA%B3%BC_%EB%8B%A4%EB%A5%B8_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83_%EB%B0%A9%EB%B2%95%EA%B3%BC%EC%9D%98_%EA%B4%80%EA%B3%84)

## Checklist

- CSS를 HTML에 적용하는 세 가지 방법은 무엇일까요?

  - 세 가지 방법 각각의 장단점은 무엇일까요?
    - Inline CSS
      - 테스트나 빠르게 수정을 하기 용이한 방법입니다.
      - 유지보수가 불편하고 코드가 길어집니다.
      - 재사용이 불가능합니다.
    - Internal CSS
      - HTML의 여러 요소에 한 번에 적용할 수 있는 것이 장점입니다.
      - 다른 HTML 문서에는 적용할 수 없는 것이 단점입니다.
    - External CSS
      - HTML과 분리되기 때문에 HTML의 명확한 구조를 볼 수 있게 합니다.
      - 하나의 CSS 파일을 여러 HTML에 적용할 수 있습니다.
      - CSS가 로드되기까지 렌더링 되지 않는 것이 단점입니다.
      - CSS 파일을 연결하는 것 자체가 웹 사이트의 전체적인 로딩 시간을 지연시킬 수 있습니다.

- 그럼 External CSS 방식을 사용할 때 속도를 개선할 방법은 무엇일까요?

  - `@import`는 병렬이 아닌 직렬 방식이기 때문에 로딩 시간을 늘립니다.
  - 하나의 CSS 파일을 개별 파일로 나눠 연결하면 속도가 개선됩니다.
  - 로드가 완료되기 전까지는 렌더링되지 않는 점을 개선하기 위해서 body 안의 각 엘리먼트 앞에 연결할 수 있습니다.
    근본적인 속도를 향상시킬 순 없지만 체감 속도를 향상시키는 방법입니다.
  - 속성 정렬을 ABC 순으로 하면 3% 정도의 향상이 있습니다.
  - Extend이 아닌 Mixin을 사용하면 23% 정도의 향상이 있습니다.

- CSS 규칙의 우선순위는 어떻게 결정될까요?

  1. 제작자보다 사용자의 스타일시트를 우선으로 적용합니다.  
     `!important` 선언을 한 사용자 스타일 > `!important` 선언을 한 작성자 스타일 >
     작성자 스타일 > 사용자 스타일 > User Agent 선언 (브라우저 자체의 선언)

  2. id, class, element 개수에 따른 명시도(Specificity)를 계산합니다.  
     인라인 스타일은 가장 높은 명시도를 갖습니다.

  3. 명시도가 같다면 마지막에 지정된 스타일이 우선 적용됩니다.

- CSS의 박스모델은 무엇일까요? 박스가 화면에서 차지하는 크기는 어떻게 결정될까요?
  - 브라우저의 렌더링 엔진은 박스 모델에 따라 각각의 요소를 사각형 박스로 표현합니다.
  - 박스 모델은 모든 HTML 요소를 포함하는 박스로서, margin, border, padding, content의 4가지로 구성됩니다.
  - 박스가 화면에서 차지하는 크기는 CSS로 결정됩니다.

- `float` 속성은 왜 좋지 않을까요?
  - float은 부모 요소가 자식 요소의 크기를 반영하지 못하거나, 상속되는 문제가 발생하기 때문입니다.
  - float된 요소의 부모에 `clearfix` 클래스를 추가해 `clearfix::after`에 `clear:both`를 지정해주면 해결됩니다. (+)
  - float은 원래 신문 레이아웃처럼 이미지 주변에 텍스트가 둘러싸는 간단한 레이아웃을 구현할 수 있도록 도입되었습니다.

- Flexbox(Flexible box)와 CSS Grid의 차이와 장단점은 무엇일까요?
  - Flex는 1차원으로 수평, 수직 영역 중 하나의 방향으로만 레이아웃을 나눌 수 있습니다.
  - Grid는 2차원으로 수평 수직을 동시에 영역을 나눌 수 있습니다.
  - 같은 화면을 구현할 때 Flex는 Grid보다 더 많은 코드량을 필요로 하고, 복잡해지고, 성능이 느리다는 단점이 있습니다.
  - 그렇지만 caniuse.com에서 확인해보면 Grid는 Flex 대비 브라우저 지원률이 많이 떨어집니다.

- CSS의 비슷한 요소들을 어떤 식으로 정리할 수 있을까요?
  - 부모 요소의 상속을 활용해서 자식 요소의 중복을 줄입니다.
  - 중복되는 요소들을 하나의 클래스에 묶어 재사용합니다.
  - SASS의 mixin을 사용할 수 있습니다.

## Quest (-)

- Quest 01에서 만들었던 HTML을 바탕으로, [이 그림](screen.png)의 레이아웃과 CSS를 최대한 비슷하게 흉내내 보세요. 꼭 완벽히 정확할 필요는 없으나 align 등의 속성은 일치해야 합니다.
- **주의사항: 되도록이면 원래 페이지의 CSS를 참고하지 말고 아무것도 없는 백지에서 시작해 보도록 노력해 보세요!**

## Advanced

- 왜 CSS는 어려울까요?
  - 불필요한 선택자(Selector)의 과용과 연산 기능의 한계, 구문(Statement)의 부재 등의 문제가 있습니다.
- CSS의 어려움을 극복하기 위해 어떤 방법들이 제시되고 나왔을까요?
  - CSS 전처리기(Preprocessor)가 있습니다. 전처리기는 표준 CSS 보다 훨씬 많은 기능을 사용해서 편리하게 작성할 수 있습니다. 전처리기로 작성하고, 웹에서 동작 가능한 표준 CSS로 컴파일합니다.
- CSS가 브라우저에 의해 해석되고 적용되기까지 내부적으로 어떤 과정을 거칠까요?
  - CSS를 파싱해 CSSOM을 생성하고 최종적으로 DOM과 결합해 렌더 트리가 만들어집니다. 렌더 트리는 HTML 요소의 레이아웃을 계산하기 위해 사용되고 픽셀을 렌더링하는 페인팅 처리에 입력됩니다.
- 웹 폰트의 경우에는 브라우저 엔진 별로 어떤 과정을 통해 렌더링 될까요?

  - The default behavior : Lazy loading of fonts (https://web.dev/optimize-webfont-loading)
    1.  The browser requests the HTML document.
    2.  The browser begins parsing the HTML response and constructing the DOM.
    3.  The browser discovers CSS, JS, and other resources and dispatches requests.
    4.  The browser constructs the CSSOM after all of the CSS content is received and combines it with the DOM tree to construct the render tree.
    5.  Font requests are dispatched **"after the render tree indicates which font variants are needed to render the specified text on the page"**.
    6.  The browser performs layout and paints content to the screen.
    7.  If the font is not yet available, the browser may not render any text pixels.
    8.  After the font is available, the browser paints the text pixels.

  - 웹 폰트 최적화 방법 (https://d2.naver.com/helloworld/4969726)
