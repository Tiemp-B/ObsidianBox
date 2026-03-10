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
	- nmbd (NetBIOS message Block daemon)
		137, 138 포트로 브로드 캐스팅 방식으로 검색한 후, 139 포트로 접속
		- NetBIOS Name Service (UDP 137)
		- NetBIOS Datagram Service (UDP 138)
		- NetBIOS Session Service (TCP 139)
	- smbd
		- Direct SMB(TCP 445)
	- winbindd
		- Windows 도메인 인증 연동. 필수 아님
2. 클라이언트

## 삼바 서비스 설치
### 관련 패키지
- samba : samba 데몬, 관련 라이브러리 및 스크립트 등을 포함
- samba-common : 삼바 서버, 클라이언트에서 공통으로 사용하는 설정 및 명령어
	- smb.conf 설정 파일과 설정파일 검사하는 testparm 등
- samba-client : sambaclient, smbtree 등의 삼바 클라이언트 관련 명령어
- samba-swat : 삼바 설정파일을 웹으로 이용 및 관리. 901포트

## 삼바 서비스 서버 설정 파일 smb.conf
설정 파일 : `/etc/samba/smb.conf`
### smb.conf의 주요 구성
두 영역으로 구분되며, `[]`으로 세부 섹션을 구성한다
- Global Section
- Share Definition
### Global Section

| 설정 항목               | 설정 설명                                                                                                                                                                                                                                                                                        |
| :------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| workgroup           | 공유 그룹명 지정                                                                                                                                                                                                                                                                                    |
| server string       | 서버에 대한 설명<br>기본값: `server string = Samba Server Version %v`                                                                                                                                                                                                                                  |
| netbios name        | 이름을 이용한 접속에 사용                                                                                                                                                                                                                                                                               |
| interfaces          | 사용할 네트워크 인터페이스 설정 <br>`interfaces = lo eth0 192.168.12.2/24 192.168.13.2/24`                                                                                                                                                                                                                 |
| hosts allow         | 접근 가능한 호스트 지정                                                                                                                                                                                                                                                                                |
| log file            | 삼바 서버의 로그파일 지정<br>기본값: `log file = /var/log/samba/log.%m`                                                                                                                                                                                                                                    |
| max log size        | 로그 파일의 최대 KB 설정<br>초과시 기존 파일은 .old 로 변환 후 새 로그 파일 생성                                                                                                                                                                                                                                         |
| security            | 클라이언트가 삼바 서버에 접근할 때 인증 레벨을 부여하는 보안 옵션<br>- user : OS에 로그온한 사용자명으로 패스워드 확인<br>- share : 인증없이 서버 접근 가능 (비사용 권장)<br>- server : 윈도우 서버와 같은 다른 삼바 서버에 사용자명과 패스워드를 전달하여 확인 (비사용 권장)<br>- domain : 윈도우 서버의 도메인 컨트롤러에 사용자명과 패스워드를 전달하여 확인. samba 3.0부터 값을 ads으로 지정하여 Active directory Service를 이용 가능 |
| passdb backend      | security가 user인 경우 사용하는 패스워드 저장 방식<br>기본값 : `passdb backend = tdbsam`                                                                                                                                                                                                                        |
| hide dot files = no | 리눅스의 숨길 파일이 윈도우 OS의 파일 목록에 표시                                                                                                                                                                                                                                                                |
### Share Definition
공유 폴더의 주요 설정 옵션

| 옵션                      | 설명                          |
| :---------------------- | :-------------------------- |
| \[디렉터리명]                | 공유폴더 이름 지정                  |
| comment                 | 폴더에 대한 설명 기술                |
| path                    | 디렉터리의 절대경로                  |
| read only = yes         | 읽기 전용                       |
| writable = yes          | 쓰기 가능                       |
| write list = \[사용자 리스트] | 쓰기 가능한 사용자 지정. @으로 그룹 지정 가능 |
| public = no             | 개인 사용자만 사용 가능               |
| browseable = no         | 이용 가능 공유 리스트에 표시되지 않음       |
| create mask = 값         | 기본 접근 권한 지정                 |
| follow symlinks = no    | 심볼릭 링크를 따르지 않도록 설정          |
| printable = yes         | 삼바 프린터를 네트워크 프린터로 공유        |
### Samba 사용자 등록 및 패스워드 설정
1. 리눅스 계쩡 등록
2. `/etc/samba/smbusers` 설정 파일을 이용하여 리눅스 계정과 삼바 이용자명을 매핑
3. 루트권한으로 [[smbpasswd]] 명령을 이용하여 삼바 계정과 패스워드 설정
4. [[pdbedit]] 명령으로 사용자 목록 및 세부 내용을 확인할 수 있다
## 삼바 서비스 이용



# 2. NFS(Network File System) 서비스
## 개요
### 특징
- TCP/IP를 이용하여 원격 기기의 파일 시스템을 마운트하는 서비스
- RPC를 이용하므로 rpcbind 데몬 필요
### 주요 패키지
- rpcbind : rpcbind 데몬, RPC 서비스 명령어
- nfs-utils : NFS 관련 데몬 및 명령어
## 설치
#### NFS 서버 설정
- 설정 파일 : /etc/exports
- 형식 : `[공유 디렉터리] [접속 허가 호스트](옵션) ...`
	`/home/targetdirectory 192.168.1.1`
- 접속 허가 호스트는 IP 주소, 도메인 이름 등









