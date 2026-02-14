## 환경설정
### 리눅스 네트워크 환경설정의 개요
1. 호환성
	- 대부분의 리눅스는 네트워크 디바이스의 호환성 제공
	- 배포판 운영 사이트에서 관련 정보 제공
	- 레드햇 리눅스 : http://hardware.redhat.com/hcl
2. 다양성
	- 다양한 네트워크 프로토콜과 네트워크 디바이스를 기본적으로 제공
	- ppp, slip, x.25, atm, wlan, can, fddi, bluetooth, zigbee, 6lowpan 등
	- 리눅스에서 제공하지 않는 경우 해당 디바이스 제조사가 호환되는 모듈 파일을 설치해야 한다.
### 인터넷 접속을 위한 Ethernet card 설치
1. 대부분의 카드 드라이버는 호환되나 최신의 경우 드라이버가 포함되어 있지 않는 경우 제조사서 호환 드라이버를 설치해야 함
2. 드라이버를 받은 후 modprobe나 insmod를 통해 드라이버를 시스템에 로드해야 한다.
3. 재부팅 시 자동으로 로드되도록 /etc/modprobe.d 디렉터리 안에 설정해야 한다.

### 인터넷 접속을 위한 네트워크 인터페이스 설정 방법
1. GUI 기반 설정
	a. X 윈도우의 네트워크 설정창을 진입한다.
	b. 터미널에서 다음과 같이 진행한다.
2. 텍스트 기반
	- nmtui 명령어를 사용하여 Network Manager를 실행하여 설정한다.
3. 명령어를 통한 IP 수동 설정
	```bash
		# ens33 인터페이스에 IP 주소 배정, netmask와 broadcast는 생략 가능
		ifconfig ens33 192.168.100.100 netmask 255.255.255.0 broadcast 192.168.100.255
		# 접두어 길이 표기법
		ifconfig ens33 192.168.100.100/24
		# 인터페이스 활성화
		ifconfig ens33 up
		
		# 라우팅 테이블에 게이트웨이 주소 추가
		route add default gw 192.168.100.1
	```
	- 이 방식은 영구적이지 않다.

1. 네트워크 설정 파일을 통한 IP 수동 설정
	- 설정 파일에 직접 기입하여 설정이 가능
	- 설정 후 "systemctl restart network"를 통해 서비스 재시작 필수
	RedHat 계열
	- 파일: /etc/sysconfig/network-scripts/ifcfg-ens33
		- 네트워크 인터페이스 별 설정이 가능
		- 디바이스명, 프로토콜, IP 등의 설정이 가능
		```bash
		# 설정 대상 이더넷 인터페이스
		DEVICE=ens33
		# IP 할당 방법
		BOOTPROTO=static
		# 이더넷 카드의 MAC 주소
		HWADDR=xx:xx:xx:xx:xx
		# 브로드캐스트 주소
		BROADCAST
		# IP 주소
		IPADDR=
		# 넷마스크 주소
		NETMASK=
		# 네트워크 주소
		NETWORK=
		```
	- 파일: /etc/sysconfig/network-scripts/ifcfg-eth0
		```bash
		# 게이트웨이 주소
		GATEWAY=
		# 시스템 시작 시 자동 활성화 여부
		ONBOOT=yes
		# DHCP 서버의 DNS 정보를 resolv.conf 파일에 저장 여부를 설정
		PEERDNS=yes
		# 1차 DNS 서버의 주소
		DNS1=
		# 일반 계정 권한으로 제어 가능 여부
		USERCTL=no
		# 네트워크 매니저(네트워크 관리 데몬) 사용 여부
		NM_CONTROLLED=yes
		```
ㄲ



