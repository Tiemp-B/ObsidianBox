```table-of-contents
```
# 1. 보안 솔루션을 이용한 대비 및 대처
## 방화벽
### 개념과 기능
- 외부의 악의적 트래픽 방어
- 내->외, 외->내 모두 통제 가능
- 기능
    - 접근제어
    - 로깅 및 감사 추적
    - 사용자 및 호스트 인증
    - 등
### 종류
- 스크리닝(screening) 라우터
    - 방화벽 기능이 있는 라우터로 내외부 연결 연결
    - 장점 : 필터링 속도 빠름, 네트워크 전체 방어 가능
    - 단점 : 패킷 필터링 규칙 구성, 검증 및 로그 관리 어려움
- 베스천 호스트(Bastion Host)
    -  방화벽 기능을 탑재한 호스트로 내외부 연결
    - 장점 : 호스트 기반의 SW로 지능적 정보 분석
    - 단점 : Bastion Host 자체 보안 취약점 존재 가능
- 듀얼홈(Dual-Homed) 게이트웨이
    - 2개의 네트워크 카드를 내장한 Bastion으로 내외부 연결
    - 장점 : 네트워크가 분리되어 내부 IP 노출 방지
    - 단점 : Bastion Host 자체 보안 취약점 존재 가능
- 스크린드 호스트 게이트웨이
    - 듀얼홈과 스크리닝을 혼합
    - 장점 : 네트워크 계층과 응용 계층에 걸친 방어
    - 단점 : 높은 구축 비용과 스크리닝 라우터의 ARP 스푸핑에 취약
- 스크린드 서브넷 게이트웨이
    - 스크리닝 라우터를 듀얼홈을 중심으로 양쪽 연결
    - Bastion Host는 프록시 서버로 명확하게 허용되지 않은 모든 트래픽 거부
    - 장점 : 다단계 방어 구조
    - 단점 : 높은 구축 및 응답성 저하
## 침입 탐지 시스템 (IDS ; Intrusion Detection System)
## IDS 개념
- 네트워크 및 서비스에 대한 공격을 실시간 탐지
### 주요 기능
- 데이터 수집
- 정보 분석
- 침입 탐지
- 추적 및 보고
### 유형
1. 데이터 소스 기준
    - HIDS : 호스트 기반
        - 서버에 직접 설치되어 탐지 수행
    - NIDS : 네트워크 기반
        - 네트워크 세그먼트별 탐지 장비 설치
2. 침입 탐지 방식 기준
    - 오용 탐지
        - 알려진 공격 패턴 등록 후 비교
        - 오탐율 낮음
        - 새로운 공격에 취약
    - 이상 탐지
        - 정상적인 패턴 대비 이상 패턴인 경우 공격으로 판단
        - AI등의 방식으로 새로운 공격 패턴에 대응
        - 오탐율이 존재함
## 침입 방지 시스템 (IPS ; Intrusion Prevention System)
### IPS 개념
- IDS의 수동적 방어 시스템을 발전시켜 능동적 방어 및 차단 등의 사전 대응을 중심
- IPS는 침입 경고 이전에 공격을 차단하는 것이 목적


# 2. Snort를 이용한 대비 및 대처
## snort의 개요
### 특징
- 리눅스에서 사용 가능한 공개형 IDS 프로그램
- 구성
    - 스니퍼
    - 프리 프로세서
    - 탐지 엔진
    - 로깅
### 주요 기능
탐지 룰을 이용하여 네트워크 트래픽 분석 및 침입 탐지
- 패킷 스니퍼
- 패킷 로거
- 네트워크 IDS
## snort의 Rule 설정
### Rule 구조
`액션 프로토콜 소스IP 소스포트 방향 목표IP 목표포트 (msg:""; content:"")`
- 헤더
    - action
    - protocol
    - source
    - direction
    - destination
- 룰 옵션 분류
    - General
    - Payload
    - non-payload
    - post-detection
- 룰 옵션 주요 항목
    - msg
    - sid
    - content
    - depth
    - offset
    - distance
    - within
    - nocase
    - sameip

# iptables를 이용한 대비 및 대처
## iptables의 개요
### 특징
- 리눅스 방화벽
- 패킷 필터링 정책으로 특정 패킷을 분석하고 허용/차단
- NAT(Network Address Translation : IP주소를 변환해 라우팅을 원할하게 함)에도 사용 가능
- 커널의 넷필터 모듈로 네트워크 패킷 필터링
- 최근은 firewalld를 기본 방화벽으로 하나 iptables로 상세하고 명확한 규칙 설정이 가능하다
### 패킷 흐름

![[Pasted image 20260313192526.png]]

