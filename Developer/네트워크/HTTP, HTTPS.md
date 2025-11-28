---
cssclasses: cornell-note
tags:
  - http
  - https
  - web
  - networking
  - security
---

# Summary

HTTP는 웹에서 클라이언트와 서버 간 데이터를 주고받는 비연결·비암호화 프로토콜이다.  
HTTPS는 HTTP에 SSL/TLS 암호화를 추가하여 보안성을 확보한 프로토콜로,  
기밀성·무결성·인증을 제공해 현대 웹 통신의 표준으로 자리 잡았다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>HTTP 개요</aside>

HTTP(HyperText Transfer Protocol)는  
웹 브라우저와 서버 간 데이터를 주고받기 위한 애플리케이션 계층 프로토콜이다.

특징:  
- **비연결(Connectionless)**  
- **무상태(Stateless)**  
- 텍스트 기반 요청/응답  
- 기본 포트 **80**

요청 형태: GET, POST, PUT, DELETE, HEAD 등  
응답은 상태 코드: 200, 301, 404, 500 등으로 구성된다.

<aside>HTTP의 한계</aside>

HTTP는 암호화되지 않은 평문 전송이기 때문에  
다음 위험을 가진다:

- 패킷 도청 (Sniffing)  
- 중간자 공격(Man-in-the-Middle)  
- 데이터 변조  
- 클라이언트/서버 위조 가능  

이 문제를 해결하기 위해 HTTPS가 도입되었다.

<aside>HTTPS 개요</aside>

HTTPS(HyperText Transfer Protocol Secure)는  
HTTP 위에 **[[SSL]]/[[TLS]] 암호화 계층을 덧씌운 프로토콜**이다.

특징:  
- 암호화(Confidentiality)  
- 무결성(Integrity)  
- 서버 인증(Authentication)  
- 기본 포트 **443**

일반적인 HTTPS 요청 경로:  
브라우저 → TLS 핸드셰이크 → 암호화 채널 생성 → 암호화된 HTTP 데이터 전송

<aside>SSL/TLS의 역할</aside>

HTTPS에서 TLS는 다음을 제공한다:

- RSA/ECDHE 기반 키 교환  
- AES/ChaCha20 기반 대칭키 암호화  
- SHA-2 기반 무결성 검증  
- 디지털 인증서 기반 서버 신원 확인  

핵심: **HTTP 자체는 동일하고, 전송만 암호화된다.**

<aside>HTTP vs HTTPS 비교</aside>

| 구분 | HTTP | HTTPS |
|------|-------|--------|
| 암호화 | 없음 | TLS로 암호화 |
| 안전성 | 낮음 | 높음 |
| 인증서 | 불필요 | 필요 (CA 발급) |
| 포트 | 80 | 443 |
| 사용 분야 | 내부망, 테스트 | 웹 서비스 전반 |
| SEO | 낮음 | 우대 (Google) |

현대 웹에서는 HTTPS가 사실상 필수다.

<aside>HTTPS 인증서</aside>

HTTPS는 **CA(Certificate Authority)** 가 발급한 인증서를 사용한다.  
인증서에는 다음 정보가 포함된다:

- 도메인  
- 서버 공개키  
- CA의 디지털 서명  
- 유효 기간  

대표 CA: Let's Encrypt, DigiCert, GlobalSign 등

브라우저는 인증서를 검증해 서버가 진짜인지 확인한다.

<aside>HTTP/2와 HTTP/3</aside>

- **HTTP/2**: 멀티플렉싱, 헤더 압축  
- **HTTP/3**: QUIC 기반, 지연 시간 감소 및 성능 향상  
- HTTP/2/3는 사실상 **HTTPS 기반으로만 동작**  

<aside>사용 사례</aside>

- 웹 서비스(로그인/결제)  
- 모바일 앱 API  
- IoT 기기 통신  
- 클라우드 플랫폼(K8s, AWS, GCP)  

HTTPS는 모든 민감 데이터 전송의 기본 프로토콜이다.

<aside>핵심 정리</aside>

- HTTP는 기본 웹 프로토콜, HTTPS는 보안 강화 버전  
- HTTPS는 TLS 기반 암호화·무결성·인증 제공  
- 대부분의 웹 서비스가 HTTPS를 표준으로 사용  
- 인증서, 키 교환, 암호 모드 등 TLS 구조가 핵심 기반
