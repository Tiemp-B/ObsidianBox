---
tags:
  - 리눅스
  - 명령어
  - 스왑
---

# 명령어 역할
블록 단위로 데이터를 복사

# 옵션


# 예제
```bash
# SWAP 파일 생성. 블록 사이즈=1024바이트, 블록 수=1048576
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```

# 연관 명령어
- [[dd]]
- [[mkswap]]
- [[swapon]]
- [[swapoff]]

