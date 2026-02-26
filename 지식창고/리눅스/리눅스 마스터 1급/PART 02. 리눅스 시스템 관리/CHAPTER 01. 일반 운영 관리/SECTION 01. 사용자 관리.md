# 1. 사용자의 분류
## 사용자의 종류
1. 루트 계정
	시스템에 대한 모든 권한을 가진 사용자
2. 시스템 계정
	리눅스 설치 시 기본으로 생성되는 계정.
	각 역할별로 제한적인 권한 보유
3. 사용자 계정
	실제 리눅스 사용자
# 2. 루트 계정 관리
## 루트 계정이란
### 정의
시스템 접근에 대한 제한을 받지 않는 완전한 권한을 갖는 사용자
시스템의 대표 관리자가 루트 계정을 보유
### UID
루트 계정의 UID는 0이다
## 루트 계정 권한 획득 방법
### root 사용자로 로그인
- 기본적으로 root 사용자로 로그인 불가하도록 설정 되어 있으나 아래 방법으로 로그인 가능하게 할 수 있다
```bash
$ sudo passwd root
```
- su 명령어로 root 사용자로 전환할 수 있다
### root 사용자로 임시 전환
sudo를 사용하고 비밀번호를 입력하여 root 권한 대행이 가능하다
### 현 사용자를 root 사용자로 지정
/etc/passwd 파일에서 사용자의 UID를 0으로 지정하면 root 권한을 가지게 된다
## 루트 계정 관리 방안
- root 사용자는 시스템의 초기 환경 설정 시에만 이용하고 SSH를 통해 root 사용자 로그인이 되않도록 설정해야 한다
- root 계정은 유일해야 한다
- PAM(Pluggable Authentication Modules)를 통하여 root 사용자로 로그인 할 수 없도록 설정
- root 계정으로 로그인하는 것은 지양하며, sudo 명령을 권장한다
## root 비밀번호 분실 대응
1. GRUB2 부트 메뉴에서 환경설정 변경을 위해 'e' 입력
2. linux16의 옵션 중 `ro`를 `rw`로 변경하고 `init=/sysroot/bin/sh`를 추가로 입력
3. `Ctrl + X`로 단일 사용자 모드로 부팅 시도
4. `chroot /sysroot` 시스템에 접근
5. `passwd root`로 비밀번호 설정
6. `touch /.autorelabel` selinux 정보 갱신 
7. `exit` chroot를 종료 
8. `reboot` 리부트
## SSH로 root 로그인 막기
1. /etc/ssh/sshd_config 파일
2. PermitRootLogin 항목을 no로 설정한다
3. `systemctl restart sshd` 혹은 `service sshd restart`로 sshd 서비스를 재시작한다

# 3. 시스템 계정 관리
## 시스템 계정
### 시스템 계정이란
- 메일 관리, SSH 연결 등 시스템의 특정 서비스에 대한 권한을 행사가 가능한 계정
- bin, daemon, adm, lp, sync, shutdown, halt, mail과 같은 계정들이 시스템 계정.
- /etc/passwd 파일에서 1~499의 UID를 가진다.
	- 기본 설정 시스템 계정의 경우 1~99의 범위를 가진다
	- 시스템 운용 중 추가되는 시스템 계정
		- 레드햇 100~499
		- 데비안 100~999
		- 배포판마다 상이할 수 있다
## 시스템 계정 관리 방안
- 서비스별로 권한을 분리하여 시스템 계정을 생성

# 4. 사용자 계정 관리
## 사용자 계정
### 사용자 계정이란
- 일반 사용자.
- 시스템 파일과 디렉터리에 제한적으로 접근 가능하게 하여 시스템을 보호
- 개인 혹은 그룹 단위로 권한 설정하여 접근 범위 설정이 가능하다
- UID
	- 레드햇 6버전 : 500 이상
	- 레드햇 7 이후, OPENSUSE, 데비안 : 1000 이상
	- /etc/login.defs에 저장되어 있다.
## 사용자 생성
### 명령어
1. [[useradd]]
2. [[adduser]]
	두 명령어의 차이
	- 레드햇에선 adduser는 useradd에대한 링크이므로 동일하다
	- 우분투에서 adduser를 사용하면 대화힉으로 생성할 수 있다
3. [[passwd]]
# 5. 그룹 계정 관리
## 그룹이란
- 사용자를 하나로 묶어 관리가 가능하게 한다.
- 그룹에 보안 설정 등의 권한을 주는 방식으로 일괄적으로 그룹에 속한 사용자에 적용이 가능함

### 명령어
- [[groupadd]]
- [[groupmod]]
- [[groupdel]]
- [[gpasswd]]
- [[newgrp]]

### 그룹
- 관리자
	그룹에 멤버를 추가, 제거, 비밀번호 변경의 권한
- 멤버

# 6. 사용자 환경설정 파일
크게 2 종류로 나눠진다
- 계정 및 그룹 설정 파일
	- /etc/passwd
		사용자 계정의 아이디, 그룹 정보 등의 계정 정보
	- /etc/shadow
		암호화된 패스워드 및 정책 설정 정보
	- /etc/group
		사용자 그룹의 기본 정보
	- /etc/gshadow
		사용자 그룹의 암호화된 패스워드 정보
- 계정 환경설정 파일
	- /etc/default/useradd
		useradd 명령어의 기본 설정
	- /etc/login.defs
		로그인 수행 시 기본 설정
	- /etc/skel
		홈 디렉터리 생성 시 기본으로 제공하는 파일
## 계정 및 그룹 설정 파일
### 1. /etc/passwd
로그인 시 필요한 UID, GID, 홈 디렉터리, 셸 등의 사용자 계정 정보 포함
모든 사용자가 읽을 수 있으나 루트 권한으로만 쓰기가 허용
```bash
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
username:x:12:100:example_user:/home/user:/bin/bash
```
구성
`A:B:C:D:E:F:G`
- A: 사용자명. 1~32자
- B: x->암호화된 패스워드를 /etc/shadow에 보관중
- C: UID
- D: GID
- E: 사용자 설명
- F: 홈 디렉터리
- G: 사용하는 셸 위치

### 2. /etc/shadow
패스워드를 해시 알고리즘으로 암호화한 값과 패스워드와 연관된 여러 속성을 담고 있는 파일
`A:B:C:D:E:F:G:H:`
- A: 사용자명
- B: 암호화된 패스워드. \$id\$salt\$hashed 형식이다
	- $id란
		- $1\$ : MD5
		- \$2a$ : Blowfish
		- $2y\$ : Blowfish
		- $5\$ : SHA-256
		- $6\$ : SHA-512
- C: 패스워드 변경일. 1970년 1월 1일 기준
- D: 패스워드 최소 유지기간
- E: 패스워드 최대 사용기간
- F: 패스워드 만료 경고일
- G: 만료 유예기간
- H: 계정 비활성화 날짜
### 3. /etc/default/useradd
useradd으로 사용자 생성 시 사용되는 기본 설정 값
`useradd -D` 로도 확인 가능하다
항목
- GROUP
	GID
- HOME
	홈 디렉터리를 생성할 기본 디렉터리
- INACTIVE
	비밀번호 만료
- EXPIRE
- SHELL
- SKEL
- CREATE_MAIL_SPOOL

### 4. /etc/gshadow




















