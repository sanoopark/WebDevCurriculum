# Quest 07. node.js의 기초

## Introduction

- 이번 퀘스트에서는 node.js의 기본적인 구조와 개념에 대해 알아 보겠습니다.

## Topics

- node.js
- npm
- CommonJS와 ES Modules

## Resources

- [About node.js](https://nodejs.org/ko/about/)
- [Node.js의 아키텍쳐](https://edu.goorm.io/learn/lecture/557/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-node-js/lesson/174356/node-js%EC%9D%98-%EC%95%84%ED%82%A4%ED%85%8D%EC%B3%90)
- [npm](https://docs.npmjs.com/about-npm)
- [npm CLI commands](https://docs.npmjs.com/cli/v7/commands)
- [npm - package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json)
- [How NodeJS Require works!](https://www.thirdrocktechkno.com/blog/how-nodejs-require-works)
- [MDN - JavaScript Modules](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Modules)
- [ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)
- [require vs import](https://www.geeksforgeeks.org/difference-between-node-js-require-and-es6-import-and-export/)

## Checklist

- node.js는 무엇인가요? node.js의 내부는 어떻게 구성되어 있을까요?

  - Node.js는 V8 엔진에 비동기 처리 라이브러리인 Libuv를 결합한 자바스크립트 런타임 환경입니다.

    - V8 엔진 : 자바스크립트를 바이트코드로 컴파일하고 실행하는 프로그램
    - 컴파일 : 주어진 언어로 작성된 프로그램을 다른 언어의 동등한 프로그램으로 변환하는 프로세스
    - 바이트코드 : CPU가 아닌 가상 머신에서 이해할 수 있는 이진 코드
    - Libuv : Node.js가 non-blocking I/O operation을 수행할 수 있도록 이벤트 루프를 제공하는 라이브러리
    - [Node.js 이벤트 루프에 대한 문서](https://nodejs.org/ko/docs/guides/event-loop-timers-and-nexttick/)
    - [Node.js 내부 동작 원리에 대해 쉽게 설명한 글](https://sjh836.tistory.com/149)

- npm이 무엇인가요? `package.json` 파일은 어떤 필드들로 구성되어 있나요?

  - Node Package Manager
  - Node.js의 기본 패키지 관리자입니다.
  - 패키지 관리자 : 패키지를 관리하는 작업을 자동화, 안전처리 하기 위해 사용되는 도구
  - 패키지란 : 코드의 배포를 위해서 사용되는 코드의 묶음
  - 라이브러리와의 차이 : 라이브러리는 코드 작성을 위해 필요한 코드의 묶음

  - `package.json` : 확장 모듈을 배포할 때 해당 모듈 정보를 담거나, 애플리케이션을 개발할 때 확장 모듈에 대한 의존성을 관리하기 위해 사용하는 파일

    - `name`
      
      프로젝트 이름으로, 중앙 저장소에 배포할 때 version과 함께 필수 항목입니다.
      url로 사용되고, 설치할 때 디렉토리 이름이 되기 때문에 url이나 디렉터리에서 쓸 수 없는 이름을 사용하면 안 됩니다.
      대문자를 포함해서는 안 되며, require() 함수의 인수로 사용되며 짧고 알기 쉬운 것으로 짓는 것이 좋습니다.

    - `version`
      
      프로젝트 버전을 정의합니다. 3단계 버전을 사용하며, - 로 태그 이름을 적을 수 있습니다.

    - `description`
      
      프로젝트 설명으로, 문자열로 기술합니다.
      npm search로 검색된 리스트에 표시되기 때문에 사람들이 패키지를 찾아내고 이해하는 데 도움이 됩니다.

    - `keywords`
      
      프로젝트를 검색할 때 참조되는 키워드입니다.
      description과 마찬가지로 npm search로 검색된 리스트에 표시됩니다.

    - `homepage`
      
      프로젝트 홈페이지 주소입니다.
      url 항목과는 다르며, url을 설정하면 예상치 못한 움직임을 하게 되므로 주의합니다.

    - `author`
      
      프로젝트 작성자 정보로, 한 사람만을 지정합니다. JSON 형식으로 name, email, url 옵션을 포함합니다.

    - `contributors`
      
      프로젝트에 참여한 공헌자 정보로, 여러 사람을 배열로 지정할 수 있습니다.

    - `repository`
      
      프로젝트의 소스 코드를 저장한 저장소의 정보입니다.
      소스 코드에 참여하고자 하는 사람들에게 도움이 될 수 있습니다. 프로젝트의 홈페이지 url을 명시해서는 안 됩니다.

    - `scripts`
      
      프로젝트에서 자주 실행해야 하는 명령어를 scripts로 작성해두면 npm 명령어로 실행 가능합니다.

    - `config`
      
      소스 코드에서 config 필드에 있는 값을 환경 변수처럼 사용할 수 있습니다.

    - `private`
      
      이 값을 true로 작성하면 중앙 저장소로 저장하지 않습니다.

    - `dependencies`
      
      프로젝트 의존성 관리를 위한 부분입니다. 이 프로젝트가 어떤 확장 모듈을 요구하는지 정리할 수 있습니다.
      애플리케이션을 설치할 때 이 내용을 참조하여 필요한 확장 모듈을 자동으로 설치합니다.
      따라서 개발한 애플리케이션이 특정한 확장 모듈을 사용한다면 여기에 꼭 명시를 해주어야 합니다.
      또한, npm install 명령은 여기에 포함된 모든 확장 모듈들을 설치하게 되어 있습니다.

    - `devDependencies`
      
      개발할 때만 의존하는 확장 모듈을 관리합니다.

    - `engine`
      
      실행 가능한 노드 버전의 범위를 결정합니다.

- npx는 어떤 명령인가요? npm 패키지를 `-g` 옵션을 통해 글로벌로 저장하는 것과 그렇지 않은 것은 어떻게 다른가요?

  - npx : npm의 도구로서, 일회성으로 npm 레지스트리에 있는 패키지를 실행하고 설치하는 CLI 도구

    - `npm run` 없이 `devDependencies`의 패키지를 실행할 때
    - 일회성으로 명령을 실행할 때
    - 다른 노드 버전으로 명령을 실행할 때
    - gist의 스크립트를 실행할 때

  - `-g` 글로벌 옵션

    - 해당 프로젝트 뿐만 아니라 다른 프로젝트에서도 해당 모듈을 사용할 수 있게 시스템 디렉토리에 설치하는 것

- 자바스크립트 코드에서 다른 파일의 코드를 부르는 시도들은 지금까지 어떤 것이 있었을까요? CommonJS 대신 ES Modules가 등장한 이유는 무엇일까요?

  - CJS(CommonJS)

    - `require`, `module.exports`
    - Node.js의 모듈 시스템에 사용됨
    - 모듈을 동기적으로 불러옴

  - ESM(ECMAScript Module)

    - import, export
    - 표준 자바스크립트 모듈 시스템
    - 이전의 모듈 시스템들의 장점들을 채택 (CJS의 문법, AMD의 비동기 로드)
    - 최신 브라우저에서도 모듈 시스템을 사용할 수 있음
      - `<script type="module" src="index.mjs">`

  - ES Moudles가 등장한 이유

    - 최초에는 HTML에 `<script>`를 작성하고, 브라우저에서 이것을 순서대로 로드하는 방식이었습니다.
    - 그런데 중복되지 않는 변수의 이름과 모듈 로드 순서를 고려해야 하는 불편이 있었고 모듈화에 대한 필요성이 부각되었습니다.
    - CJS 방식은 비동기 로드가 아니므로 브라우저에서는 사용할 수 없기 때문에 표준화에 대한 요구로 ES Modules가 등장했습니다.

  - [JavaScript 번들러로 본 조선시대 붕당의 이해](https://wormwlrm.github.io/2020/08/12/History-of-JavaScript-Modules-and-Bundlers.html)

- ES Modules는 기존의 `require()`와 동작상에 어떤 차이가 있을까요? CommonJS는 할 수 있으나 ES Modules가 할 수 없는 일에는 어떤 것이 있을까요?

  - [CommonJS와 ES Modules은 왜 함께 할 수 없는가?](https://yceffort.kr/2020/08/commonjs-esmodules)

- node.js에서 ES Modules를 사용하려면 어떻게 해야 할까요? ES Modules 기반의 코드에서 CommonJS 기반의 패키지를 불러오려면 어떻게 해야 할까요? 그 반대는 어떻게 될까요?

  - 트랜스파일러의 동작처럼 두 모듈 방식을 하나로 통일시켜서 두 모듈을 지원하는 코드로 바꿀 수 있습니다.
  - [You don't know JS module](https://ui.toast.com/weekly-pick/ko_20190418)

## Quest

- 스켈레톤 코드에는 다음과 같은 네 개의 패키지가 있으며, 용도는 다음과 같습니다:
  - `cjs-package`: CommonJS 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `esm-package`: ES Modules 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `cjs-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, CommonJS 기반의 프로젝트입니다.
  - `esm-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, ES Modules 기반의 프로젝트입니다.
- 각각의 패키지의 `package.json`과 `index.js` 또는 `index.mjs` 파일을 수정하여, 각각의 `*-my-project`들이 `*-package`에 노출된 함수와 클래스를 활용할 수 있도록 만들어 보세요.

## Advanced

- node.js 외의 자바스크립트 런타임에는 어떤 것이 있을까요?
