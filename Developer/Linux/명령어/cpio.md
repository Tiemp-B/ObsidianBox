---
tags:
  - 리눅스
  - 명령어
  - 아카이브
---

# 명령어 역할
아카이브로 파일복사 및 파일 추출

# 옵션
- 모드
	- `cpio -o < name-list > archive` : cpio-out 모드. 아카이브 생성
	- `cpio -i < archive` : cpio-in 모드. 아카이브에서 파일 추출
	- `cpio -p destination-directory < name-list` : cpio-pass 모드. 지정 디렉터리로 복사

- -v, --verbose : 처리중인 파일들의 목록 출력
- -c : -H newc 명령어와 동일하며 SVR4 형식을 사용한다.
- -d, --make-directories : 디렉터리 생성
- -t, --list : 입력으로 들어오는 목록 출력
- -F, --files : 표준 입출력을 사용하지 않고 아카이브할 파일 지정
- -B : 5120바이트 단위 복사. 미사용시 512바이트 단위 복사
- -H, --format : 아카이브할 포맷 형식
	- bin
	- odc
	- newc
	- crc
	- tar
	- hpbin
	- hpodc
	- 등
- -0, --null : 개행문자가 아닌 null 문자로 종료되는 파일 목록을 읽는다.
# 예제
- copy-out
	`ls | cpio -ov  -H tar > home/account/backup.tar`
- copy-in
	```bash
	# 추출
	cpio -iv < home/account/backup.cpio
	# backup.cpio 내의 파일 목록만을 출력
	cpio -ivt < home/account/backup.cpio
	```
# 연관 명령어


