---
tags:
  - 리눅스
  - 명령어
  - 백업
---

# 명령어 역할
주로 파티션 단위 백업할 때 사용하는 명령어
`dump [options] [backupdevice] [target_file_or_device]`
# 옵션
- -0~9 : 레벨. 0은 전체 백업 그 후로는 부분 백업. 증분 백업
- -f : 장치/파일 지정
- -u : dump 완료 후 /etc/dumpdates 라는 파일에 백업 정보 기록

# 예제


# 연관 명령어
- [[dump]]
- [[dd]]
- 

