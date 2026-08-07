---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - ROS파라미터서버·ROS2Lifecycle노드·DDS디스커버리 (2026-08-07)

이 세세항목은 필기 1과목에서 이미 다룬 통신 패턴(발행-구독·요청-응답·액션)·필드버스(CAN 등)는 반복하지 않고, ROS/ROS2 고유 아키텍처에 집중한다는 것이 페이지1 개요에 명시돼 있음. 개요(허브) 링크 정상. 문제은행 10문항 전부 기존 3페이지 + 과목1 교차 참조로 커버 확인. 목표(추가정보 발굴)에 맞춰 ROS/ROS2 아키텍처 고유의 미반영 개념을 조사했다.

## Phase 1 — 조사

### ROS(1) 파라미터 서버(Parameter Server) — 누락된 핵심 구성요소 (신규)
- 기존 페이지2는 ROS의 구조를 노드·마스터·패키지로 설명하는데, ROS1 아키텍처의 또 다른 핵심 구성요소인 **파라미터 서버**가 빠져 있었음
- 파라미터 서버는 마스터가 함께 제공하는 **전역 설정값 저장소**로, 로봇 이름·센서 임계값처럼 여러 노드가 공유해야 하는 값을 코드에 하드코딩하지 않고 실행 시점에 조회·변경할 수 있게 해줌
- 토픽(지속적 데이터 스트림)이나 서비스(1회성 요청-응답)와 달리, 파라미터는 **비교적 정적인 설정값**을 위한 것이라는 점이 성격 차이
- 출처: [ROS Parameter Server - Clearpath Robotics](https://docs.clearpathrobotics.com/docs/ros1noetic/ros/ros/tutorials/ros101/intermediate/ros_parameter_server/), [What is ROS Parameter Server? - The Construct](https://www.theconstruct.ai/ros-5-mins-012-ros-parameter-server/)

### ROS2 Lifecycle Node(관리형 노드) — ROS1과 달라진 노드 관리 방식 (신규)
- 기존 페이지3은 ROS2의 통신 계층(DDS/QoS) 변화만 다루고, ROS2에서 노드 자체의 상태 관리가 어떻게 개선됐는지는 다루지 않았음
- ROS1의 노드는 실행되면 바로 동작하는 단순한 구조였지만, ROS2는 **Lifecycle Node(관리형 노드)** 개념을 도입해 노드가 `Unconfigured → Inactive → Active → Finalized`라는 명시적 상태를 거치도록 함
- Inactive 상태에서는 노드가 설정은 마쳤지만 아직 발행·구독 등 실제 동작(콜백)은 하지 않아, 여러 노드를 미리 준비시켜 놓았다가 **동시에 Active로 전환**하는 등 시스템 전체의 시작·종료를 더 정교하게 제어할 수 있음
- 출처: [How to Use ROS 2 Lifecycle Nodes - Foxglove](https://foxglove.dev/blog/how-to-use-ros2-lifecycle-nodes), [Managed nodes - design.ros2.org](https://design.ros2.org/articles/node_lifecycle.html)

### DDS 디스커버리(Discovery) 메커니즘 — "마스터 없이 서로 찾는다"의 구체적 원리 (신규)
- 기존 페이지3은 "DDS는 마스터 없이 노드가 서로를 자동으로 찾는다"고만 서술하고, 그 구체적 방식은 다루지 않았음
- DDS 표준은 **SDP(Simple Discovery Protocol)** 라는 완전한 P2P 방식의 탐색 프로토콜을 규정하며, 별도 서버·브로커 없이 참여자(participant)들이 네트워크상에서 서로를 찾음
- 일반적으로 **멀티캐스트(multicast)** 메시지로 서로의 존재를 알리는 방식을 기본으로 사용하며, 멀티캐스트가 불가능한 네트워크 환경에서는 참여자 목록을 수동 설정하거나 별도의 디스커버리 서버를 두는 대안도 있음(구현체별 차이, 참고 수준)
- 출처: [Discovery of DDSI participants - Eclipse Cyclone DDS](https://cyclonedds.io/docs/cyclonedds/latest/about_dds/discovery_participants.html)

## Phase 2 — 자체 검토

- ROS2 Lifecycle Node의 세부 상태 전이(activate/deactivate/cleanup/shutdown 등 전이 함수명)까지는 넣지 않고, 4대 상태와 "왜 필요한가"라는 개념만 반영(§2 원칙)
- DDS 디스커버리는 구현체별(FastDDS 서버/클라이언트 방식 등) 차이가 있어, 페이지에는 "SDP+멀티캐스트가 기본"이라는 표준 수준의 개념만 반영하고 구현체별 차이는 조사md에만 참고로 남김
- 파라미터 서버는 ROS1 고유 개념이며 ROS2는 노드별 파라미터로 구조가 달라졌으나, 이 세세항목의 NCS·문제은행 범위가 ROS1 아키텍처 기초를 포함하므로 반영이 적절하다고 판단

## Phase 3 — 결론

2개 페이지(2. ROS 아키텍처 — 파라미터 서버 1건, 3. ROS2와 DDS QoS — Lifecycle Node·DDS 디스커버리 2건)에 신규 개념 3건 반영. Box 용어는 신규 생성하지 않고 기존 `ROS(Robot Operating System)`·`DDS(Data Distribution Service)` Box 용어에 보강.
