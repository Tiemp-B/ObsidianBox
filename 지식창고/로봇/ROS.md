---
cssclasses: cornell-note
tags:
  - 로봇
---

# Summary

ROS(Robot Operating System)은 로봇 소프트웨어 개발을 위한 미들웨어 프레임워크이다.
Ubuntu상에서 동작하며, 여러 기능들을 모듈화하고 서로 통신하게끔 한다.


---

<div class="cues-header">Cues</div>

# Notes

<aside>핵심 개념</aside>

1. 노드
    - 하나의 프로그램 단위
    - 독립적 실행
2. 토픽
    - 노드 간 단방향 데이터 스트림 통신 방식
    - Publisher : 토픽에 데이터 발행
    - Subscriber : 토픽을 구독하여 데이터 받음
3. 서비스
    - 요청 -> 응답의 양방향 통신
    - 일회성 통신
4. 액션
    - 요청/응답이나 시간이 걸리는 작업에 사용
    - 진행 상황(Feedback)을 중간에 받을 수 있음
5. 메시지
    - 노드 간 주고 받는 데이터 형식
    - 기본 제공: std_msgs/String, geometry_msgs/Twisst 등
    - 커스텀 메시지도 정의 가능
6. 패키지
    - ROS 프로젝트의 기본 단위
7. 마스터
    - 노드들이 서로 찾을 수 있도록 돕는 중앙 등록소
    - roscore 명령어
    - ROS2에서는 DDS(Data Distribution Service) 기반으로 변경

---

<aside>문단 2 제목</aside>

문단 2 설명

---

<aside>문단 3 제목</aside>

문단 3

