---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - CoAP Observe·MQTT-SN·LoRaWAN SF·ADR·상보필터 (2026-08-07)

이 세세항목은 NCS 대응 학습모듈이 없어(§1-2에 따라 문제은행+도메인지식 기반) 기존 5페이지가 이미 정확한 도메인지식으로 작성돼 있고, 개요(허브) 링크도 이미 정상이었다. 목표(추가정보 발굴)에 맞춰 각 페이지에 새로 엮을 개념을 조사했다.

## Phase 1 — 조사

### CoAP의 Observe 확장(RFC 7641) — 구독형 동작 (신규)
- 기존 페이지2는 "CoAP는 1:1 요청-응답, MQTT는 발행-구독"이라고 대비했는데, CoAP도 **Observe 옵션(RFC 7641)** 을 쓰면 클라이언트가 리소스를 한 번 구독(GET + Observe 옵션)해 두고, 서버가 값이 바뀔 때마다 알아서 알림을 보내주는 **구독형(옵서버 패턴) 동작**이 가능함
- 다만 MQTT처럼 브로커가 다수 구독자를 중계하는 구조는 아니고, 서버(리소스 보유 디바이스)가 자신을 구독한 클라이언트 목록을 직접 관리하는 **1:N 직접 통지** 방식 — "CoAP는 구독 개념이 아예 없다"는 것은 과장이며, "MQTT와 동일한 브로커 중계 발행-구독"이라는 것도 오답
- 출처: [RFC 7641 - Observing Resources in CoAP](https://datatracker.ietf.org/doc/html/rfc7641)

### MQTT-SN — 센서 네트워크용 초경량 MQTT 변형 (신규)
- 기존 페이지2 제목이 "CoAP와 경량 IoT 프로토콜"인데, CoAP 외 경량 프로토콜 소개가 없었음. **MQTT-SN(MQTT for Sensor Networks)** 은 MQTT의 발행-구독 개념은 유지하면서, TCP 대신 **UDP나 ZigBee 같은 비TCP 매체**에서도 동작하도록 경량화한 변형
- 토픽 이름 대신 **16비트 토픽 ID**를 써서 매 메시지의 오버헤드를 더 줄이고, MQTT-SN ↔ MQTT 변환을 담당하는 **게이트웨이**를 통해 표준 MQTT 브로커와 연결됨
- CoAP(요청-응답형 경량화)와 MQTT-SN(발행-구독형 경량화)은 "경량화의 두 갈래"로 대비하기 좋은 소재
- 출처: [MQTT-SN: A Lightweight MQTT for NB-IoT Sensors](https://motive.com/glossary/what-is-mqtt-sn), [Introduction to MQTT-SN](http://www.steves-internet-guide.com/mqtt-sn/)

### LoRaWAN의 스프레딩 팩터(SF)와 적응형 데이터 전송률(ADR) (신규)
- 기존 페이지3은 "LoRaWAN은 느리다"고만 서술했는데, 왜/어떻게 느려지는지의 메커니즘이 빠져 있었음. **스프레딩 팩터(SF7~SF12)** 를 높일수록 신호가 잡음에 더 강해져 더 멀리 도달하지만, 하나의 심볼에 더 많은 처프(chirp)를 실어 보내는 대가로 **전송 속도는 느려짐** — 거리와 속도가 SF로 조절되는 트레이드오프
- **ADR(Adaptive Data Rate)**: 네트워크 서버가 게이트웨이에 가까운(신호 좋은) 단말에는 **낮은 SF·높은 속도**를, 먼(신호 약한) 단말에는 **높은 SF·낮은 속도**를 자동으로 배정해, 각 단말이 필요 이상으로 느리게/많은 전력으로 송신하지 않도록 최적화하는 기능
- 출처: [LoRaWAN Spreading Factor Explained - RF Wireless World](https://www.rfwireless-world.com/terminology/understanding-spreading-factor-lorawan), [What is Adaptive Data Rate (ADR)? - Wattsense](https://support.wattsense.com/hc/en-150/articles/11407112285725-What-is-the-Adaptative-Data-Rate-ADR)

### 상보 필터(Complementary Filter) — 칼만 필터의 경량 대안 (신규)
- 기존 페이지4는 평균/칼만 필터/다수결만 나열했는데, 칼만 필터와 자주 비교되는 **상보 필터**가 빠져 있었음. 상보 필터는 복잡한 확률 모델·행렬 연산 없이, 저주파 성분은 한 센서(예: 가속도계)에서, 고주파 성분은 다른 센서(예: 자이로)에서 각각 가져와 단순 가중합으로 결합하는 방식
- 계산량이 훨씬 적어 로봇의 저사양 MCU에도 올리기 쉬운 반면, 정상상태 정확도는 칼만 필터보다 다소 낮음 — "정밀도가 중요하면 칼만, 자원이 부족하고 빠른 반응이 필요하면 상보 필터"로 대비 가능
- 출처: [Sensor Fusion Techniques: Kalman vs. Complementary Filters](https://eureka.patsnap.com/article/sensor-fusion-techniques-kalman-filters-vs-complementary-filters), [From Complementary Filter to Kalman: Sensor Fusion in Drones](https://medium.com/@sayedebad.777/from-complementary-filter-to-kalman-sensor-fusion-in-drones-5fdd2a641e1a)

## Phase 2 — 자체 검토

- CoAP Observe는 "구독형이지만 브로커 중계가 아닌 1:N 직접 통지"라는 뉘앙스를 페이지 본문에 명확히 반영해, 기존 "CoAP=1:1 요청응답"과 모순처럼 보이지 않게 서술 필요
- 상보 필터의 "정확도 vs 반응속도" 수치(0.5도, 40% 등)는 출처마다 실험 조건이 달라 구체적 수치는 페이지에 넣지 않고 정성적 트레이드오프만 반영(§2 원칙)
- MQTT-SN은 기존 Box 용어 `MQTT.md`와 형제 관계이므로, 신규 Box 용어를 만들고 `MQTT.md`의 "관련 노트"에도 상호 링크 추가

## Phase 3 — 결론

4개 페이지(CoAP, LoRaWAN, 센서데이터융합, +CoAP페이지에 MQTT-SN 추가)에 새 개념을 반영하기로 결정. Box 용어는 MQTT-SN, 상보 필터(Complementary Filter) 신규 생성.
