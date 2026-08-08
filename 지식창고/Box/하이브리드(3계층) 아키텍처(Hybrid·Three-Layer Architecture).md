---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 로봇소프트웨어아키텍처설계
---

# Summary

하이브리드(3계층) 아키텍처는 반응 계층·실행 계층·숙고 계층 세 층으로 구성되어, [[Subsumption 아키텍처(Subsumption Architecture)|Subsumption]](반응형)의 빠른 대응과 Deliberative(숙고형)의 정교한 계획을 함께 활용하는 절충형 로봇 제어 아키텍처다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>3계층 구조</aside>

| 계층 | 역할 |
|---|---|
| 반응 계층(Reactive Layer) | 센서 입력에 즉각 반응하는 저수준 실시간 제어 |
| 실행 계층(Executive/Sequencing Layer) | 반응 계층과 숙고 계층을 조정하며 작업 순서를 관리 |
| 숙고 계층(Deliberative Layer) | 환경 모델을 바탕으로 한 고수준 계획·추론 |

<aside>순수 방식의 단점을 보완</aside>

순수 Subsumption은 빠르지만 복잡한 목표 달성을 위한 계획 능력이 부족하고, 순수 Deliberative는 정교하지만 계획 수립에 시간이 걸려 실시간 반응이 어렵다. 하이브리드 아키텍처는 **반응 계층이 즉각적인 위험(장애물 등)에 대응하는 동안, 숙고 계층이 장기적인 경로·작업 계획을 수립**하도록 역할을 나눠 두 방식의 단점을 서로 보완한다.

"하이브리드 아키텍처는 Subsumption과 Deliberative 중 하나를 완전히 대체하는 새로운 단일 계층 방식이다"라는 서술은 오답이다 — 하이브리드 아키텍처의 핵심은 오히려 **반응 계층과 숙고 계층을 함께 조합**해 실행 계층이 조정하는 다층 구조라는 점이다.

---

<aside>핵심 정리</aside>

- 하이브리드(3계층) 아키텍처는 반응·실행·숙고 세 계층으로 구성되어 Subsumption과 Deliberative의 장점을 함께 활용한다
- 반응 계층은 즉각 대응, 숙고 계층은 장기 계획, 실행 계층은 둘을 조정하는 역할을 맡는다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 로봇 소프트웨어 아키텍처 스타일 비교]]
- 관련: [[Subsumption 아키텍처(Subsumption Architecture)]]
