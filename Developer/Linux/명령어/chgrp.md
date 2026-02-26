---
tags:
  - 리눅스
  - 명령어
  - 권한
---
# 명령어 역할
파일, 디렉터리의 그룹 소유권만 변경한다. 루트 권한이 필요한 chown과는 달리 본인이 소유한 파일에 대해 본인이 속한 그룹 내에서 소유권 변경이 가능하다
`chgrp [options] group file(s)`

# 옵션
- -R, --recursive
- -c, --changes
- -f, --silent, --quite
- -h, --no-dereference
	심볼릭 링크 자체의 파일 및 그룹의 소유권을 변경

# 예제


# 연관 명령어
- [[chmod]]
- [[chown]]
- [[chgrp]]
- [[umask]]

