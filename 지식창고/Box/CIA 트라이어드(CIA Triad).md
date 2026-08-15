---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 보안
---

# Summary

CIA 트라이어드는 정보보안의 3대 핵심 목표인 **기밀성(Confidentiality)·무결성(Integrity)·가용성(Availability)**을 가리키는 프레임워크로, 로봇 통신 보안을 설계할 때의 기본 점검 기준이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>CIA 트라이어드의 3요소</aside>

| 요소 | 의미 | 위협받으면 |
|---|---|---|
| 기밀성(Confidentiality) | 인가된 사람만 데이터를 볼 수 있어야 함 | 도청, 정보 유출 |
| 무결성(Integrity) | 데이터가 허가 없이 변조되지 않아야 함 | 데이터 조작, 명령 위·변조 |
| 가용성(Availability) | 필요할 때 정상적으로 서비스를 이용할 수 있어야 함 | [[DDoS(Distributed Denial of Service)]] 등으로 인한 서비스 중단 |

<aside>로봇 시스템에서의 적용 예</aside>

로봇 원격 제어 명령이 도청되면 기밀성 침해, 명령이 중간에 조작되면 무결성 침해, 제어 서버가 DDoS 공격으로 마비되면 가용성 침해다 — 로봇 보안 설계는 이 세 가지를 모두 방어 대상으로 삼아야 한다.

---

<aside>핵심 정리</aside>

- CIA 트라이어드는 기밀성·무결성·가용성 세 가지 보안 목표를 가리킨다
- 암호화(기밀성)만으로는 충분하지 않고, 변조 방지(무결성)와 서비스 지속(가용성)도 함께 필요하다

---

<aside>관련 노트</aside>

- 원 페이지: [[1. 보안 기본 개념]]
- 관련: [[인증(Authentication)]], [[인가(Authorization)]], [[DDoS(Distributed Denial of Service)]]
