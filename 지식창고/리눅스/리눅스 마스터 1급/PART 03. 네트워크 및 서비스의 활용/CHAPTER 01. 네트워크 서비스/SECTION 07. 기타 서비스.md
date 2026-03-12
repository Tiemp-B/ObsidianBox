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
- Rocky Linux 8은 기본적으로 TCP Wrapper 미지원.
### hosts.allow, hosts.deny 설정 파일
- 하나의 줄에 하나의 규칙
- 2줄 이상 기술 시 줄 마지막에 \\(역슬래시) 입력
- `[데몬 목록] : [클라이언트 목록] : [셸 명령어]`
- 데몬 목록
    - 서비스의 실행 데몬 이름 지정
    - ','로 여러 데몬 이름 지정 가능
    - 예약어 가능
- 클라이언트 목록
    - 접근 제어의 대상이 되는 호스트명/IP 주소 wlwjd 
    - \[사용자명@호스트]의 형식으로 사용자를 함께 지정 가능
    - ','로 여러 클라이언트 지정
    - 예약어 가능
- 셸 명령어
    - 설정항목과 일치할 경우 실행할 셸 명령어로 Twist 방식과 spawn 방식 가능
    - Twist : 현 프로세스의 실행 이미지를 교체하여 실행. 결과를 클라이언트에 전송
    - Spawn : 새로운 자식 프로세스를 생성하는 방식. 결과를 클라이언트에 전송 안함
- 목록 지정을 위한 주요 예약어
    - ALL : 모든 서비스 데몬/ 클라이언트
    - LOCAL : '.'을 포함하지 않는 모든 호스트
    - KNOWN : IP와 호스트명을 알 수 있는 경우
    - UNKNOWN : IP와 호스트명을 알지 못하는 경우
    - PARANOID : DNS lookup을 이용하여 호스트 이름으로 IP를 확인 가능한 경우
    - EXCEPT : 예외 항목 지정
- 셸 명령어의 주요 특수 문자
    - %a : 클라이언트의 IP 주소
    - %A : 서버의 IP 주소
    - %c : 사용자명, 호스트명, IP 주소 등의 클라이언트 정보
    - %d : 서비스명
    - %h : 클라이언트의 호스트명 혹은 IP주소
    - %H : 서버 호스트명 혹은 IP 주소
    - %n : 클라이언트의 호스트명
    - %N : 서버의 호스트명
    - %u : 클라이언트의 사용자명
    - %p : 서비스 데몬 프로세스 아이디
    - %s : 데몬 프로세스, 호스트명, IP 주소 등의 서버 정보
    - \%% : %문자
- 설정 예시
    ```bash
    # 192.168.9.0 에 속한 모든 클라이언트 허가
    [hosts.allow]
    ALL : 192.168.9.0/255.255.255.0
    # telnetd를 제외한 모든 서비스에 대하여 모든 클라이언트의 접속을 허가
    [hosts.allow]
    ALL EXCEPT in.telnetd : ALL
    # www.sample.com을 제외한 sample.com 도메인의 모든 호스트에 대하여 telnetd 서비스 접근 허가
    [hosts.allow]
    in.telnetd : .sample.com EXCEPT \
    www.sample.com
    # 192.168.9.7 에 sshd 서비스 허용. syslog 기록
    [hosts.allow]
    sshd : 192.168.9.7 : severity local0.alert
    # deny로 접근 금지
    [hosts.allow]
    sshd : 192.168.9.2 : deny
    # 특정 호스트가 telnetd 서비스 사용 불가 설정. 접속 시도 시 메시지 전달
    [hosts.deny]
    in.telnetd : 192.168.9.10 : twist /bin/echo \
    "%a is denied" 
    ```

서비스의 지정은 서비스명이 아닌 데몬명으로 지정한다.
telnet이 아닌 in.telnetd이 맞다 























