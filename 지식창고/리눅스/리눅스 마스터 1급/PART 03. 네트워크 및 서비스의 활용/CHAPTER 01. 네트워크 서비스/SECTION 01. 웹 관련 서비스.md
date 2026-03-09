# 1. 웹의 개념과 구성요소
## 웹의 개념
- 다양한 시스템이 인터넷으로 상호 연결되어 데이터를 공유하는 서비스
- 웹 브라우저를 사용하여 하이퍼텍스트 형식으로 구성된 웹 문서를 탐색

## 웹의 구성 요소
### 웹 문서(HTML)
- HTML은 W3C(World Wide Web Consortium. 웹 표준을 개발하는 국제 컨ㅗ시엄)에서 주관하여 관리
- .html 확장자를 가진 HTML 문서와 .php, .jsp, .asp 등의 확장자를 가진 동적 문서로 구성
- 동적 웹 문서는 PHP, 자바 서블릿, 파이썬 등의 외부 모듈에 의해 동적으로 생성
- HTML 문서에 자바 스크립트와 같은 프로그램 루틴을 추가하여 기능을 추가할 수 있다
### 웹 서버
- 웹 브라우저(클라이언트)의 요청에 따라 웹 문서를 전달하는 서비스 프로그램
- Apache, IIS, Nginx, GWS 등의 웹서버가 존재
	- Apache 
		- 아파치 재단이 주도하는 대표적 오픈소스 웹 서버
		- 요청에 따라 프로세스, 스레드를 생성하여 처리
		- Loadable Module 기능을 제공하여 서버의 동작 확장 가능
	- IIS
		- 마이크로소프트가 개발 및 제공
		- 마이크로소프트 ASP(Active Server Page)를 지원
		- GUI기반의 관리콘솔 제공
	- Nginx
		- NGINX가 개발 및 제공. 비동기 이벤트 방식으로 동작
		- 로드밸런스, HTTP 캐시, 리버스 프록시 등의 기능을 기본으로 제공
	- GWS
		- 구글이 제공한는 웹서버
- 최근의 웹서버는 동적 페이지, 로그인 및 세션 관리, 다중 웹 호스팅, QoS(Quality of Service) 제한 등의 다양한 기능을 제공한다
- MSA : Micro Service Architecture
	- 많은 서비스들이 웹을 기반으로 동작하며 이를 효과적으로 개발, 운영하는 것이 중요
	- 이를 위한 개발 방법론, 설계 기법이 MSA
	- 마이크로 서비스 아키텍처는 전체 서비스를 작은 단위의 독립적 서비스로 설계 및 구현한 후, 상호 연동하는 방식으로 서비스를 개발
### 웹 브라우저
사용자의 요청을 웹 서버에 전달하고 필요한 데이터 및 컨텐츠를 표시
- 파이어폭스
- 크롬
- 오페라
- 엣지
- 사파리
### HTTP 프로토콜
웹 브라우저와 웹서버의 상호 통신용 프로토콜
데이터를 요청 및 전송하기 위한 표준 규약

## 웹의 발전 동향
### 웹 1.0
- 1990년대의 정적 HTML 중심
- 웹 사이트를 체계적으로 분류한 디렉터리 기반 검색
### 웹 2.0
- 2004년 오라일리가 주창한 참여, 공유, 개방 중심의 웹
- 위키피디아와 같은 집단 지성을 활용한 서비스
- 웹이 서비스 플랫폼으로 확장되는 계기가 되었다
### 웹 3.0
- 시멘틱 웹 기술을 기반으로 지능형 웹
- 자원을 관계와 의미 정보로 처리할 수 있는 온톨로지로 표현
- 맞춤형 콘텐츠 및 서비스 제공

# 2. 웹의 동작 원리와 HTTP 프로토콜
## 웹의 동작 원리
### 기본 구조
- 방화벽
- 웹서버
- WAS:Web Application Server
- DB
### 동작 원리
1. 주소 입력
2. DNS 조회를 통해 IP 변환
3. TCP 3way 연결로 웹 서버에 연결 요청. HTTP의 경우 80, HTTPS는 443 포트를 사용한다
4. HTTP 프로토콜로 웹 서버에 요청을 한다
5. show.php는 서버에서 실행되는 기능으로, 관련 기능에 따라 WAS와 상호 연동한다.
6. 웹 서버는 최종 정보를 웹 브라우저에 응답하고, 웹 브라우저는 전송 받은 내용을 표시
7. TCP 4way 연결 종료 방식으로 연결 종료
## HTTP 프로토콜
HyperText Transfer Protocol
웹 클라이언트와 웹 서버 사이의 데이터 요청/전송 표준 규약
### 요청 메소드
- GET
- HEAD
- POST
- PUT
- DELETE
- CONNECT
- TRACE
- OPTIONS
### HTTP 응답, 응답 코드
응답으로 웹 서버는 HTTP 프로토콜 버전, 웹서버 정보, 상태코드, 데이터 정보 등을 전송한다

상태코드는 HTTP 규약(RFC2616)에 정의된 값으로, 응답 정보 및 서버의 상태 확인이 가능
- HTTP 상태 코드
	1xx (조건부 응답, 정보 교환)
	- 100 : Continue
	- 101 : Switching Protocols
	2xx (성공)
	- 200 : complete
	- 201 : Created
	- 202 : Accepted
	- 203 : Non-Authoritative Info
	- 204 : No Content
	- 205 : Reset Content
	- 206 : Partial Content
	3xx (리다이렉션)
	- 300 : Multiple Choices
	- 301 : Moved Permanently
	- 302 : Moved Temporary
	- 303 : See Other
	- 304 : Not Modified
	- 305 : Use Proxy
	4xx (요청 오류)
	- 400 : 클라이언트의 잘못된 요청(문법 오류 등)
	- 401 : 요청에 대한 권한 부족
	- 402 : 결재 필요한 요청
	- 403 : 리소스에 대한 권한 부족
	- 404 : 존재하지 않는 리소스 
	- 405 : 지정 방식의 요청 불가
	- 406 : 불가
	- 407 : 프록시 인증 필요
	- 408 : 요청 시간 초과
	- 409 : 충돌
	- 410 : Gone
	- 411 : Length Required
	- 412 : Precondition Failed
	- 413 : Request Entity Too Large
	- 414 : Request URI Too Large
	- 415 : Unsupported Media Type
	5xx (서버 오류)
	- 500 : 서버 내부 오류
	- 501 : Not Implemented
	- 502 : Bad Gateway
	- 503 : Service Unavailable
	- 504 : Gateway Timeout
	- 505 : HTTP Version Not Supported
### HTTP 헤더 구조
프로토콜의 요청과 응답은 헤더(부가 정보)와 바디(실 데이터)로 구성된다
헤더와 바디는 `\r\n`의 개행문자로 구분된다

헤더의 종류
- 공통 헤더
	- Date : 메시지 생성한 일시. `Tue, 19 Nov 2019 04:13:24 GMT`
	- Connection : Keep-Alive 설정
	- Cache-Control : 캐시 속성 설정
		- no-store
		- no-cache
		- must-revalidate
		- public
		- private
		- max-age
		- 등
	- Content-Type
	- Content-Encoding
	- Content-Length

- 요청 헤더
	- Method, URL, HTTP 버전 : `Get /example/test.html HTTP/1.1`
	- Accept : 

























