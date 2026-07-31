---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신
---

# Summary

ROS Action은 로봇 내비게이션처럼 **완료까지 시간이 오래 걸리는 작업**을 위해 설계된 ROS 통신 모델로, 목표 전송·중간 진행 상황(피드백) 수신·중도 취소가 모두 가능하다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Action이 Service와 다른 점</aside>

- [[ROS Service]]는 요청을 보내고 응답이 올 때까지 기다리는 단발성 [[요청-응답 모델(Request-Response)]]로, 오래 걸리는 작업에는 부적합(응답을 계속 기다려야 함)
- Action은 목표(Goal)를 보낸 뒤, 작업이 진행되는 동안 **피드백(Feedback)을 주기적으로 수신**할 수 있고, 필요하면 작업을 완료 전에 취소(Cancel)할 수 있음
- 목표 전송 → 진행 중 피드백 → 최종 결과(Result) 수신까지 하나의 흐름으로 관리됨

"ROS Action은 Service와 마찬가지로 요청을 보낸 뒤 진행 상황을 전혀 알 수 없이 최종 결과만 기다리는 방식이다"라는 서술은 오답이다 — Action의 핵심은 오히려 **작업 도중 피드백을 지속적으로 받을 수 있고 중도 취소도 가능**하다는 점이며, 이것이 Service와의 결정적 차이다.

<aside>로봇 작업에서의 활용 예</aside>

"목표 지점까지 이동하라"는 내비게이션 명령처럼 수 초~수 분이 걸리고 중간에 취소될 수도 있는 작업은 Action으로 구현하는 것이 적합하다 — 짧고 즉시 끝나는 계산(예: "현재 배터리 잔량 조회")은 Service로 충분하다.

---

<aside>핵심 정리</aside>

- ROS Action은 오래 걸리는 작업을 위해 목표 전송·중간 피드백·중도 취소를 지원하는 통신 모델이다
- 피드백 없이 최종 결과만 기다리는 방식이 아니라는 점이 Service와의 핵심 차이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 통신 모델(발행-구독·요청-응답·액션)]]
- 관련: [[ROS Service]], [[ROS(Robot Operating System)]]
