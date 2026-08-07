---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - 입실론탐욕·정책경사Actor-Critic·도메인무작위화 (2026-08-07)

NCS 대응 모듈 있음(LM1903080311_14v1 "로봇 학습 알고리즘 개발"). 기존 5페이지가 이미 이 모듈을 뼈대로 정확히 작성돼 있고, 개요(허브) 링크도 정상. 문제은행 11문항 전부 기존 페이지에서 커버 확인. 목표(추가정보 발굴)에 맞춰 강화학습·시뮬레이션 관련 페이지에 새로 엮을 개념을 조사했다.

## Phase 1 — 조사

### 입실론-탐욕(ε-greedy) — 탐색-활용 트레이드오프 (신규)
- 기존 페이지3(강화학습 심화)의 Q-learning 설명은 "Q값이 갱신된다"까지만 다루고, **학습 중 에이전트가 실제로 어떤 행동을 선택하는지**(탐색이냐 활용이냐)는 다루지 않았음
- **탐색(Exploration)**: 아직 잘 모르는 행동을 시도해 새로운 정보를 얻는 것 / **활용(Exploitation)**: 지금까지 알고 있는 것 중 가장 좋은(Q값이 가장 높은) 행동을 선택하는 것 — 둘 사이의 균형이 강화학습의 핵심 트레이드오프
- **ε-탐욕 정책**: 확률 ε으로는 무작위 행동(탐색), 확률 (1-ε)으로는 현재 Q값이 가장 높은 행동(활용)을 선택하는 가장 단순하고 널리 쓰이는 전략. 학습 초반에는 ε을 크게 해 탐색 위주로, 학습이 진행될수록 ε을 점차 줄여 활용 위주로 전환하는 것이 일반적
- "학습 중에는 항상 Q값이 가장 높은 행동만 선택해야 한다"는 서술은 탐색 없이 활용만 하면 더 나은 행동을 영영 발견하지 못할 수 있다는 점을 무시한 오답
- 출처: [Epsilon-Greedy Q-learning - Baeldung](https://www.baeldung.com/cs/epsilon-greedy-q-learning), [Exploration-exploitation tradeoff - Milvus](https://milvus.io/ai-quick-reference/what-is-the-explorationexploitation-tradeoff-in-reinforcement-learning)

### 정책 경사(Policy Gradient)·Actor-Critic — Q-learning과 다른 접근 (신규)
- 기존 페이지3은 강화학습 알고리즘으로 Q-learning(가치 기반, value-based)만 다뤘는데, 이는 강화학습 알고리즘의 한 갈래일 뿐임
- **가치 기반(Q-learning)**: 각 (상태,행동)의 가치(Q값)를 먼저 학습하고, 그중 가장 높은 값을 주는 행동을 선택 — 이산적인 행동(예: 상/하/좌/우)에 적합
- **정책 기반(Policy Gradient)**: 가치를 거치지 않고 "어떤 상태에서 어떤 행동을 할 확률"을 나타내는 정책 자체를 직접 학습 — 로봇 관절 각도처럼 **연속적인 행동 공간**에 적합하고 더 안정적으로 수렴하는 경향
- **Actor-Critic**: 정책(Actor, 행동을 선택)과 가치 함수(Critic, 그 행동이 얼마나 좋은지 평가)를 함께 학습해 두 접근의 장점을 결합한 방식 — 정책 경사 방식의 분산(변동성) 문제를 줄이는 데 쓰임
- "강화학습 알고리즘은 Q-learning처럼 가치를 학습하는 방식이 유일하다"는 서술은 정책 기반·Actor-Critic 계열을 무시한 오답
- 출처: [Policy Gradient vs Actor-Critic - Medium](https://medium.com/@rizvaanpatel/policy-gradient-vs-actor-critic-a-simplified-guide-for-reinforcement-learning-beginners-afe0ffebd91d), [Difference between policy gradients and Q-learning - Milvus](https://milvus.io/ai-quick-reference/what-is-the-difference-between-policy-gradients-and-qlearning)

### 도메인 무작위화(Domain Randomization) — Sim-to-Real Gap을 줄이는 실제 기법 (신규)
- 기존 페이지5는 "Sim-to-Real Gap이 존재한다"까지만 서술하고, 이를 줄이는 구체적 기법은 다루지 않았음
- **도메인 무작위화**: 시뮬레이션 학습 중 질감·조명·마찰·질량 같은 환경 파라미터를 매번 무작위로 바꿔가며 훈련시켜, 정책이 특정 시뮬레이션 설정에 과도하게 맞춰지지 않고 **다양한 조건에 강건(robust)** 해지도록 만드는 기법 — 실물의 정확한 물리 파라미터를 몰라도, 실물이 "무작위화한 범위 안 어딘가"에 속하기만 하면 정책이 잘 작동할 가능성이 높아짐
- 진전된 형태로 훈련 도중 무작위화 범위 자체를 자동으로 넓혀가는 ADR(Automatic Domain Randomization)도 있음(참고 수준)
- 출처: [Understanding Domain Randomization for Sim-to-real Transfer (arXiv)](https://arxiv.org/abs/2110.03239)

## Phase 2 — 자체 검토

- ε-greedy의 ε 감소 스케줄(예: 선형/지수 감소)은 구현마다 다양해 페이지에는 "초반엔 크게, 점차 줄임" 정도의 개념만 반영
- Policy Gradient/Actor-Critic은 수식을 넣지 않고 Q-learning과의 대비(이산 vs 연속 행동공간, 가치기반 vs 정책기반)만 개념 수준으로 반영 — 딥러닝 세부 구조(신경망 구성 등)는 이 세세항목 범위를 넘어서므로 제외
- ADR은 참고 수준으로만 조사md에 남기고 페이지 본문에는 반영하지 않음(도메인 무작위화 자체로도 충분한 개념 추가)

## Phase 3 — 결론

2개 페이지(3. 강화학습 심화 — ε-greedy·Policy Gradient/Actor-Critic 2건, 5. 훈련 데이터와 시뮬레이션 환경 — 도메인 무작위화 1건)에 신규 개념 3건 반영. Box 용어는 탐색-활용 트레이드오프(ε-greedy), 정책 경사(Policy Gradient), 도메인 무작위화(Domain Randomization) 신규 생성.
