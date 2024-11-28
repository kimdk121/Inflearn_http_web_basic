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

## HTTP 메서드
#### HTTP 메서드 종류
- GET : 리소스 조회
- POST : 요청 데이터 처리, 주로 등록에 사용
- PUT : 리소스를 대체, 해당 리소스가 없으면 생성
- PATCH : 리소스 부분 변경
- DELETE : 리소스 삭제

## HTTP 메서드 활용
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

#### 회원 관리 시스템
- 회원 목록 /members -> GET
- 회원 등록 /members -> POST
- 회원 조회 /members/{id} -> GET
- 회원 수정 /members/{id} -> PATCH, PUT, POST
- 회원 삭제 /members/{id} -> DELETE

#### 파일 관리 시스템
- 파일 목록 /files -> GET
- 파일 조회 /files/{filename} -> GET
- 파일 등록 /files/{filename} -> PUT
- 파일 삭제 /files/{filename} -> DELETE
- 파일 대량 등록 /files -> POST

- 컬렉션
  - POST 기반
    - 클라이언트는 등록될 리소스의 URI를 모른다.
    - 서버가 새로 등록된 리소스 URI를 생성해준다.
    - 서버가 관리하는 리소스 디렉토리
- 스토어
  - PUT 기반
    - 클라이언트가 리소스 URI를 알고 있어야 한다.
    - 클라이언트가 직접 리소스의 URI를 지정한다.
    - 클라이언트가 관리하는 리소스 저장소
- 컨트롤 URI
  - GET, POST 기반
    - HTML FORM은 GET, POST만 사용하니까 제약이 있음
    - 이 제약을 해결하기 위해 동사로 된 리소스 경로 사용
    - HTTP 메서드로 해결하기 애매한 경우 사용

## HTTP 상태코드
#### 상태코드
- 1xx (Informational) : 요청이 수신되어 처리중
  - 거의 사용하지 않음
- 2xx (Successful) : 요청 정상 처리
  - 200 OK
  - 201 Created
  - 202 Accepted : 요청이 접수 되었으나 처리가 완료되지 않음
    - 배치 처리 같은 곳에서 사용
  - 204 No Content : 서버가 요청을 성공적으로 수행했지만, 응답 페이로드 본문에 보낼 데이터가 없음
    - 웹 문서 편집기에서의 save 버튼 (같은 화면을 유지해야 함)
- 3xx (Redirection) : 요청을 완료하려면 추가 행동이 필요
  - 리다이렉션
    - 영구 리다이렉션 : 특정 리소스의 URI가 영구적으로 이동
      - /members -> /users 라거나 /event -> /new-event
      - 301 Moved Permanently
        - 리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음(MAY)
      - 308 Permanent Redirect
        - 301과 기능은 같음
        - 리다이렉트시 요청 메서드와 본문 유지 (처음 POST를 보내면 리다이렉트도 POST)
    - 일시 리다이렉션 : 일시적인 변경
      - 주문 완료 후 주문 내역 화면으로 이동
      - 302 Found
        - 리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음(MAY)
      - 303 See Other
        - 302와 기능은 같음
        - 리다이렉트시 요청 메서드가 GET으로 변경
      - 307 Temporary Redirect
        - 302와 기능은 같음
        - 리다이렉트시 요청 메서드와 본문 유지 (요청 메서드를 변경하면 안된다. MUST NOT)
      - Post/Redirect/Get
        - Post로 주문후에 새로 고침으로 인한 중복 주문 방지
        - POST로 주문후에 주문 결과 화면을 GET 메서드로 리다이렉트
        - 새로고침해도 결과 화면을 GET으로 조회
        - 중복 주문 대신에 결과 화면만 GET으로 다시 요청
    - 특수 리다이렉션
      - 결과 대신 캐시를 사용
    - 기타 리다이렉션
      - 300 Multiple Choices : 안쓴다
      - 304 Not Modified
        - 캐시를 목적으로 사용
        - 클라이언트에게 리소스가 수정되지 않았음을 알려준다. 따라서 클라이언트는 로컬 PC에 저장된 캐시를 재사용한다. (캐시로 리다이렉트 한다.)
        - 304 응답은 응답에 메시지 바디를 포함하면 안된다. (로컬 캐시를 사용해야 하므로)
        - 조건부 GET, HEAD 요청시 사용
- 4xx (Client Error) : 클라이언트 오류, 잘못된 문법 등으로 서버가 요청을 수행할 수 없음
  - 400 Bad Request : 클라이언트가 잘못된 요청을해서 서버가 요청을 처리할 수 없음
    - 요청 구문, 메시지 등등 오류
    - 클라이언트는 요청 내용을 다시 검토하고 보내야함
  - 401 Unauthorized : 클라이언트가 해당 리소스에 대한 인증이 필요함
    - 인증 (Authentication) : 본인이 누구인지 확인 (로그인)
    - 인가 (Authorization) : 권한 부여
  - 403 Forbidden : 서버가 요청을 이해했지만 승인을 거부함
    - 인증 자격 증명은 있지만 접근 권한이 불충분한 경우
  - 404 Not Found : 요청 리소스를 찾을 수 없음
    - 요청 리소스가 서버에 없음
- 5xx (Server Error) : 서버 오류, 서버가 정상 요청을 처리하지 못함
  - 500 Internal Server Error : 서버 문제로 오류 발생
    - 서버 내부 문제로 오류 발생
  - 503 Service Unavailable : 서비스 이용 불가
    - 서버가 일시적인 과부하 또는 예정된 작업으로 잠시 요청을 처리할 수 없음
    - Retry-After 헤더 필드로 얼마뒤에 복구되는지 보낼 수 있음

































