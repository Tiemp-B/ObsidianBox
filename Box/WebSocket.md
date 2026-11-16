---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 웹
---

# Summary

WebSocket은 클라이언트와 서버 사이에 **하나의 연결을 계속 유지**하면서 양방향으로 데이터를 주고받을 수 있는 통신 프로토콜로, 매번 새 연결을 여는 [[AJAX(Asynchronous JavaScript and XML)]] 폴링보다 실시간 통신에 효율적이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>WebSocket이 폴링보다 효율적인 이유</aside>

- 처음 한 번 HTTP로 연결을 맺은 뒤, 그 연결을 **계속 유지(지속 연결)**하며 서버와 클라이언트 양쪽 모두 원할 때 데이터를 보낼 수 있음
- AJAX 폴링은 갱신할 때마다 새 HTTP 요청·응답 왕복이 필요해 오버헤드가 크지만, WebSocket은 연결을 한 번만 맺으면 이후 오버헤드가 훨씬 작음
- 서버도 클라이언트의 요청 없이 먼저 데이터를 보낼 수 있는 **양방향(full-duplex)** 통신이라는 점이 HTTP 요청-응답과의 핵심 차이

<aside>로봇 모니터링에서의 활용</aside>

로봇 상태를 실시간으로 대시보드에 표시할 때, 매번 새 요청을 보내는 AJAX 폴링보다 WebSocket으로 연결을 유지하며 상태 변화를 즉시 전달받는 방식이 지연·오버헤드 면에서 더 효율적이다.

---

<aside>핵심 정리</aside>

- WebSocket은 연결을 유지하며 양방향으로 데이터를 주고받는 실시간 통신 프로토콜이다
- 매번 새 연결을 여는 AJAX 폴링보다 오버헤드가 작고, 서버도 먼저 데이터를 보낼 수 있다

---

<aside>관련 노트</aside>

- 원 페이지: [[4. WebSocket과 실시간 통신]], [[4. WebSocket과 상태 동기화]], [[2. MQTT·WebSocket과 실시간 모니터링 통신]]
- 관련: [[AJAX(Asynchronous JavaScript and XML)]], [[MQTT]], [[상태 동기화(State Synchronization)]]
