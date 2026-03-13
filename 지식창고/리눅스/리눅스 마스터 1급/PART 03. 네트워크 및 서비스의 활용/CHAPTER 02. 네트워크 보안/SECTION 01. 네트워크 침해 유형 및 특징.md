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
- 주소 등의 정보를 변조하여 공격의 탐




























