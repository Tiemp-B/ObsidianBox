---
tags:
  - 리눅스
---

# 명령어 역할
라우팅 테이블을 표시 및 수정
패킷의 목적지 주소와 넷마스크로 얻은 네트워크 주소와 라우팅 테이블에 매칭되는 경로가있다면 해당 경로에 설정된 네트워크 인터페이스를 통해 패킷을 라우팅한다
```bash
형식
route
route add [-net|-host] target [netmask Nm] [gw Gw] [[dev] If]
route del [-net|-host] target [gw Gw] [netmask Nm] [[dev] If]
```

## 설명
### 테이블 정보
- Destination : 목적지 호스트나 네트워크의 주소
- Gateway :  외부 네트워크와 연결되어 있는 게이트웨이 주소
- Genmask : 넷마스크 주소. 0.0.0.0 의 경우 내부 네트워크
- Flags : 라우팅 경로의 플래그
	- U : 정보 유효
	- H : 목적지가 호스트
	- G : 목적지로 가려면 게이트웨이 경유 필요
	- D : 데몬 또는 ICMP 리다이렉트 메세지를 통해 설치된 상태
	- M : 데몬 또는 ICMP 리다이렉트 메세지를 통해 수정된 상태
- Metric : 목적지 호스트나 네트워크까지 도달하기 위한 비용
- Ref : 경로 참조 횟수
- Use : 경로 탐색 횟수
- Iface : 패킷을 내보낼 네트워크 인터페이스

# 옵션


# 예제
1. 디폴트 게이트웨이 추가/제거
```bash
# add 옵션 default gw 옵션으로 디폴트 게이트웨이 추가
route add default gw 10.0.2.2 dev eth0
# del 옵션으로 디폴트 게이트웨이 삭제
route del default gw 10.0.2.2 
```
2. 특정 네트워크에 대한 라우팅 정보 추가/제거
```bash
# -net 옵션, netmask 옵션으로 특정 네트워크를 목적지로 하는 라우팅 정보 추가
route add -net 10.0.2.128 netmask 255.255.255.128 gw 10.0.2.2 dev eth0
# 제거
route del -net 10.0.2.128 netmask 255.255.255.128 gw 10.0.2.2 dev eth0
```
3. 특정 호스트에 대한 라우팅 정보 추가 및 제거
```bash
# -host 옵션을 사용하여 특정 호스트를 목적지로 하는 라우팅 정보 추가
route add -host 10.0.2.50 dev eth0
# del 옵션과 -host 옵션을 사용하여 특정 호스트를 목적지로 하는 라우팅 정보 삭
```

# 연관 명령어


