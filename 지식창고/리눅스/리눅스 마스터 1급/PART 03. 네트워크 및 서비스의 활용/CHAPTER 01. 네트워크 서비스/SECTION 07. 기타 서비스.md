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
- xinetd 방식(inetd의 개선판. 요청의 중앙 관리 슈퍼 데몬)의 많은 서비스가 단독 데몬으 전환되거나 systemd에 의한 관리 방식으로 통합(ex. rsync, telnet 등). CentOS 6 이후부터 systemd 방식으로 넘어가고 있다
- systemd 방식 : socket 기능(On-demand Activation : 소켓에 요청이 들어오면 서비스 실행)
### xinetd
1. 특징
	- 리눅스 커널 2.4 이후 inetd의 확장판 xinetd 사용
	- 기본 설정 파일 : `/etc/xinetd.conf`
	- 패키지 : xinetd
	- 자체적으로 접근 제어 기능과 확장된 로깅 기능 등을 제공
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
    - enabled : 사용 가능한 서비스 목록
    - disabled : 금지 서비스 목록
    - includedir /etc/xinetd.d : 각각의 서비스에 대한 개별 설정 디렉터리
        - 파일명은 서비스명
4. 서비스 주요 설정
    - service : 서비스 명
    - type : 유형 (RPC, INTERNAL(`/etc/services`에 서비스로 등록), UNLISTED 등)
    - disable : no로 설정하여 서비스 사용
    - socket_type : TCP->stream, UDP->dgram, IP직접 접근->raw
    - port : 서비스 포트 지정
    - wait : 요청 받은 즉시 처리, 대기 후 처리
    - user : 서비스 실행 권한
    - server : 실행 데몬 파일의 절대 경로
    - server_args : 데몬에 전달할 인자
    - log_on_failure : +/- 로 xinet.conf에서 지정한 log_on_failure 항목으로 변경
    - access_times : `16:00-17:00`형식의 서비스 이용 가능 시간 지정
    - redirect : 다른 서버로 포워딩
    - nice : 우선순위. -20~19

## TCP Wrapper
### 개념
- inetd 데몬에 의해 관리되는 서비스에 대한 접근 제어
- 데몬명 : **tcpd**
- 설정 파일
    - `/etc/hosts.allow`
    - `/etc/hosts.deny`
- allow -> deny 순으로 적용. 중복 시 allow를 따른다
- 





















