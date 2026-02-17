---
tags:
  - 리눅스
---

# 명령어 역할
라우팅 테이블을 표시 및 수정
패킷의 목적지 주소와 넷마스크로 얻은 네트워크 주소와 라우팅 테이블에 매칭되는 경로가있다면 해당 경로에 설정된 네트워크 인터페이스를 통해 패킷을 라우팅한다
```bash
형식
route
route add [-net|-host] target [netmask Nm] [gw Gw] [[dev] If]
route del [-net|-host] target [gw Gw] [netmask Nm] [[dev] If]
```

## 설명
### 컬럼
- Destination : 목적지 호스트나 네트워크의 주소
- Gateway :  외부 네트워크와 연결되어 있는 게이트웨이 주소
- Genmask : 

# 옵션


# 예제


# 연관 명령어


