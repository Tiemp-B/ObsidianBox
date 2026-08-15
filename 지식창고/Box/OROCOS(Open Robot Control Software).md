---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 로봇소프트웨어아키텍처설계
---

# Summary

OROCOS(Open Robot Control Software)는 **실시간성이 중요한 저수준 제어 루프**를 컴포넌트 기반으로 구현하는 데 특화된 오픈소스 로봇 제어 프레임워크다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>OROCOS의 특화 영역</aside>

- 로봇 제어 시스템 중에서도 특히 **실시간 제어 루프(모터 제어, 센서 피드백 등)를 실시간 보장이 필요한 수준으로** 구현하는 데 초점
- 컴포넌트(Task Context) 단위로 제어 로직을 구성해 재사용성을 높임
- 상위 응용 로직·시각화보다는 하드웨어에 가까운 저수준 실시간 제어에 강점을 둔 프레임워크

<aside>로봇 소프트웨어 프레임워크 생태계에서의 위치</aside>

[[ROS(Robot Operating System)]]가 로봇 전체 시스템의 노드 간 통신·상위 애플리케이션 개발에 강점이 있다면, OROCOS는 그중에서도 실시간 보장이 필요한 제어 루프 부분을 담당하는 데 특화되어 있어, 실제로는 ROS와 OROCOS를 함께 조합해 쓰는 사례도 있다.

---

<aside>핵심 정리</aside>

- OROCOS는 실시간성이 중요한 저수준 제어 루프에 특화된 컴포넌트 기반 로봇 제어 프레임워크다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 프레임워크의 목적과 OROCOS]]
- 관련: [[ROS(Robot Operating System)]]
