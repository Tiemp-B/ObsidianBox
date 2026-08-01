---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - RTOS
  - 실시간시스템
---

# Summary

VxWorks는 항공·우주·국방 등 **매우 높은 신뢰성과 안전성이 요구되는 분야**에서 오랫동안 검증되어 온 상용 실시간 운영체제(RTOS)다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>VxWorks의 특징</aside>

- 예측 가능한 실시간 스케줄링과 높은 안정성을 목표로 설계된 상용(유료 라이선스) RTOS
- 항공기 비행 제어, 우주 탐사선(화성 탐사 로버 등), 국방 장비처럼 실패가 곧 치명적 사고로 이어지는 고신뢰성 응용 분야에서 오랜 실적을 쌓아옴
- [[FreeRTOS]] 같은 오픈소스 경량 RTOS보다 기능이 풍부하고 지원·인증 체계가 갖춰져 있지만, 라이선스 비용이 발생함

"VxWorks는 오픈소스 무료 RTOS로, FreeRTOS와 동일한 라이선스 모델을 갖는다"라는 서술은 오답이다 — VxWorks의 핵심은 오히려 **상용(유료) RTOS**라는 점이며, 이 점이 오픈소스인 FreeRTOS와의 라이선스 모델 차이다.

<aside>다른 RTOS와의 비교</aside>

VxWorks, [[QNX]]는 모두 고신뢰성 상용 RTOS 계열이지만, VxWorks는 특히 항공우주·국방 분야에서, QNX는 마이크로커널 구조 기반의 장애 격리 강점으로 각각 널리 채택되어 왔다.

---

<aside>핵심 정리</aside>

- VxWorks는 항공·우주·국방 등 고신뢰성 분야에서 널리 쓰이는 상용 RTOS다
- 오픈소스가 아니라 라이선스 비용이 있는 상용 제품이다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 실시간 운영체제와 스케줄링]]
- 관련: [[QNX]], [[FreeRTOS]], [[RTOS]]
