---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 소프트웨어시험
  - 신뢰성
---

# Summary

MTBF(평균 고장 간격)와 MTTR(평균 수리 시간)은 시스템의 신뢰성·유지보수성을 정량적으로 나타내는 대표적인 지표로, 둘을 함께 쓰면 시스템 가용성(Availability)을 계산할 수 있다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>MTBF(Mean Time Between Failures)</aside>

수리 가능한 시스템이 고장과 고장 사이 정상 동작한 **평균 시간**이다.

$$\text{MTBF} = \frac{\text{총 가동시간}}{\text{고장 횟수}}$$

값이 **클수록** 자주 고장 나지 않는, 신뢰성이 높은 시스템이다.

<aside>MTTR(Mean Time To Repair)</aside>

고장이 발생한 뒤 다시 정상 가동되기까지 걸리는 **평균 시간**이다.

$$\text{MTTR} = \frac{\text{총 다운타임}}{\text{고장 횟수}}$$

값이 **작을수록** 고장이 나도 빨리 복구되는, 유지보수성이 좋은 시스템이다.

"MTBF는 값이 작을수록, MTTR은 값이 클수록 좋은 시스템이다"라는 서술은 두 지표의 방향을 뒤바꾼 오답이다 — MTBF는 **클수록**(자주 안 고장), MTTR은 **작을수록**(빨리 복구) 좋다.

<aside>가용성(Availability)과의 관계</aside>

두 지표를 함께 쓰면 시스템이 정상 동작하는 시간 비율인 가용성을 계산할 수 있다.

$$\text{Availability} = \frac{\text{MTBF}}{\text{MTBF} + \text{MTTR}}$$

같은 MTBF라도 MTTR이 작을수록(빨리 고치면) 가용성이 높아진다.

---

<aside>핵심 정리</aside>

- MTBF(평균 고장 간격)는 클수록, MTTR(평균 수리 시간)은 작을수록 좋은 시스템이다
- 가용성 = MTBF / (MTBF + MTTR)로, 두 지표를 함께 고려해야 시스템의 실질적인 신뢰성을 파악할 수 있다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 신뢰성과 안정성 시험(BIBO·성능·부하)]]
