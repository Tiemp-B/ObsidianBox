```table-of-contents
```
# 개요
CopyFail(CVE-2026-31431)은 2026년 4월 말 발견된 리눅스 커널의 매우 심각한 로컬 권한 상승 취약점

사용자 공간 암호화 인터페이스(AF_ALG)와 splice 시스템 콜을 이용해 메모리 캐시를 변조로 일반 사용자가 즉시 루트 권한을 획득 가능
2017년 이후 주요 리눅스 배포판 전체에 영향을 미침

# 키워드
## AF_ALG
AF_ALG는 커널의 암호화 서브시스템을 사용자 공간에서 접근할 수 있게 열어둔 소켓

응용 프로그램이 해당 소켓을 통해 커널의 하드웨어 암호화 가속기를 사용하여 SW를 구현하도록 한다. 즉, 암호화를 하려는 응용 프로그램이 접근하는 소켓이며, 빠른 암호화를 위해 하드웨어 가속이 가능한 커널 영역에서 동작하게 한다.
## splice()
두 파일 디스크립터 사이에서 데이터를 복사하지 않고 이동시키는 시스템 콜

```
[일반 read/write 구조]
디스크 -> 커널 버퍼 -> 사용자 버퍼 -> 커널 버퍼 -> 목적지
                  |복사발생     |복사발생
[splice()]
디스크 -> 커널 버퍼 -> 목적지
                |페이지 참조만 전달=복사 없음
```

## authencesn
Linux 커널 암호화 서브시스템의 AEAD(Authenticated Encryption with Associated Data) 래퍼 알고리즘.
IPsec의 확장 시퀀스 번호(ESN) 지원을 위해 설계

- AEAD : 암호화 + 인증을 동시에 수행
- authenc : 기본 IPsec 인증 암호화 래퍼
- authencesn : authenc의 ESN 버전
- ESN : 64비트 확장 시퀀스 번호

기존 authenc의 최적화를 위해 페이지 캐시를 scatterlist에 splice로 직접 연결하였고, 이로 인해 보안 문제가 발생하게 되었다.

# 발동 방식
## 구조
1. AF_ALG 소켓을 열어 authencesn 알고리즘에 바인딩.
2. 타겟이 되는 `/usr/bin/su`등의 setuid 바이너리를 열어 그 페이지 캐시페이지를 splice로 소켓의 TX scatterlist에 주입
3. 이를 4바이트 단위로 잘라 sendmsg()와 