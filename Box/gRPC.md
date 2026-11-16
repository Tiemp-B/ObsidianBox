---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 미들웨어
---

# Summary

gRPC는 Google이 개발한 오픈소스 원격 프로시저 호출(RPC) 프레임워크로, HTTP/2와 Protocol Buffers를 기반으로 REST/JSON 방식보다 가볍고 빠른 통신을 제공한다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>gRPC의 핵심 구성 요소</aside>

- **HTTP/2**: 하나의 연결로 여러 요청·응답을 동시에 주고받을 수 있는 전송 계층을 사용해, HTTP/1.1 기반 통신보다 오버헤드가 적음
- **Protocol Buffers(protobuf)**: 텍스트 기반의 JSON과 달리, 메시지를 **이진(binary) 형식으로 직렬화**해 전송 크기를 줄이고 파싱 속도를 높임
- 서비스 정의(.proto 파일)를 작성하면 여러 프로그래밍 언어로 **클라이언트·서버 코드를 자동 생성**할 수 있어 언어가 다른 시스템 간에도 쉽게 연동 가능

<aside>로봇·분산 시스템에서의 활용</aside>

여러 대의 로봇, 백엔드 서비스, 모바일 앱을 연결하는 마이크로서비스 구조에서 gRPC를 원격 호출 수단으로 활용하는 사례가 많다. 언어가 다른 컴포넌트(예: C++ 로봇 제어 노드와 Python 백엔드) 간에도 자동 생성된 코드로 쉽게 통신을 구현할 수 있다.

---

<aside>핵심 정리</aside>

- gRPC는 HTTP/2와 Protocol Buffers(이진 직렬화)를 기반으로 하는 현대적인 RPC 프레임워크다
- REST/JSON 방식보다 가볍고 빠르며, 여러 언어의 클라이언트·서버 코드를 자동 생성할 수 있다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 미들웨어의 개념과 종류]]
- 관련: [[미들웨어(Middleware)]]
