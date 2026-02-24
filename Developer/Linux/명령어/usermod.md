---
tags:
  - 리눅스
  - 명령어
  - 계정관리
---

# 명령어 역할
사용자 셸, 홈 디렉터리, 그룹, UID, GID 등의 사용자 설정을 변경
useradd 명령어에서의 설정 대부분을 수정 가능
`usermod [options] username`
# 옵션
- -a, --append
	사용자에게 그룹을 추가하기 위해 -G 옵션과 같이 사용
- -c, --comment
	사용자에 대한 정보 추가
- -d, --home
	홈 디렉터리 변경.
	-m 옵션을 추가하여 현 홈 디렉터리 내용을 새로운 홈 디렉터리로 복사 및 강제 생성
- -e, --expiredate
	YYYY-MM-DD 형식으로 비활성화 날짜를 지정
- -f, --inactive
	패스워드 만료 후 계정 유효 기간
- -g, --gid
	존재하는 그룹의 이름이나 GID를 입력하여 변경
- -G, --groups
	guswo wlwjd rmfnqdp cnrkgkf rmfnqdfm wlwjd
- -l, --login
	사용자의 로그인 이름 변경
- -L, --lock
	사용자의 패스워드에 락을 걸어 로그인 막음
- -m, --move-home
	홈 디렉터리의 내용을 새로운 홈 디렉터리로 옮김
	-d 옵션과 같이 사용
- -p, --password
	암호화된 패스워드 설정
- -s, --shell
	사용자의 새로운 셸을 지정
- -u, --uid
	사용자의 UID 지정
- -U, --unlock
	락 해제

# 예제
```bash
# 디렉터리 변경
usermod -d /home/whiteblue blue
# 디렉터리 변경 -m으로 내용 복사
usermod -dm /home/whiteblue blue

# 그룹 설정
usermod -g newgroup blue
```


# 연관 명령어


