---
tags:
  - 리눅스
  - 명령어
  - 권한
---

# 명령어 역할
파일 혹은 디렉터리의 권한을 수정한다
`chmod [option] mode file(s)`

# 옵션
- -R, --recursive : 특정 디렉터리 내의 파일과 디렉터리에 대하여 재귀적으로 허가권을 수정한다
- -C, --changes : 변경된 파일이나 디렉터리에 대한 자세한 정보 출력
- -f, --silent, --quite : 에러 메시지의 출력 제한
- --reference : 모드 대신 다른 파일을 지정하여 해당 권한을 복사

- u=(rwx) : 사용자
- a=(rwx) : 다른 사용자 전부
- g=(rwx) : 그룹

- u/a/g+/-(rwx) : 특정하여 추가 및 제거 가능

- 특수 비트
	- Set-UID
		`chmod u+s filename`
	- Set-GID
		`chmod g+s filename`
	- 스티키 비트


# 예제


# 연관 명령어


