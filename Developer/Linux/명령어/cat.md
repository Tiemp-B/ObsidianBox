---
tags:
  - 리눅스
  - 명령어
  - 텍스트
---
# 명령어 역할
파일의 텍스트 내용을 보거나 다른 새로운 파일로 복사 및 기존 파일과 병합
`cat [option] file`
# 옵션
- -b, --number-nonblank
- -n, --number
- -E, --show-ends
- -T, --show-tabs
- -v, --show-nonprinting
- -A, --show-all
- -s, --squeeze-blank

# 예제
```bash
# 파일을 읽어 새 파일에 작성. 기존 파일을 덮어쓴다
cat readme.txt > newreadme.txt
# 파일을 읽어 
cat readme.txt >> newreadme.txt
```

# 연관 명령어


