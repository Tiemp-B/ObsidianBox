---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - 속도장애물(VO)과RVO (2026-08-08)

개요(허브) 링크 정상, NCS 자료 대조 aside 없음(이미 클린). 문제은행 세부항목 슬롯("3. 로봇 충돌회피" 1문항)은 "1. 머니퓰레이터 충돌회피" 소관(포텐셜 필드 반발력)으로 이미 배정 확인, 이 세세항목 소관 문항 없음. 3라운드 웹검색 반복 적용.

## Phase 1 — 3라운드 반복 검색

### 1라운드 — 후보 개념 탐색
- "velocity obstacle algorithm collision avoidance moving robot definition cone" 검색 → 속도 장애물(VO, Velocity Obstacle)은 상대방이 현재 속도를 유지한다고 가정할 때 충돌을 일으키는 모든 속도의 집합이며, 이 영역 밖의 속도를 선택하면 충돌을 피할 수 있다는 원리 확인 — 기존 페이지는 Elastic Force·가상센서만 다루고 VO는 전혀 없음(신규 공백)
- "reciprocal velocity obstacle RVO multi-robot collision avoidance difference from VO" 검색 → RVO는 VO와 달리 회피 책임을 양쪽 로봇이 절반씩 나눠 진다는 점에서 다르며, VO만 쓰면 두 로봇이 서로 반응하며 진동(oscillation)하는 문제가 생긴다는 점 확인

### 2라운드 — 파생 심화 검색
- "속도 장애물 VO 알고리즘 충돌회피 원뿔 상대속도 로봇" 검색 → 한국어 자료로 충돌 원뿔(Collision Cone)이 로봇 중심에서 장애물까지의 두 접선으로 이루어진 부채꼴 형태이며, 속도 장애물은 이 충돌 원뿔을 상대속도 공간으로 옮긴 것과 물리적으로 같다는 설명 확인
- "RVO 상호 속도 장애물 진동 문제 VO 한계 다중로봇" 검색 → RVO가 VO의 진동 문제를 해결하기 위해 고안되었으며, 회피 책임을 양쪽이 나눠 갖는 매우 단순한 방법으로 부드럽고 안전한 이동을 가능하게 한다는 점 재확인

### 3라운드 — 반영 후보 구체화 검증
- "VO RVO 예시 두 로봇 서로 피하다가 진동 responsibility 분담" 검색 → 두 로봇이 각자 VO만으로 서로를 피하려다 반응이 서로를 계속 쫓아가며 흔들리는 "왕복 춤(reciprocal dance)" 현상이라는 구체적 예시 확인 — 시험 오답 포인트로 활용 가능한 명확한 실패 사례

## Phase 2 — 자체 검토

- 속도 장애물(VO)·RVO는 "이동로봇 충돌회피"라는 이 세세항목의 핵심 주제(동적 환경에서 움직이는 로봇 간의 충돌 회피)에 정확히 부합하고, 기존 Elastic Force(경로 재설정)·가상센서(상대운동 반영 거리 보정)와는 다른 접근(속도 공간에서의 충돌 판단)이라 신규 반영
- ORCA(Optimal Reciprocal Collision Avoidance) 같은 RVO의 후속 최적화 기법이나 충돌 원뿔의 기하학적 유도까지는 심화·실기 범위에 가까워 넣지 않고, VO·RVO의 정의·차이·진동 문제까지만 반영(§2 원칙)
- 새로운 알고리즘 개념이라 Box 용어로 별도 생성해 향후 다른 세세항목에서도 참조할 수 있게 함

## Phase 3 — 결론

1개 페이지(2. Elastic Force 알고리즘과 가상센서 알고리즘)에 신규 개념 1건(속도 장애물 VO와 RVO) 반영. 신규 Box 용어 `속도 장애물(Velocity Obstacle)과 RVO` 생성.
