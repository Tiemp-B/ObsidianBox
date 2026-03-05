---
cssclasses: cornell-note
tags:
  - 네트워크
  - 프로토콜
---
# Summary

SMB(Server Message Block)는 네트워크 상에서 파일, 프린터, 직렬 포트 등의 자원을 공유하기 위한 클라이언트-서버 기반의 애플리케이션 계층 프로토콜이다. 1983년 IBM이 설계하고 Microsoft가 발전시켜 Windows 네트워크의 핵심 프로토콜로 자리잡았다. 버전이 거듭될수록 성능과 보안이 크게 향상되었으나, 구버전(SMB 1.0)의 심각한 취약점으로 인해 WannaCry, NotPetya 등 대규모 랜섬웨어 공격의 경로가 된 바 있다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>정의 및 기원</aside>

SMB(Server Message Block)는 네트워크를 통해 파일, 프린터, 직렬 포트 등 시스템 자원에 대한 공유 접근을 제공하는 **클라이언트-서버 통신 프로토콜**이다.

- **1983년** Barry A. Feigenbaum이 IBM에서 DOS의 로컬 파일 접근을 네트워크 파일 시스템으로 전환하기 위해 설계
- **1987년** Microsoft와 3Com이 OS/2용 LAN Manager에 SMB를 구현
- **1990년** Microsoft가 LAN Manager 제품에 SMB를 통합하며 본격적으로 발전
- **1992년** Samba 출시 - UNIX 시스템을 위한 오픈소스 SMB 서버

---

<aside>동작 방식</aside>

SMB는 **요청-응답(Request-Response)** 방식으로 동작한다.

1. 클라이언트가 서버에 SMB 연결 요청 전송
2. 서버가 응답하여 통신 채널 수립
3. 클라이언트와 서버가 지원 가능한 **최상위 SMB 버전을 협상(Negotiate)**
4. 인증 완료 후 공유 자원(파일, 프린터 등)에 접근

> 두 Windows 10 PC 간에는 SMB 3.1.1로 통신하고, Windows 8 ↔ Windows 10 간에는 SMB 3.0으로 통신하는 방식으로 자동 협상된다.

---

<aside>포트 정보</aside>

|포트|프로토콜|용도|
|---|---|---|
|**445** (TCP)|SMB Direct|Windows 2000 이후 기본 SMB 포트|
|**139** (TCP)|NetBIOS over TCP/IP|구형 SMB 세션 서비스|
|137 (UDP)|NetBIOS|이름 서비스|
|138 (UDP)|NetBIOS|데이터그램 서비스|

---

<aside>버전 역사</aside>

|버전|출시|주요 특징|
|---|---|---|
|**SMB 1.0**|1983 (IBM)|NetBIOS 기반, 블록 크기 64KB 제한, OpLock 도입|
|**CIFS**|1996|SMB 1.0 방언, Windows 95에 탑재, 대용량 파일·하드링크 지원|
|**SMB 2.0**|2006 (Vista)|명령어 수 수백 개 → 19개로 축소, WAN 지원, 파이프라이닝 도입|
|**SMB 2.1**|2010 (Win7)|OpLock → Lease 모델 교체, 캐싱 성능 향상|
|**SMB 3.0**|2012 (Win8)|암호화, Multichannel, SMB Direct(RDMA), Transparent Failover 도입|
|**SMB 3.1.1**|2015 (Win10)|사전 인증 무결성, 연결별 암호화 알고리즘 협상 지원|
|**SMB over QUIC**|2022 (WinServer 2022)|TCP 대신 QUIC 프로토콜 위에서 동작, VPN 없는 안전한 원격 접근|

---

<aside>SMB vs CIFS 구분</aside>

두 용어는 혼용되는 경우가 많지만 의미가 다르다.

- **CIFS**는 SMB의 방언(Dialect) 중 하나로, 정확히는 **SMB 1.0**을 지칭
- CIFS는 느리고 보안이 취약하며 네트워크 대역폭을 과도하게 사용("Chatty Protocol")
- 현대 시스템에서는 **CIFS 사용을 지양**하고 SMB 2.0 이상을 사용해야 함

---

<aside>보안 취약점 — EternalBlue & WannaCry</aside>

SMB 1.0의 가장 심각한 보안 사례:

- **EternalBlue (CVE-2017-0144)**: NSA가 개발한 SMBv1 원격 코드 실행 취약점으로, Shadow Brokers에 의해 2017년 유출
- **WannaCry (2017.05.12)**: EternalBlue를 이용해 포트 445로 전파된 랜섬웨어. 150개국 이상 감염
- **NotPetya (2017.06.27)**: 동일한 취약점을 이용, 65개국 이상에서 **10억 달러 이상의 피해** 발생
- 2022년 기준, 포트 445에 대한 공격의 **91.88%**가 여전히 EternalBlue 익스플로잇 시도

---

<aside>보안 권고사항</aside>

- **SMB 1.0 비활성화**: Windows 10 및 Windows Server 2019 이상에서는 기본적으로 미설치
- **최신 패치 적용**: MS17-010 패치 (2017년 3월 Microsoft 배포)
- **포트 445 방화벽 차단**: 외부 인터넷에 절대 노출 금지
- **SMB 2.0 이상 사용 유지**: SMBv2, SMBv3는 비활성화 권장하지 않음
- PowerShell로 SMB 버전 확인: `Get-SmbServerConfiguration` / `Get-SmbConnection`

---

<aside>크로스플랫폼 지원</aside>

SMB는 Windows 전용이 아니며 다양한 환경에서 구현된다.

- **Samba**: Linux/UNIX용 오픈소스 SMB 구현체. macOS의 파일 공유도 Samba 기반
- **Linux 커널**: `cifs`, `smbfs` 등 SMB 클라이언트 구현 내장
- **NAS 장치**: Synology, QNAP 등 대부분의 NAS가 SMB 지원
- **Android/iOS**: Mopria, Files 앱 등을 통해 SMB 공유 접근 가능