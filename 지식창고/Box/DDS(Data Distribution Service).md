---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신
---

# Summary

DDS(Data Distribution Service)는 [[UDP]] 위에서 동작하는 **발행-구독 기반 실시간 데이터 배포 미들웨어 표준**으로, 토픽마다 세밀한 QoS 프로파일을 지정할 수 있으며 ROS2의 기본 통신 계층으로 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>DDS의 핵심 특징</aside>

- 중앙 브로커 서버 없이 발행자(Publisher)와 구독자(Subscriber)가 **네트워크상에서 서로를 자동으로 찾아 직접 연결**하는 탈중앙 구조(Discovery) — 표준이 규정하는 **SDP(Simple Discovery Protocol)** 라는 완전한 P2P 탐색 프로토콜로, 보통 멀티캐스트 메시지로 서로의 존재를 알려 상대를 찾음
- 토픽별로 신뢰성(신뢰성 있게 재전송할지), 이력 깊이(과거 몇 개 메시지를 유지할지), 마감시한 등 세밀한 [[QoS(Quality of Service)]] 프로파일을 독립적으로 설정 가능
- 주로 UDP 기반으로 지연시간을 최소화하면서, QoS 설정으로 필요한 만큼의 신뢰성을 확보

"DDS는 반드시 중앙 브로커 서버를 거쳐야만 발행자와 구독자가 통신할 수 있는 구조다"라는 서술은 오답이다 — DDS의 핵심 특징은 오히려 **중앙 브로커 없이 발행자·구독자가 자동으로 서로를 찾아 직접 통신**하는 탈중앙 구조다.

<aside>ROS2와의 관계</aside>

ROS2는 노드 간 [[발행-구독 모델(Publish-Subscribe)]] 통신을 자체 구현하지 않고 DDS를 실제 전송 계층으로 채택했다 — 토픽마다 QoS를 다르게 설정(예: 센서 데이터는 최신값 우선, 제어 명령은 신뢰성 우선)할 수 있는 것은 DDS의 QoS 프로파일 덕분이다.

---

<aside>핵심 정리</aside>

- DDS는 중앙 브로커 없이 발행자·구독자가 자동으로 서로를 찾는 탈중앙 실시간 데이터 배포 미들웨어다
- 토픽별 세밀한 QoS 설정이 가능하며, ROS2의 기본 전송 계층으로 쓰인다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. ROS2와 DDS QoS]], [[2. 원격제어 통신 프로토콜 개요]]
- 관련: [[QoS(Quality of Service)]], [[발행-구독 모델(Publish-Subscribe)]], [[UDP]]
