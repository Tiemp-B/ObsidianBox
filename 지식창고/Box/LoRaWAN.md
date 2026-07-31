---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 무선통신
  - IoT
---

# Summary

LoRaWAN은 [[LPWAN(Low Power Wide Area Network)]] 범주의 대표적인 통신 규격으로, LoRa라는 독자적인 변조 방식을 물리 계층으로 사용해 **수 km 범위의 저전력·저속 통신**을 구현한다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>LoRaWAN의 구조</aside>

- 물리 계층(LoRa 변조 방식)은 확산 스펙트럼 기술을 이용해 잡음에 강하고 먼 거리까지 신호를 전달
- 다수의 단말(센서)이 게이트웨이 하나에 스타(star) 토폴로지로 연결되며, 게이트웨이는 다시 네트워크 서버로 데이터를 전달
- 배터리 하나로 수년간 동작 가능할 정도로 저전력이며, 대신 전송 속도와 전송 빈도는 낮게 제한됨

"LoRaWAN은 여러 단말이 서로를 직접 중계하는 메시(mesh) 네트워크 구조를 기본으로 한다"라는 서술은 오답이다 — LoRaWAN의 핵심 구조는 오히려 **단말들이 게이트웨이 하나로 직접 연결되는 스타 토폴로지**이며, 메시 구조가 아니다.

<aside>다른 LPWAN 기술과의 관계</aside>

LoRaWAN은 비면허 대역을 사용해 별도의 통신사 가입 없이 자체 네트워크를 구축할 수 있다는 점이 셀룰러 기반 LPWAN 기술(NB-IoT 등)과의 차이점이다 — 넓은 농장·산업단지 등에 분산된 로봇·센서의 원격 모니터링에 적합하다.

---

<aside>핵심 정리</aside>

- LoRaWAN은 LoRa 변조 방식을 물리 계층으로 쓰는 대표적인 LPWAN 규격이다
- 단말-게이트웨이 간 스타 토폴로지 구조이며, 메시 네트워크가 아니다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. LoRaWAN과 저전력 광역 통신]], [[7. 로봇 제어기 통신 프로토콜 심화]]
- 관련: [[LPWAN(Low Power Wide Area Network)]]
