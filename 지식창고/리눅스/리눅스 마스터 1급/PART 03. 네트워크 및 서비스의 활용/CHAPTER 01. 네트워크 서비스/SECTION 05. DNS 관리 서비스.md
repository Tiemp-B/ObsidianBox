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
- 















