---
tags:
  - 리눅스
  - 명령어
  - 계정관리
---
# 명령어 역할
계정을 생성하는 명령어로 명령어 adduser와 동일한 기능을 가진다.
생성된 계정 정보는 파일 /etc/passwd, /etc/shadow, /etc/group에 저장된다

```bash
useradd [옵션] 계정명
```
# 옵션
- -s, --shell
	사용자의 로그인 기본 셸을 지정
- -d, --home
	계정의 홈 디렉터리를 지정
- -D, --defaults
	사용자 생성에 사용하는 기본값을 보거나 설정
- -f, --inactive
	패스워드 만기된 후 계정이 영구히 말소될 때까지의 기간 지정
	미설정시 /etc/default/useradd의 INACTIVE 값을 따른다
- -e, --expiredate
	계정의 유효기간을 설정
	미지정시 /etc/default/useradd의 EXPIRE 필드를 따른다
- c
	파일 /etc/passwd에 새로운 사용자 설명을 추가
- G
	계정이 속한 그룹 외의 다른 그룹에 계정 추가

# 예제


# 연관 명령어
- [[passwd]]
- [[adduser]]

