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


















