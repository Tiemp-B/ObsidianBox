---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - HAL·BSP·부트로더 (2026-08-07)

NCS 별도 모듈 확인 없음(§1-2, 임베디드 시스템 일반 지식 기반). 이 세세항목 전용 문제은행 슬롯은 없고(형제 세세항목 "3. 미들웨어 프로세스 관리" 슬롯의 모듈화 장점 문항 2건이 이 페이지로 커버됨, 기존 확인 유지), 개요(허브) 링크 정상. 목표(추가정보 발굴)에 맞춰 임베디드 계층 구조에서 미반영된 표준 개념을 조사했다.

## Phase 1 — 조사

### HAL(Hardware Abstraction Layer) — 디바이스 드라이버와 미들웨어 사이의 또 다른 계층 (신규)
- 기존 페이지2는 계층을 어플리케이션-미들웨어-디바이스 드라이버-운영체제-하드웨어로만 나누는데, 실무 임베디드 시스템에서는 디바이스 드라이버 근처에 **HAL(하드웨어 추상화 계층)** 이 별도로 위치하는 경우가 많음
- HAL은 서로 다른 종류의 하드웨어를 **비슷하게 보이도록 감싸는** 소프트웨어 계층으로, 디바이스 드라이버보다 더 일반적인 수준에서 하드웨어 차이를 흡수한다 — 디바이스 드라이버가 특정 장치 하나에 특화된 반면, HAL은 여러 하드웨어에 공통 인터페이스를 제공해 상위(커널·미들웨어) 코드가 하드웨어 종류가 바뀌어도 그대로 동작하게 함
- 디바이스 드라이버가 오히려 HAL을 이용해 자신의 구조를 단순화하는 경우도 많음(드라이버 위에 HAL이 있는 게 아니라, 드라이버가 HAL을 호출)
- 출처: [What is a Hardware Abstraction Layer - Lenovo](https://www.lenovo.com/us/en/glossary/hardware-abstraction-layer/), [HAL - ScienceDirect Topics](https://www.sciencedirect.com/topics/computer-science/hardware-abstraction-layer)

### BSP(Board Support Package)·부트로더(Bootloader) — 보드마다 갖춰야 하는 하드웨어 특화 소프트웨어 묶음 (신규)
- 기존 페이지는 "펌웨어"만 다루고, 특정 보드(하드웨어)에 맞춰 OS를 동작시키기 위해 필요한 소프트웨어 묶음인 **BSP**는 다루지 않았음
- **BSP**: 부트로더·디바이스 드라이버·(경우에 따라 커널 설정)를 포함해, 임베디드 운영체제가 **특정 보드(하드웨어)에서 동작**하도록 해주는 하드웨어 특화 소프트웨어 묶음
- **부트로더(Bootloader)**: 전원이 켜졌을 때 가장 먼저 실행되어, 운영체제(커널)를 메모리에 적재해 실행을 넘겨주는 작은 프로그램. 네트워크 등을 통해 새 소프트웨어 이미지를 올리는 업데이트 기능도 겸하는 경우가 많음
- 로봇 제어 보드가 바뀌면(예: MCU 변경), 그 보드에 맞는 BSP(부트로더+드라이버)를 새로 갖춰야 기존 OS·미들웨어가 그 위에서 동작할 수 있음
- 출처: [Board support package - Wikipedia](https://en.wikipedia.org/wiki/Board_support_package), [Understanding the Linux BSP](https://siliconsignals.io/blog/understanding-linux-board-support-package/)

## Phase 2 — 자체 검토

- HAL과 디바이스 드라이버의 상하 관계는 구현체마다 다를 수 있어(“드라이버가 HAL을 이용” vs “HAL이 드라이버 위에서 통합”), 페이지에는 "여러 하드웨어를 비슷하게 보이도록 추상화한다"는 핵심 개념 위주로 반영하고 구현체별 세부 배치는 조사md에만 남김
- BSP의 세부 구성요소(커널 설정 파일, 디바이스 트리 등)까지는 넣지 않고 "부트로더+드라이버 묶음"이라는 핵심 정의만 반영

## Phase 3 — 결론

1개 페이지(2. 로봇 소프트웨어 계층 구조)에 신규 개념 2건(HAL, BSP+부트로더) 반영. Box 용어는 `HAL(Hardware Abstraction Layer)`, `BSP(Board Support Package)` 신규 생성.
