---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 보안
---

# Summary

SQL Injection은 사용자 입력값에 **SQL 문법을 몰래 삽입**해, 원래 의도하지 않은 쿼리를 데이터베이스가 실행하도록 만드는 대표적인 웹 애플리케이션 취약점이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>SQL Injection의 동작 원리</aside>

- 사용자 입력을 검증 없이 SQL 쿼리 문자열에 그대로 이어붙이면, 입력값에 포함된 따옴표·세미콜론 등이 **쿼리의 구조 자체를 바꿔버릴** 수 있음
- 예를 들어 로그인 폼의 아이디 입력란에 `' OR '1'='1`을 넣으면, 조건문이 항상 참이 되어 인증을 우회할 수 있음
- 이렇게 조작된 쿼리로 인증 우회, 데이터 유출, 데이터 변조·삭제까지 가능해짐

"SQL Injection은 서버의 네트워크 대역폭을 소진시켜 서비스를 마비시키는 공격이다"라는 서술은 오답이다 — SQL Injection의 핵심은 대역폭 소진(가용성 공격)이 아니라 **입력값으로 쿼리 구조 자체를 조작**해 인증 우회·데이터 유출·변조를 일으키는 것이다.

<aside>방어 기법과의 관계</aside>

[[Prepared Statement(매개변수화된 쿼리)]]는 쿼리 구조와 입력값을 분리해 전달함으로써 SQL Injection을 근본적으로 방지하는 표준적인 대응책이다.

---

<aside>핵심 정리</aside>

- SQL Injection은 사용자 입력에 SQL 문법을 삽입해 쿼리 구조를 조작하는 취약점이다
- 대역폭 소진 공격이 아니라 인증 우회·데이터 유출·변조를 목표로 한다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 웹 애플리케이션 취약점]]
- 관련: [[Prepared Statement(매개변수화된 쿼리)]], [[XSS(Cross-Site Scripting)]]
