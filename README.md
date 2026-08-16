Jae Hyeong Kim, Backend Developer
---

## 📞 Contacts
- Email: kkuldangi2@gmail.com
- LinkedIn: [LinkedIn/김재형](https://www.linkedin.com/in/%EC%9E%AC%ED%98%95-%EA%B9%80-b75920345/)
- Velog: [velog.io/@KJH](https://velog.io/@kkuldangi3/posts)

## About

Java와 Spring 기반의 백엔드 시스템을 설계하고, 검색 성능과 데이터 정합성을 개선해 왔습니다.
AI의 판단을 권한·멱등성·상태 전이 같은 백엔드 규칙 안에서 안전하게 연결하는 일에 관심이 있습니다.

- Elasticsearch와 Redis를 활용해 로컬 캐시 히트 경로의 검색 응답을 최대 5~7초에서 평균 0.8ms 수준으로 개선했습니다.
- 1GB 약품 데이터를 전처리하고 GPT Batch API를 적용해 예상 LLM 변환 비용을 약 $200에서 실제 $11.18로 줄였습니다.
- Kafka와 transactional outbox를 활용해 장시간 AI 작업을 비동기화하고, 중복·역전된 결과가 최신 상태를 덮어쓰지 않도록 설계했습니다.

## Core Skills

- Primary: Java
- Backend: Spring Boot, REST API, Spring Security, JUnit 5
- Data & Messaging: PostgreSQL, MySQL, Redis, Elasticsearch, Kafka
- Infra: Docker, Docker Compose, AWS EC2, GitHub Actions
- Project Technologies: Python, FastAPI, Spring AI, RAG, OpenAI API, Vector DB


## Projects

### Fruition — LLM Wiki에서 착안한 문서 생성·정리 업무를 돕고 지식을 쌓아주는 AI Agent 워크스페이스

- Team Project
- Period / Role: 2026.05 ~ / AI 워크플로 설계 및 통합

**Service Boundary Design**

- Problem: 인증·문서·AI 기능이 하나의 서비스와 데이터베이스에 결합되면 변경 범위가 커지고, 장시간 AI 작업의 장애가 핵심 문서 기능으로 전파될 수 있었습니다.
- Solution:
  - 데이터 소유권과 장애 경계를 기준으로 인증·문서·AI 서비스를 독립 배포 단위로 분리했습니다.
  - 서비스 간 직접 DB 참조를 제거하고 내부 API와 Redis projection으로 필요한 데이터만 전달했습니다.
- Result: 서비스별 데이터 소유권과 책임을 명확히 하고, AI 서비스의 지연이나 장애가 문서 서비스로 직접 전파되지 않는 구조를 만들었습니다.

**Asynchronous AI Workflow**

- Problem: 장시간 AI 작업을 동기 요청으로 처리하면 응답 시간이 길어지고, 재시도 과정에서 중복 실행이나 오래된 결과의 역전 반영이 발생할 수 있었습니다.
- Solution:
  - Kafka command/event와 transactional outbox를 적용해 AI 작업을 비동기화했습니다.
  - `document_id`를 메시지 키로 사용해 동일 문서의 처리 순서를 보존하고 서로 다른 문서는 병렬 처리했습니다.
  - receipt·revision·unique constraint를 조합해 at-least-once 전달의 중복과 오래된 결과를 차단했습니다.
- Result: AI worker 중지, 재개 후 backlog가 모두 소비되고 consumer lag가 0으로 복구되는 것을 통합 테스트로 검증했습니다.

**Evidence-Grounded Search and Answer Validation**

- Problem:
  - 사용자가 파일명을 정확히 기억하지 못해도 질문이나 개념만으로 관련 문서를 찾아야 했습니다.
  - LLM이 생성한 답변이 실제 업로드 문서의 어느 내용에 근거하는지도 확인할 수 있어야 했습니다.

- Solution:
  - 업로드 문서를 문서별 요약·근거 페이지와 여러 문서의 공통 개념을 통합한 지식 페이지로 구조화하고, 관련이 있으면 연결하도록 했습니다.
  - BM25와 Embedding 점수를 결합해 질문과 관련된 문서 및 지식 페이지의 순위를 계산했습니다.
  - 검색 결과에서 원본 문서의 근거 문단까지 추적해 답변과 함께 제시하도록 구성했습니다.
  - evaluator가 질문과 근거, 답변의 정합성을 검사하고 기준을 통과하지 못하면 피드백을 반영해 다시 생성하도록 설계했습니다.

- Result:
  - 파일명을 몰라도 개념이나 자연어 질문으로 관련 정보를 탐색할 수 있게 했습니다.
  - 답변과 함께 사용된 원본 문서와 근거 문단을 확인할 수 있도록 했습니다.
  - 근거가 부족한 답변은 제한된 횟수 안에서 재생성하는 검증 흐름을 구축했습니다.


### [Pilltip: 개인맞춤 AI 의약관리 애플리케이션](https://github.com/PillTipKR/Pilltip)

- Team Project
- Period / Role: 2025.03 ~ 2025.12 / Backend/AI Developer
- Stack: Spring Boot, MySQL, Weaviate, Elasticsearch, Redis, Docker Compose, Spring AI, GPT Batch API, FCM

**Search Performance Optimization**

- Problem:
    - `LIKE '%keyword%'` 검색과 사용자 맞춤 DUR 판단을 위한 다중 JOIN으로 인해 로컬 Postman 측정 기준 최대 5~7초의 응답 지연이 발생했습니다.

- Solution:
    - RDBMS의 약품 데이터를 Elasticsearch로 동기화하는 `DataSync` 파이프라인을 구축했습니다.
    - Provider 패턴과 Initializer를 적용해 N-gram·Edge N-gram 기반 인덱스 매핑과 생명주기를 애플리케이션에서 관리했습니다.
    - DUR 판정 결과를 Redis에 `{type}:DUR:{durType}:{drugId}` 형식으로 캐싱해 검색 결과 반환 시 반복적인 DB JOIN 없이 태깅할 수 있도록 설계했습니다.

- Result:
    - 검색 경로에서 다중 JOIN과 반복적인 DUR 조회를 제거했습니다.
    - 로컬 Postman 측정 기준, 캐시 히트 경로의 평균 응답 시간을 최대 5~7초에서 약 0.8ms 수준으로 단축했습니다.

**LLM Cost Optimization**

- Problem: 1GB 규모의 약품 데이터 변환에 약 `$200`의 LLM 비용이 예상되었습니다.
- Solution:
  - 정규표현식 기반 데이터 클리닝을 수행했습니다.
  - 문장을 block 단위로 보고 fuzzy matching과 사전 기반 어미 처리를 적용했습니다.
  - 샘플 분석으로 약 70% 중복률을 확인하고, 팀을 설득해 1주일의 전처리 시간을 확보했습니다.
  - GPT Batch API를 적용해 비실시간 대량 변환 비용을 추가 절감했습니다.
- Result: 변환 대상 데이터를 `1GB -> 326MB`로 줄이고, 비용을 `$200 -> $11.18`로 낮췄습니다.

**RAG Architecture**

- Problem: 사용자 증상과 약품 효능을 의미 기반으로 연결해야 했지만, 임신 여부·복용약·기저질환 같은 민감 정보를 외부 LLM에 전달해서는 안 됐습니다.
- Solution:
  - 약품 효능 정보를 Vector DB에 임베딩하고 사용자 증상과 유사도 기반으로 매핑하는 RAG 흐름을 구성했습니다.
  - 외부 LLM에는 자연어 증상만 전달하고 민감 정보에 따른 DUR 판단은 내부 코드에서 수행하도록 책임을 분리했습니다.
- Result: 의미 기반 약품 정보 탐색을 유지하면서 민감 정보가 외부 LLM 호출 범위를 벗어나지 않도록 제한했습니다.


## Open Source Contribution

### [Rhwp](https://github.com/edwardkim/rhwp)
- Period: 2026.04 ~ 2026.06

Rust 기반 HWP/HWPX 라이브러리에서 이슈 분석, 수정 계획, PR 작성, 테스트와 CI 대응을 수행했습니다.

- 기존 코드와 테스트를 추적해 HWP/HWPX 라이브러리 이슈 7건을 재현 및 분석하고 [PR 7건](https://github.com/edwardkim/rhwp/pulls?q=is%3Apr+author%3AMartinel2) 기여

## Activities
- AWS Skill Builder·AWS Training 과정 이수 · 2026.06 ~ 2026.07
  - AWS Cloud Practitioner Essentials
  - Machine Learning Engineering on AWS (3일)
  - Developing Generative AI Applications on AWS (2일)
- 부산대학교 APPTIVE Backend Mentor · 2025.03 ~ 2026.01
  - 멘티 12명을 대상으로 REST API·DB 교육 6회와 코드 리뷰를 진행했습니다.
  - 전체 멘토링 완주율 94%를 달성하고 공로상을 수상했습니다.
- SK Summit 2025 부산대학교 대표 전시 부스 운영 / 2025.11
- 정보처리기사 취득 / 2025.09
- K-ICT Week in Busan 부산대학교 대표 전시 부스 운영 / 2025.07

## 🏆 Awards
* 부산대학교 정보컴퓨터공학부 졸업과제 SW/AI 분과 / 금상 / 2025.10.01 / 부산대학교 의생명공학대학
* AI커리어스쿨 창업톤(L:AUNCH) / 장려상 / 2025.09.28 / Root Impact x Google.org
* 부산 DATA WEEK - 데이터 활용 우수사례 공모전 / 최우수상 / 2025.09.23 / 부산테크노파크
* 2025 SW 중심대학 디지털 경진대회 SW부문/ 후원기업상(딥노이드) / 2025.08.12 / SW중심대학협의회


## 📖 Education
### 부산대학교 학사 (2022.03 ~ 2026.02)
- 정보컴퓨터공학
- GPA : 4.12 / 4.5 (최우등 졸업)

### 대구대학교 중퇴 (2019.03 ~ 2022.02)
- 컴퓨터공학부
- GPA : 4.2 / 4.5 

## 💡 PS

![Solved.ac Profile](http://mazassumnida.wtf/api/v2/generate_badge?boj=kkuldangi3)


