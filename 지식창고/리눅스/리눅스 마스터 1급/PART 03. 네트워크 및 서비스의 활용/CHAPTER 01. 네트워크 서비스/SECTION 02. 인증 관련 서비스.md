```table-of-contents
```
# 1. 개요
## 리눅스 인증의 개요
### 인증과 인가
- 인증 : 시스템을 사용하는 클라이언트가 등록된 사용자인지 확인
- 인가 : 인가된 크라이언트에게 권한을 부여. 권한에 따라 사용 가능한 서비스, 자원이 달라진다
### 네트워크 기반 인증 서비스의 필요성
- 다수의 시스템을 운영할 경우 사용자 등록, 패스워드 관리 등의 어려움 발생
	-> 네트워크 기반 인증서비스가 필요
- 네트워크 기반 인증 서비스 : 인증에 필요한 정보를 인증 서버에 등록한 후, 필요한 시스템에 인증 관련 정보 제공
- 예 : NIS(Network Information Service), LDAP(Lightweight Directory Access Protocl) 등

## NIS(Network Information Service)
- Sun 사가 개발
- 호스트명, 사용자명, 사용자 암호 등의 시스템 정보의 검색, 관리.
- RPC(Remote Procedure Call)를 사용
- NIS 서버에 등록된 사용자 계정, 암호, 그룹 정보 등을 네트워크를 이용하여 다른 시스템에 제공
- telnet, samba, ssh 등의 서비스에서 사용 가능
- 발전된 형태인 NIS+는 RPC에서 데이터 암호화와 인증을 지원하고, 권한 설정/복제













