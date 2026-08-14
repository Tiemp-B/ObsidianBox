---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신
---

# Summary

요청-응답 모델은 클라이언트가 요청을 보내고 **서버가 그 요청 하나에 대응하는 응답을 돌려주는** 단발성 통신 패턴으로, 발행-구독처럼 지속적으로 데이터가 흐르는 방식과는 다르다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>요청-응답 모델의 특징</aside>

- 클라이언트가 명시적으로 요청을 보내야만 서버가 응답함 — 서버가 먼저 나서서 데이터를 보내지 않음
- 하나의 요청에는 하나의 응답이 짝을 이루는 1:1 상호작용이 기본
- [[REST API(Representational State Transfer)]], [[ROS Service]]가 이 모델을 구현한 대표적인 사례

<aside>다른 통신 모델과의 비교</aside>

요청-응답(단발성 1:1), [[발행-구독 모델(Publish-Subscribe)]](토픽 기반 다대다), [[액션 모델(Action Pattern)]](장시간 작업 관리)은 각각 다른 통신 목적에 맞게 선택되는 패턴이다.

---

<aside>핵심 정리</aside>

- 요청-응답 모델은 클라이언트의 요청에 서버가 응답하는 단발성 1:1 통신 패턴이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 통신 모델(발행-구독·요청-응답·액션)]]
- 관련: [[발행-구독 모델(Publish-Subscribe)]], [[액션 모델(Action Pattern)]], [[REST API(Representational State Transfer)]], [[ROS Service]]
