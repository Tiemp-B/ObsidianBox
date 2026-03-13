```table-of-contents
```
# 1. 네트워크 침해 유형 및 특징
## 스니핑
### 개념
- 한 서브 네트워크 내에서 전송되는 패킷의 내용을 임의로 확인하는 기법
### 네트워크 무차별 모드와 TCP Dump
- 네트워크 설정을 **무차별 모드**로 변경한 후 **TCP Dump**를 이용하면 네트워크 내 모든 패킷 확인 가능
- 무차별 모드 설정: `ifconfig [Network Interface Name] promisc`
- 일반 모드 설정: `ifconfig [네트워크 인터페이스 이름] -promisc`
- TCP Dump 명령어 : [[tcpdump]]
### 대응 방법
- 암호화 통신 방식(ex. SSL:SSecure Socket Layer) 이용
## 스푸핑
### 개념
- 서비스 혹은 패킷 정보를 임의로 변경하여 공격
- 주소 등의 정보를 변조하여 공격의 탐지 및 역추적이 난해
### 기법
1. IP Spoofing
    - 공격자가 자신의 IP를 변조하여 IP 기반 인증 등의 서비스 무력화
    - 대응 방안 : IP 인증 최소화 및 TCP sequence 번호(패킷의 순서와 신뢰성을 위한 32비트 고유 번호)를 무작위로 구성
2. ARP Spoofing
    - IP 와 MAC의 매핑 정보를 네트워크에 브로드캐스트하여 대상 호스트들의 ARP 테이블이 악의적인 정보로 변조
    - 대응 방안 : `arp -s [IP] [MAC]`로 정적 aRP 매핑 정보 등록
3. DNS Spoofing
    - DNS 요청에 위조 정보를 응답
    - 변조된 악의적 서비스로 접근 유도
## DoS/DDoS
### DoS의 개념
- Denial of Service
- 공격 대상의 취약점을 공격하여 과도한 부하 발생시키는 가용성 침해 공격
### DoS 유형
1. 파괴 공격
    - 한계 초과로 장치 파괴를 목적
2. 시스템 자원 고갈 공격
    - 반복 처리로 CPU, 메모리 등의 자원 고갈 목적
3. 네트워크 자원 고갈 공격
    - 과도한 패킷 유발로 대역폭 고갈 목적
### DoS 세부 기법
1. Ping of Death
    - ICMP Echo 패킷을 매우 크게 전송하여 문제 유발
2. Teardrop Attack
    - IP fragmentation에 따라 패킷 재조립시 오프셋을 임의 변조하여 문제 유발
3. TCP SYN Flooding
    - TCP 3-way handshaking 연결 방식에서 SYN flag를 대량으로 발송하며 TCP 연결 처리를 지속적으로 발생하도록 하여 문제 유발 
4. UDP Flooding
    - 대량의 UDP 패킷을 전송하여 공격 대상의 자원 소모
    - 공격 시 발신자의 IP가 변조(spoofing)되므로 응답 메시지는 공격자에게 가지 않음
5. Land Attack
    - 공격 대상에 IP 패킷을 보낼 때 `발신자 IP, 수신자 IP를 모두 공격 대상의 IP`로 하여문제 유발
6. Smurf Attack
    - 공격 대상의 IP 주소를 발신자로 브로드캐스트를 통해 다수의 시스템에 ICMP Request 패킷을 전송
    - 수신자들은 공격 대상의 IP로 응답 패킷을 보내게 되어 부하 유발
7. Mail Bomb
    - 동일한 이메일 주소를 대상으로 대량의 메일 동시 발송
    - 네트워크 자원과 디스크 자원 동시 공격
8. NTP 증폭 공격
    - monlist 요청 방식을 악용한 DDoS
    - 공격자의 적은 패킷이 증폭되어 공격 대상에게 전송

### DDoS


























