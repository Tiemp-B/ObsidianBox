---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 시리얼통신
---

# Summary

SPI는 **MOSI·MISO·SCK·SS(슬레이브 선택) 4개 선**을 사용해 마스터-슬레이브 간 고속 동기 시리얼 통신을 수행하는 프로토콜로, [[I2C]]보다 빠르지만 배선 수가 더 많다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>SPI의 4개 신호선</aside>

| 신호선 | 역할 |
|---|---|
| MOSI(Master Out Slave In) | 마스터 → 슬레이브 데이터 전송 |
| MISO(Master In Slave Out) | 슬레이브 → 마스터 데이터 전송 |
| SCK(Serial Clock) | 마스터가 생성하는 클럭 신호 |
| SS(Slave Select) | 통신할 슬레이브를 선택하는 신호(슬레이브마다 별도 필요) |

MOSI·MISO가 분리되어 있어 **전이중(full-duplex, 송수신 동시 가능)** 통신이 가능하다는 것이 SPI의 특징이며, 여러 슬레이브를 연결하려면 슬레이브마다 별도의 SS 선이 필요하다.

<aside>I2C와의 비교</aside>

[[I2C]]는 2선으로 여러 슬레이브를 주소로 구분해 연결하는 반면, SPI는 4선(+슬레이브마다 추가 SS선)을 쓰는 대신 속도가 더 빠르다 — 배선 수를 아끼려면 I2C, 속도가 중요하면 SPI를 선택하는 트레이드오프가 있다.

---

<aside>핵심 정리</aside>

- SPI는 MOSI·MISO·SCK·SS 4개 선으로 전이중 통신하는 고속 시리얼 프로토콜이다
- 반이중 방식이 아니라 MOSI·MISO 분리로 동시 송수신이 가능한 전이중 방식이다

---

<aside>관련 노트</aside>

- 원 페이지: [[7. 로봇 제어기 통신 프로토콜 심화]]
- 관련: [[I2C]]
