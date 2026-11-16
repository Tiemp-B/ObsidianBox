---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 보안
---

# Summary

DoS(서비스 거부) 공격은 **단일 장치(공격자 1명)가** 표적 서버에 과도한 트래픽·요청을 보내 정상 서비스를 마비시키는 공격으로, 여러 장치가 동원되는 [[DDoS(Distributed Denial of Service)|DDoS]]와 구분된다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>DoS의 동작 방식</aside>

- 하나의 공격 지점(단일 IP)에서 표적 서버가 처리할 수 있는 한계를 넘는 트래픽·요청을 집중적으로 보냄
- 서버의 연결·대역폭·연산 자원을 고갈시켜 정상 사용자의 요청을 처리하지 못하게 만듦
- 공격 출처가 하나뿐이라, 해당 IP를 차단하는 것만으로도 비교적 쉽게 방어할 수 있다는 점이 DDoS와의 핵심 차이

<aside>DDoS와의 차이</aside>

DoS는 단일 장치가 공격 주체인 반면, DDoS는 다수의 장치(봇넷)에 공격이 **분산(Distributed)**되어 있어 특정 IP 하나만 차단하는 방식으로는 막기 어렵다 — 이 "단일 대 분산" 차이가 두 공격의 핵심 구분 포인트다.

---

<aside>핵심 정리</aside>

- DoS는 단일 장치가 표적 서버에 과부하를 일으켜 서비스를 마비시키는 공격이다
- 공격 출처가 하나뿐이라 DDoS보다 방어(IP 차단)가 상대적으로 쉽다

---

<aside>관련 노트</aside>

- 관련: [[DDoS(Distributed Denial of Service)]], [[CIA 트라이어드(CIA Triad)]]
