# Quest 06. 인터넷의 이해

## Introduction

- 이번 퀘스트에서는 인터넷이 어떻게 동작하며, 서버와 클라이언트, 웹 브라우저 등의 역할은 무엇인지 알아보겠습니다.

## Topics

- 서버와 클라이언트, 그리고 웹 브라우저
- 인터넷을 구성하는 여러 가지 프로토콜
  - IP
  - TCP
  - HTTP
- DNS

## Resources

- [OSI 모형](https://ko.wikipedia.org/wiki/OSI_%EB%AA%A8%ED%98%95)
- [IP](https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%EB%84%B7_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
  - [Online service Traceroute](http://ping.eu/traceroute/)
- [TCP](https://ko.wikipedia.org/wiki/%EC%A0%84%EC%86%A1_%EC%A0%9C%EC%96%B4_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
  - [Wireshark](https://www.wireshark.org/download.html)
- [HTTP](https://ko.wikipedia.org/wiki/HTTP)
  - Chrome developer tool, Network tab
- [DNS](https://ko.wikipedia.org/wiki/%EB%8F%84%EB%A9%94%EC%9D%B8_%EB%84%A4%EC%9E%84_%EC%8B%9C%EC%8A%A4%ED%85%9C)
  - [Web-based Dig](http://networking.ringofsaturn.com/Tools/dig.php)

## Checklist

- Internet Protocol Suite란 무엇일까요? (+)

  - 인터넷에서 컴퓨터들이 서로 정보를 주고받는 데 쓰이는 프로토콜의 모음
  - 인터넷 프로토콜 스위트 중 TCP와 IP가 가장 많이 쓰이기 때문에 TCP/IP 프로토콜 스위트라고도 불림
    - TCP/IP ?
      - TCP/IP = IP(패킷 통신 방식의 인터넷 프로토콜) + TCP(전송 제어 프로토콜)
      - https://youtu.be/Fh1GAi63CfA

- 인터넷은 어떻게 동작하나요? Internet Protocol Suite의 레이어 모델에 입각하여 설명해 보세요. (?)

  - 근거리에서 서로 떨어진 두 전자기기가 유선/무선으로 서로 통신하는 프로토콜은 어떻게 동작할까요?
  - 근거리에 있는 여러 대의 전자기기가 서로 통신하는 프로토콜은 어떻게 동작할까요?
  - 아주 멀리 떨어져 있는 두 전자기기가 유선/무선으로 서로 통신하는 프로토콜은 어떻게 동작할까요?
  - 두 전자기기가 신뢰성을 가지고 통신할 수 있도록 하기 위한 프로토콜은 어떻게 동작할까요?
  - HTTP는 어떻게 동작할까요?

- 우리가 브라우저의 주소 창에 www.knowre.com 을 쳤을 때, 어떤 과정을 통해 서버의 IP 주소를 알게 될까요?

  1. 사용자가 웹 브라우저를 통해 찾고 싶은 웹 페이지의 URL 주소를 입력함
  2. 캐싱된 DNS 기록들을 통해 URL의 도메인 네임과 대응되는 IP 주소가 있는지 확인함
     - 브라우저 캐시
     - OS 캐시
     - Router 캐시
     - ISP 캐시 (ISP는 DNS 서버를 구축하고 있음)
  3. 캐싱된 DNS 기록이 없으면 URL의 도메인 네임을 DNS 서버에 검색함
     - DNS(Doman Name System)
       - 도메인 네임과과 IP 주소를 저장하고 있는 데이터베이스 (전화번호부)
       - 사람들이 웹사이트 주소에 쉽게 접속할 수 있게 매핑을 해주는 역할
     - ISP의 DNS 서버가 www.knowre.com 을 호스팅하고 있는 서버의 IP 주소를 찾기 위해 DNS query를 날림
  4. 브라우저가 IP 주소를 받으면 인터넷 프로토콜(TCP)을 통해 서버와 연결됨
  5. HTTP를 통해 HTTP 요청 메시지를 생성하고, TCP를 통해 해당 IP 주소로 요청을 전송함
  6. 웹 서버는 도착한 HTTP 요청 메시지의 URL을 통해 해당하는 데이터를 검색함
  7. HTTP를 통해 HTTP 응답 메시지를 생성하고 TCP를 통해 응답함
  8. 브라우저에서 응답 받은 정적 파일을 브라우저 엔진이 렌더링해서 화면에 나타냄

## Quest (?)

- tracert(Windows가 아닌 경우 traceroute) 명령을 통해 www.google.com 까지 가는 경로를 찾아 보세요.
  - 어떤 IP주소들이 있나요?
  - 그 IP주소들은 어디에 위치해 있나요?
- Wireshark를 통해 www.google.com 으로 요청을 날렸을 떄 어떤 TCP 패킷이 오가는지 확인해 보세요
  - TCP 패킷을 주고받는 과정은 어떻게 되나요?
  - 각각의 패킷에 어떤 정보들이 담겨 있나요?
- telnet 명령을 통해 http://www.google.com/ URL에 HTTP 요청을 날려 보세요.
  - 어떤 헤더들이 있나요?
  - 그 헤더들은 어떤 역할을 하나요?

## Advanced (?)

- HTTP의 최신 버전인 HTTP/3는 어떤 식으로 구성되어 있을까요?
- TCP/IP 외에 전세계적인 네트워크를 구성하기 위한 다른 방식도 제안된 바 있을까요?
