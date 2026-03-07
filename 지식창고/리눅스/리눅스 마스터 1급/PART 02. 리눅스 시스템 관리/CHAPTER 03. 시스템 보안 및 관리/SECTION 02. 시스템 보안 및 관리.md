```table-of-contents
```
# 1. 시스템 보안 관리
## 리눅스 보안
### 물리적 보안
- 물리적 보안이란
	- 민감한 서버에 대하여 허가 받지 않은 사용자가 물리적으로 접근하지 못하게 하는 것
	- 서버실에서 서버 케이스를 열고 디스크에 접속한다면 아무런 의미가 없음
- 방안
	- CCTV로 서버 감시
	- 동작 감지 및 열화상
	- 경비 강화
	- 등
### 시스템 보안
- BIOS 보안
	- BIOS 설정을 변경하여 CD-ROM, USB 등으로 부팅하여 복구모드로 진입 가능하므로 BIOS에 비밀번호 설정
- 패스워드 보안
	- root 사용자는 허가되고 제한된 사용자에게만 제한을 걸어야 한다. UID가 0인 root가 아닌 사용자가 있는지 점검한다.
	- /etc/shadow 를 사용하여 해시를 사용한다
	- 무작위 대입 공격을 방어하기 위해 강력한 패스워드 설정
		- Joh The Ripper 등의 크래킹 도구를 대비하여 랜덤 문자열 단어의 패스워드
	- 강력한 패스워드 입력을 강제하기 위해 PAM(Pluggable Authentication Modules) 중 pam_cracklib.so를 사용
	- chage 명령어나 User Manager 애플리케이션으로 특정 사용자의 패스워드 만료일을 설정하여 정기적으로 변경하도록 유도
- 관리자 계정 보안
	- su, sudo 명령어를 통해 필요할 때 일시적으로 권한 부여
		- root 사용자의 로그인 제한은 /etc/passwd에서 root 사ㅇ자의 셸 설정을 /sbin/nologin으로 변경한다.
	- SSH 프로토콜을 통한 root 사용자 로그인을 막기 위해서 /etc/ssh/sshd_config 파일에서 `PermitRootLogin no`를 기입한다
### 서비스 및 운영 보안
- 필수 서비스만 사용
	- 최소 설치 및 필요 내용만 추가하는 것
- 시스템 정보 숨김
	- 로그인 시 /etc/issue 또는 /etc/issue.net의 내용이 사용자의 터미널에 출력한다. 이를 가려서 배포판과 커널의 버전을 숨기는 것도 보안이다.
- 부트로더 패스워드 설정
	- 부트로더를 통해 root의 패스워드를 변경이 가능한데 이를 막기 위해 부트로더 패스워드를 설정한다
	- `grub-crypt` 명령어를 통해 패스워드의 해시 암호화 코드를 생성한다
	- 그 후 암호화된 코드를 grub2.cfg에 적용한다
- 보안 서비스 사용
	- telnet 보다는 ssh를 사용한다.
### 파일 시스템 보안
- 소유권과 허가권
	- 파일 및 디렉터리의 소유권 및 허가권을 필요한 만큼만 설정.
- 관련 명령어
	- [[lsattr]]
	- [[chattr]]
	- [[getfacl]]
	- [[setfacl]]
### 네트워크 보안
- sysctl을 통한 보안 강화
	- sysctl은 /proc/sys 디렉터리 이하의 커널 매개변수를 확인하거나 설정하는 명령어로서 세커널을 통해 리눅스 보안 강화
	- /proc/sys/net 이하에는 네트워크 관련 커널 설정을 할 수 있는 경로
	- [[sysctl]]
# 2. SELinux(Security-Enhanced Linux)
## SELinux의 개요
### SELinux의 정의
- 미국의 NSA(National Security Agency)에 의해 연구된 프로젝트
- 강제 접근 제어(MAC : Mandatory Access Control)와 같은 접근 제어 정책을 제공하는 리눅스 커널 보안 모듈
- MAC는 모든 주체와 객체에 대해 국부적으로 허가하는 접근 제어 정책
### SELinux의 특징
- 리눅스 커널의 기본 기능으로 포함됨
- [[제로데이 공격]]으로 공격받더라도 피해 최소화
## SELinux의 설정 및 해제
### 동작 모드
- enforce
- permissive
- disable
### 명령어
- [[sestatus]]
- [[setenforce]]
- /etc/sysconfig/selinux 파일에 SELINUX 변수의 값을 수정하여 영구 반영 가능
# 3. 시스템 보안 유틸리티
## ssh(Secure SHell)
### ssh의 정의
- 호스트와 클라이언트 간의 패킷을 암호화하여 송수신
- 포트 번호 22번
### ssh 연결 방법
1. 클라이언트 패키지 설치
	- 레드햇 : `yum install -y openssh-clients`
	- 데비안 : `apt install -y openssh-client`
2. 서버 패키지 설치
	- 레드햇 : `yum install -y openssh-server`
	- 데비안 : `apt install -y openssh-server`
