```table-of-contents
```
# 1. 시스템 로그 및 개요
## 개요
### 목적
- 시스템이 동작하는 동안에 실행하는 앱, 각종 이벤트를 위한 로그정보를 저장하여 성능, 보안, 서버 오류 등의 이슈를 해결
### 생성
- syslogd나 rsyslogd와 같은 시스템 데몬에 의해 생성
- 레드햇 7 계열 이후에서는 systemd-journald와 rsyslogd 데몬에 의해 로그가 관리
### 확인
- 대부분의 리눅스 로그는 /var/log 디렉터리 아래에 텍스트 형식 파일로 저장
- 로그 파일을 확인하려면 루트 권한이 필요

## 주요 시스템 로그 파일

| 레드햇       | 데비안                                     | 설명                                                             |
| :-------- | :-------------------------------------- | :------------------------------------------------------------- |
| messages  | syslog                                  | 전체 시스템의 모든 동작 사항과 정보 메시지와 이벤트                                  |
| secure    | auth.log                                | 시스템의 로그인 행위에 대하여 성공, 실패, 인증 과정에 대한 로그                          |
| boot.log  | boot.log                                | 부팅 시 발생하는 메시지와 부팅 정보                                           |
| maillog   | mail.log                                | 메일서버 로그 기록                                                     |
| kern      | kern.log                                | 커널에서 발생하는 에러 및 경고, 정보 로그                                       |
| dmesg     | dmesg                                   | 디바이스 드라이버가 남기는 로그<br>dmesg 명령어로 로그 확인 가능                       |
| faillog   | faillog                                 | 로그인 실패 시 로그가 기록<br>무차별 대입 공격과 같은 해킹에 대한 간단한 점검                 |
| cron      | syslog                                  | 예약 작업 수행 시 발생하는 로그 기록<br>데비안에서의 cron은 별도 파일 없이 syslog에 합께 기록된다 |
| yum.log   | dpkg.log                                | yum 명령어를 통해 패키지 설치, 삭제 등 명령 수행 시 기록                            |
| httpd     | apache2/access.log<br>apache2/error.log | 웹 서버 아파치의 httpd 데몬이 기록하는 로그                                    |
| mysql.log | mysql/error.log                         | 데이터베이스 mysql 데몬이 기록하는 로그 파일                                    |
| xferlog   | xferlog                                 | FTP 접속 연관된 로그 파일                                               |
| lastlog   | lastlog                                 | 각 사용자의 마지막 로그인 기록을 보관<br>바이너리 형식으로 lastlog 명령어로 확인 가능          |
| wtmp      | wtmp                                    | 각 사용자의 매 로그인과 로그아웃 기록<br>바이너리 형식의 last 명령어로 확인 가능              |
| btmp      | btmp                                    | 모든 로그인 실패기록<br>바이너리 형식으로 lastb 명령어로 확인 가능                      |
| utmp      | utmp                                    | 사용자의 현재 로그인 상태를 보관                                             |
## 시스템 로그 파일 명령어
- [[dmesg]]
- [[lastlog]]
- [[last]]
- [[lastb]]
# 2. 시스템 로그 관리
## 시스템 로그의 생성 및 관리
- 초기에는 syslog 패키지를 통하여 로그를 수집
- 원격 로깅 기능이 가능항 rsyslog 패키지의 등장
- 레드햇 6.5부터는 syslog가 아닌 syslogd가 기본 탑재
### syslog
80년대 sendmail 프로젝트의 일부로 에릭 알만이 개발
로그 파일에 로그를 출력하는 기능을 수행하는 syslogd 데몬이 필요
- /etc/syslog.conf 설정 파일 기반 /var/log/ 디렉터리에 로그 생성
### rsyslog
2004년 레이너 게르하드를 주축으로 오픈소스 프로젝트로 시작.
IP 통신을 통한 로그 기능 구현을 목적
- rsyslog : the Rocket-fast SYStem for log processing
- /sbin/rsyslogd 데몬을 통해 로그 기능을 수행
- /etc/rc.d/init.d/syslogd 스크립트를 통해 부팅 시 데몬 시작
- /etc/rsyslog.conf 설정 파일 기반 /var/log 디렉터리에 로그 생성
- 멀티 스레드 지원
- 지원 프로토콜 : TCP, SSL, TLS, RELP
- 지원 데이터베이스 : MySQL, PostgreSQL, Oracle 등

관련 파일
- /etc/rc.d/init.d/rsyslog
	시스템 시작시 데몬을 실행하는 스크립트
- /etc/rsyslog.conf
	
- /etc/sysconfig/
- /sbin/rsyslogd













