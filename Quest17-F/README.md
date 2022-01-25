# Quest 17-F. 번들링과 빌드 시스템

## Introduction

- 이번 퀘스트에서는 현대적 웹 클라이언트 개발에 핵심적인 번들러와 빌드 시스템의 구조와 사용 방법에 대해 알아보겠습니다.

## Topics

- Webpack
- Bundling
  - Data URL
- Transpiling
  - Source Map
- Hot Module Replacement

## Resources

- [Webpack](https://webpack.js.org/)
- [Webpack 101: An introduction to Webpack](https://medium.com/hootsuite-engineering/webpack-101-an-introduction-to-webpack-3f59d21edeba)

## Checklist

### # 여러 개로 나뉘어진 파일들을 하나로 합치는 작업은 성능 상 어떤 이점이 있을까요?

- 파일을 하나로 합치기 때문에 HTTP 요청을 줄여줍니다.

### # 이미지를 Data URL로 바꾸어 번들링하는 것은 어떤 장점과 단점이 있을까요?

- 장점

  - 서버에 이미지를 요청하지 않아도 되므로 간단한 구현이 가능합니다.
  - 이미지가 최초 렌더링에 포함될 수 있습니다.

- 단점

  - 코드 가독성을 떨어뜨립니다.
  - Base64 인코딩은 8비트를 6비트로 표현하는 것이므로 원본 크기보다 33% 커집니다.
  - 캐싱이 안 되므로 성능에 좋지 않습니다.

### # Source Map이란 무엇인가요? Source Map을 생성하는 것은 어떤 장점이 있을까요?

- Source Map은 배포용으로 빌드한 파일과 원본 파일을 서로 연결시켜주는 기능입니다.
- Webpack을 통해 하나의 파일로 합쳐지면 어떠한 부분에서 에러가 발생했을 때 디버깅하기 매우 어려운데, Source Map을 이용하여 배포용 파일의 특정 부분이 원본 소스의 어떤 부분인지 확인할 수 있습니다.

### # Webpack의 필수적인 설정은 어떤 식으로 이루어져 있을까요?

- [Webpack Getting Started](https://webpack.js.org/guides/getting-started/)

### # Webpack의 플러그인과 모듈은 어떤 역할들을 하나요?

- [웹팩 핸드북 플러그인](https://joshua1988.github.io/webpack-guide/concepts/plugin.html)

### # Webpack을 이용하여 HMR(Hot Module Replacement) 기능을 설정하려면 어떻게 해야 하나요?

- HMR은 브라우저를 새로 고치지 않아도 웹팩으로 빌드한 결과물이 웹 애플리케이션에 실시간으로 반영될 수 있게 도와주는 설정입니다. 브라우저 새로 고침을 위한 LiveReload 대신에 사용할 수 있으며 웹팩 데브 서버와 함께 사용할 수도 있습니다.
- `module.exports = { devServer: { hot: true } }`

## Quest

- 직전 퀘스트의 소스만 남기고, Vue의 Boilerplating 기능을 쓰지 않고 Webpack 관련한 설정을 원점에서 다시 시작해 보세요.
  - 필요한 번들링과 Source Map, HMR 등의 기능이 모두 잘 작동해야 합니다.

## Advanced

- Webpack 이전과 이후에는 어떤 번들러가 있었을까요? 각각의 장단점은 무엇일까요?