## 구조
### 종류
- filter : 기본 테이블. 패킷 필터링 기능
- nat : NAT: IP주소 및 포트 변환 관리
- mangle : 성능 향상을 위한 TOS(Type Of Service) 설정과 같이 패킷 데이터 변경하는 특수 규칙
- raw : 연결 추적을 위한 세부 기능
- security : SELinux에서 사용하는 접근 제어 규칙 적용
### filter 테이블

| 체인      | 적용 시점      | 설정                 |
| :------ | ---------- | ------------------ |
| INPUT   | 외부->로컬     | 들어오는 패킷을 필터링       |
| OUTPUT  | 로컬->외부     | 나가는 패킷 필터링         |
| FORWARD | 외부->외부(경유) | 현 시스템을 경유하는 패킷 필터링 |
- 값
    - ACCEPT
    - DROP
    - REJECT
### nat 테이블

| 체인          | 적용 시점         | 설정                 |
| :---------- | ------------- | ------------------ |
| PREROUTING  | 라우팅 결정 이전     | 들어오는 패킷의 목적지 주소 변환 |
| POSTROUTING | 라우팅 결정 이후     | 나가는 패킷의 출발지 주소 변환  |
| OUTPUT      | 로컬 프로세스 발생 패킷 | 로컬에서 생성된 패킷의 주소 변환 |

### mangle 테이블
패킷의 헤더 값을 변조하는 테이블. 주소가 아닌 패킷 속성 수정

| 체인          | 적용 시점          | 설정             |
| :---------- | -------------- | -------------- |
| PREROUTING  | 라우팅 결정 이전      | 들어오는 패킷 변조     |
| POSTROUTING | 라우팅 결정 이후      | 나가는 패킷 변조      |
| INPUT       | 라우팅 후 로컬 전달 이전 | 로컬로 들어오는 패킷 변조 |
| OUTPUT      | 로컬 프로세스 발생 직후  | 로컬에서 나가는 패킷 변조 |
| FORWARD     | 라우팅 후 전달 중     | 경유 패킷 변조       |

## iptable 사용
`iptables [-t 테이블명] [action] [체인 이름] [match 규칙] [-j 타깃]` 형식
- -t 테이블 : filter, nat, mangle, raw 테이블 지정 가능. 생략시 filter
- action : 체인을 대상으로 수행할 명령 지정
    체인을 대상 action
    - -N, --new-chain : 새 정책
    - -X, --delete-chain : 비어 있는 정책 체인 제거
    - -L, --list : 현재 정책 체인 목록 표시
    - -F, --flush : 지정 체인에 설정된 모든 정책 삭제
    - -C : 패킷 테스트
    - -P, --policy : 체인의 기본 정책 설정
    - -Z, --zero : 체인 내의 모든 규칙의 패킷과 바이트 카운트를 0으로 설정
    체인 내부를 대상 action
    - -A, --append : 새로운 정책을 가장 마지막에 추가
    - -I \[체인] \[라인번호], --insert : 지정 체인의 지정 라인번호에 추가
    - -D \[체인] \[라인번호], --delete : 지정 체인의 지정 라인의 정책 제거
    - -R \[체인] \[라인번호], --replace : 정책 수정
- match : 
    - -s, --source : 출발지 IP, 도메인 설정
    - -d, --destination : 목적지 IP, 도메인 설정
    - ! : 뒤에 따라오는 규칙 제외
    - -p, --protocol : 프로토콜 설정
    - -i, --in-interface : 입력 네트워크 인터페이스
    - -o, --out-interface : 출력 네트워크 인터페이스
    - --sport : 소스 포트 지정. ':'로 범위 지정 가능
    - --dport : 타깃 포트 지정. ':'로 범위 지정 가능
    - --tcp-flags : SYN, ACK, FIN, RST, URG, PSH, ALL, NOTE 등의  TCP flag 지정
    - --syn : TCP flag로 SYN만 가진 것을 지정
    - --icmp-type : ICMP 타입지정
    - -m, --match : 특정 모듈/규칙과 매치
    - --state 
    - --string
- 기타 옵션
    - -n, --numeric
    - -v, --verbose
    - --line-numbers
- -j 타깃
    - ACCEPT
    - REJECT
    - DROP
    - LOG
    - RETURN

### 예제
- `iptables -A INPUT -s 192.168.10.7 -d localhost -j DROP`
- `iptables -A INPUT -p tcp -dport 10:100 -j DROP`
## 설정 정책 저장과 자동 적용
iptables로 설정한 정보는 리부팅 시 제거되기에 파일로 저장하고 부팅 시 재설정해야 한다
- `iptables-save > 세이브파일.sh`
- `iptables-restore < 세이브파일.sh`
- `service iptables save` 정책을 `/etc/sysconfig/iptables`에 저장되며 자동으로 적용된다.

## iptables를 이용한 NAT 구성
### NAT 개념
- 네트워크 주소를 변환하는 기능 수행
- 하나의 공인 IP를 다수의 호스트가 공유 가능

