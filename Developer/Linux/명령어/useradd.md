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
- -g, --gid
	사용자의 그룹(이미 존재)을 설정.
		미설정시 /etc/login.defs의 USERGROUPS_ENAB 변수에 따라 사용자명과 동일한 그룹을 설정하거나 /etc/default/useradd의 GROUP을 지정한다
- -G, --groups
	계정이 속한 그룹 외의 다른 그룹에 계정 추가
- -k, --skel
	-m 옵션을 통해 홈 디렉터리 생성할 때 복사할 기본 파일을 지정할 때 사용
- -m, --create-home
	홈 디렉터리를 지정할 때 사용하고 디렉터리가 없으면 생성
- -M
	홈 디렉터리의 생성을 막음
- -N, --no-user-group
	사용자와 동일한 이름으로 그룹을 생성하지 않는다
	-g 옵션, 혹은 /etc/default/useradd의 GROUP 변수에 지정된 그룹으로 사용자가 추가
- -p, --password
	평문이 아닌 암호화된 패스워드를 설정 가능
	이 옵션은 사용자에게 패스워드 노출이 가능하므로 비권장된다
- -u, --uid 
	사용자의 유일한 UID 값 설정
- -r, --system
	시스템 계정








# 예제


# 연관 명령어
- [[passwd]]
- [[adduser]]

