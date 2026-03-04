---
tags:
  - 리눅스
  - 명령어
  - 압축
---

# 명령어 역할
수많은 파일을 하나의 아카이브 파일로 만드는 유틸리티
유닉스의 TAR는 순수하게 파일을 아카이브하는 역할만 수행
리눅스의 TAR는 COMPRESS, GZIP, BZIP2, XZ 등으로 압축하는 것도 지원

# 옵션
### 주 동작 모드
- -A, --catenate, --concatenate : tar 파ㅣㅇㄹ간의 병합
- -c, --create : 새 아카이브 생성
- --delete : 아카이브에서 삭제
- -d, --diff, --compare : 아카이브 및 파일 시스템 차이점 찾기
- -r, --append : 아카이브에 파일 추가
- --test-label : 아카이브 볼륨 레이블을 시험하고 빠져나간다
- -u, --update : 아카이브 내 사본보다 최신인 파일만 추가
- -x, --extract, --get : 아카이브 파일 추출

### 동작 조절 옵션
- --check-device : 증분 아카이브를 만들 때 장치 번호 검사
- -g, --listed-incremental= : 최신 GNU 형식 증분 백업 처리
- -S, --sparase : 성긴 파일을 제대로 처리
- 등등

### 로컬 파일 이름 선택
- --add-file=<파일> : 설정 <파일>을 아카이브에 추가
- -C, --directory=<디렉터리> : 지정 디렉터리로 전환하여 진행
- --exclude=<패턴> : 주어진 <패턴> 값에 해당하는 파일 제외
- 등등의 exclude 명령어
- -T, --files-from=<파일> : <파일>에서 추출할 이름을 가져오거나 지정 이름으로 만든다
- 등등

### 덮어쓰기 관리
- -k, --keep-old-files : 추출 시 기존 파일을 바꾸지 않고 오류로 간주
- --keep-newer-files : 아카이브 사본보다 최신인 기존 파일은 바꾸지 않음
- 등등

### 확장 파일 속성 처리
- --acls : POSIX ACL 지원 활성화
- --no-acls : POSIX ACL 지원 비활성화
- --no-selinux
- --no-xattrs : 확장 속성 지원 비활성화
- 등등

### 장치 선택 및 전환
- --force-local : 콜론이 있어도 로컬 아카이브 파일로 간주
- -f, --file=<아카이브> 아카이브 파일명 또는 장치명이 <아카이브>
- -F, --info-script=<명칭>, --new-volume-script=<명칭> : 각 테이프 끝 부분 도달 시 스크립트 실행
- 등등

### 장치 블로킹


### 아카이브 형식 선택
- -H, --format=<형식>
	형식 목록
	- gnu
	- oldgnu
	- pax
	- posix
	- ustar
	- v7
- -V, --label=<텍스트> : <텍스트> 볼륨 이름을 지닌 아카이브 생성.

### 압축 옵션
- -a, --auto-compress
- -I, --use-compress-program=<프로그램> : <프로그램>으로 압축 진행. -d 옵션으로 연계해야 한다.
- -j, --bzip2 : bzip2로 아카이브를 필터링
- -J, --xz : xz
- --lzip : lzip
- --lzma : xz --format=lzma로 필터링
- --lzop : lzop
- --no-auto-compress : 후위 확장자 사용 안함
- -zstd : zstd
- -z, --gzip, --gunzip, --ungzip : gzip으로 필터링
- -Z, --compress, --uncompress




아카이브 생성/추출
- -c, --create : 새로운 tar 생성
- -x, --extract : tar 파일을 해체

처리 정보
- v, --verbose : 사용자에게 보여주는 정보량 증가
- -t, --list : tar 내에 묶여있는 파일의 목록 출력. 인자 지정 시 해당 파일 검색

인자
- -f, --file : 생성되는 tar파일명 지정
- -r, --append : tar 파일에 또 다른 파일 추가
- -h, --derefernce : 링크 파일이 가리키고 있는 원본 파일도 tar에 포함
- -C, --directory : 명령을 수행할 디렉터리 지정
- -p, --preserve-permissions: tar 파일에서 파일을 추출할 때 사용자 권한 유지

압축 기법
- -Z, --compress, --uncompress : compress를 사용하여 압축
	tar.Z 파일을 생성한다.

# 예제


# 연관 명령어


