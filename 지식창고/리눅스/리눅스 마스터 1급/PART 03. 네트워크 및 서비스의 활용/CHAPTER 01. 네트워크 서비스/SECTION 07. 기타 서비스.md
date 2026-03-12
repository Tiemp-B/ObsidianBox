```table-of-contents
```
# 1. 슈퍼 데몬
## 개요
### 개념
- 다른 서비스를 실행 및 관리하는 데몬
- inetd 방식(슈퍼 데몬 O) : 사용자의 요청 -> 서비스 실행 -> 완료 후 종료
- standalone 방식(슈퍼 데몬 X) : 데몬 상태로 실행

- 설정 파일 : `/etc/inetd.conf` 
- 접근 제어 : TCP Wrapper
### 서비스 관리 방식
- xinetd 방식(inetd의 개선판. 요청을 중앙 관ㄹ)



















