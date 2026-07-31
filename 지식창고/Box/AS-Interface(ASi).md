---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 필드버스
---

# Summary

AS-Interface(ASi)는 센서·액추에이터처럼 **on/off 신호 몇 비트만 주고받는 최하위 레벨 장치**를 하나의 2선식 케이블로 묶어 연결하는 초저가형 필드버스다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>AS-Interface의 설계 목적</aside>

- 리밋 스위치, 근접 센서, 단순 솔레노이드 밸브처럼 데이터량이 매우 작은(수 비트) 장치를 배선 절감을 목적으로 연결
- 전원과 데이터를 하나의 케이블(2선)로 동시에 전달 — 별도 전원선이 필요 없음
- [[PROFIBUS]]나 [[CAN(Controller Area Network)]] 같은 상위 필드버스보다 훨씬 단순하고 느리지만, 배선·설치 비용이 훨씬 저렴함

"AS-Interface는 대용량 센서 데이터나 비전 영상 전송에 적합한 고속 필드버스다"라는 서술은 오답이다 — AS-Interface는 오히려 **온/오프 수준의 극소량 데이터를 최소 배선으로 연결**하는 것이 목적이며, 대용량·고속 데이터에는 적합하지 않다.

<aside>필드버스 계층에서의 위치</aside>

공장 자동화·로봇 셀 배선에서는 흔히 상위(PLC-PLC 간 등)에는 [[PROFIBUS]]·[[EtherCAT]] 같은 고속 필드버스를, 최하위 센서·액추에이터 단에는 AS-Interface처럼 단순한 버스를 함께 조합해 배선 복잡도와 비용을 낮춘다.

---

<aside>핵심 정리</aside>

- AS-Interface는 on/off 수준의 최하위 장치를 2선식 케이블 하나로 연결하는 초저가형 필드버스다
- 대용량·고속 데이터 전송용이 아니라, 배선 절감이 목적이다

---

<aside>관련 노트</aside>

- 원 페이지: [[7. 로봇 제어기 통신 프로토콜 심화]]
- 관련: [[PROFIBUS]], [[CAN(Controller Area Network)]], [[필드버스(Fieldbus)]]
