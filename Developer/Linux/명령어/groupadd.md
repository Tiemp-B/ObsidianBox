---
tags:
  - 리눅스
  - 사용자
  - 그룹
---

# 명령어 역할
새 그룹을 생성
`groupadd [options] groupname`

# 옵션
- -f, --force : 이미 생성된 그룹이어도 성공으로 간주
	- -g 옵션하여 이미 존재하는 GID를 기입하면 자동으로 유일 GID를 배정한다
- -r, --system
	- 시스템 그룹 생성
	- login.defs 파일에 정의되어 있는 SYS_GID_MIN~SYS_GID_MAX의 값이 배정
- -g, --gid
	- GID 지정
- -o, --non-unique
	- 중복 GID 허용

# 예제


# 연관 명령어
- [[groupadd]]
- [[groupmod]]
- [[groupdel]]
- [[gpasswd]]
- [[newgrp]]

