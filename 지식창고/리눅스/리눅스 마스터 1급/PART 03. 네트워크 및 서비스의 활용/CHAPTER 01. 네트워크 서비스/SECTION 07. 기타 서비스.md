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

# 2. 프록시 서비스
## 개요
### 개념
- 클라이언트와 서버 사이에 위치하여 요청과 응답 과정에서 데이터를 중계하는 역할
### 목적
- 서버의 데이터를 Cache하여 인터넷 전송 속도를 빠르게 하기 위해 사용
- 서버의 가용성 향상을 위한 Load Balancing에 사용 가능
- 사용 분야
    - 응답 속도 향상
    - 서버 부하 분산
        - 다수의 서버를 서버팜으로 구성 후 요청을 규칙에 따라 특정 서버에 서비스 요청 전달
    - 접근 통제
        - 프록시 서버에 설정한 접근 통제 적책에 따라 요청 전달/제거
    - 악성코드 유입 방지
        - 프록시 서버에 설치된 백신으로 요청 컨텐츠의 악성코드 여부 점검
## 리눅스 프록시 서버 Squid
### squid 특징
- 리눅스에서 사용하는 대표적인 프록시 서버
- GPL 오픈소스 SW. 
- Caching으로 HTTP, FTP, gopher 등 서비스의 데이터 응답속도 향상
- TCP/3128 이용
### 설정 파일
- `/etc/squid/squid.conf`
    - `cache_dir [옵션]` : 캐시 데이터 저장 경로
        - `ufs [경로] [캐시 데이터 크기, MB] [첫번째 디렉터리 수] [두번째 디렉터리 수]`
        - ufs: squid 저장 포맷
    - `http_port [포트 번호]` : 포트 지정
    - acl 구문 : 별칭 지정 및 접근 권한 설정
        `acl [별칭] src [IP 주소 대역]` 
        `acl [별칭] dst [IP 주소 대역]`
        `acl [별칭] port [포트 번호]`
        `acl [별칭] srcdomain [도메인명]`
        `acl [별칭] dstdomain [도메인명]`
    - `cache_mem [크기]`
    - `cache_log [로그 경로]`
# 3. DHCP 서비스
Dynamic Host Configuration Protocol
## DHCP 개요
### 특징
- 클라이언트 호스트가 사용할 IP 주소, 게이트웨이 주소, 네임 서버 주소 등을 자동으로 할당하는 서비스
- 제한된 IP 주소 Pool을 다수의 클라이언트에게 동적으로 할당하여 IP 주소 사용 효율 향상
- IP 주소의 임대기간 설정 가능
- 저장 장치가 없는 호스트에게 IP를 자동으로 부여하고 네트워크 부팅을 지원하기 위해 사용. BOOTP(Bootstrap Protocol) 프로토콜을 사용한다
- UDP 프로토콜, 브로드캐스트 통신 방식 이용
### 패키지
`dhcp-server`
## 설정
- 데몬 : `dhcpd`
- 설정 파일 : `/etc/dhcp/dchpd.conf`
- 문법 : 설정 문장 뒤에는 반드시 ';' 가 요구된다.
### 문법
```bash
# 로그 메시지를 다른 곳으로 전달
log-facility local7;
# 특정 IP를 할당할 경우 fixed-address 항목 사용.
host sample_pc {
    hardware ethernet 08:00:07:12:c0:a5;
    fixed-address 192.168.12.22;
}
# 클라이언트에 할당할 IP 주소의 대역을 서브넷과 넷마스크 정보와 함께 지정
subnet 192.168.10.0 netmask 255.255.255.0 {
    range 192.168.10.10 192.168.10.200;
    option domain-name "sample-dhcp.com";
    option domain-name-servers name.sample.com;
    option routers 192.168.10.1;
    option broadcast-address 192.168.10.255;
    default-lease-time 600;
    max-lease-time 7200;
}
```
### dhcpd.conf 주요 설정 항목
- range
- range dynamic-bootp
- option domain-name
- option domain-name-servers
- option routers
- option broadcast-address
- default-lease-time
- max-lease-time
- option subnet-mask
- fixed-address
# 4. VNC 서비스
Virtual Network Computing
## VNC 개요
### 특징
- 비트맵 이미지 기반의 RFB(Remote Frame Buffer) 프로토콜을 이용하고 GUI 방식으로 원격 컴퓨터에 접속 및 사용하는 기능 제공
- 클라이언트는 서버의 화면을 전송받아 표시
- 서버는 클라이언트에서의 마우스, 키보드 등의 조작 정보를 서버에 전달
- TCP/5900+\[디스플레이 번호] 를 기본 포트로 사용
- 동시에 여러 클라이언트 접속하여 화면을 공유
### 패키지
- tigervnc-server
- vnc
- 
## 설정 및 실행
### 서버 접속 방법
1. 세션 공유 접속 방법
    - 로컬과 원격 호스트가 화면, 키보드, 마우스를 공유
    - 암호, 알림 등의 정보 설정
2. 독립 세션 방법
    - 별도의 세션으로 접속
    - 환경설정 파일인 `/usr/lib/systemd/system/vncserver@.service` 관련 항목 설정
### 서비스 설정
- 환경설정 파일 `/usr/lib/systemd/system/vncserver@.service`
- 설정 파일의 안내에 따라 `/etc/systemd/system/vncserver@.service`로 복사하면 복사한 파일을 참조
- 특정 user에 대한 사용자 계정명 설정 가능
- `vncpasswd` 명령으로 VNC 서버에 접속할 때 사용할 비밀번호 설정
    - 패스워드는 사용자 홈디렉터리 ~/.vnc/passwd에 저장
### 관련 명령어
- vncpasswd
- Xvnc
- vncconfig
### 실행
서버
`systemctl start vncserver@:디스플레이번호.service`
`systemctl enable vncserver@:디스플레이번호.service`
클라이언트
IP:디스플레이번호

# 5. NTP 서비스 
Network Time Protocol
##  NTP 개요
### 특징
- 컴퓨터 간 시간을 동기화하는 NTP 프로토콜을 이용하여 NTP 서버와 시간을 동기화
- 협정세계시(UTC)를 기준으로 1/000초까지 시간을 동기화
- UDP/123 이용
### NTP 계급(Stratum) 구조
- 클럭소스 수준의 계층적, 반 계층화(Semilayered)된 시스템을 사용
- 레퍼런스 시계에서 거리를 정의
- 원자시계 또는 GPS와 같은 장치가 0단계에서부터 15단계 존재
- 16은 비동기 장치
## 설치와 설정
### 패키지 및 데몬
- 패키지 : ntp
- 데몬 : ntpd
### 설정
- 설정 파일 : `/etc/ntp.conf`
    - driftfile : ntpd에 의해 자동으로 생성되는 driftfile 지정
        - driftfile : 시간 오차의 평균값을 저장하여 시간을 정확하게 유지
    - restrict : NTP 서버에 접근할 수 있는 클라이언트 제한
    - server : NTP 서버 지정
    - keys : 대칭키 암호화를 위한 키 파일 지정
        - `/etc/ntp/keys`
### 명령어
- ntpdate
- ntpq
### 비고
최근에는 ntp 대신 chrony가 기본 NTP 프로그램으로 사용된다
패키지 : cnrony
데몬 : chronyd













