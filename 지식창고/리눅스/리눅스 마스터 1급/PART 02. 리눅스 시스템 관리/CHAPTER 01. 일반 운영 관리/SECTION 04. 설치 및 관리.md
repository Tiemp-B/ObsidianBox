```table-of-contents
```

# 1.패키지를 통한 소프트웨어 설치
## 패키지 도구
### 배포판 별 패키지 도구
|   배포판    | 저수준  |          고수준           |
| :------: | :--: | :--------------------: |
|   레드햇    | rpm  |          yum           |
|   데비안    | dpkg | apt-get, apt, aptitude |
| openSUSE | rpm  |      zipper/YaST       |
- 저수준 패키지
	패키지의 설치, 업그레이드, 제거 등의 개별 동작
	의존성 고려를 안하기에 의존이 필요하면 에러가 난다. 
	해당 패키지 파일을 다운한 후 설치한다
- 고수준 패키지
	패키지의 의존성까지 고려하여 저수준 패키지를 활용

# 2. 레드햇 패키지 도구
### 저수준 패키지 관리 도구 RPM
- 개발사 : 레드햇
- 사용 배포판 : Novell NetWare, IBM's AIX, CentOS, Fedora, Oracle Linux 등
- 패키지 파일 : .rpm
- 명령어 [[rpm]]

### 고수준 패키지 관리 도구 
- [[yum]]
	옛 RHEL 계열 기본 패키지 관리
- [[dnf]]
	RHEL 8 / CentOS 8 이후의 기본 패키지 관리

# 3. 데비안 패키지 도구
### 저수준 패키지 관리 도구 dpkg


### 고수준 패키지 관리 도구 
- apt
- apt-get
- aptitude







