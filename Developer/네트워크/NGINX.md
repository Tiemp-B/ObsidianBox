---
cssclasses: cornell-note
tags:
  - nginx
  - web-server
  - reverse-proxy
  - networking
---

# Summary

Nginx는 고성능·비동기 이벤트 기반 구조를 가진 웹 서버이며,  
리버스 프록시, 로드 밸런서, 정적 파일 서버 등 다양한 용도로 사용된다.  
가볍고 빠르며 확장성이 뛰어나 현대 웹 아키텍처의 핵심 구성 요소로 자리 잡았다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Nginx 개요</aside>

Nginx(Nginx Engine X)는 이벤트 기반 아키텍처를 사용하는 고성능 웹 서버이다.  
아파치(스레드/프로세스 기반)와 달리 비동기 I/O를 적용해 높은 동시성을 처리할 수 있으며,  
정적 파일 제공, 리버스 프록시, 로드 밸런싱, SSL 오프로드 등 여러 역할을 수행한다.

주요 특징:  
- 낮은 메모리 사용량  
- 높은 동시 연결 처리 능력  
- 리버스 프록시 + 로드밸런서 역할  
- 정적 파일 처리에 매우 빠름

<aside>Nginx의 아키텍처</aside>

기본 구조는 **마스터 프로세스 + 여러 워커 프로세스** 모델이다.  

- **Master**  
  - 설정 파일 로드  
  - 워커 생성/관리  
- **Worker**  
  - 클라이언트 요청 처리  
  - 이벤트 루프 기반 비동기 처리  

각 워커는 싱글 스레드지만 이벤트 루프 방식(Epoll 등)을 사용해 다수의 연결을 효율적으로 처리한다.

<aside>주요 기능</aside>

- **웹 서버**  
  정적 파일(css, js, 이미지 등) 제공에 최적화  

- **리버스 프록시**  
  백엔드 서버(Express, Django, Spring 등) 앞단에서 요청 라우팅  

- **로드 밸런서**  
  - Round Robin  
  - Least Connections  
  - IP Hash  

- **SSL/TLS Termination**  
  HTTPS 인증서 관리 및 TLS 오프로드  

- **캐싱 서버**  
  정적 자원의 캐싱 및 응답 속도 향상  

- **HTTP/2, gRPC Proxy 지원**

<aside>주요 설정 파일 구조</aside>

기본 설정은 `/etc/nginx/nginx.conf`이다.  
핵심 블록:

- **events {}** – 워커 처리 방식  
- **http {}** – 웹 관련 설정  
- **server {}** – 가상 호스트  
- **location {}** – URL 라우팅  

예: 리버스 프록시 설정  

```
location / {  
proxy_pass http://localhost:3000;  
}
```
<aside>정적 파일 서버로서의 Nginx</aside>

Nginx는 파일 I/O를 비동기로 처리해 정적 파일 제공 속도가 매우 빠르며,  
특히 프론트엔드 빌드 결과물(dist)을 서비스할 때 널리 사용된다.

<aside>리버스 프록시 활용</aside>

Nginx는 보통 백엔드 앱 앞단에서 보안·성능 향상 역할을 한다.

- 백엔드 포트 숨기기  
- HTTPS → HTTP 내부 전달  
- CORS 처리  
- 캐싱  
- 압축(gzip, brotli)  

Cloudflare, AWS ALB/NLB 등 많은 인프라가 Nginx 구조를 모델로 한다.

<aside>운영 및 배포 환경</aside>

Nginx는 다음 환경에서 강점을 가진다.  
- Docker + Docker Compose  
- Kubernetes Ingress Controller  
- CI/CD 파이프라인의 배포 서버  
- 로드 밸런서 전면 게이트웨이  

Nginx Ingress는 K8s 환경에서 사실상 표준 게이트웨이다.

<aside>사용 사례</aside>

- 정적 웹사이트 호스팅  
- Express, Django, Spring 백엔드 앞단 리버스 프록시  
- 여러 서비스의 도메인 라우팅  
- SSL 인증서 관리(HTTPS)  
- 로드 밸런싱 및 캐싱  

<aside>핵심 정리</aside>

- Nginx는 고성능·비동기 기반 웹 서버  
- 리버스 프록시/로드 밸런서로 가장 널리 사용  
- 정적 파일 제공에 매우 빠르며 서버 앞단의 최적 선택  
- Docker, Kubernetes 등 현대 웹 아키텍처의 핵심 구성 요소다
