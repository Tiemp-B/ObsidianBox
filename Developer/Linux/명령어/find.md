---
tags:
  - 리눅스
  - 명령어
  - 파일관리
---

# 명령어 역할
사용자가 지정한 조건에 부합하는 파일 시스템에 존재하는 파일과 디렉터리를 찾는다

# 옵션
- -name : 이름. 대소문자 구분함
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
	- -print0 : 개행문자 대신 널 문자로 끝나게 한다
- -fprint : 지정한 파일에 찾은 파일의 전체 파일 경로 출력
	- 존재하는 경우 합쳐진다
- -ls : `ls -dils` 형식으로 정보 출력
- -size : 지정한 크기의 파일 
	- b : 512 바이트 블록
	- c : 바이트
	- w : 워드
	- k : 킬로
	- M
	- G
- -inum : 지정 아이노드
- -iname : name 옵션과 동일하나 대소문자 구분 안함
- -maxdepth : 지정한 깊이의 디렉터리까지만 검색
- -prune : 찾은 파일이 디렉터리인 경우 그 하위까지는 검색 안함
- -empty : 크기가 0이거나 빈 디렉터리 검색
- -newer : 지정 파일보다 최근 수정된 파일
	- 파일의 내용이 변한 시간
- -cnewer : 지정 파일보다 최근 변경된 파일
	- 파일의 메타데이터(허가권, 소유권 등)이 변한 시간

# 예제
```bash
# 현재 경로 이하의 모든 파일 및 디렉터리
find
find .
# 지정 경로 이하의 모든 파일 및 디렉터리
find . /home/usr1 /home/usr2 
# 지정 위치에서 특정 문자열이 포함된 파일
find /home/usr1/target_directory -name '*target*'
# 타입 유형 지정
find /target_directory -name -type f
```

# 연관 명령어
- [[ls]]
- [[cp]]
- [[rm]]
- [[mv]]
- [[touch]]
- [[file]]
- [[find]]


