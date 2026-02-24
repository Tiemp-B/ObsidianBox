---
tags:
  - 리눅스
---

# 명령어 역할
사용자의 패스워드 만료 정보를 설정
`chage [options] username`
# 옵션
- -d, --lastday
	패스워드를 변경해야 할 날짜 수를 지정
	1970-01-01 
- -E, --expiredate
	계정 만령 일자 설정
- -I, --inactive
	계정 만료 후 패스워드가 비활성화될 때까지 유예기간 설정
- -l, --list
	계정의 패스워드 만료 정보 출력
- -m, --mindays
	패스워드 변경까지의 최소 날짜
- -M, --maxdays
	패스워드 변경까지의 최대 날짜
- -W, --warndays
	만료에 대한 경고 메시지 출력 시기

# 예제
```bash
# 최소 사용 날짜 7일, 최대 사용 날짜 365일, 만료 5일 전부터 경고, 만료 후 3일까진 계정 유효
sudo chage -m 7 -M 365 -W 5 -l 3 test
# 계정 만료일을 지정
sudo chage -E 2019-12-24 test
# 패스워드 변경일 지정
sudo chage -d 1000 test
```

# 연관 명령어
- [[adduser]]
- [[useradd]]
- [[passwd]]
- [[su]]
- [[usermod]]
- [[userdel]]
- [[chage]]

