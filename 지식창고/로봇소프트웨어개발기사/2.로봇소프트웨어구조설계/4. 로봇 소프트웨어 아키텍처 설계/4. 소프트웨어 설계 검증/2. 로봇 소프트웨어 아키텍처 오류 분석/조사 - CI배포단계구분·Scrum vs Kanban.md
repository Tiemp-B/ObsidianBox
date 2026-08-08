---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - CI배포단계구분·ScrumvsKanban (2026-08-08)

개요(허브) 링크 정상. 문제은행(세부항목 슬롯 24문항 중 이 세세항목 소관: 논리적오류/코드리뷰×2/CI/DevOps/Agile) 전부 기존 페이지 커버 확인. 3라운드 웹검색 반복 적용.

## Phase 1 — 3라운드 반복 검색

### 1라운드 — 후보 개념 탐색
- "continuous integration vs continuous delivery vs continuous deployment" 검색 → 기존 페이지가 "CI/CD"로 뭉뚱그린 것이 실제로는 CI(빌드+테스트 자동화) → Continuous Delivery(배포 준비 상태 유지, 수동 승인 필요) → Continuous Deployment(승인 없이 완전 자동 배포)라는 3단계임을 확인
- "scrum vs kanban agile framework difference" 검색 → 기존 페이지가 "스프린트"만 언급하고 Scrum이라는 프레임워크명 자체를 명시하지 않았음. Kanban(고정 스프린트 없이 지속적 흐름+WIP 제한)과의 대비 확인

### 2라운드 — 파생 심화 검색
- "continuous deployment robotics firmware safety risk manual approval" 검색 → 협동로봇처럼 사람과 가까이서 동작하는 로봇 소프트웨어는 완전 자동 배포(Continuous Deployment)보다 **수동 승인 단계가 있는 Continuous Delivery**가 안전성 측면에서 더 흔히 권장된다는 점 확인 — 로봇 소프트웨어 맥락에 맞는 구체적 응용 포인트
- "scrum roles product owner scrum master sprint backlog" 검색 → Scrum의 핵심 역할(Product Owner: 제품 우선순위, Scrum Master: 프로세스 촉진) 확인

### 3라운드 — 반영 후보 구체화 검색
- "kanban board WIP limit software team maintenance work example" 검색 → Kanban의 WIP(Work In Progress) 제한 개념 확인 — 동시 진행 작업 수를 제한해 병목을 드러내는 방식
- "continuous delivery vs continuous deployment human approval gate example" 검색 → 두 개념의 핵심 차이가 정확히 "사람의 승인 유무" 하나임을 재확인, 시험 오답 포인트로 활용 가능

## Phase 2 — 자체 검토

- CI/Delivery/Deployment 3단계는 기존 페이지의 "CI의 장점" aside에 자연스럽게 이어붙이되, 구체적 파이프라인 도구명(Jenkins 등)까지는 넣지 않음
- 로봇 소프트웨어에서 Continuous Deployment보다 Continuous Delivery(수동 승인)가 안전성상 더 흔한 이유를 짧게 반영해, 로봇 도메인 특수성을 살림
- Scrum/Kanban은 이름과 핵심 차이(고정 스프린트+역할 vs 지속적 흐름+WIP제한)만 반영하고, Scrumban 같은 혼합형까지는 넣지 않음(§2 원칙, 과다 반영 방지)

## Phase 3 — 결론

1개 페이지(3. CI·DevOps·애자일 방법론)에 신규 개념 2건(CI/Delivery/Deployment 3단계 구분, Scrum vs Kanban) 반영. Box 용어는 `CI·지속적 전달·지속적 배포(CI·Continuous Delivery·Continuous Deployment)`, `Scrum과 Kanban` 신규 생성.
