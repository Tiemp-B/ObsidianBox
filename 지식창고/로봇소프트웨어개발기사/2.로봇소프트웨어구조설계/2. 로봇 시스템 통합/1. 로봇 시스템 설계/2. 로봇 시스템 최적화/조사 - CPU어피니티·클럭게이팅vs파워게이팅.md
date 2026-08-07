---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - CPU어피니티·클럭게이팅vs파워게이팅 (2026-08-07)

NCS 별도 모듈 확인 없음(§1-2, 임베디드 시스템 최적화 일반 지식). 개요(허브) 링크 정상. 문제은행 3문항(CPU 사용률 최적화/전력 소비 최적화/성능 향상 기법) 전부 기존 페이지 커버 확인. 목표(추가정보 발굴)에 맞춰 각 페이지에 새로 엮을 개념을 조사했다.

## Phase 1 — 조사

### CPU 어피니티(Affinity)·코어 고정(Core Pinning) — 멀티코어 실시간성 확보 기법 (신규)
- 기존 페이지2는 우선순위 조정·락 경합 최소화는 다루지만, 멀티코어 환경에서 **어떤 코어에서 실행할지**를 지정하는 기법은 다루지 않았음
- **CPU 어피니티(코어 고정)**: 특정 프로세스·스레드를 특정 CPU 코어에 고정해서만 실행되게 하는 기법 — 다른 코어로 옮겨 다니며 생기는 캐시 미스(cache miss)와 컨텍스트 스위칭 오버헤드를 줄여, 실행 시간을 더 예측 가능(deterministic)하게 만듦
- 로봇의 실시간 제어 루프(모션 제어 등)를 전용 코어에 고정하고, UI·로깅처럼 실시간성이 낮은 작업은 다른 코어에 맡기면, 비실시간 작업이 실시간 작업의 실행을 방해하는 것을 막을 수 있음
- 출처: [The Ultimate Guide to Processor Affinity](https://www.numberanalytics.com/blog/ultimate-guide-processor-affinity), [Real-time Linux communications for real-time robotic applications](https://arxiv.org/pdf/1808.10821)

### 클럭 게이팅(Clock Gating) vs 파워 게이팅(Power Gating) — DVFS와 다른 전력 절감 기법 (신규)
- 기존 페이지3은 전력 최적화로 DVFS(클럭·전압을 낮춤)만 다루는데, 하드웨어 저전력 설계에서 자주 짝으로 다뤄지는 **클럭 게이팅**·**파워 게이팅**이 빠져 있었음
- **클럭 게이팅**: 사용하지 않는 회로 블록에 **클럭 신호만 차단**해 동적 전력(스위칭 전력)을 줄이는 기법 — 전원은 계속 공급되므로 다시 켤 때 지연이 거의 없음
- **파워 게이팅**: 사용하지 않는 블록에 **전원 공급 자체를 완전히 차단**해 누설 전력(leakage power)까지 줄이는 기법 — 전력 절감 효과는 더 크지만, 다시 전원을 켜고 상태를 복구하는 데 시간이 더 걸림
- DVFS(부하에 맞춰 클럭·전압을 동적으로 조절)와 달리, 클럭·파워 게이팅은 **아예 쓰지 않는 블록을 끄는** 접근이라는 점에서 상호 보완적
- 출처: [Clock Gating vs Power Gating - Maven Silicon](https://www.maven-silicon.com/blog/what-is-the-difference-between-clock-gating-and-power-gating/), [Low-Power Design Guide: DVFS, Power Gating, Clock Gating](https://medium.com/@QuarkAndCode/low-power-design-guide-dvfs-power-gating-clock-gating-more-f812c9bf1172)

## Phase 2 — 자체 검토

- CPU 어피니티의 구체적 API(taskset, sched_setaffinity 등)는 실기 범위라 페이지에는 개념(코어 고정으로 캐시 미스·컨텍스트 스위칭 감소)만 반영
- 클럭 게이팅·파워 게이팅은 회로 설계(하드웨어) 관점 기법이지만, "임베디드 시스템의 전력 최적화 기법"이라는 이 세세항목의 틀 안에서 DVFS와 나란히 다뤄지는 것이 일반적이라 반영 — 게이팅 회로의 구체적 구현(트랜지스터 수준)까지는 넣지 않음

## Phase 3 — 결론

2개 페이지(2. CPU·메모리 최적화 기법 — CPU 어피니티 1건, 3. 전력 소비 최적화 기법 — 클럭/파워 게이팅 1건)에 신규 개념 2건 반영. Box 용어는 `CPU 어피니티(CPU Affinity)`, `클럭 게이팅과 파워 게이팅(Clock Gating·Power Gating)` 신규 생성.
