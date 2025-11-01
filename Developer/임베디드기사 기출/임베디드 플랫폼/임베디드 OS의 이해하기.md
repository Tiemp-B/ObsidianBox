---
cssclasses:
  - hover-reveal
---


## [Q.24-15 / Q.16-1]
Q. 리눅스 계층구조 중 Kernel과 User Application 사이에 위치하는 운영체제가 제공하는 인터페이스를 무엇이라고 하는가?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    System Call
  </div>
</details>

## [Q.19-12]
Q. 리눅스 사용자 프로그램에서 H/W를 제어할 때 사용되는 시스템 콜로 주로 디바이스 드라이버를 제어할 때 사용되는 것은?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    ioctl
  </div>
</details>

## [Q.15-10 / Q.20-14 / Q.21-5]
Q. 운영체제의 핵심 부분으로, 프로세스 관리, 메모리 관리, 파일 시스템 관리, 네트워크 관리, 디바이스 드라이버 관리 등 기본적인 자원 관리를 담당하는 것은?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    Kernel (커널)
  </div>
</details>

## [Q.16-10 / Q.23-8]
Q. 운영체제와 커널을 동일 메모리에 저장해 놓은 단순한 방식의 커널을 무엇이라고 하는가?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    모놀리식 커널 (Monolithic Kernel)
  </div>
  <summary>해설</summary>
  - 모놀리식 커널 : 커널의 모든 기능을 포함하는 커널 <br>
	  모든 운영체제 기능이 커널 내부에서 하나로 결합되어 동작하는 구조로, 성능이 뛰어나지만 시스템 안정성에 대한 관리가 까다로울 수 있다.<br>
  - 마이크로 커널 : 커널에 핵심적인 기능만을 포함하고 적용분야에 따라 추가하는 커널<br>
	  서버를 추가하는 방식이라 기능을 추가하기 쉽고, 시스템이 견고하며 실시간성이 높다. 그나 시스템 기능들이 서버의 형태로 존재하기 때문에 커뮤니케이션 오버헤드가 존재한다.
</details>

## [Q.22-12]
Q. 리눅스 커널 소스에서 디렉터리에서 다음의 기능에 해당하는 디렉터리명을 쓰시오
- 프로세스:
- 네트워크 : 
- 파일 시스템 :
- 디바이스 :
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    프로세스 : kernel (커널 핵심 코드와 모듈)<br>
    네트워크 : net (네트워크 관련 소스 코드와 모듈)<br>
    파일 시스템 : fs (파일시스템 소스와 모듈)<br>
    디바이스 : drivers (드라이버 소스와 모듈)
  </div>
</details>

## [Q.19-15]
Q. 리눅스의 kconfig, config, defconfig에 대하여
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    kconfig : 커널 설정 파일을 관리하는 구성 시스템으로 커널 컴파일 시 사용할 옵션 정의<br>
    config : 커널 설정 옵션을 포함하는 파일로, 커널 컴파일 시 어떤 기능이 포함될 지를 정의 <br>
    defconfig : 기본 커널 설정 파일로, 특정 하드웨어 플랫폼이나 목적에 맞춘 기본값이 포함
  </div>
</details>

## [Q.17-10 / Q.21-7]
Q. 리눅스 커널에서 디버깅을 위해 printf() 대신 사용할 수 있는 함수는?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    printk()
  </div>
</details>

## [Q.19-8 / Q.24-13]
Q. 리눅스 커널의 보안 유형 기술 2가지는?
<details class="hoverbox">
  <summary>답안</summary>
  <div class="hover-content">
    AppArmor: 경로 기반의 접근 제어, 개별 프로그램이 접근할 수 있는 파일과 네트워크 리소스를 제한<br>
    SELinux: 라벨링 기반의 강력한 접근 제어를 제공, 시스템 전체에 적용되는 정책, MAC(Mandatory Access Control, 강제적 접근 제어) 사용
  </div>
</details>
