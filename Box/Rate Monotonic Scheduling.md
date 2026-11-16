---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 스케줄링
  - 실시간시스템
---

# Summary

Rate Monotonic Scheduling(RMS)은 **주기가 짧은 작업일수록 고정된 높은 우선순위**를 부여하는 정적(static) 실시간 스케줄링 알고리즘이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>RMS의 우선순위 부여 규칙</aside>

- 각 작업의 우선순위는 작업 생성 시점에 **주기(period)에 따라 고정**되며, 실행 도중에는 바뀌지 않음(정적 스케줄링)
- 주기가 짧을수록(더 자주 실행되어야 할수록) 더 높은 우선순위를 부여 — 예: 10ms 주기 작업이 100ms 주기 작업보다 항상 우선
- 일정 조건(CPU 이용률이 특정 한계 이하)을 만족하면 모든 작업의 마감시한을 보장할 수 있음이 이론적으로 증명되어 있음

<aside>EDF와의 비교</aside>

[[Earliest Deadline First(EDF)]]는 이론적 스케줄링 가능 이용률이 더 높지만 우선순위가 동적으로 계속 바뀌어 구현·예측이 복잡한 반면, RMS는 이용률 한계는 더 낮지만 고정 우선순위라 구현이 단순하고 산업 현장에서 예측·검증이 쉬워 널리 쓰인다.

---

<aside>핵심 정리</aside>

- Rate Monotonic Scheduling은 주기가 짧을수록 높은 고정 우선순위를 부여하는 정적 실시간 스케줄링이다
- 우선순위가 실행 중 재계산되는 동적 방식이 아니다

---

<aside>관련 노트</aside>

- 원 페이지: [[1. 로봇 제어기 특성 개요]], [[2. 실시간 운영체제와 스케줄링]]
- 관련: [[Earliest Deadline First(EDF)]], [[RTOS]]
