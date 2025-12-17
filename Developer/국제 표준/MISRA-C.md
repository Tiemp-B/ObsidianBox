---
cssclasses: cornell-note
tags: software-engineering, embedded, safety, misra-c
---

# Summary

MISRA-C는 **자동차 및 임베디드 시스템에서 안전하고 신뢰성 있는 C 코드 작성을 위한 코딩 표준**이다.  
ISO 26262와 함께 사용되어 기능 안전(Functional Safety) 확보를 지원하며, **예측 불가능한 동작·언어 정의되지 않은 행동을 방지**하는 것을 목표로 한다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>MISRA-C 개요</aside>  

MISRA-C(Motor Industry Software Reliability Association – C)는  
1998년 자동차 산업의 소프트웨어 신뢰성 향상을 위해 제정된 **C 언어 사용 가이드라인**이다.  
C 언어의 자유도 높은 문법으로 인해 발생할 수 있는 **버그, 이식성 문제, 예측 불가능한 동작**을 방지하기 위해 만들어졌다.

<aside>주요 버전</aside>  

- **MISRA-C:1998** — 초기 버전, 자동차 제어용 코드 중심  
- **MISRA-C:2004** — 산업 전반으로 확대  
- **MISRA-C:2012 (3rd Edition)** — 현대 C99 표준 반영,  
  "Directive"와 "Rule"을 구분하여 명확한 적용 기준 제시  
- **Amendment 1 (2016)** — C11 호환성과 새로운 규칙 추가  

현재 대부분의 임베디드 개발에서는 **MISRA-C:2012 + Amendment 1**이 표준으로 사용된다.

<aside>규칙 체계</aside>  

MISRA-C는 **총 143개 규칙 + 16개 지침**으로 구성되며,  
각 규칙은 다음 세 가지로 분류된다.

- **Mandatory (필수):** 반드시 준수해야 함  
- **Required (권장):** 특별한 사유 없이는 위반 불가  
- **Advisory (참고):** 가능한 준수 권장  

또한 **Decidable / Undecidable** 기준으로 자동 검사 가능 여부를 구분한다.

<aside>적용 목적</aside>  

1. **안전성 향상:** 예측 불가한 런타임 오류 제거  
2. **이식성 확보:** 하드웨어·컴파일러 종속 코드 최소화  
3. **검증 용이성:** 코드 분석 및 정적 검사 자동화  
4. **품질 관리:** 코드 일관성 유지 및 리뷰 효율 개선  

<aside>주요 제한 예시</aside>  

- 동적 메모리 할당 (`malloc`, `free`) 금지  
- 전역 변수 최소화  
- 암시적 형 변환 금지  
- 포인터 연산 제한  
- 언어 정의되지 않은 동작(`undefined behavior`) 회피  
- 비트 필드·union 남용 금지  
- goto 사용 금지  

이러한 규칙들은 컴파일러·플랫폼 차이에 따른 예측 불가 동작을 방지한다.

<aside>도구 지원</aside>  

정적 분석 도구로 MISRA 규칙 준수 여부를 자동 검증할 수 있다.  
대표 도구:
- Polyspace
- LDRA Testbed
- PC-lint / FlexeLint
- Coverity
- Klocwork
- QAC / Helix QAC  

이 도구들은 위반된 규칙을 분류·보고하여 코드 품질 향상을 돕는다.

<aside>ISO 26262와의 관계</aside>  

MISRA-C는 **ISO 26262 소프트웨어 개발 단계의 품질 및 검증 요구사항을 충족하기 위한 실질적 수단**으로 활용된다.  
즉, ISO 26262이 “무엇을 해야 하는가”를 정의한다면,  
MISRA-C는 “어떻게 구현해야 하는가”를 정의한다.

<aside>적용 절차</aside>  

1. 프로젝트별 **Deviation Plan** 수립 (허용 예외 명시)  
2. 코드 작성 시 MISRA 규칙 준수  
3. 정적 분석 도구를 통한 자동 검증  
4. 코드 리뷰와 품질 승인 단계에서 검토  
5. 위반 규칙에 대한 근거 문서화 및 승인  

<aside>핵심 요약</aside>  

- MISRA-C는 **C 코드의 안전성과 일관성을 확보하기 위한 표준 규칙 집합**  
- ISO 26262 등 안전 표준의 **소프트웨어 구현 측면 지원 도구**  
- 정적 분석 도구와 함께 사용하여 품질을 정량적으로 검증  
- 임베디드 시스템, 항공, 의료기기 등 다양한 산업에서 사용되고 있다
