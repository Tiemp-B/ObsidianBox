---
cssclasses: cornell-note
tags:
  - semiconductor
  - automation
  - secs
  - gem
  - fab
  - communication
---

# Summary

SECS/GEM은 반도체 팹에서 **장비와 상위 호스트 시스템 간 통신 및 자동화를 표준화**한 SEMI 국제 표준이다.  
SECS는 통신 프로토콜의 기반을 정의하고, GEM은 이를 확장해 장비 자동 운용·모니터링·제어를 가능하게 한다.  
무인 자동화 팹(Smart Fab)의 핵심 인프라다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>SECS/GEM 개요</aside>

SECS/GEM은 SEMI에서 제정한 **반도체 장비 자동화 통신 표준**이다.  
장비(Equipment)와 팹 상위 시스템(Host, MES) 간의  
상태 보고, 명령 전달, 데이터 수집을 표준 방식으로 수행한다.

구성 관계:  
- **SECS**: 통신 프로토콜의 기본 규칙  
- **GEM**: SECS 위에서 장비 자동화를 구현하는 운영 표준  

즉, SECS는 “어떻게 통신할 것인가”,  
GEM은 “무엇을 자동화할 것인가”를 정의한다.

<aside>SECS (SEMI Equipment Communication Standard)</aside>

SECS는 장비–호스트 간 데이터 교환 규격이다.

구성 요소:  
- **SECS-I (SEMI E5)**  
  - RS-232 기반 직렬 통신  
  - 저속, 단거리  
- **HSMS (SEMI E37, SECS-II over TCP/IP)**  
  - Ethernet 기반  
  - 고속, 장거리  
  - 현대 팹의 사실상 표준  

데이터 구조는 **SECS-II 메시지** 형식을 사용한다.

<aside>SECS-II 메시지 구조</aside>

SECS-II는 계층적 메시지 구조를 가진다.

- **Stream (S)**: 기능 영역  
- **Function (F)**: 구체적 명령/응답  

예시:  
- S1F1: 장비 상태 요청  
- S1F2: 장비 상태 응답  
- S6F11: 이벤트 보고  

모든 장비와 호스트는 동일한 S/F 규칙을 따른다.

<aside>GEM (Generic Equipment Model)</aside>

GEM(SEMI E30)은 SECS 기반 **장비 자동화 동작 모델**이다.  
GEM을 구현한 장비는 “GEM-compliant” 장비로 분류된다.

GEM이 정의하는 핵심 기능:  
- 장비 상태(State Model)  
- 이벤트(Event) 보고  
- 알람(Alarm) 관리  
- 원격 명령(Remote Command)  
- 변수(Variable) 수집  
- 레시피 관리(Recipe Management)

<aside>장비 상태 모델</aside>

GEM은 장비 상태를 표준 상태로 정의한다.

대표 상태:  
- OFFLINE  
- ONLINE  
- IDLE  
- RUN  
- ALARM  

이를 통해 MES는 장비 상태를 일관되게 인식하고 제어할 수 있다.

<aside>이벤트와 알람</aside>

- **Event**: 공정 시작, 종료, 웨이퍼 로딩 등 정상 동작 보고  
- **Alarm**: 장비 이상, 인터락, 공정 오류 보고  

S6F11(Event Report)을 통해 실시간 모니터링이 가능하다.

<aside>레시피 및 공정 제어</aside>

GEM은 레시피 다운로드/업로드, 선택, 실행을 표준화한다.

- 공정 조건 중앙 관리  
- 장비 간 레시피 일관성 확보  
- 휴먼 에러 감소  

이는 대량 생산 환경에서 필수 기능이다.

<aside>SECS/GEM의 역할</aside>

- 무인 자동화 팹 구현  
- 장비 벤더 간 통합  
- 실시간 공정 모니터링  
- 생산 이력 및 트레이서빌리티 확보  
- 스마트 팹·AI 공정 제어 기반 제공  

SECS/GEM 없이는 대규모 반도체 팹 운영이 불가능하다.

<aside>SECS/GEM과 SEMI 표준 연계</aside>

- E5 / E37: 통신 계층  
- E30: GEM  
- E40: Process Job Management  
- E87: Carrier Management  
- E90: Substrate Tracking  
- E94: Control Job Management  

이 표준들이 결합되어 **완전 자동화 팹**을 구성한다.

<aside>핵심 정리</aside>

- SECS는 장비–호스트 통신 규약  
- GEM은 장비 자동화 동작 모델  
- HSMS(TCP/IP)가 현대 팹 표준  
- 이벤트·알람·레시피·상태 관리 제공  
- 스마트 팹·무인 자동화의 핵심 국제 표준

--