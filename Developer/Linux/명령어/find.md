---
tags:
  - 리눅스
  - 명령어
  - 파일관리
---

# 명령어 역할
사용자가 지정한 조건에 부합하는 파일 시스템에 존재하는 파일과 디렉터리를 찾는다

# 옵션
- -name
- -user
- -group
- -uid
- -gid
- -perm : 허가권
- -type : 파일 유형
	- b : 블록 디바이스
	- c : 캐릭터 디바이스
	- d : 디렉터리
	- p : 파이프
	- f : 파일
	- l : 심볼릭 링크
	- s : 소켓
- -atime : 마지막 access time
- -ctime : 마지막 change time
- -mtime : 마지막 modify time
- -exec : 패턴에 부합하는 파일을 찾을 때마다 실행할 명령어 지정
- -ok : -exec와 기능에 사용자 확인 요구
- -print : 표준 출력으로 전체 파일 경로 출력. 개행 문자로 종료


# 예제


# 연관 명령어
- [[ls]]
- [[cp]]
- [[rm]]
- [[mv]]
- [[touch]]
- [[file]]
- [[find]]


