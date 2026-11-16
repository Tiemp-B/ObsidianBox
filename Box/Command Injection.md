---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 보안
---

# Summary

Command Injection(OS 커맨드 인젝션)은 사용자 입력값이 검증 없이 **OS 셸 명령어의 일부로 실행**되어, 공격자가 서버에서 임의의 시스템 명령을 실행할 수 있게 되는 취약점이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Command Injection의 동작 방식</aside>

- 애플리케이션이 사용자 입력을 그대로 셸 명령어 문자열에 이어붙여 실행할 때, 입력값에 `;`, `|`, `&&` 같은 셸 제어 문자를 삽입하면 원래 의도하지 않은 **추가 명령**이 함께 실행됨
- 이렇게 실행된 명령으로 서버의 파일을 읽거나, 시스템 설정을 변경하거나, 추가 악성 프로그램을 실행시킬 수 있음

<aside>SQL Injection과의 관계</aside>

대상이 데이터베이스 쿼리(SQL)가 아니라 OS 셸 명령이라는 점만 다를 뿐, "**입력값이 코드로 해석되어 실행**된다"는 근본 원리는 [[SQL Injection]]과 동일하다.

---

<aside>핵심 정리</aside>

- Command Injection은 사용자 입력이 OS 셸 명령의 일부로 실행되는 취약점이다
- 인자를 분리해 전달하는 API 사용, 화이트리스트 검증이 기본 방어책이다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 웹 애플리케이션 취약점]]
- 관련: [[SQL Injection]]
