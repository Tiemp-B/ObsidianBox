---
cssclasses: cornell-note
tags: [통신, RS-232, 용어]
---

# Summary

RS-232 등에서 통신 양 끝의 역할 구분. **DTE**는 데이터를 생산·소비하는 단말(PC 등), **DCE**는 DTE와 회선 사이에서 신호를 변환·중계하는 장비(모뎀 등)다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>DTE (Data Terminal Equipment)</aside>

- 데이터를 **생산하거나 사용하는** 종단 장치 (PC·단말기·MCU 등)
- 관례상 **수(male) 커넥터**

<aside>DCE (Data Circuit-terminating Equipment)</aside>

- DTE와 통신 회선 사이에서 **신호를 변환·중계**하는 장치 (모뎀 등)
- 관례상 **암(female) 커넥터**

<aside>연결 규칙</aside>

- **DTE ↔ DCE**: 스트레이트 케이블 (핀이 1:1 대응)
- **DTE ↔ DTE**: 양쪽 다 송신 → 충돌 → **교차 케이블([[널 모뎀(Null Modem)|널 모뎀]])** 필요
- **DCE ↔ DCE**: 교차 케이블

---

<aside>관련 노트</aside>

- 규격: [[RS-232]]
- 교차 연결: [[널 모뎀(Null Modem)]]
