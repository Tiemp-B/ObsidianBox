---
cssclasses: cornell-note
tags: [로봇소프트웨어개발기사, 자료조사]
---

# 조사 - HadoopvsSpark (2026-08-07)

개요(허브) 링크 정상. 문제은행 3문항(OROCOS컴포넌트/프레임워크목적/빅데이터분산처리프레임워크) 전부 기존 페이지 커버 확인.

## Phase 1 — 조사

### Hadoop vs Spark — 디스크 기반 vs 인메모리 처리 (신규)
- 기존 페이지2는 "Apache Hadoop, Apache Spark" 같은 빅데이터 분산 처리 프레임워크를 이름만 나열하고, 둘의 차이는 다루지 않았음
- **Hadoop(MapReduce)**: 각 연산 단계(Map/Reduce) 결과를 **디스크(HDFS)에 다시 기록**하며 처리 — 안정적이지만 디스크 입출력으로 인한 지연이 큼
- **Spark**: 중간 결과를 **메모리(RAM)에 유지**한 채 여러 연산을 이어서 처리 — 디스크 입출력을 최소화해 반복 연산(예: 센서 로그를 여러 번 훑는 분석)에서 Hadoop보다 훨씬 빠름
- 로봇 다수의 센서 로그를 실시간에 가깝게 반복 분석해야 하는 경우는 Spark가, 대용량 로그를 안정적으로 배치 처리하면 되는 경우는 Hadoop이 적합
- 출처: [Hadoop vs. Spark: What's the Difference? - IBM](https://www.ibm.com/think/insights/hadoop-vs-spark), [Hadoop vs Spark - AWS](https://aws.amazon.com/compare/the-difference-between-hadoop-vs-spark/)

## Phase 2 — 자체 검토

- 성능 배수("100배 빠름" 등) 수치는 조건에 따라 편차가 커서 페이지 본문에는 반영하지 않고, "디스크 vs 메모리"라는 구조적 차이와 그로 인한 반복 연산 성능 차이만 정성적으로 반영(§2 원칙)
- RDD 등 Spark 내부 자료구조 세부사항까지는 넣지 않음

## Phase 3 — 결론

1개 페이지(2. 프레임워크의 목적과 OROCOS)에 신규 개념 1건(Hadoop vs Spark) 반영. Box 용어는 `Hadoop과 Spark(디스크 기반·인메모리 분산 처리)` 신규 생성.
