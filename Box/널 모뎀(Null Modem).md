---
cssclasses: cornell-note
tags: [통신, RS-232, 용어]
---

# Summary

두 **DTE**(PC 등)를 모뎀(DCE) 없이 직접 연결하기 위한 **교차(cross) 케이블**. 한쪽의 송신선을 상대의 수신선으로 엇갈려 이어 송신 충돌을 피한다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>왜 필요한가</aside>

- DTE↔DTE를 스트레이트로 이으면 양쪽의 **송신선(TxD)이 서로 맞물려** 데이터가 전달되지 않음(충돌)
- **TxD ↔ RxD를 교차**해 이으면, 한쪽이 보낸 신호가 상대의 수신선으로 들어감
- 흐름 제어선(RTS/CTS 등)도 교차로 연결

<aside>용도</aside>

- 모뎀(DCE) 없이 **두 컴퓨터를 직접** 시리얼로 연결할 때
- [[DTE와 DCE|DTE↔DTE]] 연결의 표준 케이블

---

<aside>관련 노트</aside>

- 규격: [[RS-232]]
- 역할 구분: [[DTE와 DCE]]
