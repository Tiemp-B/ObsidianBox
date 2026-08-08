---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - 일반화관계·주액터vs보조액터 (2026-08-07)

개요(허브) 링크 정상(개요 aside를 "NCS 자료 대조"에서 "이미 다룬 내용과의 관계"로 정리). 문제은행 2문항(시나리오 고려요소/포함요소) 전부 기존 페이지 커버 확인.

## Phase 1 — 조사

### 일반화(Generalization) 관계 — 세 관계에 이은 4번째 관계 (신규)
- 기존 페이지3은 사용 사례 다이어그램의 관계를 "연결·포함·확장 세 가지"로 한정해 서술하는데, UML 표준에는 **일반화(Generalization)** 관계가 하나 더 있음
- **일반화**: 두 액터 사이 또는 두 사용 사례 사이에 "~은 ~의 한 종류다(is-a)"라는 상속 관계를 표현 — 부모 액터·사용 사례의 속성/행동을 자식이 그대로 물려받으면서 자신만의 특성을 추가
- 포함(include)·확장(extend)이 사용 사례 사이의 "실행 관계"(반드시 함께/조건부로 호출)를 다루는 반면, 일반화는 "분류 관계"(상속)를 다룬다는 점에서 성격이 다름
- 예: "결제한다"는 사용 사례에 "카드로 결제한다", "현금으로 결제한다"가 일반화 관계의 자식 사용 사례가 될 수 있음
- 출처: [UML Use Case Diagrams - DEV Community](https://dev.to/edgaras/uml-use-case-diagrams-2pk4), [How to make use case diagram using Generalization](https://geeksww.com/tutorials/miscellaneous/uml/resources/making_use_case_diagram_using_generalization_in_uml.php)

### 주 액터(Primary Actor) vs 보조 액터(Secondary Actor) — 액터의 두 역할 (신규)
- 기존 페이지2는 액터를 "시스템과 상호작용하는 외부 객체"로만 정의하는데, 액터가 사용 사례에서 맡는 역할에 따른 구분(주/보조)은 다루지 않았음
- **주 액터(Primary Actor)**: 목표를 가지고 사용 사례를 **시작(개시)** 시키는 액터 — 사용 사례의 "누구를 위한 것인가"에 해당
- **보조 액터(Secondary Actor)**: 사용 사례가 목표를 달성하도록 시스템에 **도움을 주는** 액터 — 사용 사례를 직접 시작하지 않고, 시스템이 필요할 때 호출해 정보·결과를 제공받음
- 출처: [Types of Actor in a Use Case Model - Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/types-of-actor-in-use-case-model/), [Use Case Actors: Primary versus Secondary](https://thetelepathic.wordpress.com/2015/11/26/use-case-actors-primary-versus-secondary/)

## Phase 2 — 자체 검토

- 일반화는 포함·확장과 성격이 다른 별개 범주(실행 관계 vs 분류 관계)라는 점을 명확히 서술해, 기존 "세 관계" 서술과 단순 나열식으로 섞이지 않도록 함
- 주/보조 액터 구분은 로봇 예시(예: 재난 구조 로봇의 "사용자"는 주 액터, 원격 관제 서버는 보조 액터)로 자연스럽게 연결

## Phase 3 — 결론

2개 페이지에 반영: 2. 도메인 분석과 사용 사례 — 주/보조 액터 1건, 3. 사용 사례 다이어그램의 관계 — 일반화 관계 1건. Box 용어는 `일반화 관계(Generalization)`, `주 액터와 보조 액터(Primary·Secondary Actor)` 신규 생성.
