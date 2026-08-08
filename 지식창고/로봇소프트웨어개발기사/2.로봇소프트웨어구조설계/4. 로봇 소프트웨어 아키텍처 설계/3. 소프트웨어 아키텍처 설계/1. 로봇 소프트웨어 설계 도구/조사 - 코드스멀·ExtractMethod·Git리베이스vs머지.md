---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - 코드스멀·ExtractMethod·Git리베이스vs머지 (2026-08-08)

개요(허브) 링크 정상. 문제은행 확인: 이 세부항목 슬롯 24문항 중 이 세세항목(CASE도구/버전관리/Git/리팩토링) 소관 문항(Q5,12,13,14,18,23) 전부 기존 페이지 커버 확인, SOLID·캡슐화·디자인패턴·MVC·예외처리 등은 형제 세세항목("2. 객체지향 소프트웨어 설계") 또는 다른 과목 소관으로 확인. **이번 배치부터 웹검색 3라운드 반복 규칙 적용**(사용자 지시, 2026-08-08).

## Phase 1 — 3라운드 반복 검색

### 1라운드 — 후보 개념 탐색
- "code smells refactoring definition types" 검색 → 코드 스멀(리팩토링이 필요하다는 신호), 종류(중복 코드/긴 메서드/큰 클래스 등) 확인. Long Method가 SRP(단일 책임 원칙) 위반과 연결된다는 언급 확인 — SOLID는 이미 형제 세세항목에서 다루므로 이 연결점은 교차 언급만 하고 SOLID 자체는 재작성하지 않기로 결정
- "git rebase vs merge difference" 검색 → merge(이력 보존, 협업 브랜치)와 rebase(이력 재작성, 개인 정리) 대비 확인. 기존 페이지는 merge(git pull=fetch+merge)만 다루고 rebase가 없었음

### 2라운드 — 1라운드에서 파생된 개념 심화 검색
- "Martin Fowler refactoring catalog extract method" 검색 → 리팩토링의 대표 기법인 **Extract Method**(긴 코드 덩어리를 별도 메서드로 분리) 확인. Fowler의 카탈로그는 70여 개 기법을 포함하나, 이 중 가장 기본적이고 자주 언급되는 것이 Extract Method
- "git cherry-pick conflict resolution merge conflict basics" 검색 → 충돌 해결의 구체적 절차(충돌 마커 `<<<<<<<`/`=======`/`>>>>>>>`, git add로 해결 표시) 확인

### 3라운드 — 반영 후보를 좁혀 구체화 검색
- "long method code smell extract method example before after" 검색 → Long Method(보통 20~30줄 이상)가 가장 대표적인 코드 스멀이며, Extract Method로 해결하는 것이 정석 패턴임을 재확인 — 로봇 제어 코드 리팩토링 예시(기존 페이지의 변수명 개선 예시)에 자연스럽게 이어붙일 수 있음
- "three-way merge algorithm git conflict how it determines" 검색 → Git이 병합 시 **공통 조상(merge base)** 을 기준으로 두 브랜치의 변경을 비교해, 같은 줄을 서로 다르게 고친 경우에만 충돌로 판단한다는 원리(3-way merge) 확인 — 기존 페이지의 "충돌 시 비교·병합 지원"이라는 서술을 구체화

## Phase 2 — 자체 검토

- 코드 스멀 종류는 Long Method 하나만 대표로 반영(중복코드/큰클래스 등 전체 나열은 과다 반영으로 판단, §2 원칙)
- SRP와의 연결은 "리팩토링이 지향하는 방향 중 하나가 SOLID의 SRP와 통한다"는 정도로만 짧게 언급하고, SOLID 자체 설명은 형제 세세항목 링크로 대체(중복 방지)
- Extract Method는 Fowler 카탈로그 전체가 아니라 이 하나만 대표 예시로 반영
- 3-way merge는 merge base라는 핵심 개념만 반영하고, longest common subsequence 같은 알고리즘 세부까지는 넣지 않음

## Phase 3 — 결론

2개 페이지에 반영: 2. CASE 도구와 버전 관리 — Git rebase vs merge, 3-way merge 원리 2건. 3. 리팩토링 — 코드 스멀(Long Method)+Extract Method 1건. Box 용어는 `코드 스멀과 Extract Method(Code Smell·Extract Method)`, `Git 머지 vs 리베이스(Merge·Rebase)` 신규 생성.
