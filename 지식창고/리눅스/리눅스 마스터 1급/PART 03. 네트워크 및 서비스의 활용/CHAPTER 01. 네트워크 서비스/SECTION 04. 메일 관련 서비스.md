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
## sendmail 
### 패키지
- sendmail
- sendmail-cf
### 주요 설정 파일

| 설정 파일명                     | 설명                                                                                                                                                                                                                            |
| :------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /etc/mail/sendmail.cf      | 주 설정 파일                                                                                                                                                                                                                       |
| /etc/mail/sendmail.mc      | 설정 보조 파일. m4 유틸리티로 `m4 sendmail.mc > sendmail.cf`로 사용.                                                                                                                                                                        |
| /etc/aliases               | 메일의 별칭 혹은 특정 계정으로 수신한 이메일을 다른 계정으로 전달<br>여러 사람에게 전달할 때에 사용<br>`[수신 계정]: [전달 계정]`<br>`:include:[파일 이름]` 으로 사용자 이름이 저장된 파일 설정 가능<br>sendmail의 참조 파일은 /etc/aliases.db 이므로 /etc/aliases 수정 후 `newaliases`나 `sendmail -bi` 명령으로 적용 |
| /etc/mail/access           | 메일 서버 접속 제어. 스팸 메일 방지 등에 적용<br>형식 : `[정책 대상] [정책]`                                                                                                                                                                            |
| /etc/mail/virtusertable    | 가상의 메일 계정으로 들어오는 메일을 특정 계정으로 전달하는 정보                                                                                                                                                                                          |
| /etc/mail/local-host-names | sendmail에서 수신할 메인과 도메인과 호스트, 즉 메일 수신지 설정                                                                                                                                                                                      |
| ~/.forward                 | 사용자 개인이 수신한 메일을 다른 메일로 포워딩 설정                                                                                                                                                                                                 |
### /etc/mail/sendmail/cf
sendmail의 기본 동작 방식 지정
- Cw : 메일 수신 호스트의 이름 설정. 보통 도메인명. 기본`Cwlocalhost`
- Fw : 여러 개의 도메인명을 수신 호스트의 이름으로 이용








