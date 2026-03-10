```table-of-contents
```
# 1. SAMBA 서비스 
## 개요
### 특징
- GPL 라이선스
- 리눅스와 윈도우 간 디렉터리, 파일, 프린터 등을 공유하는데 사용
- TCP/IP 기반으로 NetBIOS상에서 동작하는 SMB(Server Message Block) 프로토콜
	- NetBIOS : 로컬 네트워크 내 컴퓨터 간 통신 및 자원 공유 API/프로토콜
- SAMBA에서 설정한 그룹과 호스트명이 윈도우의 Network Neighborhodd에 컴퓨터 이름으로 표시
- 삼바를 사용하면 컴퓨터 이름을 이용한 접속 가능 => WINS(Windows Internet Name Service)
- CIFS(Common Internet File System)는 SMB를 인터넷까지 확장한 표준 프로토콜
### 구성
1. 서버
	- nmbd
		137, 138 포트로 브로드 캐스팅 방식으로 검색한 후, 139 포트로 접속
		- NetBIOS Name Service (UDP 137)
		- NetBIOS Datagram Service (UDP 138)
		- NetBIOS Session Service (TCP 139)
	- smbd
		- Direct SMB(TCP 445)
2. 클라이언트

## 삼바 서비스 설치
### 관련 패키지
- samba : samba 데몬, 관련 라이브러리 및 스크립트 등을 포함
- samba-common : 삼바 서버, 클라이언트에서 공통으로 사용하는 설정 및 명령어
- samba-client : sambaclient, smbtree 등의 삼바 클라이언트 관련 명령어
- 