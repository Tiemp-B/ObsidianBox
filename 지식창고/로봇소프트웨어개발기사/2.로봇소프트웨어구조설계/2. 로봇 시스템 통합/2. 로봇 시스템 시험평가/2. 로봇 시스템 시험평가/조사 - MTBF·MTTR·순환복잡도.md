---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - MTBF·MTTR·순환복잡도 (2026-08-07)

NCS 대응 모듈 있음(LM1903080310 학습3 "신뢰성 시험평가"). 개요(허브) 링크 정상. 문제은행 확인: 이 세세항목(신뢰성/BIBO/부하테스트) 소관 문항 전부 이미 커버됨(이전 배치 "1. 로봇 시스템 평가 절차"에서 확인 완료).

## Phase 1 — 조사

### MTBF·MTTR — 신뢰성 지표의 구체적 정의 (신규)
- 기존 페이지2는 "결함 발생률·평균 고장 간격 등 통계적 지표"라고만 서술하고, 그 지표들의 구체적 정의는 다루지 않았음
- **MTBF(Mean Time Between Failures, 평균 고장 간격)**: 수리 가능한 시스템이 고장과 고장 사이 정상적으로 동작한 평균 시간 — 총 가동시간 ÷ 고장 횟수. 값이 클수록 신뢰성이 높음
- **MTTR(Mean Time To Repair, 평균 수리 시간)**: 고장이 발생한 뒤 다시 정상 가동되기까지 걸리는 평균 시간 — 총 다운타임 ÷ 고장 횟수. 값이 작을수록 유지보수성이 좋음
- 두 지표를 함께 쓰면 시스템 가용성(Availability) = MTBF / (MTBF + MTTR)로 계산할 수 있음
- 출처: [MTBF, MTTR, MTTA, and MTTF - Atlassian](https://www.atlassian.com/incident-management/kpis/common-metrics), [Mean time between failures - Wikipedia](https://en.wikipedia.org/wiki/Mean_time_between_failures)

### 순환 복잡도(Cyclomatic Complexity, McCabe) — 분기 커버리지와의 직접 연결 (신규)
- 기존 페이지3은 자동화 정적 분석 도구가 검출하는 항목 중 하나로 "코드 복잡도"를 언급만 하고 정의하지 않았고, 페이지4는 분기 커버리지 100%에 필요한 테스트 케이스 개수를 개별 예시로만 계산했는데, 이 둘을 잇는 표준 지표가 **순환 복잡도**임
- **순환 복잡도(McCabe's Cyclomatic Complexity)**: 코드의 제어 흐름 그래프에서 서로 독립적인 경로의 개수를 세는 복잡도 지표 — 대략 "조건문·반복문의 개수 + 1"로 계산
- 순환 복잡도 값은 그 코드의 **분기 커버리지 100%를 달성하는 데 필요한 테스트 케이스 개수의 상한(upper bound)** 과 같음 — 값이 클수록 테스트에 필요한 노력이 커짐
- 출처: [Cyclomatic Complexity in Software Testing - Guru99](https://www.guru99.com/cyclomatic-complexity.html), [Cyclomatic Complexity Metric - GMetrics](https://dx42.github.io/gmetrics/metrics/CyclomaticComplexityMetric.html)

## Phase 2 — 자체 검토

- MTBF/MTTR의 가용성 공식(Availability = MTBF/(MTBF+MTTR))은 참고 수준으로 페이지에 반영하되, 계산 문제 수준의 심화는 넣지 않음
- 순환 복잡도는 정적 분석(코드 복잡도 측정)과 동적 분석(분기 커버리지 테스트 케이스 설계) 두 페이지를 잇는 개념이라, 두 페이지 모두에 짧게 교차 언급하는 형태로 반영

## Phase 3 — 결론

2개 페이지(2. 신뢰성과 안정성 시험 — MTBF/MTTR 1건, 3. 정적 분석과 코딩 표준 + 4. 동적 분석과 코드 커버리지 — 순환 복잡도 1건, 양쪽에 교차 반영)에 신규 개념 2건 반영. Box 용어는 `MTBF·MTTR(평균 고장 간격·평균 수리 시간)`, `순환 복잡도(Cyclomatic Complexity)` 신규 생성.
