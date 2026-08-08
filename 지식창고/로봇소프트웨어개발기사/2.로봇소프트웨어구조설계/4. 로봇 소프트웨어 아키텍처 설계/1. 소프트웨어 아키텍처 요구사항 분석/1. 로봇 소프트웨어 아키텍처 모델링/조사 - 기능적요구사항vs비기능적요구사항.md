---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - 기능적요구사항vs비기능적요구사항 (2026-08-07)

개요(허브) 링크 정상. **문제은행 확인 결과 진짜 공백 발견**: "6. 로봇 소프트웨어 아키텍처 요구사항 분석에서 기능적 요구사항의 예는?" 문항이 이 세세항목("소프트웨어 아키텍처 요구사항 분석") 소관인데, 기존 2페이지(개요/4계층구조) 어디에도 기능적/비기능적 요구사항 구분이 전혀 없었음 — 이번 배치의 최우선 보강 대상.

## Phase 1 — 조사

### 기능적 요구사항(Functional Requirements) vs 비기능적 요구사항(Non-Functional Requirements) (신규, 문제은행 공백 보강)
- **기능적 요구사항**: 시스템이 **무엇을 해야 하는가**를 정의 — 시스템의 기능·서비스·동작 자체 (예: 로봇의 "장애물 회피", "음성 명령 인식", "경로 계획 수립")
- **비기능적 요구사항**: 시스템이 **어떻게 동작해야 하는가**를 정의 — 성능·보안·신뢰성·확장성 같은 품질 제약 (예: "장애물 회피는 100ms 이내에 반응해야 한다", "센서 데이터는 암호화되어야 한다")
- 두 요구사항은 상호 보완적이며, 기능적 요구사항이 충족되어도 비기능적 요구사항(성능·안정성 등)을 만족하지 못하면 실제로 쓸 수 없는 시스템이 될 수 있음
- 로봇 소프트웨어 아키텍처 4계층(Driver/Platform/Algorithm/UI) 각각에도 두 유형의 요구사항이 함께 존재함 — 예: Algorithm 계층의 "경로 계획을 수행한다"는 기능적 요구사항이고, "경로 계획은 50ms 이내에 완료되어야 한다"는 비기능적 요구사항
- 출처: [Functional vs Non-Functional Requirements - GeeksforGeeks](https://www.geeksforgeeks.org/software-engineering/functional-vs-non-functional-requirements/), [Functional vs. Non-Functional Requirements - Jama Software](https://www.jamasoftware.com/requirements-management-guide/writing-requirements/functional-vs-non-functional-requirements/)

## Phase 2 — 자체 검토

- 기능적/비기능적 요구사항은 소프트웨어공학 일반 개념으로, 로봇 4계층 아키텍처와 자연스럽게 연결되는 예시로 반영해 이 세세항목 고유의 맥락을 유지
- 비기능적 요구사항의 세부 하위분류(ISO 25010 품질특성 등)까지는 넣지 않고, "무엇을(기능) vs 어떻게(비기능)"라는 핵심 구분과 로봇 예시만 반영

## Phase 3 — 결론

1개 페이지(1. 로봇 소프트웨어 아키텍처 모델링 개요 또는 2. 4계층 구조)에 신규 개념 반영. Box 용어는 `기능적 요구사항과 비기능적 요구사항(Functional·Non-Functional Requirements)` 신규 생성.
