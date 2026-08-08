---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - 지역최솟값탈출법·VFH교차링크 (2026-08-07)

개요(허브) 링크 정상. 문제은행 2문항(포텐셜필드 단점/정적·동적환경 차이) 전부 기존 페이지 커버 확인. 목표(추가정보 발굴)에 맞춰 포텐셜 필드의 한계(지역 최솟값)를 극복하는 방법을 조사했다.

## Phase 1 — 조사

### 지역 최솟값 탈출법 — 가상 목표·벽 추종(Wall Following) (신규)
- 기존 페이지3은 지역 최솟값 문제를 "단점"으로만 서술하고, 이를 실제로 어떻게 극복하는지는 다루지 않았음
- **벽 추종(Wall Following)**: 인력과 척력의 합력이 거의 0이 되어 멈추려는 상황이 감지되면, 로봇이 장애물의 표면을 따라(벽을 추종하듯) 우회 이동해 힘의 균형이 깨지는 지점까지 빠져나온 뒤 다시 원래의 포텐셜 필드 이동으로 복귀하는 방식
- **가상 목표(Virtual Local Target)**: 지역 최솟값에 갇힐 위험이 감지되면, 원래의 전역 목표 대신 일시적으로 가까운 가상의 임시 목표를 설정해 그쪽으로 먼저 이동시킨 뒤, 그 가상 목표에 도달하면 다시 원래 목표를 향해 이동을 재개하는 방식
- 지역 최솟값은 크게 (1) 로봇이 오목한(concave) 영역에 갇히는 경우, (2) 장애물이 목표 방향과 정확히 겹쳐 인력·척력이 상쇄되는 경우 두 가지 원인으로 발생함
- 출처: [An Improved Wall Following Method for Escaping from Local Minimum](https://www.researchgate.net/publication/224108686_An_Improved_Wall_Following_Method_for_Escaping_from_Local_Minimum_in_Artificial_Potential_Field_Based_Path_Planning), [Virtual local target method for avoiding local minimum](https://link.springer.com/article/10.1631/jzus.2003.0264)

### VFH(Vector Field Histogram) — 이미 다른 세세항목에서 다룬 대안 알고리즘 (교차 링크만)
- VFH는 이미 이 vault의 `3.모션소프트웨어 / 1. 경로계획 소프트웨어 개발 / 2. 로봇 경로계획 / 3. 이동로봇 지역 경로계획 / 2. DWA와 VFH`에서 상세히 다루고 있음(방향별 장애물 밀도 히스토그램 기반 지역 경로계획, DWA와의 비교까지 포함)
- 포텐셜 필드의 지역 최솟값 문제를 원천적으로 피하는 대안 알고리즘이라는 점에서 이 페이지와 연결할 가치가 있으나, 내용을 중복 작성하지 않고 교차 링크만 추가

## Phase 2 — 자체 검토

- 지역 최솟값의 두 가지 발생 원인(오목 영역/힘 상쇄)은 기존 페이지의 "U자 장애물" 예시가 사실상 두 원인이 겹친 경우임을 명확히 하는 데 도움이 되어 반영
- VFH 상세 원리는 중복 작성하지 않고, "이미 다룬 곳" 안내만 제공

## Phase 3 — 결론

1개 페이지(3. 장애물 회피와 포텐셜 필드)에 신규 개념 1건(지역 최솟값 탈출법) + VFH 교차 링크 1건 반영. 신규 Box 용어는 생성하지 않고 기존 `포텐셜 필드(Potential Field)` Box 용어에 탈출법 보강.
