---
cssclasses: cornell-note
tags: computer-science, academic, cs-note
---

# Summary

컴퓨터 과학(Computer Science)은 **프로그래밍 언어와 알고리즘을 중심으로 하드웨어·소프트웨어·데이터·네트워크의 상호작용을 탐구하는 학문**이다.  
기초적으로는 자료 구조와 알고리즘, 심화적으로는 운영체제·컴퓨터 구조·네트워크·데이터베이스를 포함하며,  AI, 보안, 분산 시스템, 이론 CS 등으로 확장된다.  
즉, “효율적인 계산을 위한 논리와 시스템의 과학”이다.

---

<div class="cues-header">Cues</div>

# Notes

1. 프로그래밍 (Programming)

- **핵심 개념:** 언어 문법, 제어 구조, 함수, 클래스, 메모리 모델  
- **주요 언어:** C, C++, Python, Java, Rust, Go  
- **패러다임:** 절차형(Procedural), 객체지향(OOP), 함수형(Functional), 이벤트 기반(Event-driven)  
- **소프트웨어 설계 원칙:** 추상화, 캡슐화, 모듈화, 인터페이스  
- **성능 요소:** 메모리 효율, 캐시 활용, 비동기/병렬 프로그래밍  
- **실무 적용:**  
  - 시스템 프로그래밍 (POSIX, 파일 I/O)  
  - 네트워크 소켓 프로그래밍 (TCP/UDP, HTTP, gRPC)  
  - 임베디드 C/RTOS 개발  
  - 프레임워크(Spring, Django, Express) 기반 애플리케이션 구현  

---

2. 알고리즘 (Algorithms)

- **기초 개념:** 시간복잡도, 공간복잡도, Big-O 표기  
- **정렬:** 버블, 삽입, 선택, 병합, 퀵, 힙, 계수, 기수  
- **탐색:** 선형 탐색, 이진 탐색, 해시 탐색, 이진 탐색 트리  
- **그리디 알고리즘:** 동전 교환, 활동 선택, Huffman 코딩  
- **동적 프로그래밍(DP):** 피보나치, 배낭 문제, LCS, LIS  
- **그래프 탐색:** BFS, DFS, Dijkstra, Floyd-Warshall, Kruskal, Prim  
- **고급 기법:** 분할정복, 백트래킹, 세그먼트 트리, 비트마스크  
- **응용:** 최단 경로 탐색, 스케줄링, 최적화 문제, 코딩테스트 문제 해결  

---

3. 운영체제 (Operating Systems)

- **기능:** 하드웨어 자원 관리, 프로세스 제어, 메모리 관리, 파일 시스템 관리  
- **핵심 구성:** 커널(Kernel), 프로세스(Process), 스레드(Thread), 인터럽트(Interrupt)  
- **스케줄링:** FCFS, SJF, Round Robin, Priority  
- **동기화:** 세마포어(Semaphore), 뮤텍스(Mutex), 모니터(Monitor)  
- **메모리 관리:** 페이징(Paging), 세그멘테이션(Segmentation), 가상 메모리(Virtual Memory)  
- **응용:**  
  - 리눅스 프로세스 관리 및 시스템 콜  
  - 컨테이너 가상화(Docker, cgroup, namespace)  
  - RTOS 기반 실시간 시스템 설계  

---

4. 컴퓨터 구조 (Computer Architecture)

- **핵심 구성요소:** ALU, 레지스터, 제어 장치, 메모리, 버스, 캐시  
- **명령어 사이클:** Fetch → Decode → Execute → Writeback  
- **파이프라이닝, 슈퍼스칼라, 분기 예측, 캐시 일관성**  
- **CPU 구조:** RISC vs CISC, ARM, RISC-V  
- **확장:**  
  - GPU 병렬 연산 구조 (SIMD, CUDA Core)  
  - SoC(System-on-Chip), FPGA 설계  
  - 저전력 임베디드 프로세서  

