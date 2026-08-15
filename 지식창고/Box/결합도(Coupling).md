---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 소프트웨어아키텍처
---

# Summary

결합도(Coupling)는 서로 다른 모듈이 **얼마나 서로에게 의존하고 있는지**를 나타내는 지표로, 결합도가 낮을수록 한 모듈의 변경이 다른 모듈에 미치는 영향이 적어 유지보수가 쉬워진다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>결합도의 높고 낮음</aside>

- 결합도가 높다: 한 모듈이 다른 모듈의 내부 구현·자료구조에 직접 의존해, 한쪽을 바꾸면 다른 쪽도 함께 고쳐야 함
- 결합도가 낮다: 모듈 간 상호작용이 명확한 인터페이스(자료 전달 등)로만 이루어져, 내부 구현이 바뀌어도 서로에게 영향이 적음
- 좋은 설계는 **결합도를 낮추고** [[응집도(Cohesion)]]는 높이는 것을 목표로 함

<aside>ATAM·메트릭과의 관계</aside>

[[ATAM(Architecture Tradeoff Analysis Method)]] 같은 아키텍처 평가에서는 결합도를 정량적 메트릭으로 측정해, 수정 용이성 같은 품질 속성을 뒷받침하는 근거로 활용한다.

---

<aside>핵심 정리</aside>

- 결합도는 모듈 간 의존 정도를 나타내며, 낮을수록 유지보수가 쉬운 좋은 설계로 평가된다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 모듈 결합도]]
- 관련: [[응집도(Cohesion)]], [[ATAM(Architecture Tradeoff Analysis Method)]]
