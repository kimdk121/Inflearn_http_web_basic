# Inflearn_http_web_basic
모든 개발자를 위한 HTTP 웹 기본 지식

## 인터넷 네트워크
#### IP
- 지정한 IP 주소에 데이터 전달
- 패킷이라는 통신 단위로 데이터 전달

#### IP 프로토콜의 한계
- 비연결성
  - 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송
- 비신뢰성
  - 패킷 소실 발생
  - 패킷 전달 순서 문제 발생
- 프로그램 구분
  - 같은 IP를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상이면

#### TCP 특징
- 연결지향 - TCP 3 way handshake (가상 연결) - 요청 보냄 > 요청 + 수락 받음 > 수락 보냄
- 데이터 전달 보증
- 순서보장
- 신뢰할 수 있는 프로토콜
- 현재는 대부분 TCP 사용

#### UDP 특징
- 데이터 전달 및 순서가 보장되지 않지만, 단순하고 빠름
- IP와 거의 같다. + PORT + 체크섬 정도만 가능
- 애플리케이션에서 추가 작업 필요

#### PORT
- IP 는 목적지 서버를 찾고, PORT는 그 서버의 애플리케이션을 찾는다.
- FTP - 20, 21
- TELNET - 23
- HTTP - 80
- HTTPS - 443

#### DNS (Domain Name System)
IP는 외우기 어렵기 때문에 도메인을 DNS 서버에 등록해놓으면 IP를 반환해준다.

## URI와 웹 브라우저 요청 흐름
- URI (Uniform Resource Identifier)
  - URL (Uniform Resource Locator)
  - URN (Uniform Resource Name)
- 프로토콜 (HTTPS)
- 호스트명 (www.google.com)
- 포트번호 (443)
- 패스 (/search)
- 쿼리 파라미터 (q=hello&hl=ko)










