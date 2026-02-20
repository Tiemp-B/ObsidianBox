---
tags:
  - 리눅스
  - DNS
---

# 명령어 역할
네임 서버의 정보를 조회하거나 IP를 통해 도메인명을 질의할 수 있는 명령어
`nslookup [option] hostname|address [dns]`

옵션 없이 입력하는 경우 대화 모드에 진입한다.
# 옵션
- -type=, -q=
	- mx : Mail Record
	- ns : NS 레코드. Namer Server Record
	- cname : CNAME
	- A : A레코드 (IPv4)
	- AAAA : 
# 예제


# 연관 명령어
- [[nslookup]]
- [[dig]]
- [[host]]
- [[hostname]]
- [[hostnamectl]]

