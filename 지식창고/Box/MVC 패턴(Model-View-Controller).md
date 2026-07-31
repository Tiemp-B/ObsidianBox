---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 로봇소프트웨어아키텍처설계
---

# Summary

MVC 패턴은 애플리케이션을 **데이터(Model)·화면(View)·입력 처리(Controller)** 세 역할로 분리해, 화면이 바뀌어도 데이터 로직을 건드리지 않도록 하는 대표적인 소프트웨어 아키텍처 패턴이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>MVC 각 요소의 역할</aside>

| 요소 | 역할 |
|---|---|
| Model | 데이터와 비즈니스 로직을 담당 — 화면과 무관하게 독립적으로 존재 |
| View | 사용자에게 보여지는 화면 — Model의 데이터를 표시만 함 |
| Controller | 사용자 입력을 받아 Model을 갱신하고, 그 결과를 View에 반영 |

Model은 View를 직접 알지 못하며, View가 여러 개(웹 화면, 모바일 화면 등)로 바뀌어도 Model 로직은 그대로 재사용할 수 있다는 것이 핵심 이점이다.

"MVC 패턴에서는 View가 데이터를 직접 가공·저장하는 로직을 포함해야 한다"라는 서술은 오답이다 — MVC의 핵심은 오히려 **View는 표시만 담당하고, 데이터 가공·저장 로직은 Model에 있어야 한다**는 역할 분리이며, 이를 어기면 MVC의 이점(재사용성·유지보수성)이 사라진다.

<aside>다른 디자인 패턴과의 관계</aside>

MVC의 Model이 상태 변화를 View에 알리는 방식은 흔히 [[옵저버 패턴(Observer Pattern)]]으로 구현된다 — Model이 바뀌면 이를 구독하고 있는 View들이 자동으로 갱신되는 구조다.

---

<aside>핵심 정리</aside>

- MVC는 데이터(Model)·화면(View)·입력 처리(Controller)를 분리하는 아키텍처 패턴이다
- View는 표시만 담당하며 데이터 가공 로직을 가지면 안 된다는 역할 분리가 핵심이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 디자인 패턴과 MVC]]
- 관련: [[옵저버 패턴(Observer Pattern)]], [[싱글톤 패턴(Singleton Pattern)]]
