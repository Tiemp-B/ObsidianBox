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
	패스워드 만료 이후 계정 비활성화할 때까지 유예기간을 지정
- -n, --mindays
	비번을 변경 후 다음 변경까지의 유지 일 수
- -q, --quiet
	아무런 화면 출력 없이 명령 수행
- -w, --warndays
	패스워드 만료 전 경고 날짜를 지정
- x, --maxdays
	패스워드 최대 사용기간을 설정


# 예제


# 연관 명령어
계정관리
- [[adduser]]
- [[useradd]]
- [[passwd]]
- [[su]]
- [[usermod]]
- [[userdel]]
- [[chage]]
비밀번호 관리
[[ㅔㅈ]]