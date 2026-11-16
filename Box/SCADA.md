---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 모니터링
  - 산업자동화
---

# Summary

SCADA(감시 제어 및 데이터 수집)는 넓은 지역에 분산된 [[PLC(Programmable Logic Controller)]]·[[RTU(Remote Terminal Unit)]]로부터 데이터를 수집해 **중앙에서 감시하고, 필요시 원격으로 제어 명령을 내려보내는** 산업 자동화 감시 시스템이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>SCADA 시스템의 계층 구조</aside>

- 현장 계층: PLC·RTU가 센서 신호를 읽고 액추에이터를 직접 제어
- 통신 계층: 현장 장치와 중앙 시스템을 잇는 통신망([[Modbus]], [[PROFIBUS]] 등)
- 감시 계층: [[HMI(Human-Machine Interface)]] 화면으로 사람에게 상태를 보여주고, 데이터를 기록·분석

SCADA는 현장 제어 로직 자체를 직접 수행하기보다, **현장 장치가 수집한 데이터를 모아 감시하고 상위 판단·명령을 내리는** 역할에 가깝다.

<aside>DCS와의 관계</aside>

[[DCS(Distributed Control System)]]가 하나의 플랜트 내에서 제어 기능 자체를 분산 배치하는 데 초점을 둔다면, SCADA는 지리적으로 넓게 흩어진 설비를 원격으로 감시·수집하는 데 더 초점을 둔다는 차이가 있다.

---

<aside>핵심 정리</aside>

- SCADA는 현장 PLC·RTU의 데이터를 수집해 중앙에서 감시하고 원격 제어하는 산업 자동화 시스템이다
- 단순 시각화 화면이 아니라 데이터 수집·원격 제어까지 포함한다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. SCADA 구조와 산업용 모니터링 시스템]], [[4. 데이터 시각화와 알람(HMI)]], [[7. 로봇 제어기 통신 프로토콜 심화]]
- 관련: [[PLC(Programmable Logic Controller)]], [[RTU(Remote Terminal Unit)]], [[HMI(Human-Machine Interface)]], [[DCS(Distributed Control System)]]
