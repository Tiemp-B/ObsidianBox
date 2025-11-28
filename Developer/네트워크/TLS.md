---
cssclasses: cornell-note
tags: security, tls, cryptography, network
---

# Summary

TLS(Transport Layer Security)는 인터넷 통신을 보호하는 표준 보안 프로토콜로,  
SSL의 후속 버전으로 발전하여 현재 HTTPS와 대부분의 보안 통신에서 사용된다.  
대칭키·비대칭키·해시를 결합해 암호화·인증·무결성을 제공하며 TLS 1.3은 더 빠르고 안전한 최신 규격이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>TLS 개요</aside>

TLS는 안전한 네트워크 전송을 위한 표준 프로토콜로,  
이전 버전인 SSL의 취약점을 개선하여 설계되었다.  
주요 목적은  
- 데이터 암호화  
- 서버/클라이언트 인증  
- 메시지 무결성 확보  
을 통해 안전한 네트워크 통신을 보장하는 것이다.

현재 실제 서비스에서는 **SSL 대신 TLS를 사용**하며,  
일반적으로 HTTPS는 TLS 기반 보안 통신을 의미한다.

<aside>TLS의 동작 방식</aside>

TLS 통신은 크게 두 단계로 이루어진다.  
1. **Handshake(핸드셰이크)**: 인증과 대칭키 생성  
2. **Record Layer**: 생성된 세션 키로 암호화된 데이터 송수신  

핸드셰이크는 비대칭키 기반(ECDHE/RSA 등), 본 통신은 대칭키 기반(AES/ChaCha20)으로 진행하여  
보안성과 속도를 동시에 확보한다.

<aside>TLS 핸드셰이크 흐름</aside>

- 클라이언트가 지원 가능한 암호 알고리즘 목록 전송  
- 서버가 사용할 알고리즘 선택  
- 서버 인증서 제공  
- 키 교환(ECDHE 등)으로 세션 키 생성  
- 암호화된 채널 생성 후 데이터 송수신  

핵심은 **보안 연결 설정 후 모든 데이터는 대칭키로 암호화**된다는 점이다.

<aside>TLS 1.2 vs TLS 1.3</aside>

TLS 1.3은 최신 규격으로, 다음과 같은 개선점이 있다.  

- 핸드셰이크 단계 축소 → 속도 향상(1RTT)  
- 취약한 알고리즘 제거(RSA 키 교환, SHA-1 등)  
- Forward Secrecy 의무화(ECDHE 기반)  
- 단순하고 강력한 암호 스위트만 허용(AES-GCM, ChaCha20-Poly1305)  

대부분의 현대 브라우저와 서버는 TLS 1.3을 기본 사용한다.

<aside>암호 구성 요소</aside>

TLS는 다양한 암호 기술을 조합해 구성된다.  
- **비대칭키**(RSA, ECDSA, ECDHE): 인증·키 교환  
- **대칭키**(AES-GCM, ChaCha20): 실제 데이터 암호화  
- **해시/무결성**(SHA-2, SHA-3): 메시지 변조 방지  
이 조합으로 성능·보안·정확성을 모두 보장한다.

<aside>인증서와 인증 체계</aside>

TLS 인증은 **CA(Certificate Authority)** 를 통한 인증서를 기반으로 한다.  
인증서는 서버의 공개키와 도메인 정보를 포함하며,  
클라이언트는 CA의 서명 검증을 통해 서버 신뢰성을 판단한다.  
Let's Encrypt 등 무료 CA도 널리 사용된다.

<aside>사용 사례</aside>

- HTTPS 웹사이트  
- VPN, SSH 기반 터널링  
- 클라우드 서비스(Kubernetes API, gRPC)  
- 이메일(SMTPS, IMAPS)  
- IoT 기기 통신  

TLS는 인터넷 전반의 기본 보안 계층으로 자리잡고 있다.

<aside>핵심 정리</aside>

- TLS는 SSL의 후속이며 현대 보안 통신의 표준  
- 비대칭키로 키 교환, 대칭키로 실제 암호화 수행  
- TLS 1.3은 속도·보안 모두 강화된 최신 버전  
- HTTPS, VPN, 클라우드 네트워크 등 거의 모든 보안 통신에 사용된다
