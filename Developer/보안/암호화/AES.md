---
cssclasses: cornell-note
tags:
  - security
  - cryptography
  - aes
  - symmetric-encryption
---

# Summary

AES(Advanced Encryption Standard)는 현대 보안 시스템에서 가장 널리 사용되는 **대칭키 암호화 알고리즘**이다.  
128-bit 블록 기반으로 동작하며 키 길이(128/192/256bit)에 따라 보안 강도가 달라진다.  
빠르고 안전하며 하드웨어 가속 지원 덕분에 HTTPS, VPN, 저장 데이터 암호화 등 거의 모든 보안 환경에서 사용된다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>AES 개요</aside>

AES는 NIST가 2001년 표준으로 채택한 **블록 암호(Block Cipher)** 알고리즘이다.  
Rijndael 알고리즘을 기반으로 하며, 데이터 블록을 128bit 단위로 암호화한다.  
대칭키 방식이므로 암호화와 복호화에 동일한 키를 사용한다.

특징:  
- 빠른 성능  
- 강력한 보안성  
- 하드웨어 가속(AES-NI)  
- 다양한 암호 모드 지원 (CBC, GCM 등)

<aside>키 길이와 라운드 수</aside>

AES는 키 길이에 따라 라운드 수가 달라진다.

| 키 길이   | 라운드 수 |
| ------ | ----- |
| 128bit | 10    |
| 192bit | 12    |
| 256bit | 14    |

키가 길수록 보안성이 높지만 연산량도 증가한다.

<aside>암호화 구조</aside>

AES는 다음과 같은 과정을 반복해 암호화한다.

- SubBytes (바이트 단위 S-box 치환)  
- ShiftRows (행 단위 바이트 시프트)  
- MixColumns (열 단위 선형 변환)  
- AddRoundKey (라운드 키 XOR)

마지막 라운드는 MixColumns를 포함하지 않는다.  
이 구조는 치환과 전치 기반의 강한 혼돈·확산을 제공한다.

<aside>암호 모드 (Modes of Operation)</aside>

AES는 블록 단위 암호화이므로 운영 모드를 통해 동작 방식을 결정한다.

- **CBC (Cipher Block Chaining)**: 보안적이지만 느림  
- **CTR (Counter Mode)**: 병렬 처리 가능, 빠름  
- **GCM (Galois/Counter Mode)**: 인증 + 암호화(AEAD), HTTPS 기본  
- **ECB (Electronic Codebook)**: 패턴 노출로 인해 보안상 금지  

현대 보안 시스템에서는 대부분 **AES-GCM** 또는 **AES-CTR**을 사용한다.

<aside>보안성</aside>

AES는 현재 알려진 실질적인 공격이 없으며,  
표준 키 길이(128/192/256bit) 모두 안전하다고 평가된다.

- 128bit: 일반 산업 및 웹 서비스에서 기본  
- 256bit: 군사 등 고보안 환경  
- 하드웨어 가속(AES-NI, ARM Cryptography Extensions)로 매우 빠름  

양자컴퓨터 환경에서도 그로버 알고리즘으로 키 길이의 절반 수준만 줄어드는 정도이므로  
AES-256은 장기적으로도 안전하다고 평가된다.

<aside>사용 사례</aside>

- HTTPS/TLS 데이터 암호화  
- VPN(IPsec, OpenVPN, WireGuard)  
- 디스크 암호화(LUKS, BitLocker, FileVault)  
- 무선 통신(WPA2/WPA3)  
- 모바일/임베디드 보안  
- 암호화된 API/앱 데이터 저장  

대칭키 암호의 산업 표준으로 거의 모든 보안 기술의 핵심 구성 요소다.

<aside>핵심 정리</aside>

- AES는 가장 널리 사용되는 대칭키 블록 암호  
- 빠르고 안전하며 하드웨어 가속 지원  
- GCM, CTR 등 운영 모드에 따라 성능·보안 특성이 결정  
- HTTPS, VPN, 저장 데이터 암호화 등 다양한 환경에서 필수적으로 사용된다
