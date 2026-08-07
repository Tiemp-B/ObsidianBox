---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - Communication다이어그램명칭·Object다이어그램 (2026-08-07)

NCS 대응 모듈 있음(LM1903080304 학습2, UML 다이어그램 분류). 전용 문제은행 슬롯 없음(§1-2). 개요(허브) 링크 정상. NCS 원문 분류(use case/sequence/collaboration/statechart = 행위적, activity/class/component/deployment = 구조적)를 그대로 따랐으므로 기존 서술을 재사용하지 않되 원 분류는 유지. 목표(추가정보 발굴)에 맞춰 UML 표준의 최신 용어·인접 다이어그램을 조사했다.

## Phase 1 — 조사

### Collaboration Diagram → Communication Diagram (UML 2.0 명칭 변경) (신규)
- 기존 페이지3은 "collaboration diagram"이라는 UML 1.x 용어만 사용하는데, **UML 2.0부터는 이 다이어그램이 "Communication Diagram(커뮤니케이션 다이어그램)"으로 이름이 바뀌었음**(내용·표기법은 기능적으로 동일, 명칭만 변경)
- 시험에서 "collaboration diagram"과 "communication diagram"을 서로 다른 것으로 헷갈리게 하는 문항이 나올 수 있어, 같은 다이어그램의 신구 명칭이라는 점을 명시하는 것이 유용
- 출처: [Communication diagram - Wikipedia](https://en.wikipedia.org/wiki/Communication_diagram), [Communication Diagram - Sparx Systems UML2 Tutorial](https://sparxsystems.com/resources/tutorials/uml2/communication-diagram.html)

### 오브젝트 다이어그램(Object Diagram) — 클래스 다이어그램과의 관계 (신규)
- 기존 페이지4는 class diagram만 다루고, 그와 짝을 이루는 **오브젝트(객체) 다이어그램**은 다루지 않았음
- **클래스 다이어그램**은 클래스(설계도, 추상적 형태)를 표현하고, **오브젝트 다이어그램**은 그 클래스의 실제 **인스턴스(객체)** 를 특정 시점의 값과 함께 표현하는 "런타임 스냅샷" 성격의 다이어그램 — 클래스 다이어그램이 청사진이라면 오브젝트 다이어그램은 그 청사진으로 지어진 실제 건물의 한 순간을 찍은 사진
- 출처: [Class diagrams vs Object diagrams - Visual Paradigm](https://guides.visual-paradigm.com/class-diagrams-vs-object-diagrams-in-uml/), [UML Object Diagram - Guru99](https://www.guru99.com/uml-object-diagram.html)

## Phase 2 — 자체 검토

- NCS 원문이 채택한 4개 구조적 다이어그램(activity/class/component/deployment) 분류를 그대로 유지하고, object diagram은 "class diagram과 짝을 이루는 인접 개념"으로 class diagram aside 안에 보강하는 형태로 반영(별도 신규 다이어그램 항목으로 만들지 않음 — NCS 분류를 임의로 확장하지 않기 위함)
- Communication diagram 명칭은 collaboration diagram과 정확히 같은 대상을 가리키므로, 기존 aside 안에 "= Communication Diagram(UML2)" 형태로 병기하는 것으로 충분

## Phase 3 — 결론

2개 페이지(3. UML과 행위적 다이어그램 — Communication 명칭 병기, 4. UML 구조적 다이어그램 — Object 다이어그램 보강)에 신규 개념 2건 반영. 신규 Box 용어 없음(기존 `UML(Unified Modeling Language)` 유지, 세부 명칭은 페이지 레벨에서만 반영).
