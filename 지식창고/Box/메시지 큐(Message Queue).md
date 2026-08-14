---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 서버
---

# Summary

메시지 큐는 송신자와 수신자가 **메시지를 큐(대기열)에 넣고 꺼내는 방식**으로 비동기 통신하는 IPC 메커니즘으로, 송신자와 수신자가 동시에 준비되어 있지 않아도 통신이 가능하다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>메시지 큐의 비동기적 특성</aside>

- 송신자는 메시지를 큐에 넣고 바로 다른 작업을 계속할 수 있음(수신자가 즉시 받을 필요 없음)
- 수신자는 준비가 되었을 때 큐에서 메시지를 꺼내 처리함 — 송신·수신 시점이 정확히 일치하지 않아도 됨
- 이 덕분에 [[IPC(Inter-Process Communication)]]의 여러 방식 중에서도 프로세스 간 결합도를 낮추는 데 유리함

<aside>블로킹 큐와의 관계</aside>

메시지 큐를 구현할 때, 큐가 가득 찼거나 비어 있을 때 송신자·수신자를 대기시키는 [[블로킹 큐(Blocking Queue)]] 자료구조가 내부적으로 활용되는 경우가 많다.

---

<aside>핵심 정리</aside>

- 메시지 큐는 메시지를 큐에 넣고 꺼내는 방식으로 비동기 통신하는 IPC 메커니즘이다

---

<aside>관련 노트</aside>

- 원 페이지: [[6. IPC]]
- 관련: [[IPC(Inter-Process Communication)]], [[블로킹 큐(Blocking Queue)]]
