---
tags:
  - 리눅스
  - 공유시스템
  - SAMBA
---
# Summary

Samba는 Andrew Tridgell이 개발한 **자유-오픈소스 SMB 프로토콜 구현체**로, Linux/UNIX 시스템이 Windows 네트워크 환경과 상호 운용(interoperability)할 수 있게 해주는 소프트웨어 스위트다. 파일·프린터 공유부터 Active Directory 도메인 컨트롤러 역할까지 수행 가능하며, 거의 모든 Linux 배포판에 기본 포함될 만큼 범용적으로 쓰인다. 이름의 유래는 SMB → **S**a**MB**a.

---

<div class="cues-header">Cues</div>

# Notes

<aside>탄생 배경</aside>

Andrew Tridgell은 UNIX 서버의 디스크를 DOS PC에 마운트해야 했는데, NFS 클라이언트는 있었지만 NetBIOS 인터페이스가 필요한 애플리케이션 때문에 문제가 생겼다. 이를 해결하기 위해 그는 **패킷 스니퍼**로 SMB 프로토콜을 역공학(Reverse Engineering)하여 UNIX에 구현했다.

- **1991~1992년**: 호주국립대학교(ANU) 박사과정 중 첫 버전 개발
- **1992년 1월**: 버전 0.1, 0.5, 1.0을 연속 공개. 당시 이름은 단순히 "Unix file server for DOS Pathworks"
- **1993년 12월**: GPL2 라이선스 채택, 'smbserver'로 명명 후 → **Samba**로 최종 변경
- 이름의 유래: **SMB**에서 모음을 추가해 **S**a**M**B**a**

---

<aside>주요 기능</aside>

Samba는 단순 파일 공유 도구가 아닌 **다기능 네트워크 상호운용 스위트**다.

- **파일 공유**: UNIX 디렉토리를 Windows 네트워크 폴더처럼 노출
- **프린터 공유**: Windows 클라이언트에 프린터 서비스 제공
- **인증 및 권한 관리**: NTLM, Kerberos 기반 사용자 인증
- **도메인 컨트롤러(DC)**: Samba 4부터 Active Directory DC 역할 수행 가능
- **WINS 서버**: NetBIOS 이름 → IP 주소 매핑 서비스
- **도메인 멤버**: Windows AD 도메인에 Linux 서버/데스크톱 통합

---

<aside>핵심 데몬(Daemon) 구조</aside>

Samba는 3개의 핵심 데몬으로 구성된다.

| 데몬           | 역할                                                                |
| ------------ | ----------------------------------------------------------------- |
| **smbd**     | 파일·프린터 공유 서비스 제공. 사용자 인증, 리소스 잠금, 데이터 공유 담당. TCP 포트 139, 445 수신   |
| **nmbd**     | NetBIOS 이름 서비스 및 브라우징 지원. Windows 네트워크 이웃 목록 제공. WINS 서버 역할 가능    |
| **winbindd** | Windows NT/AD 서버의 사용자·그룹 정보를 UNIX 시스템이 이해할 수 있도록 변환. PAM 및 NSS 연동 |

설정 파일은 단일 파일 `/etc/samba/smb.conf` 로 관리된다.

---

<aside>버전 역사</aside>

| 버전                        | 주요 내용                                                                |
| ------------------------- | -------------------------------------------------------------------- |
| **Samba 1**               | LAN Manager 프로토콜 구현, 워크그룹 지원                                         |
| **Samba 2**               | NT4 스타일 도메인 컨트롤러 서비스 지원                                              |
| **Samba 3**               | NT4 도메인 전체 기능 지원, SMB2·SMB3 실험적 지원. **역공학 기반으로 개발**                  |
| **Samba 4 (2005~)**       | 완전한 Active Directory DC 구현 목표로 전면 재작성. Microsoft의 공식 스펙 공개 이후 개발 가속화 |
| **Samba 4.0 (2012년 12월)** | 최초의 안정 버전 출시. smbd3 코드를 파일 공유 기반으로, Samba4 코드를 AD 기능 기반으로 통합         |

> **Samba 4 개발의 전환점**: EU의 Microsoft 독점 남용 소송(2004) 결과, Microsoft가 프로토콜 공식 스펙을 공개하면서 역공학에 의존하던 개발 방식에서 탈피할 수 있었다.

---

<aside>SMB와 Samba의 관계</aside>

| 구분    | SMB                     | Samba                  |
| ----- | ----------------------- | ---------------------- |
| 성격    | Microsoft가 설계한 **프로토콜** | SMB의 오픈소스 **구현체**      |
| 개발 주체 | IBM/Microsoft           | Andrew Tridgell 및 커뮤니티 |
| 라이선스  | 독점(Proprietary)         | GNU GPL                |
| 동작 OS | 주로 Windows              | Linux, UNIX, macOS 등   |

Apple은 OS X 10.9(Mavericks)부터 자체 AFP 프로토콜을 버리고 SMB2를 기본 파일 공유 프로토콜로 채택했으나, Samba의 GPLv3 전환 이후 자체 SMB 구현체(SMBX)를 개발해 사용 중이다.

---

<aside>실제 활용 사례</aside>

- **NAS 장치**: Synology, QNAP 등 대부분의 NAS가 Samba를 통해 SMB 공유 제공
- **Linux 파일 서버**: 기업 환경에서 Windows 클라이언트와 Linux 서버 간 파일 공유
- **Raspberry Pi**: 가정용 미디어 서버, 개인 클라우드 구축에 광범위하게 사용
- **Active Directory 통합**: Linux 서버를 Windows AD 도메인에 멤버로 참여시키거나 AD DC로 운영
- **PlugFest**: SMB 프로토콜 구현체 간 상호운용성 테스트를 위한 연례 행사에 Samba 팀 참여

---

<aside>관련 명령어</aside>

