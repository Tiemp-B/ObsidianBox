---
cssclasses: cornell-note
tags: [통신, 네트워크, 용어]
---

# Summary

장치들을 연결하는 형상(topology). 버스·데이지 체인·스타·링·트리·메시 등이 있으며, 형상에 따라 배선량·확장성·내결함성·신호 반사 특성이 달라진다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>형상 비교도</aside>

![[네트워크 토폴로지.excalidraw]]

<aside>버스 (Bus)</aside>

- 하나의 공용 간선에 모든 장치를 연결
- 배선이 단순·저렴하나 간선 장애 시 전체 영향, 양 끝에 [[종단 저항(Termination Resistor)|종단 저항]] 필요
- 예: [[Developer/통신/직렬 통신/RS-485|RS-485]], [[CAN(Controller Area Network)|CAN]]

<aside>데이지 체인 (Daisy Chain)</aside>

- 장치를 **한 줄로 이어서** 연결(A–B–C–D), 각 장치가 다음 장치로 신호를 넘김
- 버스를 노드마다 짧은 분기 없이 **노드→노드로 직렬 연결**한 형태 → 스터브(분기)가 짧아 반사에 유리
- 끝단 노드에 종단 저항, 중간 노드는 통과
- 예: RS-485 멀티드롭, SPI 데이지 체인

<aside>스타 (Star)</aside>

- 중앙 허브/스위치에 각 장치가 개별 연결
- 한 장치 장애의 영향이 작음, 대신 허브 장애에 취약
- 예: 이더넷 스위치, USB 허브

<aside>링 (Ring)</aside>

- 장치를 고리 모양으로 연결, 신호가 순환
- 예: 토큰 링, [[EtherCAT]](논리적 링)

<aside>트리·메시 (Tree·Mesh)</aside>

- **트리**: 계층적으로 가지치기(스타의 확장)
- **메시**: 다수 노드가 서로 다중 경로로 연결 → 내결함성 높음(무선 메시 등)

---

<aside>핵심 정리</aside>

- 토폴로지 = 연결 형상; 버스/데이지체인은 배선이 적고 종단저항이 중요, 스타는 허브 집중, 메시는 내결함성↑
- 데이지 체인 = 버스를 노드→노드 직렬로 이은 형태(스터브 최소화)

---

<aside>관련 노트</aside>

- 종단: [[종단 저항(Termination Resistor)]]
- 사용 예: [[Developer/통신/직렬 통신/RS-485|RS-485]] · [[CAN(Controller Area Network)]]
