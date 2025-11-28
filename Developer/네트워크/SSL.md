---
cssclasses: cornell-note
tags: security, cryptography, ssl, tls, network
---

# Summary

SSL(Secure Sockets Layer)은 인터넷에서 데이터를 안전하게 전송하기 위한 암호화 프로토콜이다.  
현재는 보안이 강화된 TLS로 대체되었지만, 관습적으로 SSL이라는 용어가 계속 사용된다.  
암호화, 인증, 무결성을 제공해 HTTPS의 핵심 기반 기술로 사용된다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>SSL 개요</aside>  

SSL은 Netscape가 개발한 보안 전송 프로토콜로,  
인터넷 상의 데이터를 **암호화(Confidentiality)** 하고  
송신자/수신자를 **인증(Authentication)** 하며  
내용이 변조되지 않도록 **무결성(Integrity)** 을 제공한다.  

현재는 SSL 3.0 이후의 최신 프로토콜인 **TLS(Transport Layer Security)** 가 표준이다.

<aside>SSL/TLS가 해결하는 문제</aside>  

네트워크에서 발생 가능한 다음 문제를 방지한다.  
- 도청(스니핑)  
- 중간자 공격(Man-in-the-Middle)  
- 데이터 변조  
- 서버/클라이언트 위조  

이를 위해 비대칭키, 대칭키, 인증서 기반 구조를 조합해 사용한다.

<aside>핸드셰이크 과정</aside>  

SSL/TLS 연결은 **핸드셰이크(Handshake)** 를 통해 암호 설정과 인증을 수행한다.  

핵심 단계 요약:  
1. ClientHello — 지원 암호 알고리즘 목록 전송  
2. ServerHello — 서버 선택 알고리즘 반환  
3. 서버 인증서(Certificate) 전송  
4. 클라이언트가 공개키 기반으로 Pre-Master Secret 생성  
5. 양측이 대칭키(Session Key)를 생성  
6. 이후 모든 통신은 **대칭키 암호화**로 전송  

핸드셰이크는 비대칭키, 실제 데이터는 빠른 대칭키로 보호한다.

<aside>HTTPS와의 관계</aside>  

HTTPS = HTTP + SSL/TLS  
즉, HTTP 요청/응답을 SSL/TLS로 감싸 암호화한 프로토콜이다.  

이 구조 덕분에  
- 로그인 정보 보호  
- 쿠키 탈취 방지  
- 결제·은행 서비스 보안  
이 가능하다.

<aside>인증서(Certificate)</aside>  

SSL 인증서는 **CA(Certificate Authority)** 가 발급하는 서버/도메인 검증용 문서다.  

핵심 정보:  
- 서버 공개키(Public Key)  
- 도메인 이름  
- CA 서명  
- 유효 기간  

유명 CA: Let's Encrypt, DigiCert, GlobalSign 등  

클라이언트는 인증서의 CA를 신뢰하므로 서버의 신원을 검증할 수 있다.

<aside>암호 알고리즘 구성</aside>  

SSL/TLS는 여러 암호화 요소가 결합된 구조다.  
- **비대칭키:** RSA, ECDHE (키 교환 및 인증)  
- **대칭키:** AES, ChaCha20 (데이터 암호화)  
- **해시:** SHA-2, SHA-3 (무결성 체크)  

최근에는 **ECDHE + AES-GCM** 조합이 가장 일반적이다.

<aside>취약점과 폐지된 SSL 버전</aside>  

SSL 2.0/3.0은 현재 심각한 취약점이 있어 사용이 금지된다.  
대표 공격: POODLE, BEAST, Heartbleed(OpenSSL).  

따라서 현재 표준은 다음과 같다.  
- TLS 1.2 — 가장 널리 사용됨  
- TLS 1.3 — 최신, 핸드셰이크 간소화·보안 강화  

<aside>핵심 정리</aside>  

- SSL은 오늘날 TLS로 대체된 보안 통신 프로토콜  
- 암호화/인증/무결성 제공으로 네트워크 보안을 보장  
- HTTPS의 기반 기술이며 인증서·비대칭키·대칭키 조합 구조  
- TLS 1.3이 최신이며, SSL 자체는 더 이상 사용되지 않는다
