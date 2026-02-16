---
tags:
  - 리눅스
  - 네트워크
---

# 명령어 역할
network manager를 확인하는 명령어

```bash
nmcli [<옵션>] <개체> { <명령> | help}
```

# 옵션
- 개체
	- g[eneral] : Network Manager의 일반 상태 및 작업
	- c[onnection] : 네트워크 연결
	- d[evice] : 관리하는 장치
	- a[gent] : 비밀 에이전트 또는 polkit 에이전트 q
	- m[onitor] : 변경 사항을 모니터링
	- r[adio] : 라디오 스위치
	- n[etworking] : 네트워크 관리 전반
- 옵션
	- -a, --ask : 매개변수 누락되면 물어보기
	- -c, --colors : 출력에 색을 사용할지 여부. auto|yes|no
	- -e, --escape : 값에 열 구분 기호를 이스케이프. yes|no
	- -f, --fields : 출력할 필드 지정 <필드,...>|all|common
	- -g, --get-values : `-m tabular -t -f` 옵션의 줄임 <필드,...>|all|common
	- -h, --help : 이 도움말 표시
	- -m, --mode tabular|multiline : 출력 모드
	- -o, --overview : 개요 모드
	- -p, --pretty : 예쁜 출력
	- -s, --show-secrets : 암호 표시 허용
	- -t, --terse : 간결한 출력
	- -v, --version : 프로그램 버전 표시
	- -w, --wait <초> : 작업을 마칠 때 기다리는 제한 시간을 설정
# 예제
```bash
# 
nmcli c m ens33 ipv4.method auto connection autoconnect yes
# 
nmcli c m ens33 ipv4.method manual connection.autoconnect yes ipv4.addresses 10.20.30.41/24 ipv4.gateway 10.20.30.254 ipv4.dns "168.126.63.1 168.126.63.2"
```

# 연관 명령어


