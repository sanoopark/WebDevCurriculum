# Quest 16-F. 컴포넌트 기반 개발

## Introduction

- 이번 퀘스트에서는 Vue.js 프레임워크를 통해 컴포넌트 기반의 웹 클라이언트 개발 방법론을 더 자세히 알아보겠습니다.

## Topics

- Vue.js framework
- vuex
- Virtual DOM

## Resources

- [Vue.js](https://vuejs.org)
  - [Lifecycle Hooks](https://v3.vuejs.org/guide/composition-api-lifecycle-hooks.html)
  - [State Management](https://v3.vuejs.org/guide/state-management.html)
  - [Virtual DOM](https://v3.vuejs.org/guide/optimizations.html#virtual-dom)

## Checklist

### # Vue.js는 어떤 특징을 가지고 있는 웹 프레임워크인가요?

- MVVM 패턴의 ViewModel 레이어를 담당하는 화면단 라이브러리
- ViewModel? 서버의 데이터를 View로 넘겨주는 중간 지점

### # Vue.js는 내부적으로 어떤 식으로 동작하나요?

- Virtual Dom을 사용하는 Reactivity System에서 업데이트 되기 전의 스냅샷과 비교해 실제 DOM에 변경사항을 반영합니다.

### # Vue.js에서의 컴포넌트란 무엇인가요?

- 화면의 영역을 일정한 단위로 쪼개어 재활용 가능한 형태로 관리하는 것

### # Vue 컴포넌트의 라이프사이클은 어떤 식으로 호출되나요? (-)

### # 컴포넌트 간에 데이터를 주고받을 때 단방향 바인딩과 양방향 바인딩 방식이 어떻게 다르고, 어떤 장단점을 가지고 있나요?

- 데이터 바인딩 : View와 Model을 하나로 연결하는 것
- View : 사용자가 화면에서 보는 것들에 대한 구조, 배치, 외관
- ViewModel : Model의 데이터를 가공해서 View에 제공하는 레이어
- View와 ViewModel을 분리해야 하는 이유? 분리하지 않고 DOM을 직접 조작하는 기존 방식에서는 View가 변경되면 ViewModel의 로직도 변경될 가능성이 높습니다.
- 단방향 데이터 바인딩
  - ViewModel에서 View로 데이터 흐름이 단방향으로 이루어지는 방식
  - View의 변경 사항을 ViewModel에 반영하기 위해 이벤트를 사용하는 방식
  - 장점 : 데이터 흐름이 단방향이므로 데이터 추적과 디버깅이 비교적 쉽습니다.
  - 단점 : 변화를 감지하고 화면을 업데이트 하는 코드를 매번 작성해야 합니다.
- 양방향 데이터 바인딩
  - 부모와 자식 간 데이터 흐름이 양방향으로 이루어지는 방식
  - View의 변경 사항이 ViewModel에 즉각적으로 반영되는 방식
  - 장점 : 코드량을 크게 줄여줘 비교적 유지보수가 쉽습니다.
  - 단점 : 데이터의 변경을 프레임워크에서 감지하고 있다가, 데이터가 변경되는 시점에 리렌더링 되기 때문에 성능 저하가 있을 수 있습니다.

### # Vue.js 기반의 웹 어플리케이션을 위한 상태관리 라이브러리에는 어떤 것이 있을까요? 이러한 상태관리 툴을 사용하는 것에는 어떤 장단점이 있을까요? (-)

## Quest

- Vue.js를 통해 메모장 시스템을 다시 한 번 만들어 보세요.
  - 어떤 컴포넌트가 필요한지 생각해 보세요.
  - 각 컴포넌트별로 해당하는 CSS와 자바스크립트를 어떤 식으로 붙여야 할까요?
  - Vue.js 시스템에 타입스크립트는 어떤 식으로 적용할 수 있을까요?
  - 컴포넌트간에 데이터를 주고받으려면 어떤 식으로 하는 것이 좋을까요?
  - `vue-cli`와 같은 Vue의 Boilterplating 기능을 이용하셔서 세팅하시면 됩니다.

## Advanced

- React와 Angular는 어떤 프레임워크이고 어떤 특징을 가지고 있을까요? Vue와는 어떤 점이 다를까요?
- Web Component는 어떤 개념인가요? 이 개념이 Vue나 React를 대체하게 될까요?
- Reactive Programming이란 무엇일까요?
