---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 클라이언트
---

# Summary

REST API는 서버의 자원(resource)을 URI로 표현하고, **HTTP 메서드(GET/POST/PUT/DELETE)의 의미에 맞게 자원을 조회·생성·수정·삭제**하는 방식으로 설계된 웹 API 아키텍처 스타일이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>HTTP 메서드와 자원 조작의 매핑</aside>

| 메서드 | 의미 |
|---|---|
| GET | 자원 조회(서버 상태를 변경하지 않음) |
| POST | 새 자원 생성 |
| PUT | 자원 전체 수정(또는 생성) |
| DELETE | 자원 삭제 |

REST의 핵심 원칙 중 하나는 **무상태성(Stateless)**이다 — 서버는 각 요청을 이전 요청과 무관하게 독립적으로 처리하며, 클라이언트의 상태를 서버에 저장해두지 않는다.

<aside>다른 통신 방식과의 관계</aside>

REST API는 [[요청-응답 모델(Request-Response)]]의 대표적인 구현이며, 서버 상태 변화를 실시간으로 알아야 하는 경우엔 REST의 폴링 방식보다 [[WebSocket]]이나 [[발행-구독 모델(Publish-Subscribe)]] 방식이 더 적합하다.

---

<aside>핵심 정리</aside>

- REST API는 자원을 URI로 표현하고 HTTP 메서드의 의미에 맞게 조작하는 무상태 아키텍처 스타일이다
- GET은 조회 전용이며 서버 상태를 변경하지 않아야 한다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. REST API와 HTTP 메서드]]
- 관련: [[요청-응답 모델(Request-Response)]], [[AJAX(Asynchronous JavaScript and XML)]]
