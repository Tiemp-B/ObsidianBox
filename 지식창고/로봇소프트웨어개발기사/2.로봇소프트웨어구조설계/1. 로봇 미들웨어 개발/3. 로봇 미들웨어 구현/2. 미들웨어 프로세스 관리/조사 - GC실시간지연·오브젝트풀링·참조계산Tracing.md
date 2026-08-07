---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - GC실시간지연·오브젝트풀링·참조계산Tracing (2026-08-07)

NCS 대응 모듈은 별도 확인 없음(§1-2, 프로세스 관리·메모리 관리 일반 지식 기반). 개요(허브) 링크 정상. 문제은행 6문항 전부 커버 확인(모듈화 장점 2건은 형제 세세항목 "1. 모듈화 프로그래밍"에서, 데드락 1건은 과목1에서 이미 커버).

## Phase 1 — 조사 및 내부 재확인

### GC의 실시간성 트레이드오프 — 페이지에 미반영된 내용 발견 (내부 재확인)
- 기존 Box 용어 `가비지 컬렉션(Garbage Collection).md`에는 이미 "GC 일시정지(stop-the-world)로 실시간 제어 루프에서는 예측 불가능한 지연을 유발할 수 있다"는 중요한 트레이드오프가 적혀 있는데, 정작 실제 페이지("3. 가비지 컬렉션과 이벤트 기반 처리")에는 이 내용이 반영되어 있지 않음(페이지는 GC 장점 3가지만 나열)
- 웹 검색으로 확인: Stop-the-world GC는 모든 스레드를 멈추고 도달 불가능한 객체를 탐색하는데, 이 과정이 수십 ms까지 걸릴 수 있어 하드 실시간 마감시한을 위협할 수 있음(대안: 증분형/동시성 GC, 스케줄러와의 공동 스케줄링)
- 출처: [Real-Time Garbage Collection Is Real](https://michaelrbernste.in/2013/06/03/real-time-garbage-collection-is-real.html)

### 오브젝트 풀링(Object Pooling) — GC 부담을 줄이는 실무 기법 (신규)
- 실시간성이 중요한 로봇 소프트웨어에서 GC 지연을 피하는 대표적인 실무 기법은 **오브젝트 풀링**이다 — 객체를 매번 새로 생성·폐기하는 대신, 미리 만들어 둔 객체 묶음(풀)을 재사용해 GC가 회수할 대상 자체를 줄임
- 게임 엔진·임베디드 시스템에서 널리 쓰이며, "생성 비용이 큰 객체를 반복 생성/폐기하는 대신 재사용"한다는 점에서 스레드 풀과 같은 "풀링(Pooling)" 계열 최적화 패턴
- 출처: [Object Pool - Game Programming Patterns](https://gameprogrammingpatterns.com/object-pool.html)

### 참조 계산(Reference Counting) vs 추적(Tracing) — GC의 두 가지 구현 방식 (신규)
- 기존 페이지는 GC를 하나의 기법으로만 설명하는데, 실제로는 구현 방식이 크게 두 갈래로 나뉨
- **참조 계산(Reference Counting)**: 객체마다 "몇 곳에서 참조되고 있는지" 카운터를 두고, 참조가 생기면 +1, 없어지면 -1, 0이 되는 즉시 회수 — 회수가 프로그램 흐름 중 분산되어 일어나 큰 일시정지가 적지만, 서로를 참조하는 순환 참조는 회수하지 못하는 한계
- **추적(Tracing)**: 루트(전역 변수 등)에서 출발해 도달 가능한 객체를 전부 표시하고, 표시되지 않은 객체를 한꺼번에 회수 — 순환 참조도 처리 가능하지만, 탐색 시점에 큰 일시정지(stop-the-world)가 발생하기 쉬움
- 출처: [Reference counting vs. tracing garbage collection](https://wiki.tcl-lang.org/page/Reference+counting+vs.+tracing+garbage+collection)

## Phase 2 — 자체 검토

- 스레드 풀 링크는 이 vault에 아직 없다면 생성하지 않고 플레인 텍스트로만 남김(확인 필요) — 확인 결과 없으므로 링크 제거하고 개념만 서술
- Reference Counting/Tracing 세부 알고리즘(mark-sweep, mark-compact 등)까지는 넣지 않고, 두 접근의 핵심 차이(즉시 회수 vs 일괄 탐색, 순환참조 처리 여부)만 반영

## Phase 3 — 결론

1개 페이지(3. 가비지 컬렉션과 이벤트 기반 처리)에 3건 반영: GC 실시간 트레이드오프(페이지-Box용어 간 불일치 해소), 오브젝트 풀링, 참조계산 vs 추적. 신규 Box 용어 없음(기존 가비지 컬렉션 Box 용어와 완전히 정합됨).
