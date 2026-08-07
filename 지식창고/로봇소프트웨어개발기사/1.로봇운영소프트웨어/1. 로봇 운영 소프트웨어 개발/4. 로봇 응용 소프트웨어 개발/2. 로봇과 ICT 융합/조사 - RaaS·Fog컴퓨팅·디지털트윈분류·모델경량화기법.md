---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - RaaS·Fog컴퓨팅·디지털트윈분류·모델경량화기법 (2026-08-07)

이 세세항목은 NCS 대응 학습모듈이 없어(기존 확인됨, §1-2에 따라 문제은행+도메인지식 기반) 기존 5페이지가 이미 정확한 도메인지식으로 작성돼 있다. 개요(허브) 링크도 이미 정상. 목표(추가정보 발굴)에 맞춰 각 페이지에 새로 엮을 개념을 조사했다.

## Phase 1 — 조사

### RaaS(Robots as a Service) — 클라우드 로보틱스의 비즈니스 모델 (신규)
- 로봇을 직접 구매하지 않고, **클라우드 기반 구독 서비스로 로봇 장비·데이터 서비스를 임대**해 쓰는 모델. 로봇공학 버전의 SaaS(Software as a Service)라 볼 수 있음
- 실제 플랫폼 사례: **AWS RoboMaker**(머신러닝·모니터링·분석 서비스 포함, 3D 시뮬레이션으로 자율주행차량·드론 훈련에 활용된 사례 있음), **Google Cloud Robotics Platform**(AI+클라우드+로봇 결합, 클라우드 연결 협동로봇 생태계 지향), Honda RaaS, KUKA SmartFactory as a Service 등
- 시장 전망 예시(ABI Research): 2026년까지 RaaS 설치 130만 건, 매출 340억 달러 규모로 성장 전망(참고용 시장 전망치이며 절대적 사실로 단정하지 않음)
- 출처: [Robot as a service - Wikipedia](https://en.wikipedia.org/wiki/Robot_as_a_service), [What is Robots-as-a-Service (RaaS)? - GeeksforGeeks](https://www.geeksforgeeks.org/blogs/overview-of-raas-robots-as-a-service/), [AWS RoboMaker: A cheat sheet](https://www.techrepublic.com/article/aws-robomaker-a-cheat-sheet/)

### Fog Computing — 엣지와 클라우드 사이의 중간 계층 (신규)
- 엣지 계층에서 온 데이터를 **분석·집계한 뒤 클라우드로 보내기 전에 처리**하는 중간 계층. 클라우드 컴퓨팅을 네트워크 가장자리 쪽으로 확장한 것으로, 종단 장치와 클라우드 데이터센터 사이에 분산된 노드망으로 컴퓨팅·저장·네트워킹 서비스를 제공
- 클라우드로 보내는 불필요한 데이터를 걸러내 클라우드의 부담을 줄이고, 엣지 단독보다는 넓은 범위지만 클라우드보다는 낮은 지연시간을 제공
- 다중 로봇 시스템(Multi-Robot System) 아키텍처 예시: 로봇 계층(현장 로봇) → 엣지 계층(개별 로봇 근처 처리) → **포그 계층(여러 로봇이 공유하는 분산 저장·중간 처리)** → 클라우드 계층(전체 모니터링·임무 제어) — 여러 로봇이 포그 계층의 자원을 함께 요청·활용하면 매번 클라우드까지 조회하지 않아도 됨
- 출처: [Fog and Edge Computing - SUSE](https://www.suse.com/c/fog-and-edge-computing-for-faster-smarter-data-processing/), [Offloading SLAM for Indoor Mobile Robots with Edge-Fog-Cloud Computing](https://www.researchgate.net/publication/332574582_Offloading_SLAM_for_Indoor_Mobile_Robots_with_Edge-Fog-Cloud_Computing)

### 디지털 트윈의 3가지 유형 — ISO 23247 (신규)
국제표준 ISO 23247(제조업 디지털 트윈 프레임워크)이 정의하는 3가지 유형:

| 유형 | 정의 |
|---|---|
| DTP(Digital Twin Prototype) | 아직 실물(관측 대상)과 연결되지 않은 "설계도" 수준 — 요구사항, 3D 모델, 자재명세서 등 실물을 만들기 위한 정보 집합 |
| DTI(Digital Twin Instance) | 실물과 **실시간으로 동기화된** 디지털 표현 — 일반적으로 "디지털 트윈"이라고만 말하면 이 DTI를 가리킴 |
| DTA(Digital Twin Aggregate) | 여러 DTI(또는 DTP)를 모아 여러 대의 로봇/설비 전체의 경향·성능을 함께 분석하는 집합체 |

기존 페이지4의 "정적 3D 모델과의 차이" aside가 다룬 구분(실시간 동기화 여부)이 바로 DTP(연결 안 됨)와 DTI(연결됨)의 차이에 해당함 — 용어로 더 명확히 구분 가능
- 출처: [ISO 23247 Digital Twin Framework Overview](https://anvil.so/post/iso-23247-digital-twin-framework-overview), [ISO 23247 Digital Twin Framework for Manufacturing](https://www.ap238.org/iso23247/)

### 온디바이스 AI를 가볍게 만드는 모델 경량화 기법 (신규)
기존 페이지5는 "경량화된 모델"이라고만 서술하고 그 방법은 다루지 않았다. 대표적인 3가지 기법:

| 기법 | 원리 |
|---|---|
| 양자화(Quantization) | 모델 가중치를 32비트 실수 대신 8비트 정수 등 더 적은 비트로 표현해 크기·연산량 축소 |
| 가지치기(Pruning) | 모델에서 결과에 거의 영향을 주지 않는 연결(가중치)을 제거 |
| 지식 증류(Knowledge Distillation) | 크고 정확한 "교사 모델"의 출력을 "학생 모델"(경량 모델)이 모방하도록 학습시켜, 작은 모델이 큰 모델의 성능에 가깝게 근사하도록 함 |

세 기법을 함께(파이프라인으로) 적용하면 모델 크기를 크게 줄일 수 있으며, 실제로 NVIDIA Jetson·Qualcomm Snapdragon 같은 엣지 AI 하드웨어 가속기와 결합해 로봇에 탑재된다. (압축 배율은 기법·모델마다 편차가 커서 구체적 배수는 페이지에 반영하지 않고 "기법의 존재와 원리"만 반영)
- 출처: [AI Model Compression for Efficient Deployment](https://www.runpod.io/articles/guides/ai-model-compression-reducing-model-size-while-maintaining-performance-for-efficient-deployment), [Model Compression Techniques - Medium](https://medium.com/@amitkharche/model-compression-techniques-quantization-pruning-distillation-for-real-world-deployment-229f57e2c807)

## Phase 2 — 자체 검토

- RaaS 시장 전망 수치(130만 건/340억 달러)는 단일 시장조사기관(ABI Research) 추정치라 페이지 본문에는 절대수치보다 "빠르게 성장하는 추세" 정도로만 반영하고, 조사md에는 출처와 함께 참고용으로 남김
- 모델 경량화 압축 배율(4~8배, 2~10배 등)은 출처마다 편차가 커서 구체적 배수를 페이지에 넣지 않고 기법명·원리만 반영(§2 원칙에 따름)
- 나머지(Fog Computing 정의, ISO 23247 DTP/DTI/DTA 정의)는 표준·업계 정의로 명확해 추가조사 불필요

## Phase 3 — 결론

4개 페이지(클라우드/엣지/디지털트윈/AI서비스)에 각각 1개씩 신규 개념을 반영하기로 결정.
