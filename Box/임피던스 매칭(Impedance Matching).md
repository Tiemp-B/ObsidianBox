---
cssclasses: cornell-note
tags: [통신, 신호, 용어]
---

# Summary

신호원·전송 선로·부하의 **임피던스를 같게 맞추는 것**. 임피던스 불연속으로 생기는 [[신호 반사(Signal Reflection)|신호 반사]]를 억제해 전력 전달을 최대화하고 파형 왜곡을 줄인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>왜 필요한가</aside>

- 선로의 특성 임피던스와 끝단(부하)의 임피던스가 다르면 그 경계에서 **반사**가 생김
- 임피던스를 맞추면 반사가 사라져 신호가 선로 끝까지 온전히 전달됨 → **최대 전력 전달**, 파형 왜곡↓

<aside>방법</aside>

- **종단 저항(termination)**: 선로 끝에 특성 임피던스와 같은 저항을 달아 에너지를 흡수 (예: [[CAN(Controller Area Network)|CAN]] 버스 양 끝 120Ω)
- 선로 설계 시 특성 임피던스를 일정하게 유지(커넥터·분기 최소화)

---

<aside>관련 노트</aside>

- 기초: [[통신환경]]
- 해결 대상: [[신호 반사(Signal Reflection)]]
