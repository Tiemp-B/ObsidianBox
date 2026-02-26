---
tags:
  - 리눅스
  - 명령어
  - 권한
---

# 명령어 역할
소유권을 변경한다. 루트 권한이 필요하다

# 옵션
- -R, --recursive : 지정한 디렉터리 내의 파일과 디렉터리들에게도 반복적으로 적용한다
- -C, --changes : 변경된 파일이나 디렉터리에 대한 자세한 정보 출력
- -f, --silent, --quite : 에러메시지 출력 제한
- --reference : 지정한 파일/디렉터리의 소유권을 복사

# 예제
```bash
# 사용자 소유권
chown username filename
# 사용자, 그룹 소유권
chown username:groupname filename
# 그룹만
chown :groupname filename
# UIG
```

# 연관 명령어
- [[chown]]
- [[chmod]]
- 

