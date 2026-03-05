---
tags:
  - 네트워크
  - 프로토콜
---
# Summary

IPP(Internet Printing Protocol)는 인터넷을 통해 프린터와 클라이언트가 통신하기 위한 표준 프로토콜이다. HTTP를 기반으로 동작하며, 인쇄 작업의 제출·조회·취소 및 프린터 상태 확인 등을 원격으로 수행할 수 있게 해준다. 현재 macOS, Linux, Windows 등 대부분의 운영체제에서 기본 지원된다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>정의</aside>

IPP(Internet Printing Protocol)는 클라이언트(PC, 모바일 등)가 네트워크를 통해 프린터에 인쇄 명령을 전달하기 위한 **애플리케이션 계층 프로토콜**이다. 1999년 IETF에 의해 표준화(RFC 2910, 2911)되었으며, 기존의 LPD, JetDirect 등 레거시 프린팅 프로토콜을 대체하기 위해 설계되었다.

---

<aside>기반 기술</aside>

IPP는 **HTTP/1.1** 위에서 동작한다. 기본 포트는 `631`번이며, 보안 통신 시 TLS를 적용한 **IPPS(IPP over HTTPS)** 를 사용한다. 데이터 인코딩 방식으로는 HTTP의 POST 메서드와 함께 바이너리 인코딩(IPP 자체 포맷)을 사용한다.

|항목|내용|
|---|---|
|기반 프로토콜|HTTP/1.1|
|기본 포트|631|
|보안 버전|IPPS (TLS 적용)|
|표준 문서|RFC 2910, 2911, 8011|

---

<aside>주요 기능</aside>

IPP가 지원하는 핵심 기능들:

- **인쇄 작업 제출**: 문서를 프린터에 전송
- **작업 조회**: 현재 인쇄 큐 및 작업 상태 확인
- **작업 취소**: 진행 중인 인쇄 작업 취소
- **프린터 속성 조회**: 지원 용지 크기, 색상 여부, 해상도 등 확인
- **인증 및 암호화**: 사용자 인증과 데이터 암호화 지원

---

<aside>동작 방식</aside>

1. 클라이언트가 프린터의 IPP URL(`ipp://printer.example.com/printers/myprinter`)로 HTTP POST 요청 전송
2. 요청 본문에 IPP 포맷으로 인코딩된 인쇄 명령 및 문서 데이터 포함
3. 프린터(또는 프린트 서버)가 요청을 파싱하여 인쇄 작업 처리
4. 처리 결과를 IPP 응답으로 클라이언트에 반환

---

<aside>기존 프로토콜과의 비교</aside>

|프로토콜|포트|특징|
|---|---|---|
|LPD/LPR|515|오래된 Unix 기반 프린팅, 기능 제한적|
|JetDirect|9100|HP 전용, 단순 RAW 데이터 전송|
|SMB|445|Windows 파일 공유 기반, 윈도우 환경에 특화|
|**IPP**|**631**|**표준화, 양방향 통신, 보안, 크로스플랫폼**|

---

<aside>활용 사례</aside>

- **CUPS(Common Unix Printing System)**: macOS·Linux의 기본 인쇄 시스템으로 IPP를 핵심 프로토콜로 사용
- **AirPrint**: 애플의 무선 인쇄 기술로 IPP 기반 동작
- **Mopria**: 안드로이드 표준 인쇄 프레임워크도 IPP 사용
- **클라우드 프린팅**: 원격지 프린터에 인터넷으로 직접 인쇄 가능