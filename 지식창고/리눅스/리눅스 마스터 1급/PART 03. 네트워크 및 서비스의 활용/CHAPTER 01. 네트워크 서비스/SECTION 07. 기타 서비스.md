```table-of-contents
```
# 1. 슈퍼 데몬
## 개요
### 개념
- 다른 서비스를 실행 및 관리하는 데몬
- inetd 방식(슈퍼 데몬 O) : 사용자의 요청 -> 서비스 실행 -> 완료 후 종료
- standalone 방식(슈퍼 데몬 X) : 데몬 상태로 실행

- 설정 파일 : `/etc/inetd.conf` 
- 접근 제어 : TCP Wrapper(네트워크 서비스에 대한 IP 기반 접근 제어 보안 도구)
### 서비스 관리 방식
- xinetd 방식(inetd의 개선판. 요청의 중앙 관리 슈퍼 데몬)의 많은 서비스가 단독 데몬으 전환되거나 systemd에 의한 관리 방식으로 통합(ex. rsync, telnet 등)
- systemd 방식 : socket 기능(On-demand Activation : 소켓에 요청이 들어오면 서비스 실행)
### xinetd
1. 특징
	- 리눅스 커널 2.4 이후 inetd의 확장판 xinetd 사용
	- 기본 설정 파일 : `/etc/xinetd.conf`
	- 패키지 : xinetd
2. 설정 파일 예제
	```bash
	defaults
	{
		log_type		= SYSLOG daemon info
		log_on_failure	= HOST
		log_on_success	= PID HOST DURATION EXIT
		...생략
	}
	```
3. `/etc/xinetd.conf` 주요 설정
    - instances : 최대 동시 서비스 서버 수
    - log_type : 로그 기록 방식 지정 \[SYSLOG/FILE]
    - log_on_success : 서버 시작, 종룍 및 접속 시 기록할 내용 지정
    - log_on_failure : 서버 시작 실패, 접근 거부시 기록할 내용 지정
    - cps : 초당 최대 요청 및 초과시 접속 제한 시간 설정
    - only_from : 이용 가능 호스트 지정
    - per_source : 동일한 IP 주소로부터 접속할 수 있는 최대 접속 수 지정
    - enabled
    - disabled
    - includedir /etc/xinetd.d

















