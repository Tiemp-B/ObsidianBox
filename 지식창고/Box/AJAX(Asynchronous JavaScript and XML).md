---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 클라이언트
---

# Summary

AJAX는 웹 페이지 전체를 새로 고치지 않고, 백그라운드에서 서버와 **비동기적으로 데이터만 주고받아** 화면 일부를 갱신하는 기법이다. 로봇 모니터링 웹 UI에서 로봇 상태 값을 실시간처럼 갱신하는 데 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>AJAX의 핵심 동작 방식</aside>

- 브라우저의 `XMLHttpRequest`(또는 `fetch`) 객체가 페이지 전체 리로드 없이 서버에 요청을 보냄
- 서버는 HTML 전체가 아니라 필요한 데이터(JSON 등)만 응답
- 응답이 오면 JavaScript가 DOM의 해당 부분만 갱신 — 사용자는 페이지가 끊기지 않고 값만 바뀌는 것을 봄

<aside>로봇 모니터링에서의 활용과 한계</aside>

로봇 제어기 상태(배터리, 관절 각도 등)를 대시보드에 표시할 때 일정 주기로 AJAX 요청을 반복(폴링)해 값을 갱신하는 방식이 전통적으로 쓰였다. 다만 매 갱신마다 새 HTTP 요청을 여는 오버헤드가 있어, 더 빈번한 실시간 갱신이 필요하면 [[WebSocket]]처럼 연결을 유지하는 방식이 더 적합하다.

---

<aside>핵심 정리</aside>

- AJAX는 페이지 전체 리로드 없이 필요한 데이터만 비동기로 주고받는 기법이며, 대기 중에도 화면 조작이 가능하다
- 반복 갱신에는 쓸 수 있지만, 매번 새 요청을 여는 폴링 방식이라 진짜 실시간 스트리밍에는 [[WebSocket]]이 더 적합하다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 동기_비동기 통신과 AJAX]]
- 관련: [[WebSocket]], [[REST API(Representational State Transfer)]]
