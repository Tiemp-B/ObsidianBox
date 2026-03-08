---
tags:
  - 리눅스
  - 명령어
  - 권한
---

# 명령어 역할
set for Access Control List
chmod 권한 외에 특정 사용자/그룹에 세부 권한 부여 가능

`setfacl [옵션] [ACL규칠] 파일/디렉터리`

# 옵션
- -m : 규칙 추가/수정
- -x : 삭제
- -b : 모든 규칙 삭제
- -R : 하위 디렉터리 재귀 적용
- -d : 기본 ACL 설정(디렉터리만 적용)
- -k : 기본 ACL 삭제

ACL 규칙 형식
- u:사용자명:권한   : 특정 사용자
- g:그룹명:권한      : 특정 그룹
- o::권한               : 기타 사용자
- m::권한              : 마스크(유효 권한 상한선)
- d: default ACL 접두사

# 예제
```bash
setfacl -m u:user1:rw 파일명
setfacl -m g:group1:r 파일명
setfacl -x u:user1 파일명
setfacl -b 파일명

# 디렉터리에 기본 ACL 설정. 하위에 자동 적용
setfacl -d -m u:user1:rw 디렉터리명
```

# 연관 명령어


