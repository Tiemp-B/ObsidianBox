# 컴파일러 & 언어 처리

**분류:** 컴퓨터 과학 - 컴파일러 & 언어 처리

---

## 개요

컴파일러는 고급 언어를 기계어로 번역하는 시스템이다.  
언어 처리기는 어휘 분석부터 코드 최적화까지 프로그램 실행 과정을 담당한다.

## 주요 개념

### 컴파일러 단계
1. **어휘 분석 (Lexical Analysis)**
   - 토큰화
   - 정규 표현식

2. **구문 분석 (Syntax Analysis)**
   - 파싱 (Parsing)
   - 문법 트리 생성

3. **의미 분석 (Semantic Analysis)**
   - 타입 검사
   - 심볼 테이블

4. **중간 코드 생성 (IR)**
   - 추상 구문 트리 (AST)
   - 중간 표현

5. **최적화 (Optimization)**
   - 코드 최적화
   - 데드 코드 제거

6. **코드 생성 (Code Generation)**
   - 어셈블리 생성
   - 기계어 변환

### 주요 기술
- 가비지 컬렉션 (Garbage Collection)
- 링킹 (Linking)
- 런타임 관리

### 응용
- 인터프리터
- JIT (Just-In-Time) 컴파일
- LLVM
- WebAssembly (WASM)
- DSL (Domain Specific Language)

---

## 학습 자료

- [ ] 컴파일러 구조
- [ ] 어휘/구문 분석
- [ ] 파싱 알고리즘
- [ ] 코드 최적화
- [ ] LLVM 기초
