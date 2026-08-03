---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 모니터링
  - 산업자동화
---

# Summary

RTU(원격 단말 장치)는 현장의 센서·설비 신호를 수집해 **원거리의 중앙 감시 시스템(SCADA)으로 전달**하는 현장 장치로, 넓은 지역에 분산된 설비를 원격 감시할 때 PLC 대신 흔히 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>RTU의 역할과 PLC와의 차이</aside>

- RTU는 주로 원거리(수 km 이상 떨어진 상하수도, 송전선 등)에 설치되어 센서 데이터를 수집하고 통신망을 통해 중앙으로 전달하는 데 초점
- [[PLC(Programmable Logic Controller)]]는 복잡한 제어 로직 실행에 강점이 있는 반면, RTU는 전통적으로 데이터 수집·원격 통신에 더 특화되어 왔음(다만 최근에는 기능이 상당 부분 겹침)
- [[SCADA]] 시스템에서 RTU는 현장과 중앙 감시 시스템을 잇는 통신 접점 역할을 함

"RTU는 데이터를 수집만 할 뿐, 통신망을 통해 원격의 중앙 시스템으로 전달하는 기능은 없다"라는 서술은 오답이다 — RTU의 핵심은 오히려 **수집한 데이터를 원격 통신으로 중앙 SCADA 시스템에 전달**하는 것이며, 이 원격 통신 기능이 이름(Remote Terminal Unit)의 핵심이다.

<aside>SCADA 구조에서의 위치</aside>

SCADA 시스템은 현장의 RTU·PLC로부터 데이터를 수집해 중앙에서 감시·기록하고, 필요하면 원격으로 제어 명령을 내려보내는 구조를 이룬다 — RTU·PLC는 그 현장 접점 역할을 한다.

---

<aside>핵심 정리</aside>

- RTU는 현장 데이터를 수집해 원격 통신으로 중앙 SCADA 시스템에 전달하는 현장 장치다
- 데이터 수집에서 그치지 않고 원격 전달까지가 핵심 기능이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. SCADA 구조와 산업용 모니터링 시스템]]
- 관련: [[SCADA]], [[PLC(Programmable Logic Controller)]]
