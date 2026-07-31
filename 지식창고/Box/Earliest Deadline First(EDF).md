---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 스케줄링
  - 실시간시스템
---

# Summary

EDF(Earliest Deadline First)는 실시간 스케줄링 알고리즘으로, 매 순간 **마감시한(deadline)이 가장 임박한 작업에 최우선순위**를 동적으로 부여해 CPU를 할당한다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>EDF의 동작 방식</aside>

- 각 작업에 고정된 우선순위를 미리 부여하지 않고, 실행 중에도 **남은 마감시한이 짧아질수록 우선순위가 계속 재계산됨**(동적 우선순위)
- 이론적으로 CPU 이용률이 100%에 가까워도 모든 작업의 마감시한을 만족시킬 수 있음이 증명되어 있어, [[Rate Monotonic Scheduling]]보다 이론적 스케줄링 가능 이용률이 높음
- 다만 과부하 상태(스케줄링 불가능한 상황)에서는 어떤 작업이 마감을 놓칠지 예측하기 어렵다는 단점이 있음

"EDF는 작업 생성 시점에 정해진 고정 우선순위를 실행 내내 그대로 유지하는 정적 스케줄링 방식이다"라는 서술은 오답이다 — EDF의 핵심은 오히려 **마감시한에 따라 우선순위가 실행 중에도 동적으로 바뀐다**는 점이며, 고정 우선순위는 Rate Monotonic 같은 정적 스케줄링의 특징이다.

<aside>Rate Monotonic과의 비교</aside>

[[Rate Monotonic Scheduling]]은 주기가 짧은 작업일수록 고정된 높은 우선순위를 부여하는 정적 방식인 반면, EDF는 마감시한 임박도에 따라 우선순위가 계속 바뀌는 동적 방식이다 — 이론적 스케줄링 가능 이용률은 EDF가 더 높지만, 구현 복잡도와 과부하 시 예측 가능성 면에서는 Rate Monotonic이 산업 현장에서 더 선호되기도 한다.

---

<aside>핵심 정리</aside>

- EDF는 마감시한이 가장 임박한 작업에 동적으로 최우선순위를 부여하는 실시간 스케줄링 알고리즘이다
- 고정 우선순위 방식(Rate Monotonic)과 달리 우선순위가 실행 중 계속 재계산된다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 실시간 운영체제와 스케줄링]]
- 관련: [[Rate Monotonic Scheduling]], [[WCET(Worst Case Execution Time)]]
