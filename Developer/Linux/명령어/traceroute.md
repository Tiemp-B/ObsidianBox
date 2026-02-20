---
tags:
  - 리눅스
  - 네트워크
---

# 명령어 역할
네트워크 장애 분석을 위해 패킷의 경로를 추적
`traceroute hostname | address`
# 옵션
- -I, --icmp : ICMP 방식으로 경로 추적
- -T, --tcp : TCP 방식 추적
- -U, --udp : UDP 방식 추적
### probe
- -q, --queries : 각 홉당 probe 횟수 설정 (기본값: 3회)
- -w, --wait : 각 probe 응답 대기 시간 설정 (기본값: 5초)
- -N, --sim-queries : 동시에 보낼 probe의 수 설정 (기본값: 16회)
- 
# 출력
각 홉(hop)마다 3번의 probe 패킷을 전송하고 각각의 응답 시간을 표시
\*의 경우 미응답한 경우이다. 

# 예제


# 연관 명령어