3. 서비스 시작. ssh 서비스는 sshd 데몬이 관리한다.
	- `systemctl start sshd`
	- 부팅 시 자동 실행
		`systemctl enable sshd`
4. 접속
	[[ssh]] 명령어로 진행
	`ssh -l 유저명 IP주소`
	`ssh 유저명@IP주소`
### ssh 인증키
- [[ssh-keygen]] 명령어로 개인키와 공개키를 생성하고 공개키를 원격 서버에 복사해두면 비밀번 없이 ssh 접속이 가능하다
- ssh-keygen 명령어로 개인키와 공개키를 생성한다. -t 옵션을 통해 알고리즘을 결정할 수 있다. [[RSA]], [[DSA]] 등을 지정 가능
- `ssh-keygen -t dsa혹은rsa`
	홈 디렉터리의 .ssh 디렉터리에 개인키인 id_dsa와 공개키 id_dsa.pub가 생성된다
1.  ssh 서버에 .ssh 디렉터리를 생성
	`ssh IP주소 mkdir .ssh`
2. [[scp]] 명령어로 .ssh 디렉터리의 id_dsa.pub을 authorized_keys 이름으로 복사한다
	`scp id_dsa.pub IP주소:.ssh/authorized_keys`

### sshd 환경설정
- 데몬 환경설정 파일 : /etc/ssh/sshd_config
- 클라이언트 환경설정 : /etc/ssh/ssh_config
- 데몬 스크립트 : /usr/lib/systemd/system/sshd.service

- sshd 주요 환경설정 항목

| 항목                     | 설명                                                                        |
| :--------------------- | ------------------------------------------------------------------------- |
| Port                   | ssh 사용 포트(기본값 22)                                                         |
| PermitRootLogin        | yes 설정시 root로 로그인 가능                                                      |
| AllowUsers             | 허용된 사용자만 ssh 접속 허가 (미설정시 전원 가능)                                           |
| LoginGraceTime         | 로그인 대기 시간                                                                 |
| PasswordAuthentication | 비밀번호 인증을 통한 접속 활성화 여부 설정<br>공개키 인증을 비활성화하려면 yes로 한다                       |
| PubkeyAuthentication   | 보안 강화를 위해 공개키 기반 인증을 사용                                                   |
| TCPKeepAlive           | yes 설정하면 지속적으로 keepalive 메시지를 전송하여 연결상태 체크<br>네트워크 문제 발생 시 리소스 반환 및 연결 종료 |

## PAM(Pluggable Authentication Module)
### PAM이란?
사용자 동적 인증 공유 라이브러리 스위트
PAM은 저수준 인증 모듈을 고수준의 API로 통합하여 애플리케이션에 대한 동적 인증 지원 제공

PAM 관련 모듈은 아키텍처에 따라 /lib/security 혹은 /lib64/security에 위치한다.
### PAM 환경설정
- 주요 파일
	- /etc/pam.conf : 파일
	- /etc/pam.d : 디렉터리. 위 파일보다 우선된다 
- 환경설정 항목
	- `module-type` : 모듈의 유형
		- account : 사용자의 패스워드 만료, 서비스 접근 허가 등의 계정 검증
		- auth : 사용자 실제 인증
		- password : 패스워드 갱신 및 auth 모듈 연동
		- session : 세션의 시작, 종료 관련 작업
	- `control-flag` : 인증 성공, 실패에 따른 처리 방안을 정한다
		- requisite : 반드시 성공되어야 한다. 실패시 즉시 실패 반환
		- required : 반드시 성공되어야 한다. 실패시 해당 모듈타입의 체크를 모두 수행 후 실반환
		- sufficient : 성공 시 나머지 모듈의 체크 진행 안함
		- optional : 다른 모듈의 체크가 모두 성공시 이 모듈의 결과를 응용 프로그램에 반환
		- include : 지정한 환경설정 파일을 로드하여 적용
	- `module-name` : 설정의 대상이 되는 모듈의 이름
	- `module-arguments` : 모듈이름에서 지정한 모듈에게 전달하려는 파라미터
## PAM 환경설정 샘플
```bash
#%PAM-1.0
auth		required	pam_securetty.so
auth		required	pam_unix.so			nullok	
auth		required	pam_nologin.so
account		required	pam_unix.so
password	required	pam_cracklib.so		retry=3
password	required	pam_unix.so			shadow	nullok	use_authtok
session		required	pam_unix.so
```
1. `#%PAM-1.0`
	PAM 라이브러리로 하여금 PAM 버전 1.0 형식의 설정파일임을 알 수 있도록 함
2. `auth		required	pam_securetty.so`
3. `auth		required	pam_unix.so	nullok`	
auth		required	pam_nologin.so
account		required	pam_unix.so
password	required	pam_cracklib.so		retry=3
password	required	pam_unix.so			shadow	nullok	use_authtok
session		required	pam_unix.so




