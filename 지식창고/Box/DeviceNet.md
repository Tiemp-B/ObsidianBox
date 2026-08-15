---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 필드버스
---

# Summary

DeviceNet은 [[CAN(Controller Area Network)]]의 물리·데이터링크 계층을 기반으로 하는 산업용 필드버스로, 센서·액추에이터 같은 현장 장치를 PLC와 연결하는 데 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>DeviceNet의 특징</aside>

- CAN을 물리 계층으로 사용하지만, [[CANopen]]과는 별개로 발전한 애플리케이션 계층 표준(주로 북미 계열 산업 자동화에서 채택)
- 전원 공급과 데이터 통신을 하나의 케이블로 함께 전달할 수 있어 배선을 단순화함
- 하나의 버스에 여러 센서·액추에이터·PLC를 연결하는 마스터-슬레이브 또는 피어투피어 통신을 지원

<aside>다른 CAN 기반 프로토콜과의 관계</aside>

[[CANopen]]과 DeviceNet은 둘 다 CAN 기반이지만 서로 다른 애플리케이션 계층 표준이라, 같은 CAN 물리 계층을 쓰더라도 프로토콜 스택이 달라 직접 호환되지는 않는다 — 어떤 표준을 채택할지는 산업 분야·지역 관례에 따라 달라진다.

---

<aside>핵심 정리</aside>

- DeviceNet은 CAN을 물리 계층으로 쓰는 산업용 필드버스로, 센서·액추에이터를 PLC와 연결하는 데 쓰인다
- CANopen과는 서로 다른 애플리케이션 계층 표준이라 직접 호환되지 않는다

---

<aside>관련 노트</aside>

- 원 페이지: [[7. 로봇 제어기 통신 프로토콜 심화]]
- 관련: [[CAN(Controller Area Network)]], [[CANopen]]
