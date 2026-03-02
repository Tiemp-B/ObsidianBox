---
tags:
  - 리눅스
  - 명령어
  - 파일시스템
---
# 명령어 역할
하드디스크 전체나 특정 파티션을 현재 존재하는 파일 시스템의 디렉터리 구조에 붙여서 접근 가능하게 하는 명령어

# 옵션
- -a, --all : /dev/fstab에 명시된 모든 파일 시스템을 마운트
- -t, --types : 파일 시스템의 유형 지정
- -o, --options : 옵션 추가
	- 공통
		- ro
		- rw
		- atime / noatime
			- noatime(파일 접근 시간 변경 안함)의 비설정 / 설정
		- auto / noauto
		- remount
	- ext2, ext3
		- acl
			- 접근 제어 리스트를 사용하여 마운트
	- fat
		- blocksize
		- fat
			- 12, 16, 32 지정
	- iso9660
		- block
	- loop
		- loop
	- cifs
		- username
		- password
		- domain

# 예제


# 연관 명령어
- [[fdisk]] 
- [[mount]] 
- [[mkfs]]
- [[mke2fs]] 

