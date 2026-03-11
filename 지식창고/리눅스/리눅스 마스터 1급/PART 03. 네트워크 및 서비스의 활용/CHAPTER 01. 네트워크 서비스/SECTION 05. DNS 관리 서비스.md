```table-of-contents
```
# 1. DNS(Domain Name System)의 개요
## DNS의 개념
- 도메인 이름과 IP 주소를 상호 변환하는 서비스
### 동작
- DNS 서버는 클라이언트 요청에 따라 도메인명 <-> IP 주소를 변환한다
- TCP/53, UDP/53 포트 
1. 클라이언트에서 주소 입력 시 **Local DNS**에 질의
2. Local DNS는 현 DNS에 없는 경우 **Root DNS**에 질의
3. Root DNS에도 없는 경우 다른 DNS(**com DNS**)에 질의
4. com DNS에도 없는 경우 다른 DNS 서버의 주소를 받아 재질의
5. IP 주소 수신 시 Caching하고 클라이언트에 전달 
### 종류
- Primary Name Server : Master Server라고도 하며, 필수 항목
- Secondary Name Server : Slave DNS라고도 하며 Primary의 zone 파일 백업한다.
- Caching Name Server : 도메인 관리 없이 리졸빙 역할만 수행
	리졸빙 결과를 저장하고 해당 요청이 있을시 바로 응답하여 속도 향상

# 2. DNS 서비스 사용
## 구성
### 서비스 데몬
- named
### 패키지
- bind
- bind-libs
- bind-utils
### 관련 파일
기본
- /etc/named.conf : 파일
	- zone 파일, reverse zone 파일을 비롯한 주요 환경 설정 파일
	- zone 파일은 도메인명과 IP 주소 혹은 관련 리소스간 매핑을 포함
	- 리버스 존 파일을 이요하여 IP 주소에 대한 도메인 정보 조회 제공
- /var/named : 디렉터리
	- root 도메인 서버의 정보를 담은 named.ca, 사용자가 설정한 zone 파일 등을 저장하는 디렉터리
`bind-chroot`로 보안 강화
- /etc/named.conf -> /var/named/chroot/etc/named.conf
- /var/named -> /var/named/chroot/var/named
## 설정 파일 내용
구문 종류
- options
- logging
- acl
- zone
```bash
options {
	listen-on port 53 { 127.0.0.1; };
	listen-on-v6 port 53 {::;};
};
```
와 같은 형식을 지닌다.
### options 구문 주요 설정 항목
- directory
- dump-file
- statistics-file
- recursing-file
- forward
- forwarders
- allow-query
- allow-transfer
- datasize
- recursion
### logging 구문
bind 네임 서버의 로깅 방식 설정
```bash
logging {
	channel default_debug{
		file "data/named.run";
		severity dynamic;
	};
};
```
### acl 구문
Access Control List. 여러 호스트들을 하나의 이름으로 지정하여 options 구문에 적용
따라서 options의 설정이 선행되야 한다
```bash
acl "ihd" { 192.168.2.24; 192.168.4,4/24; };
```
### 











