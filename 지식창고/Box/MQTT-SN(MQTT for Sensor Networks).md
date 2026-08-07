---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - IoT
---

# Summary

MQTT-SN은 **[[MQTT]]의 발행-구독 모델은 그대로 유지**하면서, TCP 없이도 동작하도록 경량화한 변형 프로토콜로, 배터리·메모리가 극히 제한된 센서 네트워크를 겨냥한다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>MQTT와의 차이</aside>

- MQTT는 [[TCP_IP|TCP]] 위에서 동작하지만, MQTT-SN은 [[UDP]]나 ZigBee 같은 **비TCP 매체**에서도 동작할 수 있음
- 문자열 토픽 이름 대신 **16비트 토픽 ID**를 사용해 매 메시지의 오버헤드를 더 줄임
- MQTT-SN 단말은 직접 MQTT 브로커에 붙지 않고, **게이트웨이**가 MQTT-SN ↔ MQTT를 변환해 중계함

"MQTT-SN은 MQTT와 통신 모델 자체가 달라 발행-구독 개념을 쓰지 않는다"라는 서술은 오답이다 — MQTT-SN은 발행-구독 모델을 그대로 유지한 채, 전송 계층과 메시지 형식만 더 경량화한 것이다.

<aside>CoAP과의 대비</aside>

[[CoAP(Constrained Application Protocol)]]이 요청-응답 모델을 경량화한 것이라면, MQTT-SN은 **발행-구독 모델을 경량화**한 것이다 — 저전력 IoT 프로토콜 경량화의 두 갈래로 대비할 수 있다.

---

<aside>핵심 정리</aside>

- MQTT-SN은 MQTT의 발행-구독 모델을 유지하면서 UDP/ZigBee 등 비TCP 매체에서 동작하도록 경량화한 프로토콜이다
- 토픽 ID(16비트)와 게이트웨이(MQTT 브로커 변환)를 사용한다
- CoAP(요청-응답 경량화)과 MQTT-SN(발행-구독 경량화)은 경량화 방향이 다르다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. CoAP와 경량 IoT 프로토콜]]
- 관련: [[MQTT]], [[CoAP(Constrained Application Protocol)]], [[UDP]]
