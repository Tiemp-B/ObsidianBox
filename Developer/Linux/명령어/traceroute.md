---
tags:
  - 리눅스
  - 네트워크
---

# 명령어 역할
네트워크 장애 분석을 위해 패킷의 경로를 추적
`traceroute hostname | address`
# 옵션
### 프로토콜
- -I, --icmp : ICMP 방식으로 경로 추적
- -T, --tcp : TCP 방식 추적
- -U, --udp : UDP 방식 추적
### probe
- -q, --queries : 각 홉당 probe 횟수 설정 (기본값: 3회)
- -w, --wait : 각 probe 응답 대기 시간 설정 (기본값: 5초)
- -N, --sim-queries : 동시에 보낼 probe의 수 설정 (기본값: 16개)
### TTL
- -m --max-hops : 최대 홉 수 설정(기본값: 30개)
- -f, --first : 시작 TTL을 설정. `-f N`의 경우 N번째 홉부터 시작(처음 N-1개의 홉 건너뜀)
### 포트
- -p, --port : 포트 설정. `-p` 단일 설정은 UDP, `-T -p`로 TCP 설정
### 출력 형식
- -n : no DNS, DNS 역방향 조회 생략, IP만 표시, 속도 향상됨. IP주소 뒤의 괄호 내 주소가 역방향 IP
- -A, --as-path-lookups : Autonomous System 번호 표시
### 인터페이스 지정
- -i : 특정 네트워크 인터페이스를 사용하여 추적 가능
### 소스 주소 지정

# 출력
각 홉(hop)마다 3번의 probe 패킷을 전송하고 각각의 응답 시간을 표시
\*의 경우 미응답한 경우이다. 

# 예제


# 연관 명령어
- [[명령어/ip]]
- [[ping]]
- [[netstat]]
- [[mii-tool]]
- [[ss]]
- [[ethtool]]


