---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - EtherCAT
  - 통신프로토콜
---

# Summary

PDO(Process Data Object)는 [[CANopen]]·[[EtherCAT]] 계열 프로토콜에서 **실시간 제어 데이터(위치·속도·토크 명령 등)를 주기적으로 빠르게 주고받기 위한 데이터 객체**로, 설정용 데이터를 다루는 SDO와 대비된다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>PDO와 SDO의 역할 분담</aside>

| 구분 | 용도 | 특성 |
|---|---|---|
| PDO(Process Data Object) | 위치·속도·토크 등 실시간 제어 데이터 | 주기적·고속 전송, 오버헤드 최소화 |
| SDO(Service Data Object) | 파라미터 설정, 진단 정보 조회 등 | 비주기적, 상대적으로 느려도 되는 데이터 |

PDO는 매 제어 주기마다 반복 전송되어야 하므로 오버헤드를 최소화하도록 설계되어 있고, SDO는 초기 설정이나 드문 조회에 쓰여 속도보다 유연성이 중요하다.

<aside>로봇 제어기 통신에서의 위치</aside>

로봇 관절 서보 드라이버가 CANopen/EtherCAT 네트워크 위에서 매 제어 주기마다 목표 위치·속도 명령을 받는 것이 바로 PDO 통신의 전형적인 예다.

---

<aside>핵심 정리</aside>

- PDO는 실시간 제어 데이터를 주기적으로 고속 전송하기 위한 데이터 객체다
- 설정·진단 데이터를 다루는 SDO와 역할이 구분된다

---

<aside>관련 노트</aside>

- 원 페이지: [[7. 로봇 제어기 통신 프로토콜 심화]], [[1. 로봇 제어기 특성 개요]]
- 관련: [[CANopen]], [[EtherCAT]]
