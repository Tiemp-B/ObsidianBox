---
tags:
  - 리눅스
---

# 명령어 역할
네트워크 연결, 라우팅 테이블, 인터페이스의 통계 정보, 마스커레이드 연결, 멀티캐스트 멤버십 등의 네트워크 정보 출력

`netstat options`
# 옵션
첫번째 옵션
- 미지정 : 열려 있는 소켓의 모든 정보 출력
- -r, --route : 라우팅 테이블 조회
- -g, --groups : IPv4, IPv6를 위한 멀티캐스트 그룹 멤버십 정보를 조회
- -i, --interfaces, -i : 모든 네트워크 인터페이스에 대한 정보 출력
- -M, --masquerade : 마스커레이드 연결의 정보 출력
- -s, --statistics : 각 프로토콜의 통계 정보 출력

두 번째 옵션
- -v, --verbose : 풍부한 정보 제공
- -n, --numeric : 심볼릭 호스트, 사용자, 포트 대신 숫자 표기
- -A, protocol-family : 주소 패밀리를 지정한다.
	- inet, inet6, ax25, netrom, ipx, ddp, x25를 지정 가능
- -c, --continuous : 매 초마다 정보 출력
- -p, --program : 소켓과 연관된 프로그램 이름과 PID를 출력
- -l, --listening : Listen 소켓에 대한 정보 출력
- -a, --all : Listen 소켓, Listen이 아닌 소켓 모두 출력
- -t : TCP 소켓 정보
- -u : UDP 소켓 정보
- -
# 예제


# 연관 명령어


