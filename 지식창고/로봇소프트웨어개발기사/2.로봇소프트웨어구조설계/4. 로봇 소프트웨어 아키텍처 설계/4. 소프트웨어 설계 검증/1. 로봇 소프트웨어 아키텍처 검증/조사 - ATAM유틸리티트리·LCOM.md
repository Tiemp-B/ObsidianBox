---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - ATAM유틸리티트리·LCOM (2026-08-08)

개요(허브) 링크 정상. 문제은행 2문항(ATAM 특징/결합도 메트릭) 전부 기존 페이지+Box 용어 커버 확인.

## Phase 1 — 3라운드 반복 검색

### 1라운드 — 후보 개념 탐색
- "CK metrics suite Chidamber Kemerer CBO LCOM DIT" 검색 → 기존 페이지가 CBO만 다루는 CK(Chidamber & Kemerer) 메트릭 스위트가 실제로는 WMC/DIT/NOC/CBO/RFC/LCOM 6개로 구성됨을 확인. 이 중 **LCOM(응집도 부족)** 이 CBO(결합도)와 대칭을 이루는 지표
- "ATAM vs SAAM vs CBAM architecture evaluation methods" 검색 → ATAM은 SAAM(수정용이성 중심 평가)에서 발전했고, CBAM(비용-편익 분석)으로 확장된다는 계보 확인 — 다만 이 세세항목은 ATAM 자체에 집중하므로 SAAM/CBAM은 참고 수준

### 2라운드 — 파생 심화 검색
- "WMC DIT depth of inheritance tree meaning high value problem" 검색 → WMC(클래스 복잡도)·DIT(상속 깊이)의 의미 확인 — 다만 로봇 소프트웨어 검증 맥락에서 CBO·LCOM(결합도·응집도 쌍)이 가장 직접적으로 유용하다고 판단, WMC/DIT/NOC/RFC까지는 과다 반영으로 제외
- "CBAM cost benefit analysis method utility tree" 검색 → CBAM이 ATAM의 산출물을 입력으로 삼아 비용-편익을 정량화하는 후속 절차임을 확인(참고 수준)

### 3라운드 — 반영 후보 구체화 검색
- "ATAM utility tree quality attribute scenarios stimulus response" 검색 → ATAM의 핵심 산출물인 **유틸리티 트리(Utility Tree)** 구조 확인: 최상위(품질 속성: 성능·보안 등) → 중간(속성의 세분화: 예 "성능"의 세분화인 "지연시간") → 최하위(구체적 시나리오, 자극-반응-측정 3요소로 기술) — 기존 페이지는 "시나리오 기반"이라고만 서술하고 이 계층 구조 자체는 없었음
- "LCOM lack of cohesion of methods calculation meaning" 검색 → LCOM은 값이 낮을수록(0에 가까울수록) 응집도가 높아 바람직하고, 높을수록(1에 가까울수록) 클래스가 여러 무관한 역할을 섞어 담당하고 있다는 신호 — 기존 페이지의 결합도(CBO)와 정확히 대칭되는 개념

## Phase 2 — 자체 검토

- CK 메트릭 6개 전부 나열하지 않고, 기존 CBO(결합도)와 짝을 이루는 LCOM(응집도)만 선별 반영(§2 원칙, 과다 반영 방지)
- 유틸리티 트리는 ATAM의 실제 작업 산출물이라 페이지 본문에 구조(3단계 계층)만 반영하고, 자극-반응-측정의 세부 형식까지는 넣지 않음
- SAAM/CBAM은 조사md에만 참고로 남기고 페이지에는 반영하지 않음(ATAM 자체에 집중, 과다 반영 방지)

## Phase 3 — 결론

1개 페이지(2. ATAM과 결합도 메트릭)에 신규 개념 2건(유틸리티 트리, LCOM) 반영. Box 용어는 `LCOM(응집도 결여도)` 신규 생성. 기존 `ATAM(Architecture Tradeoff Analysis Method)` Box 용어에 유틸리티 트리 보강.
