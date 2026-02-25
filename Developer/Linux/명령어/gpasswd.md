---
tags:
  - 리눅스
  - 명령어
  - 계정관리
  - 그룹
---

# 명령어 역할
그룹의 패스워드를 변경. 
해당 정보는 다음 파일에 저장되어 있다
- /etc/group
- /etc/gshadow
`gpasswd [options] groupname`

# 옵션
- -a, --add 
	그룹에 사용자 추가
- -d, --delete
	그룹에서 사용자 삭제
- -r, --remove-password
	그룹 패스워드 제거
	그룹 멤버는 newgrp 명령어를 통해 그룹에 참가 가능
- -R, --restrict
	그룹의 접근 제한
- -A, --administrators
	지정 사용자를 관리자로 지정한다
- -M, --members
	

# 예제


# 연관 명령어


