---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 미들웨어
  - 로봇SW
---

# Summary

ROS(Robot Operating System)는 로봇 소프트웨어의 각 기능을 **독립된 노드(node)로 분리**하고, 노드 간 [[발행-구독 모델(Publish-Subscribe)]]·요청-응답·액션 통신으로 연결하는 오픈소스 로봇 미들웨어 프레임워크다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>ROS의 핵심 구조 — 그래프·노드·마스터</aside>

- 각 기능(센서 드라이버, 경로계획, 모터 제어 등)을 별도의 프로세스인 **노드**로 구현해, 하나의 노드가 죽어도 전체 시스템이 즉시 마비되지 않도록 함
- 노드들은 **토픽(topic)**을 통해 [[발행-구독 모델(Publish-Subscribe)]]로 데이터를 주고받거나, [[ROS Service]]/[[ROS Action]]으로 요청-응답 방식 통신을 함
- 전체 노드 간 연결 구조는 그래프로 표현되며(ROS 그래프), ROS1에서는 마스터(master)가 노드들이 서로를 찾도록 중개하는 역할을 함(ROS2는 [[DDS(Data Distribution Service)]] 기반의 탈중앙 discovery로 전환)
- ROS1은 마스터와 함께 여러 노드가 공유하는 정적 설정값을 저장하는 **파라미터 서버**를 제공함. ROS2는 노드가 실행 즉시 동작하는 ROS1과 달리, `Unconfigured→Inactive→Active→Finalized` 상태를 명시적으로 거치는 **Lifecycle Node**로 노드 시작·종료를 더 정교하게 관리할 수 있음

<aside>다른 로봇 프레임워크와의 관계</aside>

ROS는 [[OPRoS(Open Platform for Robotics Services)]]·[[OROCOS(Open Robot Control Software)]]와 함께 로봇 소프트웨어 재사용성을 목표로 하는 미들웨어이며, 특히 방대한 오픈소스 패키지 생태계와 [[Gazebo]] 시뮬레이터와의 긴밀한 연동이 강점이다.

---

<aside>핵심 정리</aside>

- ROS는 로봇 기능을 독립된 노드로 분리하고 발행-구독·서비스·액션 통신으로 연결하는 미들웨어다
- 모든 기능을 하나의 프로세스에서 처리하는 모놀리식 구조가 아니다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. ROS 아키텍처(그래프·노드·마스터)]], [[1. 로봇 구성요소간 통신프로토콜 개요]], [[3. 통신 모델(발행-구독·요청-응답·액션)]], [[3. 로봇 운영체제의 종류]], [[1. 로봇 제어기 특성 개요]]
- 관련: [[발행-구독 모델(Publish-Subscribe)]], [[ROS Service]], [[ROS Action]], [[DDS(Data Distribution Service)]], [[Gazebo]]
