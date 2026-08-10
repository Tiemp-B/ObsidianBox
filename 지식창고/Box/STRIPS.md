---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 작업지능소프트웨어개발
---

# Summary

STRIPS(Stanford Research Institute Problem Solver)는 초기 상태에서 목표 상태에 도달하는 행동열(계획)을 자동으로 생성하는 고전 AI 계획 기법으로, 각 행동을 전제조건·추가목록·삭제목록으로 정의한다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>행동의 세 구성요소</aside>

| 구성 요소 | 의미 |
|---|---|
| 전제조건(Precondition) | 그 행동을 실행하기 위해 미리 참이어야 하는 조건 |
| 추가목록(Add List) | 행동 실행 후 새로 참이 되는 조건 |
| 삭제목록(Delete List) | 행동 실행 후 더 이상 참이 아니게 되는 조건 |

STRIPS는 이 조건들을 만족시키며 초기상태에서 목표상태로 이어지는 행동열을 탐색해 계획을 자동 생성한다.

"STRIPS는 목표 상태만 정의할 뿐, 각 행동의 전제조건이나 효과는 다루지 않는다"라는 서술은 오답이다 — STRIPS의 핵심은 오히려 각 **행동을 전제조건·추가목록·삭제목록으로 명시적으로 정의**하는 것이다.

<aside>역사와 로봇 응용 사례</aside>

1971년 SRI(Stanford Research Institute)의 로봇 **Shakey**를 위해 개발된 최초의 실용 AI 계획 시스템이다. Shakey는 방·복도·문·스위치로 이루어진 제한된 환경에서 "이동/문 열기·닫기/스위치 조작/물체 밀기" 같은 행동을 STRIPS로 계획해, "발판 위의 블록을 밀어내라" 같은 목표를 스스로 행동열로 분해해 수행한 최초의 추론 기반 로봇이다.

---

<aside>핵심 정리</aside>

- STRIPS는 전제조건·추가목록·삭제목록으로 행동을 정의해, 초기상태에서 목표상태까지의 행동열을 자동 생성하는 고전 AI 계획 기법이다
- 1971년 SRI의 로봇 Shakey를 위해 개발되었으며, 이후 계획 언어(PDDL 등)에 영향을 주었다

---

<aside>관련 노트</aside>

- 원 페이지: [[4. 지식 표현과 계획 기법(퍼지추론·의미망·STRIPS)]]
- 관련: [[퍼지 추론 시스템(Fuzzy Inference System)]], [[의미망(Semantic Network)]]
