---
cssclasses: cornell-note
tags: [통신, 직렬통신, UART]
---

# Summary

UART(Universal Asynchronous Receiver/Transmitter)는 별도 클럭선 없이 **약속된 baudrate**로 동작하는 비동기 직렬 통신으로, 보드 내·근거리 모듈 간 통신에 가장 기본적으로 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>기본 동작</aside>

- **비동기**: 공유 클럭선이 없어, 송수신이 **사전에 약속된 baudrate**로 타이밍을 맞춤
- 두 기기를 **Tx↔Rx 교차**로 연결하고 GND를 공통으로 둠 (한쪽 Tx → 상대 Rx)
- 송수신 전압 레벨을 **사전에 약속**(3.3V 또는 5V)

<aside>사용처와 흐름 제어</aside>

- **사용처**: 보드 내 모듈 간, 근거리 모듈 간
- **흐름 제어(flow control)**: 필요 시 **RTS·CTS** 선을 추가해, 수신 측이 준비됐을 때만 보내도록 제어

<aside>신호 구조</aside>

데이터는 한 프레임 단위로 전송되며 **LSB부터** 보낸다.

- **대기(idle)**: HIGH
- **시작 비트(start)**: LOW (전송 시작을 알림)
- **데이터 비트**: 1 = HIGH, 0 = LOW
- **정지 비트(stop)**: 1(HIGH)
- 전송 순서: **LSB → MSB**

<aside>단점과 보완</aside>

- **단점**: 낮은 전압 + 긴 선 = **노이즈에 취약** (장거리에 부적합)
- **보완**: 전압 레벨을 키운 **[[Developer/통신/직렬 통신/RS-232]]** 로 거리·내잡음 성능을 개선

---

<aside>핵심 정리</aside>

- UART는 클럭 없이 약속된 baudrate로 맞추는 비동기 직렬 통신
- Tx↔Rx 교차 + 공통 GND, 전압(3.3/5V)·속도를 사전 약속
- 프레임: 대기 HIGH → 시작 LOW → 데이터(LSB부터) → 정지 1
- 저전압·긴 선에서 노이즈에 취약 → RS-232로 보완

---

<aside>관련 노트</aside>

- 그룹 허브: [[직렬 통신]]
- 기초: [[통신환경]]
- 보완 규격: [[Developer/통신/직렬 통신/RS-232]]
