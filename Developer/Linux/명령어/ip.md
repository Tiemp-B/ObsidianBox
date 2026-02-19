---
tags:
  - 리눅스
  - 네트워크
  - 네트워크_진단
---

# 명령어 역할
ifconfig의 대체
네트워크 인터페이스에 주소 할당이나 파라미터 설정 가능

`ip [options] [commnad] [address [dev interface]`
# 옵션 및 예제
- route : 라우팅 테이블에 항목 추가/제거

- addr : 네트워크 인터페이스의 IP 정보를 출력
	```bash
	# 인터페이스 정보 출력
	ip addr
	ip addr show
	ip addr list
	# IP 할당/제거
	ip addr add 192.168.100.100 dev eth0
	ip addr add 192.168.100.100/255.255.255.0 dev eth0
	ip addr add 192.168.100.100/24 dev eth0
	ip addr del 192.168.100.100/24 dev eth0
	```
- link : 네트워크 인터페이스의 상태 설정
	```bash
	# 활성화/비활성화
	ip link set dev eth0 down
	ip link set dev eth0 up
	# MTU(Maximum Transfer Unit:네트워크를 통해 한 번에 전송 가능한 최대 데이터 패킷 크기)
	ip link set mtu 9000 dev eth0
	```
- neighbor : ARP 캐시 관리
	```bash
	ip nei
	```


# 예제


# 연관 명령어
- [[ping]]
- [[netstat]]
- [[traceroute]]
- [[mii-tool]]
- [[ss]]
- [[ethtool]]

