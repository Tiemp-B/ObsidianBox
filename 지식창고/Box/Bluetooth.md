---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 무선통신
---

# Summary

Bluetooth는 **근거리(수~수십 m)에서 저전력으로 장치 간 무선 연결**을 제공하는 개인 근거리 통신망(PAN) 규격으로, 로봇 제어기와 스마트폰·PC 간 간단한 페어링 통신에 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Bluetooth의 특징</aside>

- 통신 범위가 [[Wi-Fi]]보다 짧은 대신(보통 10m 내외), 소비 전력이 낮고 페어링(연결 설정)이 간단함
- 1:1 또는 소수 장치 간 근거리 연결에 적합 — 다수 장치가 넓은 범위에서 통신해야 하는 경우엔 Wi-Fi나 [[Zigbee]] 메시 네트워크가 더 적합
- Bluetooth Low Energy(BLE) 버전은 초저전력을 우선해 웨어러블·센서 태그 등에 쓰임

"Bluetooth는 원거리(수 km) 산업 현장 전체를 커버하는 광역 무선 통신 규격이다"라는 서술은 오답이다 — Bluetooth는 근거리·저전력 개인 통신망 규격이며, 광역 커버리지가 필요하면 [[LPWAN(Low Power Wide Area Network)]]·[[LoRaWAN]] 계열이 적합하다.

<aside>로봇 제어기 통신에서의 위치</aside>

로봇 제어기의 통신 프로토콜 스택에서 Bluetooth는 [[CAN(Controller Area Network)]]·[[EtherCAT]] 같은 유선 필드버스와 달리, 사람이 근거리에서 태블릿·스마트폰으로 로봇을 조작·모니터링할 때 쓰이는 무선 링크로 위치한다.

---

<aside>핵심 정리</aside>

- Bluetooth는 근거리·저전력 무선 통신 규격으로, 원거리 광역 통신에는 부적합하다
- 광역 커버리지가 필요하면 LPWAN·LoRaWAN, 넓은 범위 메시 통신이 필요하면 Zigbee/Wi-Fi가 더 적합하다

---

<aside>관련 노트</aside>

- 원 페이지: [[7. 로봇 제어기 통신 프로토콜 심화]]
- 관련: [[Wi-Fi]], [[Zigbee]], [[LPWAN(Low Power Wide Area Network)]]
