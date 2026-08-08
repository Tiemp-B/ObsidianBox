---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - ACF그래프검증·IsolationForest원리 (2026-08-07)

개요(허브) 링크 정상. 문제은행 4문항(마르코프체인/정상성검증/이상치탐지/사용빈도설계) 전부 기존 페이지 커버 확인.

## Phase 1 — 조사

### ACF(자기상관함수) — 정상성을 그래프로 확인하는 보조 도구 (신규)
- 기존 페이지2는 정상성 검증을 "ADF 검정 같은 통계적 방법"으로만 서술하고, ADF와 자주 함께 언급되는 **ACF(Autocorrelation Function, 자기상관함수)** 는 다루지 않았음
- ACF는 시계열 데이터가 자기 자신의 과거 값과 얼마나 상관관계가 있는지를 시차(lag)별로 그래프로 나타낸 것 — **정상 시계열은 ACF 값이 0 근처로 빠르게 떨어지고, 비정상 시계열은 천천히 감소하며 신뢰구간을 벗어나는 경향**을 보임
- 기존 페이지가 "육안 확인은 참고용일 뿐"이라 못 박은 것과 모순되지 않도록, ACF는 단순 육안 관찰이 아니라 **신뢰구간(confidence interval)이라는 통계적 기준과 함께** 판단하는 도구라는 점을 명확히 해 ADF 검정과 상호 보완적으로 반영
- 출처: [ACF and PACF in Time Series Analysis - Medium](https://medium.com/@prathik.codes/acf-and-pacf-in-time-series-analysis-c7d32ac8dc39), [Autocorrelation function and Stationarity](https://spureconomics.com/autocorrelation-function-and-stationarity/)

### Isolation Forest — "정상 패턴 학습"의 구체적 원리 (신규)
- 기존 페이지3은 Isolation Forest를 "정상 패턴을 학습해 벗어나는 패턴을 탐지"라고만 서술하는데, 실제로는 다른 머신러닝 이상탐지 기법과 달리 **정상 패턴이 아니라 이상치 자체를 직접 격리(isolate)** 하는 독특한 원리를 씀
- 데이터를 무작위로 나누는(랜덤 분할) 여러 개의 트리를 만들면, **이상치는 적은 분할 횟수만으로 빠르게 고립**되는 반면(드물고 특이해서), 정상 데이터는 고립되기까지 훨씬 많은 분할이 필요함 — 이 "고립까지 걸린 경로 길이"의 평균을 이상치 점수로 사용해, 경로가 짧을수록 이상치일 가능성이 높다고 판단
- 출처: [Isolation forest - Wikipedia](https://en.wikipedia.org/wiki/Isolation_forest), [Anomaly detection using Isolation Forest - GeeksforGeeks](https://www.geeksforgeeks.org/machine-learning/anomaly-detection-using-isolation-forest/)

## Phase 2 — 자체 검토

- ACF를 반영하면서 기존의 "육안 확인은 참고용" 오답 포인트와 모순되지 않도록, ACF도 신뢰구간이라는 통계적 판단 기준을 함께 쓴다는 점을 명확히 서술
- Isolation Forest의 트리 구성·경로 길이 계산 수식까지는 넣지 않고, "적은 분할로 고립 = 이상치"라는 핵심 아이디어만 반영

## Phase 3 — 결론

2개 페이지에 반영: 2. 마르코프 체인과 시계열 정상성 — ACF 1건, 3. 이상치 탐지와 사용빈도 기반 설계 — Isolation Forest 원리 심화 1건. Box 용어는 `ACF(자기상관함수)`, `Isolation Forest` 신규 생성.
