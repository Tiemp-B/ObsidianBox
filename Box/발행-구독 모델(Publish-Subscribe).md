---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신패턴
  - 모니터링
---

# Summary

발행-구독(Publish-Subscribe) 모델은 발행자가 특정 **토픽에 메시지를 보내면, 그 토픽을 구독한 모든 수신자에게 자동으로 전달**되는 통신 패턴으로, 발행자와 구독자가 서로의 존재를 몰라도 통신할 수 있다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>발행-구독 모델의 특징</aside>

- 발행자(Publisher)는 특정 수신자를 지정하지 않고, 그저 정해진 토픽에 메시지를 발행(publish)함
- 구독자(Subscriber)는 관심 있는 토픽을 구독(subscribe)해두면, 그 토픽에 발행되는 모든 메시지를 자동으로 받음
- 발행자와 구독자가 서로를 몰라도 되는 **느슨한 결합(decoupling)**이 핵심 — 새 구독자가 추가되거나 발행자가 바뀌어도 서로 코드를 수정할 필요가 없음

<aside>ROS·MQTT에서의 구현</aside>

[[ROS(Robot Operating System)]]의 토픽 통신과 [[MQTT]]는 모두 발행-구독 모델을 구현한 대표적인 사례로, 여러 센서(발행자)의 데이터를 여러 모니터링 도구(구독자)가 동시에 받아볼 수 있게 한다.

---

<aside>핵심 정리</aside>

- 발행-구독 모델은 발행자가 토픽에 메시지를 보내면 구독자들이 자동으로 받는 느슨하게 결합된 통신 패턴이다
- 발행자가 구독자를 미리 알거나 지정할 필요가 없다는 점이 핵심이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 통신 모델(발행-구독·요청-응답·액션)]], [[2. MQTT·WebSocket과 실시간 모니터링 통신]], [[2. CoAP와 경량 IoT 프로토콜]], [[3. ROS2와 DDS QoS]]
- 관련: [[ROS(Robot Operating System)]], [[MQTT]], [[요청-응답 모델(Request-Response)]]
