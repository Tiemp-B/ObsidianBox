---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신
---

# Summary

UDP는 연결 수립·순서 보장·재전송 절차를 생략해 **지연시간을 최소화하는 것을 최우선**으로 하는 전송 계층 기반 기술로, [[TCP_IP|TCP/IP]]와 대비되는 저지연 통신의 대표 기술이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>UDP가 저지연을 확보하는 방식</aside>

- 통신 전 연결을 수립하는 절차(handshake)가 없어, 패킷을 바로 보낼 수 있음
- 패킷이 유실되거나 순서가 뒤바뀌어도 UDP 자체는 이를 감지·복구하지 않음(상위 애플리케이션이 필요하면 직접 처리해야 함)
- 이런 신뢰성 절차를 생략한 만큼, TCP/IP보다 지연시간과 지터가 작음

<aside>로봇 통신에서의 활용</aside>

카메라 영상 스트리밍처럼 몇 프레임 유실보다 지연이 더 치명적인 데이터, 혹은 [[DDS(Data Distribution Service)]]처럼 QoS로 신뢰성을 별도로 세밀하게 조정하는 미들웨어의 기반 계층으로 UDP가 널리 쓰인다.

---

<aside>핵심 정리</aside>

- UDP는 연결 수립·재전송 절차를 생략해 지연시간을 최소화하는 저지연 전송 기술이다
- TCP/IP보다 신뢰성은 낮지만 지연시간·지터는 작다

---

<aside>관련 노트</aside>

- 원 페이지: [[5. 네트워크 지연과 QoS]], [[2. 원격제어 통신 프로토콜 개요]]
- 관련: [[TCP_IP]], [[DDS(Data Distribution Service)]]
