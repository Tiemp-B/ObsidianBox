---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 미들웨어
  - 로봇SW
---

# Summary

OPRoS는 국내(한국)에서 개발된 로봇 소프트웨어 플랫폼으로, 로봇 기능을 **재사용 가능한 컴포넌트 단위**로 개발·조합할 수 있도록 지원하는 컴포넌트 기반 로봇 미들웨어다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>OPRoS의 설계 목표</aside>

- 로봇의 각 기능(모터 제어, 센서 처리, 내비게이션 등)을 독립된 컴포넌트로 개발해, 다른 로봇 프로젝트에서도 재사용할 수 있게 함
- 컴포넌트 간 인터페이스를 표준화해, 서로 다른 개발자가 만든 컴포넌트도 조합해 하나의 로봇 시스템을 구성할 수 있도록 지원
- [[ROS(Robot Operating System)]]와 마찬가지로 로봇 소프트웨어 개발의 중복을 줄이고 재사용성을 높이는 것이 목적

"OPRoS는 특정 로봇 하드웨어 전용으로 설계되어 다른 로봇에는 이식할 수 없는 프레임워크다"라는 서술은 오답이다 — OPRoS의 핵심은 오히려 **컴포넌트 재사용성과 이식성**을 높이기 위한 표준화된 로봇 소프트웨어 플랫폼이라는 점이다.

<aside>다른 로봇 운영체제·프레임워크와의 관계</aside>

OPRoS, [[ROS(Robot Operating System)]], [[OROCOS(Open Robot Control Software)]]는 모두 로봇 소프트웨어의 재사용성·모듈화를 목표로 하는 플랫폼이지만, 개발 주체(국가·기관)와 컴포넌트 모델의 세부 구현 방식이 다르다.

---

<aside>핵심 정리</aside>

- OPRoS는 로봇 기능을 재사용 가능한 컴포넌트 단위로 개발하는 국내 로봇 소프트웨어 플랫폼이다
- 특정 하드웨어 전용이 아니라 이식성·재사용성을 목표로 한다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 로봇 운영체제의 종류]]
- 관련: [[ROS(Robot Operating System)]], [[OROCOS(Open Robot Control Software)]]
