```table-of-contents
```
# 1. 리눅스 커널
## 커널의 개요
### 리눅스 커널이란?
유닉스 OS를 바탕으로 리누스 토발즈가 처음 개발.
GNU GPL v2 라이선스 하에 모두에게 무료로 공개됨

리눅스 커널은 **모놀리식 커널**이며 선점형 멀티태스킹, 가상메모리, 공유 라이브러리, 메모리 관리, 네트워킹, 쓰레딩 등 현대 운영체제가 가져야 할 모든 특징을 가진다.

### 커널의 컴파일

1. 커널 소스코드 다운로드.
	kernel.org 에서 원하는 커널의 소스코드의 타르볼이나 깃허브를 통해 다운이 가능하다.
2. 컴파일 필수 도구 설치
	`dnf install -y ncurses-devel make gcc bc bison flex elfutils-libelf-devel openssl-devel grub2`
3. 커널 환경 설정
	```bash
	# 기존 파일 제거
	make mrproper
	```









