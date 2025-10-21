---
cssclasses: cornell-note
tags: computer-architecture, cpu, pipeline, systems
---

# Summary
파이프라인(Pipeline)은 CPU가 [[명령어]]를 여러 단계로 나누어 동시에 처리(병렬 처리)하는 기법이다.  
명령어의 **겹침 실행(overlapping execution)** 을 통해 처리 효율을 높이며,  
CPU의 처리율(Throughput)을 향상시키는 핵심 구조적 최적화이다.

---

<div class="cues-header">Cues</div>

# Notes

파이프라인은 공장에서 작업이 여러 단계로 분업화되어 동시에 진행되는 것과 유사한 개념이다.  
각 명령어가 순차적으로 완전히 끝나기 전에 다음 명령어를 실행해 CPU 자원을 효율적으로 사용한다.

<aside>정의</aside>

CPU 파이프라인은 명령어 실행 과정을 여러 단계로 분리하고,  
각 단계를 병렬적으로 수행함으로써 CPU의 **처리 효율을 극대화**하는 기술이다.  
즉, 한 명령어가 실행 중일 때 다음 명령어는 해석 단계에 있고, 또 다음은 가져오기 단계에 있을 수 있다.

---

<aside>명령어 처리 단계 (5단계 파이프라인)</aside>

![[Pasted image 20251020075957.png]]
1. **IF (Instruction Fetch):** 명령어를 메모리에서 가져옴.  
2. **ID (Instruction Decode):** 명령어를 해석하고 필요한 자원 파악.  
3. **EX (Execute):** ALU에서 연산 수행.  
4. **MEM (Memory Access):** 메모리에 접근해 데이터 읽기/쓰기 수행.  
5. **WB (Write Back):** 결과를 레지스터에 저장.

이 다섯 단계가 서로 겹쳐 수행되며,  
각 클럭 주기마다 새로운 명령어가 투입되어 **1사이클당 1명령어 실행률**에 근접하게 된다.

---

<aside>파이프라인의 장점</aside>

- CPU의 **처리율(Throughput)** 향상  
- 각 단계가 **독립적으로 병렬 수행**  
- 하드웨어 자원을 효율적으로 활용  
- 고속 명령 실행을 위한 기반 구조 제공 (슈퍼스칼라, 멀티코어 등으로 확장 가능)

---

<aside>파이프라인의 한계와 병목 요인 (Hazard)</aside>

1. **구조적 위험 (Structural Hazard)**  
   - 두 명령어가 동시에 동일한 하드웨어 자원을 사용하려 할 때 발생.  
   - 예: 메모리 접근 충돌, ALU 자원 중복 요청.  

2. **데이터 위험 (Data Hazard)**  
   - 한 명령어의 결과가 다음 명령어의 피연산자로 필요한 경우 발생.  
   - 예: 명령어 A가 레지스터 R1을 갱신하기 전에 명령어 B가 R1을 사용.  
   - 해결 방법: Forwarding, Stall(버블 삽입), Scoreboarding.  

3. **제어 위험 (Control Hazard)**  
   - 분기(Branch)나 점프(Jump) 명령으로 인해 다음 명령어의 주소가 불확실할 때 발생.  
   - 해결 방법: Branch Prediction, Delayed Branch.  

---

<aside>성능 측정</aside>

- **CPI (Cycles Per Instruction)**: 평균 명령당 클럭 수  
  - 이상적인 파이프라인: CPI ≈ 1  
  - 실제는 Hazard로 인해 CPI > 1  
- **Throughput:** 단위 시간당 실행 가능한 명령 수  
- **Latency:** 개별 명령어가 완료되기까지의 총 시간  

---

<aside>고급 파이프라인 기술</aside>

- **슈퍼스칼라(Superscalar):** 한 클럭 주기에 여러 명령어를 동시에 발행.  
- **Out-of-Order Execution:** 명령 순서를 동적으로 재정렬해 Hazard 최소화.  
- **Speculative Execution:** 분기 예측을 통해 미리 명령어 실행.  
- **파이프라인 딥닝(Deep Pipeline):** 각 단계를 더 세분화해 클럭 주파수 향상.  

---

<aside>응용 및 설계 방향</aside>

- 현대 CPU(예: Intel Core, ARM Cortex)는 모두 **파이프라인 기반 구조** 사용.  
- 고성능 설계에서는 **파이프라인 병렬화 + 캐시 최적화 + 분기 예측**을 함께 사용.  
- 실시간 시스템에서는 **파이프라인 지연(latency)** 관리가 핵심 과제다.

---

<aside>핵심 목표</aside>

파이프라인의 목표는 **CPU의 유휴 시간을 최소화하고 명령어 실행 효율을 극대화**하는 것이다.  
즉, 단일 클럭 주기당 가능한 한 많은 명령을 처리하여 전체 시스템의 성능을 향상시키는 것이다.
