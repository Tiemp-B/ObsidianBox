---
cssclasses: cornell-note
tags: [통신, 신호, 용어]
---

# Summary

두 가닥의 선에 서로 반대 위상의 신호를 실어, 수신 측에서 **두 선의 전압 차이**로 값을 판별하는 전송 방식. 두 선에 공통으로 실린 잡음이 상쇄되어 노이즈에 강하다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>원리</aside>

- 한 쌍의 선(+, −)에 **반대 극성**의 신호를 동시에 전송
- 수신기는 두 선의 **차(差)**만 보므로, 두 선에 **똑같이 실린 잡음(공통 모드 잡음)은 상쇄**됨
- 반대 개념: **싱글엔드(single-ended)** — 통신선과 GND의 전압 차로 판별(공통 접지 잡음에 취약)

<aside>특징</aside>

- **노이즈에 강함** → 장거리·고속·전기적 잡음이 많은 환경에 유리
- 선이 2가닥 필요(싱글엔드보다 배선↑)
- 사용 예: [[CAN(Controller Area Network)|CAN]], [[RS-485]], [[USB]], 이더넷 등

---

<aside>관련 노트</aside>

- 기초: [[통신환경]]
- 사용 예: [[CAN(Controller Area Network)]], [[RS-485]]
