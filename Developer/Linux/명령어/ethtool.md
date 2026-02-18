---
tags:
  - 리눅스
  - 네트워크
  - 네트워크_진단
---

# 명령어 역할
네트워크 인터페이스 카드(NICs)를 위한 유틸리티/설정 도구
네트워크 속도, 포트, 저동 설정 등의 설정 변경 가능

`ethtool [options] interface`
# 옵션
- -i : 인터페이스의 디바이스 드라이버 정보
- --statistics, -S : 인터페이스의 통계 
- --change, -s : 인터페이스의 설정 변경
	`ethtool --change eth0 speed 100 duplex full`

# 예제


# 연관 명령어


