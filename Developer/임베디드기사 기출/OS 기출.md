---
cssclasses:
  - hover-reveal
---
## [Q.24-2 / Q.17-13]
Q. 운영체제가 각 프로세스에 대한 정보를 저장하는 자료구조로, 프로세스의 ID, 현재 상태, 프로그램 카운터, CPU 레지스터, 메모리 관리 정보 등을 포함하는 것은?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    PCB (Process Control Box)
  </div>
</details>
## [Q.24-6]
Q. 프로세스가 어떤 자원을 할당받은 상태에서 다른 자원을 기다리는 상태는?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    점유와 대기 (Hold and Wait)
  </div>
</details>
## [Q.21-4]
Q. 커널의 진입점과 인터럽트 처리 루틴에 대한 주소가 저장되어 있으며, 시스템이 부팅되거나 인터럽트가 발생할 때 참 조되는 테이블은?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    IVT (Interrupt Vector Table)
  </div>
</details>
## [Q.17-15]
Q. 교착상태 4대 조건을 서술하시오
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    1. 상호 배제(Mutual Exclusion): 자원은 한 번에 하나의 프로세스만 사용할 수 있다.
    2. 점유 대기 (Hold and wait): 프로세스가 자원을 점유한 상태에서 다른 자원을 기다린다.
    3. 비선점 (No Preemption): 자원을 강제로 빼앗을 수 없다.
    4. 순환대기 (Circular Wait): 프로세스들이 자원을 대기하는 상태에서 순환 구조를 형성한다.
  </div>
</details>
## [Q.18-17]
Q. 실행중인 프로세스의 상태를 저장하고 다른 프로세스로 전환하는 작업을 무엇이라고 하는가?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
	문맥 교환 (Context Switching)
  </div>
</details>
## [Q.19-6]
Q. 시스템 콜 서비스 중 프로세스 생성, 대체, 종료를 수행하는 것을 차례대로 쓰시오
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
	fork()
	exec()
	exit()	
  </div>
</details>
## [Q.18-12]
Q. 스레드간의 동기화 기법에 대한 설명이다. 빈 칸에 알맞은 말을 쓰시오
```
공유자원에 대해서 한 순간에 하나의 프로세스만 접근하는 것을 (  )라고 한다. 한 순간에 공유자원에 대해서 하나의 프로세스만 접근하는 방법을 (  )라고 한다. 상호배제 기법 중에서 대기를 의미하는 P연산과 진입을 의미하는 V연산을 사용하는 것은 (  )이다.
```
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    임계영역 / 상호배제 / 세마포어
    
  </div>
</details>
[[동기화]]
## [Q.18-18]
Q. POSIX 계열 운영체제에서 스레드를 생성하는 함수 이름은 무엇인가?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    pthread_create()
  </div>
  <summary>해설</summary>
  <div class="hover-content">
	  pthread.h 헤더에서
	  스레드 생성 : pthread_create()
	  스레드 종료 : pthread_join()
  </div>
</details>
## [Q.16-8 / Q.22-4]
Q. 스레드와 상호배제 구간을 정의하기 위한 동기화 객체를 무엇이라고 하는가? (상호배제 구간에서 하나의 스레드만이 공유자원에 접근할 수 있도록 제어하는 동기화 객체는?)
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    Mutex (뮤텍스)
  </div>
  <summary>해설</summary>
  상호배제 (Mutal Exclusion): 여러 대상이 동시에 같은 공유 자원에 접근시 한 대상만 접근하도록 제어하는 것
  <p>- 뮤텍스는 상호배제 구간을 정의하고, 스레드 간 동기화를 위한 변수</p>
  <p>- 뮤텍스 : 자원 개수를 제어하기 위해 존재</p>
  <p>- 세마포어: 상호배제 구간을 정의하기 위한 변수</p>
</details>
## [Q.15-7]



















