---
cssclasses: cornell-note
tags: computer-architecture, cpu, hardware, systems
---

# Summary
CPU(Central Processing Unit)는 컴퓨터의 핵심 연산 장치로,  
명령어를 해석하고 산술·논리 연산을 수행하며, 시스템의 모든 동작을 제어한다.  
주요 구성 요소는 제어 장치(Control Unit), 연산 장치(ALU), 레지스터(Register)이며,  
프로그램 명령을 처리하는 중심 역할을 수행한다.

---

<div class="cues-header">Cues</div>

# Notes

CPU는 컴퓨터의 ‘두뇌’로, 프로그램 명령어를 받아 해석하고 실행한다.  
모든 데이터 처리는 CPU의 제어 하에 이루어진다.

<aside>정의</aside>

CPU(Central Processing Unit)는 **명령어를 해석하고 실행하여 계산과 제어를 담당하는 중앙 처리 장치**다.  
메모리로부터 명령어를 가져오고(fetch), 해석(decode)하고, 실행(execute)하는 과정을 반복한다.

---

<aside>구성 요소</aside>

1. **연산 장치 (ALU: Arithmetic Logic Unit)**  
   - 덧셈, 뺄셈, 비교, 논리 연산(AND, OR, XOR 등)을 수행.  
   - CPU의 실제 “계산”을 담당하는 부분.  

2. **제어 장치 (Control Unit)**  
   - 기계어 명령어를 해석하고 실행 단계를 제어.  
   - 데이터 흐름과 신호를 조정하여 ALU, 레지스터, 메모리 간 상호작용을 관리.  

3. **레지스터 (Registers)**  
   - CPU 내부의 초고속 임시 저장 공간.  
   - 명령어 주소, 연산 중간 결과, 상태 플래그 등을 저장.
   - 
   - 대표적인 특수 목적 종류:  
     - **Program Counter (PC):** 다음 실행할 명령어의 주소 저장  
     - **Instruction Register (IR):** PC에서 현재 명령어를 읽어와 저장. CU가 이 레지스터를 해석 및 수행  
     - **LR (Link Register)**: 함수 호출 시 수행 후 복귀될 주소 저장
     - **PSR (Program Status Register)**: 명령 수행 후 연산 결과 등에 대한 CPU 상태 정보 기록. 상태 정보 중 ALU 산술 연산에 대한 결과 비트로 Overflow, Negative, Zero, Carry, Parity 등이 있다.
     - **MAR (Memory Address Register)**: 메모리 또는 IO로의 읽기/쓰기 동작이 수행될 주소 저장된 레지스터
     - **MBR (Memory Buffer Resgister)**: 메모리 또는 IO에서 읽거나 쓸 데이터가 임시 저장되는 레지스터
     - **SP (Stack Pointer)**: [[스택]]의 현재 위치 주소를 저장
     - **Accumulator (ACC):** 연산 결과 저장  
     - 범용 레지스터 (예: R0~R15): 데이터의 임시 저장, 함수의 인수, 변수, 연산 결과 저장 등의 일반적 사용

---

<aside>명령어 처리 과정 (Instruction Cycle)</aside>

1. **Fetch (가져오기):** 
	- PC메모리에서 명령어를 읽어온다.  
2. **Decode (해석):** 제어 장치가 명령어의 의미를 분석한다.  
3. **Execute (실행):** ALU가 명령어에 따라 연산을 수행한다.  
4. **Write Back (기록):** 결과를 레지스터나 메모리에 저장한다. (효율 개선을 위한 신기술)

이 과정을 반복하면서 프로그램이 실행된다.

---

<aside>성능 지표</aside>

- **클럭 속도 (Clock Speed):** 초당 명령 실행 주기 수 (GHz 단위).  
- **IPC (Instructions Per Cycle):** 한 클럭 주기당 처리 가능한 명령 수.  
- **코어 수 (Cores):** 병렬로 명령을 실행할 수 있는 독립적 처리 유닛의 개수.  
- **캐시 메모리 (Cache):** CPU 내부의 빠른 데이터 접근용 메모리.  
- **파이프라인 (Pipeline):** 명령어의 여러 단계를 겹쳐 실행해 효율 향상.  

---

<aside>CPU의 구조적 발전</aside>

- **단일 코어 → 멀티 코어(Multi-Core):** 병렬 처리 성능 향상.  
- **슈퍼스칼라(Superscalar):** 하나의 사이클에 여러 명령어 동시 실행.  
- **Out-of-Order Execution:** 명령어 순서를 동적으로 조정해 효율 증가.  
- **Speculative Execution:** 분기 예측을 통해 미리 연산 수행.  
- **RISC vs CISC:**  
  - RISC(단순 명령어): 단순하고 빠른 명령 실행 (예: ARM, RISC-V)  
  - CISC(복잡 명령어): 다양한 연산을 단일 명령으로 수행 (예: x86)  

---

<aside>CPU와 주변 구성 요소의 관계</aside>

- **메모리:** 명령어와 데이터를 저장, CPU가 이를 읽고 쓴다.  
- **입출력 장치:** 제어 신호를 통해 CPU가 외부와 데이터 교환.  
- **버스(Bus):** CPU, 메모리, I/O 간 데이터 전송 통로.  

---

<aside>응용 및 설계 방향</aside>

- **고성능 컴퓨팅(HPC):** 병렬 연산과 파이프라이닝 최적화.  
- **임베디드 시스템:** 저전력, 실시간 반응성 중심의 설계.  
- **모바일 프로세서:** ARM 기반 저전력 설계 구조.  
- **데이터센터 및 AI용 CPU:** 다중 스레드 및 벡터 연산 지원 강화.  

---

<aside>핵심 목표</aside>

CPU 설계의 목표는 **“더 많은 명령어를 더 빠르고 효율적으로 처리하는 것”**이다.  
이를 위해 병렬성, 예측, 캐시 구조, 클럭 최적화 기술이 지속적으로 발전하고 있다.
