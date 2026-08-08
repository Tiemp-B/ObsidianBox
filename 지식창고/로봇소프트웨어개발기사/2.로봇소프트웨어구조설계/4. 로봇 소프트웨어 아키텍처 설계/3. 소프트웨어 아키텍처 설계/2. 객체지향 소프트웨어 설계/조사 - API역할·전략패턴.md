---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - API역할·전략패턴 (2026-08-08)

개요(허브) 링크 정상. **문제은행 공백 발견**: "API(Application Programming Interface)의 역할은?" 문항이 이 세부항목 슬롯에 있는데, 캡슐화·SOLID·디자인패턴·MVC 등 이 세세항목의 기존 3페이지 어디에도 API 자체를 다룬 곳이 없었음 — vault 전체 검색으로도 미반영 확인. 이번 배치 최우선 보강 대상. 3라운드 웹검색 반복 적용.

## Phase 1 — 3라운드 반복 검색

### 1라운드 — 후보 개념 탐색
- "API application programming interface role purpose" 검색 → API는 서로 다른 소프트웨어 컴포넌트가 통신하도록 하는 규칙·프로토콜의 집합이며, 내부 구현을 몰라도 정해진 방식으로 기능을 요청할 수 있게 하는 **추상화** 역할을 한다는 점 확인
- "factory pattern strategy pattern common design patterns robotics" 검색 → 기존 페이지(싱글톤/옵저버/MVC)에 없는 **전략(Strategy) 패턴**이 로봇 항법(내비게이션) 알고리즘 교체에 자주 쓰인다는 점 확인

### 2라운드 — 1라운드에서 파생된 개념 심화 검색
- "strategy pattern robot navigation algorithm switching example" 검색 → 로봇의 행동 모드(공격적/방어적/중립 등)나 항법 알고리즘을 런타임에 교체하는 전형적인 전략 패턴 예시 확인
- "API hardware abstraction robot software interface example sensor actuator" 검색 → 로봇 소프트웨어에서 API는 흔히 **HAL(하드웨어 추상화 계층)** 이 제공하는 표준 인터페이스 형태로 구현되어, 로봇 제어 코드를 로봇 독립적으로 작성할 수 있게 한다는 점 확인 — 과목2 "모듈화 프로그래밍"에서 이미 다룬 HAL 개념과 자연스럽게 연결됨(중복 작성 대신 교차 링크)

### 3라운드 — 반영 후보를 좁혀 구체화 검색
- "API vs interface difference contract abstraction implementation details" 검색 → API의 핵심은 "무엇을 할 수 있는지(계약)"만 정의하고 "어떻게 구현되는지"는 감춘다는 점을 재확인 — 이 vault의 시험 문항 스타일(오답 포인트)에 맞춰 "API는 내부 구현까지 노출한다"는 오답을 만들 근거 확보
- "strategy pattern vs state pattern difference" 검색 → 전략 패턴(클라이언트가 알고리즘을 선택·주입)과 상태 패턴(객체 스스로 상태에 따라 행동 전환)의 차이 확인 — 상태 패턴은 이미 "2. 상태 기계와 예외 처리"(로봇 작업 시나리오 정의) 세세항목에서 사실상 다룬 개념이라, 전략 패턴 신규 추가 시 상태 패턴과의 대비를 짧게 언급해 두 세세항목을 연결

## Phase 2 — 자체 검토

- API는 "인터페이스"와 거의 같은 의미로 쓰이므로, 페이지2(캡슐화) 근처에 배치해 "캡슐화가 감추는 내부, API/인터페이스가 노출하는 외부 접점"이라는 대비로 자연스럽게 연결
- HAL과의 연결은 교차 링크만 추가하고 HAL 자체 재설명은 하지 않음(과목2에 이미 있음)
- 전략 패턴은 로봇 항법 예시로 반영하고, 상태 패턴과의 대비는 "이미 다룬 상태 기계"로 짧게만 연결(중복 방지)

## Phase 3 — 결론

2개 페이지에 반영: 2. 캡슐화와 SOLID 원칙 — API의 역할 1건(문제은행 공백 보강, 최우선), 3. 디자인 패턴과 MVC — 전략(Strategy) 패턴 1건. Box 용어는 `API(Application Programming Interface)`, `전략 패턴(Strategy Pattern)` 신규 생성.
