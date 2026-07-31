---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 클라이언트
---

# Summary

Promise는 비동기 작업이 **아직 끝나지 않았지만 나중에 성공(resolve) 또는 실패(reject)로 결과가 정해질 값**을 표현하는 객체로, 콜백을 중첩하지 않고도 비동기 처리 순서를 명확하게 표현할 수 있게 해준다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Promise의 상태와 콜백 지옥 해결</aside>

- Promise는 대기(pending) → 완료(fulfilled) 또는 실패(rejected) 세 상태 중 하나를 가짐
- 여러 비동기 작업을 순서대로 처리할 때, 콜백 함수를 콜백 안에 계속 중첩시키는 대신 `.then()`을 체이닝해 **평평한 순서로 표현**할 수 있음
- 여러 비동기 작업이 모두 끝나길 기다리거나(`Promise.all`), 하나만 끝나도 되는 경우 등 다양한 조합 방식을 제공

"Promise는 비동기 작업의 결과를 콜백 함수의 중첩 구조로만 표현할 수 있게 하는 방식이다"라는 서술은 오답이다 — Promise의 핵심은 오히려 **콜백 중첩(콜백 지옥) 없이도 `.then()` 체이닝으로 순서를 평평하게 표현**할 수 있게 하는 것이다.

<aside>AJAX와의 관계</aside>

브라우저의 `fetch` API처럼 [[AJAX(Asynchronous JavaScript and XML)]] 방식의 비동기 통신 결과는 흔히 Promise 형태로 반환되어, 응답이 왔을 때 처리할 로직을 `.then()`으로 이어 붙이는 식으로 사용된다.

---

<aside>핵심 정리</aside>

- Promise는 비동기 작업의 미래 결과(성공/실패)를 표현하는 객체로, `.then()` 체이닝으로 콜백 중첩 문제를 해결한다
- 콜백을 중첩시키는 방식이 아니라, 오히려 그 문제를 해결하기 위한 대안이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 동기_비동기 통신과 AJAX]]
- 관련: [[AJAX(Asynchronous JavaScript and XML)]], [[이벤트 루프(Event Loop)]]
