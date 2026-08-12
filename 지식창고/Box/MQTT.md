---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - IoT
---

# Summary

MQTT는 **브로커를 중심으로 한 발행-구독(Publish-Subscribe) 모델**의 경량 메시징 프로토콜로, TCP 위에서 동작하며 대역폭이 제한된 IoT·로봇 모니터링 환경에서 널리 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>MQTT의 발행-구독 구조</aside>

- 발행자(Publisher)는 특정 "토픽"에 메시지를 보내고, 구독자(Subscriber)는 관심 있는 토픽을 구독해 메시지를 받음 — 발행자와 구독자는 서로를 직접 알 필요가 없고 **브로커가 중계**함
- [[요청-응답 모델(Request-Response)]]과 달리, 발행자는 누가 구독하는지 몰라도 되고 구독자는 여러 발행자의 메시지를 하나의 토픽으로 받을 수 있음
- QoS 레벨(0/1/2)로 메시지 전달 신뢰성을 선택할 수 있음(최대 한 번, 최소 한 번, 정확히 한 번)

"MQTT는 발행자와 구독자가 브로커 없이 서로 직접 연결해 메시지를 주고받는 P2P 프로토콜이다"라는 서술은 오답이다 — MQTT의 핵심은 오히려 **브로커가 중간에서 발행자·구독자를 중계**하는 구조이며, 발행자와 구독자는 서로 직접 연결되지 않는다.

<aside>로봇 모니터링에서의 활용</aside>

여러 로봇(발행자)이 상태 데이터를 각자의 토픽으로 발행하면, 모니터링 대시보드(구독자)가 필요한 토픽만 구독해 받아보는 구조로 다대다 상태 모니터링을 효율적으로 구성할 수 있다. [[CoAP(Constrained Application Protocol)]]과 달리 발행-구독 모델이라는 점이 핵심 차이다.

---

<aside>핵심 정리</aside>

- MQTT는 브로커를 통한 발행-구독 모델의 경량 메시징 프로토콜이다
- 발행자·구독자가 직접 연결되는 P2P 방식이 아니라, 브로커가 중계하는 구조다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. MQTT·WebSocket과 실시간 모니터링 통신]], [[1. 로봇 제어기 특성 개요]], [[3. SCADA 구조와 산업용 모니터링 시스템]]
- 관련: [[발행-구독 모델(Publish-Subscribe)]], [[CoAP(Constrained Application Protocol)]], [[QoS(Quality of Service)]], [[MQTT-SN(MQTT for Sensor Networks)]]
