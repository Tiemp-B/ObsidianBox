---
tags:
  - 리눅스
  - 네트워크
  - 네트워크_진단
---

# 명령어 역할
ICMP(Internet Control Message Protocol: 인터넷 제어 메시지 프로토콜. 장치가 IP 패킷 전송 중 발생한 오류를 보고하거나 네트워크 상태를 진단하는데 사용하는 제어 프로토콜)을 이용한 네트워크 상태 진단 도구
운격의 호스트가 네트워크에 연결된 상태인지 확인하고 네트워크 지연시간 측정 가능

`ping options hostname|address`

# 옵션
- -c : count. ping을 보낼 횟수(기본: 무제한)
- -i : interval. 보낼 시간 간격(기본: 1초)
- -s : size. 보낼 데이터의 크기(최대 65507)
- -f : flood. 최대한 많이 보낸다. -i 미설정 시 0으로 하여 최대한 많은 요청 전송
- -w : seconds. ping 시작 후 몇 초 뒤에 실행을 멈출지 결정
- -I : interface 네트워크 인터페이스가 다수인 경우 전송할 인터페이스 지정

# 예제


# 연관 명령어
- [[netstat]]
- [[traceroute]]
- [[mii-tool]]
- [[ss]]
- [[ethtool]]
- [[ip]]

