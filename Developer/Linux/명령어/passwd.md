---
tags:
  - 리눅스
  - 명령어
  - 계정관리
---

# 명령어 역할
생성된 계정자의 패스워드를 입력 및 변경하는 명령어
생성된 패스워드는 /etc/shadow 파일 안에 기록된다.

```bash
passwd [옵션] 계정명
```
# 옵션
- -S, --status
	계정 상태 표시
- -d, --delete
	계정 패스워드 삭제
- -l, --lock
	계정을 lock 상태로 변경하여 로그인을 막는다
- -u, --unlock
	계정을 lock 상태를 해제
- -e, --expire
	패스워드 만료. 다음 로그인 시 패스워드를 변경해야 함
- -i, --inactive
	패스워드 만료 이후
- -n, --mindays
- -q, --quiet
- -w, --warndays
	패스워드 만료 전 경고 날짜를 지정
- x, --maxdays
	패스워드 최대 사용기간을 설정


# 예제


# 연관 명령어


