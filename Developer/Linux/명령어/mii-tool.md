---
tags:
  - 리눅스
---

# 명령어 역할
media independent interface tool. 네트워크 인터페이스의 연결 상태를 확인하고 설정을 변경하는 데 사용
MII란?
논리 계층의 MAC과 물리 계층의 PHY를 연결시켜주는 인터페이스


`mii-tool [option] interface`

# 옵션
- -v, --verbose : 상세 정보 출력
- -r : 지정 네트워크 인터페이스 재시작
- -F, --force : 네트워크 인터페이스의 정보를 강제 변경
- -V, --version :
- -R, --reset : mii를 리셋하여 초기 상태로 설정한다.
- -r, --restart : 초기화(auto-negotiation) 시작
# 예제


# 연관 명령어
- [[명령어/ip]]
- [[ping]]
- [[netstat]]
- [[traceroute]]
- [[ss]]
- [[ethtool]]

