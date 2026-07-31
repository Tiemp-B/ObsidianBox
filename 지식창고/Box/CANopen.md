---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 통신프로토콜
  - 필드버스
---

# Summary

CANopen은 [[CAN(Controller Area Network)]]의 물리·데이터링크 계층 위에 **표준화된 통신 프로파일과 장치 프로파일을 추가한 상위 프로토콜**로, 서로 다른 제조사의 장치가 CAN 버스 위에서 호환되도록 규격화한다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>CANopen이 CAN에 추가하는 것</aside>

- CAN 자체는 전기적 신호와 메시지 중재 방식만 정의하고, 메시지 안에 어떤 의미의 데이터를 담을지는 규정하지 않음
- CANopen은 [[PDO(Process Data Object)]](실시간 프로세스 데이터), SDO(설정용 서비스 데이터), 장치별 표준 프로파일(모터 제어, I/O 등) 등을 추가로 정의해 **의미 있는 데이터 교환 방식**을 표준화함
- 이 덕분에 서로 다른 제조사의 CANopen 지원 모터 드라이버·I/O 모듈을 같은 버스에서 상호 운용 가능

"CANopen은 CAN과 완전히 무관한 별도의 물리 계층·전기 신호 규격이다"라는 서술은 오답이다 — CANopen은 CAN의 물리·데이터링크 계층을 **그대로 사용**하면서, 그 위에 애플리케이션 계층 프로파일을 추가한 것이다.

<aside>로봇 시스템에서의 활용</aside>

여러 축의 로봇 관절 모터 드라이버가 각각 다른 제조사 제품이라도, CANopen의 표준 모션 제어 프로파일을 지원하면 같은 상위 제어기(마스터)가 통일된 방식으로 위치·속도 명령을 내릴 수 있다.

---

<aside>핵심 정리</aside>

- CANopen은 CAN의 물리·데이터링크 계층 위에 표준 통신·장치 프로파일을 추가한 애플리케이션 계층 프로토콜이다
- 서로 다른 제조사 장치 간 상호 운용성을 CAN 자체보다 더 높여준다

---

<aside>관련 노트</aside>

- 원 페이지: [[7. 로봇 제어기 통신 프로토콜 심화]]
- 관련: [[CAN(Controller Area Network)]], [[PDO(Process Data Object)]]
