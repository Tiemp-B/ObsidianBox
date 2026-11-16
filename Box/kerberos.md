---
cssclasses: cornell-note
tags:
  - security
  - authentication
  - kerberos
  - network
  - cryptography
---

# Summary

Kerberos는 신뢰된 제3자(Key Distribution Center, KDC)를 기반으로 하는 **네트워크 인증 프로토콜**이다.  
패스워드를 네트워크로 직접 전송하지 않고, **티켓(ticket)과 대칭키 암호화**를 이용해  
사용자와 서비스 간의 상호 인증을 제공한다.  
대규모 조직 환경(기업, 대학, 클라우드, Active Directory)의 표준 인증 방식으로 사용된다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Kerberos 개요</aside>

Kerberos는 MIT에서 개발한 네트워크 인증 프로토콜로,  
불안전한 네트워크 환경에서도 **안전한 사용자 인증**을 제공하는 것을 목표로 한다.  

핵심 특징:  
- 패스워드 평문 전송 없음  
- 대칭키 암호 기반  
- 중앙 집중형 인증 서버(KDC)  
- Single Sign-On(SSO) 지원  

<aside>등장 배경</aside>

초기 네트워크 환경에서는  
- 패스워드 스니핑  
- 재전송 공격(Replay Attack)  
- 서버 위조  

문제가 심각했다.  
Kerberos는 이를 해결하기 위해 **티켓 기반 인증 구조**를 도입했다.

<aside>구성 요소</aside>

Kerberos는 다음 세 가지 핵심 요소로 구성된다.

- **Client**: 인증을 요청하는 사용자  
- **Service Server**: 실제 서비스 제공 서버  
- **KDC(Key Distribution Center)**  
  - AS(Authentication Server)  
  - TGS(Ticket Granting Server)  

KDC는 신뢰의 중심 역할을 수행한다.

<aside>티켓 개념</aside>

Kerberos 인증은 티켓(ticket)을 중심으로 동작한다.

- **TGT(Ticket Granting Ticket)**  
  - 사용자 인증 후 발급  
  - 이후 서비스 요청에 사용  

- **Service Ticket**  
  - 특정 서비스 접근 권한 증명  

티켓은 **유효 시간**을 가지며 재사용 공격을 방지한다.

<aside>인증 절차 흐름</aside>

1. 사용자가 AS에 인증 요청  
2. AS가 사용자 검증 후 **TGT 발급**  
3. 사용자가 TGS에 서비스 요청 + TGT 제출  
4. TGS가 **Service Ticket 발급**  
5. 사용자가 서비스 서버에 티켓 제출  
6. 상호 인증 후 서비스 이용  

이 과정에서 패스워드는 네트워크에 노출되지 않는다.

<aside>암호화 방식</aside>

Kerberos는 **대칭키 암호화**를 사용한다.

- 사용자 ↔ KDC: 사용자 비밀키(패스워드 기반)  
- KDC ↔ 서비스: 서비스 비밀키  
- 세션 키(Session Key)로 통신 보호  

공개키 기반 구조(PKI)는 Kerberos v5 이후 선택적으로 확장 가능하다.

<aside>시간 동기화의 중요성</aside>

Kerberos는 **시간 기반 유효성 검증**을 사용한다.

- 티켓에 타임스탬프 포함  
- 클라이언트와 서버 간 시간 오차 허용 범위 제한  

따라서 **NTP 기반 시간 동기화**가 필수다.

<aside>장점</aside>

- 패스워드 노출 방지  
- 재전송 공격 방어  
- 중앙 집중형 인증 관리  
- SSO 구현 가능  
- 대규모 조직에 적합  

<aside>한계와 주의점</aside>

- KDC 장애 시 전체 인증 불가(SPOF)  
- 시간 동기화 필수  
- 초기 설정 및 운영 복잡  
- 클라우드·인터넷 환경에서는 추가 구성 필요  

<aside>주요 활용 사례</aside>

- **Microsoft Active Directory**  
- 기업 내부 SSO 시스템  
- Hadoop, Spark 클러스터 인증  
- 대학교·연구기관 인증 시스템  
- 내부 마이크로서비스 인증  

<aside>핵심 정리</aside>

- Kerberos는 티켓 기반 네트워크 인증 프로토콜  
- KDC 중심의 대칭키 암호 구조  
- 패스워드 평문 전송 없이 안전한 인증 제공  
- 대규모 조직과 SSO 환경의 사실상 표준 인증 방식
