---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - 자유도DOF·병렬형로봇 (2026-08-07)

NCS 원문에 없는 로봇공학 기초 지식으로, 문제은행 힌트 기반 보강 페이지 성격 유지(기존 방식과 동일). 개요(허브) 링크 정상. 문제은행 4문항(DH파라미터/직교좌표로봇특징×2/순기구학) 전부 기존 페이지 커버 확인.

## Phase 1 — 조사

### 자유도(Degrees of Freedom, DOF) — 관절 개수 논의의 기초 개념 (신규)
- 기존 페이지들은 "관절 3개", "관절 2개+직동 1개"처럼 관절 개수를 계속 언급하는데, 정작 이를 통칭하는 표준 용어인 **자유도(DOF)** 자체는 정의하지 않았음
- **자유도**: 로봇의 자세(위치+방향)를 완전히 결정하는 데 필요한 독립적인 변수의 개수 — 회전 관절(revolute)·직동 관절(prismatic) 하나당 보통 1자유도씩 추가됨
- 산업용 로봇 팔은 대부분 **6자유도**(3차원 위치 X,Y,Z + 3차원 방향 roll,pitch,yaw)를 가져야 공간상 임의의 위치·자세를 모두 표현할 수 있음 — 자유도가 부족하면 도달할 수 없는 자세가 생기고, 초과하면(여유자유도, redundant) 같은 자세를 여러 관절각 조합으로 도달 가능
- 출처: [What are degrees of freedom in robotics - Standard Bots](https://standardbots.com/blog/degrees-of-freedom), [Robotic Arm Classification: DOF](https://thesmartwarehouse.org/topics/robotic-arm-classification-degrees-of-freedom-dof/)

### 병렬형(Parallel) 로봇 — 직교/원통/극좌표/관절/SCARA와 구분되는 6번째 구조 (신규)
- 기존 페이지2의 5가지 구조(직교/원통/극좌표/관절/SCARA)는 모두 베이스에서 엔드이펙터까지 관절·링크가 한 줄로 이어지는 **직렬(serial) 구조**임 — 이와 근본적으로 다른 **병렬(parallel) 구조**가 빠져 있었음
- **직렬 로봇**: 베이스-링크-관절-링크-...-엔드이펙터로 이어지는 하나의 개루프(open loop) 사슬 — 뒤쪽 링크의 정밀도가 앞쪽 링크에 누적되어 의존적
- **병렬 로봇(대표: 델타 로봇)**: 여러 개의 짧은 팔이 각각 독립적으로 베이스와 엔드이펙터(이동 플랫폼)를 동시에 연결하는 구조 — 각 팔의 오차가 누적되지 않아 강성·정밀도가 높고, 무거운 모터를 베이스에 고정해 팔 자체는 가벼워 매우 빠른 픽앤플레이스(pick-and-place) 작업에 적합
- 출처: [Understanding the Differences Between Parallel and Serial robots - Flexiv](https://www.flexiv.com/news/understanding-the-differences-between-parallel-and-serial-robots), [Delta Robot Explained - PLC Programming](https://plcprogramming.io/blog/delta-robot-explained)

## Phase 2 — 자체 검토

- 자유도는 이미 페이지들이 암묵적으로 다루던 "관절 개수" 논의를 명시적 용어로 정리하는 것이라 위화감 없이 반영 가능
- 병렬형 로봇은 기존 5가지 표(모두 직렬)에 새 행을 추가하기보다, "이 5가지는 모두 직렬 구조"라는 상위 프레이밍 + 병렬 구조와의 대비로 반영해 기존 NCS 문제은행 기반 5분류 체계를 훼손하지 않음

## Phase 3 — 결론

1개 페이지(2. 로봇 구조 분류)에 신규 개념 2건 반영. Box 용어는 `자유도(Degrees of Freedom)`, `병렬형 로봇(Parallel Robot)` 신규 생성.
