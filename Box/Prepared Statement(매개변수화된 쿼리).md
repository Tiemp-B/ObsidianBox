---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 보안
---

# Summary

Prepared Statement(매개변수화된 쿼리)는 SQL 쿼리의 구조(명령어)와 사용자 입력값을 **명확히 분리**해 전달하는 방식으로, 입력값이 쿼리 구조 자체를 바꾸지 못하게 해 [[SQL Injection]]을 막는 핵심 방어 기법이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Prepared Statement가 SQL Injection을 막는 원리</aside>

- 문자열을 그대로 이어붙여 쿼리를 만드는 방식은 사용자 입력에 SQL 문법(따옴표, 세미콜론 등)이 섞이면 쿼리 구조 자체가 바뀌어버릴 위험이 있음
- Prepared Statement는 쿼리 구조(`SELECT * FROM users WHERE id = ?` 같은 틀)를 먼저 DB에 전달해 확정하고, 사용자 입력값은 **오직 데이터로만** `?` 자리에 바인딩됨
- 입력값에 SQL 문법이 섞여 있어도 데이터로만 취급되므로 쿼리 구조를 변경할 수 없음

<aside>웹 애플리케이션 취약점 대응에서의 위치</aside>

[[SQL Injection]]은 대표적인 웹 애플리케이션 취약점 중 하나이며, Prepared Statement는 이에 대한 가장 근본적이고 표준적인 방어책으로 꼽힌다 — 문자열 이어붙이기로 쿼리를 만드는 관행 자체를 없애는 것이 핵심이다.

---

<aside>핵심 정리</aside>

- Prepared Statement는 쿼리 구조와 사용자 입력값을 분리해 전달함으로써 SQL Injection을 막는 기법이다
- 입력값을 필터링·이스케이프하는 방식이 아니라, 애초에 데이터로만 취급되게 하는 방식이다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 웹 애플리케이션 취약점]]
- 관련: [[SQL Injection]]
