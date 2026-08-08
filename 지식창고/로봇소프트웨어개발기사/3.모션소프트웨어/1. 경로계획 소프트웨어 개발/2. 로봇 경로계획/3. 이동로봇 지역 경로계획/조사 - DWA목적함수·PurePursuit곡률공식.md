---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - DWA목적함수·PurePursuit곡률공식 (2026-08-08)

개요(허브) 링크 정상, NCS 자료 대조 aside 없음(이미 클린). 문제은행(세부항목 슬롯 14문항 중 이 세세항목 소관 "DWA 요소×2"·"Pure Pursuit 특징"·"VFH 첫단계"·"VFH 특징" 5문항, Potential Field 1문항은 과목2에서 이미 커버) 전부 기존 페이지 커버 확인. 3라운드 웹검색 반복 적용.

## Phase 1 — 3라운드 반복 검색

### 1라운드 — 후보 개념 탐색
- "pure pursuit algorithm curvature formula 2y/L^2 steering angle lookahead distance" 검색 → Pure Pursuit의 실제 계산은 곡률 공식 $\kappa=2\sin\alpha/L_d$과 조향각 $\delta=\tan^{-1}(2L\sin\alpha/L_d)$로 이루어짐을 확인 — 기존 페이지는 절차(목표점 선택→원호 계산→조향각 결정)만 설명하고 실제 공식이 없음(신규 공백)
- "DWA dynamic window approach objective function formula heading clearance velocity weighted sum" 검색 → DWA는 목적함수 $G(v)=\alpha\cdot heading(v)+\beta\cdot dist(v)+\gamma\cdot vel(v)$로 세 요소에 가중치를 곱해 합산한 값이 최대인 속도를 선택함을 확인 — 기존 페이지는 세 요소를 나열만 하고 가중합 구조가 없음(신규 공백)

### 2라운드 — 파생 심화 검색
- "Pure Pursuit 알고리즘 곡률 공식 전방주시거리 조향각 유도" 검색 → 한국어 자료에서 동일한 공식($k=2\sin\alpha/L_d$, $\delta=\tan^{-1}(2L\sin\alpha/L_d)$) 확인. 전방주시거리가 짧으면 빠른 피드백으로 추종은 정밀하지만 오버슈팅(기존 페이지의 "진동" 서술과 동일 개념), 길면 급격한 경로 변화 추종은 떨어지지만 부드럽게 수렴한다는 트레이드오프 재확인(기존 서술과 일치)
- "DWA 목적함수 가중치 헤딩 클리어런스 속도 로봇 지역경로계획" 검색 → 한국어 자료로 DWA 목적함수가 방향(heading)·장애물과의 거리(dist)·속도(velocity) 세 요소의 가중합이며, 각 가중치를 조정해 실제 상황에 맞게 로봇의 경로 선택 성향을 바꿀 수 있다는 점 확인

### 3라운드 — 반영 후보 구체화 검증
- "DWA G(v) = alpha*heading + beta*dist + gamma*velocity 평가함수 공식" 검색 → $G(v,\omega)=\sigma(\alpha\cdot heading+\beta\cdot dist+\gamma\cdot velocity)$로, 서로 다른 단위를 가진 세 항을 정규화(normalization)한 뒤 가중합한다는 세부 구조까지 확정. 목적은 장애물 회피·목표 지향·빠른 속도라는 세 요소를 동시에 반영하는 것임을 재확인

## Phase 2 — 자체 검토

- 두 공식 모두 기존 aside(DWA의 "세 요소 나열", Pure Pursuit의 "절차 3단계")를 구체화하는 자연스러운 확장이라 반영
- DWA의 정규화(normalization) 세부 절차나 Pure Pursuit의 자전거 모델(bicycle model) 전체 유도까지는 실기 범위에 가까워 넣지 않고, 완성된 공식과 그 의미(무엇을 최대화/어떻게 조향각을 구하는지)만 반영(§2 원칙)
- 전방주시거리·가중치 조정의 트레이드오프는 기존 페이지에 이미 있어 중복 설명하지 않음

## Phase 3 — 결론

2개 페이지(2. DWA와 VFH, 3. Pure Pursuit 경로 추종)에 신규 개념 2건(DWA 목적함수 공식, Pure Pursuit 곡률 공식) 반영. 신규 Box 용어 없음.
