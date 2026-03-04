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
- -p, --preserve-permissions: tar 파일에서 파일

# 예제


# 연관 명령어


