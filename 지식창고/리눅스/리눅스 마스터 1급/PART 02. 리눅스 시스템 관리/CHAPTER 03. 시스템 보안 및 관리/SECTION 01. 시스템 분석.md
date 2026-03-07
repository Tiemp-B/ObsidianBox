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

## rsyslog로 로그 관리리
### 관련 파일
- /etc/rc.d/init.d/rsyslog
	시스템 시작시 데몬을 실행하는 스크립트
- /etc/rsyslog.conf
	rsyslogd 데몬의 환경설정 파일
	- 기본 구조
		`facility.priority action`
		- 섹션
			- Global Directives : 데몬의 전역 설정, 메시지 큐 크기, 외부 모듈 로드 등
			- Templates : 로그 메시지의 형식 보관. Rules에서 사용
			- Output channels : 출력 채널에 대한 세부 설정을 저장
				`$cosjfaud, vkdlfdlfma, chleozmrl, chleozmrl tl tlfgod audfud`
			- Rules(slector + action) : 로그 규칙 설정
				- selector : ';'으로 여러 개 지정 가능
					- facility
						로그 메시지를 발생하는 프로그램 
					- priority 
						로그 메시지의 수준. 지정 수준보다 높은 메시지만 출력
						'='으로 특정 수준만, '!'으로 특정 수준을 제외
						','으로 여러 facility 설정 가능. 순차 적용됨
						- 0, emerg, panic : 시스템 운용 불가
						- 1, alert : 시스템 사용가능하나 위험 발생
						- 2, crit : 중요 메시지
						- 3, error, err : 에러
						- 4, warning, warn : 경고
						- 5, notice : 알림
						- 6, info : 정보
						- 7, debug : 디버깅
						- 8, none : 지정 우선순위 없음
				- action
					로그 파일을 지정. 네트워크로 메시지를 전달하는 등의 설정 가능
					- file : 지정 파일에 기록
					- @host : UDP 프로토콜로 지정 호스트에 전달
					- @@host : TCP 프로토콜로 지정 호스트에 전달
					- user : 지정한 사용자가 로그인한 터미널로 전달
					- 콘솔 또는 터미널 : 지정 터미널로 메시지 전달
			```bash
			# 셀렉터1 => 모든 facility의 crit 수준의 메시지만 해당 경로에 기록
			# 셀렉터2 => user 서비스의 경우 로그메시지 출력 안
			*.=crit;user.none    /var/log/critical
			# 모든 facility에 대해 alert 이상 메시지가 발생하면 모든 사용자에
			*.alert    *
			# mail의 로그 중 debug가 아닌 것만 기록
			mail.*;mail.!=debug     /var/log/mail-messages
			# A와 B의 alert 로그를 UDP로 전달
			A,B.=alert    @192.168.0.1
			```
	
- /etc/sysconfig/
	rsyslogd 데몬을 실행할 때 옵션 설정
	rsyslog v3 부터는 옵션을 사용하지 않고 rsyslog.conf 설정 파일을 사용
- /sbin/rsyslogd
	rsyslogd 데몬의 파일 경로
### 로그 용량 관리
1. logrotate 명령어
2. logrotate 환경설정
	/etc/logrotate.conf로 시스템 전체에 대한 환경설정
	/etc/logrotate.d로 개별 서비스를 위한 설정
	```bash
	# 로그 파일 로테이트
	# daily, weekly, monthly, yearly
	# 최대 4번의 로테이트 수행
	rotate n
	# 각 로테이션을 마치고 빈 로그 파일 생성
	create 허가권 소유자 그룹
	# 각 로그 파일의 마지막에 날짜를 붙인다
	dateext
	# 로그 파일 압축
	compress
	# 지정 경로의 환경설정 파일도 적용
	include /etc/logrotate.d
	
	# 특정 로그에 대한 설정 
	/var/log/wtmp{
	    mothnly
		create 0664 root utmp
		minsize 1M
		rotate 1
	}
	# 파일 처리
	# missingok : missing ok 로그파일이 없어도 에러를 출력하지 않는다
	# nomissingok : 로그파일 없으면 에러 출력
	# compress : gzip 압축
	# nocompress : 압축 안함
	# delaycompress : 다음 로테이션 때 압축
	# copytruncate : 파일 복사 후 원본 삭제
	# maxage N : N일 이상된 파일 삭제
	/var/log/btmp {
		missingok
	}
	# 스크립트
	# prerotate : 로테이션 전 실스크립트
	# postrotate : 로테이션 후 
	```














