---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - Warm standby (2026-08-08)

개요(허브) 링크 정상, NCS 자료 대조 aside 없음(이미 클린). 문제은행(세부항목 슬롯 1문항 "포텐셜 필드 반발력 설명")은 기존 척력 aside가 이미 정확히 커버 확인. 3라운드 웹검색 반복 적용.

## Phase 1 — 3라운드 반복 검색

### 1라운드 — 후보 개념 탐색
- "hot standby cold standby warm standby redundancy difference three types" 검색 → 동적 중복 구조의 대기 방식은 실무에서 흔히 **Hot/Warm/Cold 3가지**로 나뉘는데, 기존 페이지는 Hot·Cold 2가지만 다루고 그 중간 형태인 Warm standby가 빠져 있음(신규 공백)
- "N-modular redundancy generalization TMR voting fault tolerance systems" 검색 → TMR은 N중 모듈 이중화(NMR, N은 홀수)의 기본형(N=3)이라는 관계 확인. 다만 TMR은 이미 별도 Box 용어로 충분히 다뤄져 있고, NMR 일반화는 §2 원칙상 과다 반영으로 판단해 이번 배치에서는 제외

### 2라운드 — 파생 심화 검색
- "웜 스탠바이 콜드 스탠바이 핫 스탠바이 차이 이중화 로봇" 검색 → 한국어 자료에서도 핫 스탠바이(활성 모듈만 유효 데이터 송신, 대기 모듈은 항상 함께 동작)와 별개로 웜 스탠바이가 존재함을 확인, 다만 세부 차이 설명은 제한적이라 영어 자료로 보강
- "N중 모듈 이중화 TMR 일반화 다수결 홀수 모듈" 검색 → 홀수 개의 장치로 다수결을 구성한다는 일반 원리는 확인했으나, 문제은행에 관련 문항이 없고 기존 TMR 용어와 중복되는 내용이 많아 반영 대상에서 제외 확정

### 3라운드 — 반영 후보 구체화 검색
- "warm standby definition partial synchronization" 계열 재확인(1라운드 영어 자료) → Warm standby는 예비 모듈이 **켜진 채로 대기**하지만 주 모듈만큼 완전히 동기화되지는 않은 상태이며, 결함 발생 시 짧은 전환 시간(brief switchover)을 거쳐 가동된다는 정의 확정 — Cold standby(꺼진 채 대기, 긴 복구 시간)와 Hot standby(완전 동기화, 즉시 전환) 사이의 중간 지점

## Phase 2 — 자체 검토

- Warm standby는 기존 페이지의 Hot/Cold standby 표를 완성하는 세 번째 유형이라 자연스럽게 반영. 실무에서 Hot/Cold/Warm 세 유형을 구분하는 문제가 출제될 수 있어 실질적 가치가 있다고 판단
- NMR(N중 모듈 이중화) 일반화는 문제은행에 근거가 없고 기존 TMR 용어와 상당 부분 중복되어 §2 원칙("과다 반영 방지")에 따라 이번 배치에서는 반영하지 않음
- 신규 Box 용어를 만들기보다, 기존 페이지의 Hot/Cold standby 표를 확장하는 형태로 반영(개념 하나를 표에 추가하는 수준이라 별도 용어 문서로 분리할 만큼 크지 않음)

## Phase 3 — 결론

1개 페이지(3. 충돌 검출 센서의 하드웨어 중복 구조)에 신규 개념 1건(Warm standby) 반영. 신규 Box 용어 없음.
