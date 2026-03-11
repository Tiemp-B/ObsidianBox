```table-of-contents
```
# 1. 메일 관련 서비스의 개요
## 메일 서비스
### 개념
`아이디@메일서버명`형식의 메일 주소로 전자메일을 주고 받는 서비스
### 프로토콜
- SMTP(Simple Mail Transfer Protocol)
	- 메일 서버 간의 송수신 및 메일 클라이언트에서 메일 서버로 메일 전송
	- TCP 110 포트
- POP/POP3 : Post Office Protocol
	- 메일 서버에 도착한 메일을 수신하는 프로토콜
	- 클라이언트 프로그램으로 메일을 가져온 후 서버에서 삭제
	- TCP 110 포트
- IMAP : Internet Messaging Access Protocol
	- 메일 서버에 도착한 메일을 수신하는 프로토콜
	- POP과 다르게 메일을 서버에 남겨두고 나중에 삭제 가능
	- TCP 143 포트
### 관련 프로그램 분류
- MTA : Mail Transfer Agent
	- SMTP 메일 전송 프로그램
- MDA : Mail Deliver Agent
	- 메일 박스에 도착한 메일을 전달하는 대리인 역할
- MUA : Mail User Agent
	- 메일을 수신/발신에 사용하는 프로그램
### 메일 전송 구조


# 2. 메일 관련 서비스 사용
## sendmail 패키지
### 주요 설정 파일

|









