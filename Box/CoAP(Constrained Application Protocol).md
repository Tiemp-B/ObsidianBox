---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 로봇응용
---

# Summary

CoAP은 메모리·연산 능력이 제한된 IoT 장치를 위해 설계된 **경량 애플리케이션 계층 프로토콜**로, HTTP와 비슷한 REST 방식을 쓰면서도 UDP 위에서 동작해 오버헤드를 줄인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>CoAP의 설계 목적과 특징</aside>

- HTTP처럼 GET/POST/PUT/DELETE 같은 [[REST API(Representational State Transfer)]] 방식의 메서드를 사용해 개발자에게 익숙함
- [[TCP_IP|TCP]] 대신 [[UDP]] 위에서 동작해 연결 설정 오버헤드를 없애고, 헤더 크기도 HTTP보다 훨씬 작게 설계됨 — 저전력·저용량 IoT 장치에 적합
- 신뢰성이 필요한 메시지는 CoAP 자체의 재전송 메커니즘으로 일부 보완함

<aside>다른 IoT 프로토콜과의 비교</aside>

CoAP은 REST 방식(요청-응답)의 경량화에 초점을 둔 반면, [[MQTT]]는 [[발행-구독 모델(Publish-Subscribe)]] 방식으로 다대다 메시지 배포에 초점을 둔다 — 둘 다 IoT 경량 프로토콜이지만 통신 모델 자체가 다르다. [[MQTT-SN(MQTT for Sensor Networks)|MQTT-SN]]은 MQTT의 발행-구독 모델 자체를 경량화한 별도의 프로토콜이다.

<aside>Observe 확장 — CoAP도 구독형 동작 가능</aside>

CoAP은 기본이 요청-응답이지만, Observe 옵션(RFC 7641)을 쓰면 리소스 값이 바뀔 때마다 서버가 클라이언트에게 알아서 통지하는 구독형 동작도 가능하다. 다만 MQTT처럼 브로커가 다수 구독자를 중계하는 구조가 아니라, 서버가 구독자 목록을 직접 관리하며 통지한다는 점이 다르다.

---

<aside>핵심 정리</aside>

- CoAP은 UDP 기반의 경량 REST 스타일 프로토콜로, 제한된 IoT 장치를 위해 설계됐다
- TCP 기반 HTTP와 달리 헤더가 훨씬 작고, MQTT(발행-구독)와는 통신 모델 자체가 다르다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. CoAP와 경량 IoT 프로토콜]]
- 관련: [[MQTT]], [[REST API(Representational State Transfer)]], [[UDP]]
