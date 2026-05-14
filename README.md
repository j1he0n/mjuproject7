# mjuproject7

E-Commerce 생필품 물가 변동 모니터링 및 데이터 파이프라인 구축빅데이터 프로그래밍 기말 프로젝트 (11주차: 프로젝트 제안 및 아키텍처 정의)  


1. 문제 정의 (Problem Definition)
- 분석 배경: 온라인 쇼핑 플랫폼의 가격 변동은 실시간으로 발생하며, 소비자 물가에 직결되는 생필품의 경우 그 변동 폭과 패턴을 분석하는 것이 중요합니다. -
- 해결 과제: 단일 플랫폼의 가격 확인을 넘어, 여러 플랫폼의 대량 데이터를 주기적으로 수집하고 Hadoop 생태계를 통해 분산 처리함으로써 물가 변동 인사이트를 도출합니다.
- 데이터 수집 계획:
  - 출처: 네이버 쇼핑 API 및 주요 커머스 사이트 (생수, 라면, 화장지 등 주요 생필품 카테고리).
  - 규모: 일 단위 자동 수집 스크립트를 통해 누적 100MB 이상의 데이터를 확보합니다.
  - 형태: JSON 또는 CSV 포맷으로 수집하여 HDFS에 적재합니다.

2. 기술 스택 (Tech Stack)
  - Language: Python 3.x
  - Ingestion: BeautifulSoup (웹 크롤링), Requests (API 호출)
  - Storage: Apache Hadoop HDFS
  - Processing: Apache Spark (Main), Apache Hive (Batch Analysis)
  -  Analysis: Spark SQL 및 HiveQL을 활용한 대량 데이터 집계
  -  Visualization: Matplotlib, Seaborn

 3. 구현 계획 (Pipeline Strategy)
  - Data Collection: Python 기반 수집 스크립트를 작성하여 HDP Sandbox 환경에서 정기적으로 실행하고 Raw 데이터를 수집합니다.
  -  Data Ingestion & Storage: 수집된 데이터를 HDFS의 /user/data/raw 경로에 저장하고 파티셔닝을 수행합니다.
  -  Data Preprocessing: Spark를 사용하여 중복 제거, 결측치 처리, 가격 데이터 타입 변환(Int) 등 전처리를 수행합니다.
  -   Core Analysis: 다음 3가지 핵심 질문에 대한 답을 도출합니다.
     Q1: 주차별/월별 생필품 평균 가격 변동 추이는 어떠한가?
     Q2: 플랫폼별 특정 브랜드의 가격 차이와 최저가 유지 비율은 어떠한가?
     Q3: 요일별 할인 정책(주말 vs 평일)에 따른 가격 변동 상관관계가 존재하는가?

 
 4. GitHub Repository
구조
Plaintext<repo-name>/
├── README.md       # 프로젝트 개요 및 실행 가이드
├── data/           # 샘플 데이터 (100~1000줄)
├── src/            # 소스 코드 폴더
│   ├── ingest/     # 수집 스크립트 (Python)
│   ├── pipeline/   # Spark 처리 로직
│   └── analyze/    # Hive 쿼리 및 분석 코드
└── reports/        # 최종 보고서 및 시각화 결과물



  7. AI Tool UsageGemini 3 Flash: 프로젝트 주제 선정 보조, 시스템 아키텍처 설계 가이드라인 작성 및 README.md 초안 구성.   
