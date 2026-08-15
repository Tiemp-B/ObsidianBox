---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 로봇훈련
---

# Summary

Q-learning은 환경의 모델(상태 전이 확률)을 몰라도, 시행착오를 통해 **각 상태-행동 쌍의 가치(Q값)를 직접 업데이트**해 최적 행동을 학습하는 대표적인 모델-프리(model-free) 강화학습 알고리즘이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Q-learning의 핵심 갱신 방식</aside>

- Q값(상태 $s$에서 행동 $a$를 했을 때의 기대 누적 보상)을 테이블(또는 함수)로 유지하며, 매 경험마다 다음 식으로 갱신함:

$$Q(s,a) \leftarrow Q(s,a) + \alpha \left[ r + \gamma \max_{a'} Q(s',a') - Q(s,a) \right]$$

- 실제로 취한 행동과 무관하게, 다음 상태에서 **가장 좋은 행동의 Q값(최댓값)**을 이용해 갱신함(off-policy) — 탐험 중에 다른 행동을 했더라도 최적 정책을 학습해나감
- 환경의 상태 전이 확률을 몰라도, 반복된 경험(상태-행동-보상-다음상태)만으로 학습 가능

<aside>강화학습 기초와의 관계</aside>

Q-learning은 강화학습의 핵심 요소(상태·행동·보상·정책)를 이용해 최적 행동가치함수를 학습하는 구체적 알고리즘이며, 이미 강화학습의 기본 개념 자체는 다른 페이지에서 다뤘으므로 여기서는 Q-learning 고유의 갱신 방식에 집중한다.

---

<aside>핵심 정리</aside>

- Q-learning은 상태-행동 쌍의 Q값을 시행착오로 갱신하는 모델-프리 강화학습 알고리즘이다
- 다음 상태의 최댓값 Q를 이용해 갱신하는 off-policy 방식이며, 환경 모델을 사전에 알 필요가 없다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 강화학습 심화]]
- 관련: [[강화학습(Reinforcement Learning)]], [[탐색-활용 트레이드오프(Exploration-Exploitation Tradeoff)]], [[정책 경사(Policy Gradient)]]
