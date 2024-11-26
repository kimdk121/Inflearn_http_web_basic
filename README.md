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
- 프로토콜 (HTTPS) - 호스트명 (www.google.com) - 포트번호 (443) - Path (/search) - 쿼리 파라미터 (q=hello&hl=ko)

## HTTP 기본
#### HTTP (HyperText Transfer Protocol)
- HTML, TEXT
- IMAGE, 음성, 영상, 파일
- JSON, XML (API)
- 거의 모든 형태의 데이터 전송 가능, 서버간 데이터를 주고 받을 때도 대부분 HTTP 사용

#### 기반 프로토콜
- TCP : HTTP/1.1, HTTP/2
- UDP : HTTP/3
현재는 HTTP/1.1을 주로 사용하지만 HTTP/2, HTTP/3도 사용이 증가하는 중

#### HTTP 특징
- 클라이언트 서버 구조
  - Request Response 구조
  - 클라이언트는 서버에 요청을 보내고, 응답을 대기
  - 서버가 요청에 대한 결과를 만들어서 응답
- 무상태 프로토콜(Stateless)
  - 상태를 유지하지 않아 응답 서버를 쉽게 변경할 수 있어 무한하게 서버증설이 가능
  - 대용량 트래픽에 관련된 부분이라 중요함!
- 비연결성
  - 기본적인 연결을 유지하지 않는다
  - 1시간 동안 수천명이 서비스를 사용해도 실제 서버에서 동시에 처리하는 요청은 수십개 이하로 매우 작음
  - 서버 자원을 매우 효율적으로 사용할 수 있음
- HTTP 메세지 구성
  - start-line
  - header
  - empty line
  - message body
- 단순함 + 확장가능

#### HTTP 메서드 종류
- GET : 리소스 조회
- POST : 요청 데이터 처리, 주로 등록에 사용
- PUT : 리소스를 대체, 해당 리소스가 없으면 생성
- PATCH : 리소스 부분 변경
- DELETE : 리소스 삭제

#### 클라이언트에서 서버로 데이터 전송
- 쿼리 파라미터를 통한 데이터 전송
  - GET
  - 주로 정렬 필터 (검색어)
- 메시지 바디를 통한 데이터 전송
  - POST, PUT, PATCH
  - 회원 가입, 상품 주문, 리소스 등록, 리소스 변경

#### 4가지 상황
- 정적 데이터 조회
  - 이미지, 정적 텍스트 문서
  - GET 사용
  - 쿼리 파라미터 미사용
- 동적 데이터 조회
  - 주로 검색, 게시판 목록에서 정렬 필터 (검색어)
  - GET 사용
  - 조회 조건을 줄여주는 필터, 조회 결과를 정렬하는 정렬 조건에 주로 사용
  - GET은 쿼리 파라미터를 사용해서 데이터를 전달
- HTML Form을 통한 데이터 전송
  - 회원 가입, 상품 주문, 데이터 변경
  - POST 사용
  - GET 사용 (HTML FORM 에서 사용 가능 => 쿼리파라미터로 들어감)
  - Content-Type : x-www-form-urlencoded (기본타입)
  - Content-Type : multipart/form-data (바이트전송)
- HTTP API를 통한 데이터 전송
  - 회원 가입, 상품 주문, 데이터 변경
  - 통신
    - 서버 to 서버
      - 백엔드 시스템 통신
    - 앱 클라이언트
      - 아이폰, 안드로이드
    - 웹 클라이언트
      - HTML에서 Form 전송 대신 자바 스크립트를 통한 통신에 사용 (Ajax)
      - React, VueJs 같은 웹 클라이언트와 API 통신 
  - GET 사용 (HTML FORM 에서 사용 가능 => 쿼리파라미터로 들어감)
  - Content-Type : application/json을 주로 사용 (사실상 표준)






