---

5. 네트워크 (Computer Networks)

- **구조:** OSI 7계층 / TCP/IP 4계층  
- **프로토콜:** ARP, ICMP, IP, TCP, UDP, DNS, HTTP/HTTPS  
- **라우팅 알고리즘:** RIP, OSPF, BGP  
- **전송:** 3-way Handshake, 혼잡 제어, 흐름 제어  
- **응용 계층:** REST API, gRPC, MQTT, WebSocket  
- **보안:** SSL/TLS, HTTPS, VPN, NAT, 방화벽  
- **실무 응용:** IoT 통신, 클라우드 네트워크(VPC, Load Balancer, Proxy)  

---

6. 데이터베이스 (Database Systems)

- **모델:** 관계형(RDBMS), 비관계형(NoSQL)  
- **SQL 기본:** SELECT, JOIN, GROUP BY, INDEX  
- **트랜잭션:** ACID, Lock, Deadlock, MVCC  
- **정규화, 무결성, 인덱싱**  
- **분산 DB:** 샤딩, 레플리케이션, CAP 이론  
- **응용:** ORM, Query Optimization, Data Warehouse  

---

7. 인공지능 & 데이터 사이언스 (AI & Data Science)

- **기초 수학:** 선형대수, 확률, 미적분  
- **머신러닝:** 회귀, 분류, 군집화, SVM, 의사결정트리  
- **딥러닝:** CNN, RNN, Transformer, Attention  
- **프레임워크:** TensorFlow, PyTorch, scikit-learn  
- **응용:** MLOps, AI 추론 가속(TensorRT, ONNX), Edge AI  

---

8. 보안 (Security)

- **암호학:** 대칭키/비대칭키, 해시, 전자서명  
- **네트워크 보안:** SSL/TLS, HTTPS, VPN  
- **시스템 보안:** 인증(Authentication), 접근 제어(Authorization)  
- **웹 보안:** SQL Injection, XSS, CSRF  
- **확장:** 블록체인, Secure Boot, HSM, Zero Trust  

---

9. 소프트웨어 공학 (Software Engineering)

- **소프트웨어 개발 생명주기 (SDLC)**  
- **객체지향 설계 원칙 (SOLID)**  
- **디자인 패턴:** Singleton, Factory, Observer, MVC, DI  
- **테스트:** 단위, 통합, 회귀 테스트  
- **CI/CD:** Git, Jenkins, Docker, Kubernetes  
- **응용:** 대규모 시스템 설계, 마이크로서비스, DevOps  

---

10. 컴파일러 & 언어 처리 (Compilers & PL)

- **단계:** 어휘 분석 → 구문 분석 → 중간 코드 생성(IR) → 최적화 → 코드 생성  
- **기술 요소:** 가비지 컬렉션(GC), 링킹, 런타임 시스템  
- **응용:** 인터프리터, JIT 컴파일, LLVM, WASM, DSL 설계  

---

11. 이론 컴퓨터 과학 (Theoretical Computer Science)

- **오토마타와 형식언어(Formal Language)**  
- **튜링 머신(Turing Machine)**  
- **복잡도 이론:** P, NP, NP-Complete, NP-Hard  
- **계산 가능성과 결정 문제**  
- **응용:** 알고리즘 증명, 계산 복잡도 분석, 최적화 문제 연구  

---

12. 확장 분야 (Extended Areas)

- **임베디드 시스템:** MCU, RTOS, 센서 제어, 드라이버 개발  
- **클라우드 & DevOps:** Docker, Kubernetes, AWS, CI/CD  
- **분산 시스템:** CAP 이론, Consistency Model, Consensus (Paxos, Raft)  
- **고급 응용:** 컴퓨터 비전, 자연어 처리, 음성 인식  
- **신기술:** 양자컴퓨팅, 엣지컴퓨팅, HPC(고성능 컴퓨팅)

---
