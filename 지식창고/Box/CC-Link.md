---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 필드버스
---

# Summary

CC-Link는 일본에서 개발된 산업용 필드버스로, PLC와 다수의 I/O·센서·액추에이터 모듈을 하나의 버스로 연결해 배선을 단순화하는 데 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>CC-Link의 특징</aside>

- PLC(마스터)와 다수의 원격 I/O 슬레이브 장치를 하나의 케이블로 연결하는 마스터-슬레이브 구조
- [[PROFIBUS]]·[[DeviceNet]] 등과 마찬가지로 필드버스 계열이며, 특히 일본계 산업 자동화 설비(공작기계, 생산라인)에서 널리 채택됨
- 배선 수를 줄이면서도 결정론적(주기적으로 정해진 시간 안에 데이터가 오가는) 통신을 지원해 실시간 제어에 적합

<aside>다른 필드버스와의 관계</aside>

CC-Link, [[PROFIBUS]], [[DeviceNet]], [[Profinet]], [[EtherCAT]] 등은 모두 "PLC/제어기와 다수의 현장 장치를 하나의 버스로 묶는다"는 목적은 같지만, 지역(유럽계·일본계 등)과 세대(이더넷 기반 여부)에 따라 다른 표준으로 발전해온 것이다.

---

<aside>핵심 정리</aside>

- CC-Link는 PLC를 마스터로 하는 마스터-슬레이브 구조의 산업용 필드버스다
- 배선 절감과 결정론적 실시간 통신이 목적이다

---

<aside>관련 노트</aside>

- 원 페이지: [[7. 로봇 제어기 통신 프로토콜 심화]]
- 관련: [[PROFIBUS]], [[DeviceNet]], [[필드버스(Fieldbus)]]
