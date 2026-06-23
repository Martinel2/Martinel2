Jae Hyeong Kim, Backend Developer
---

## 📞 Contacts
- Email: kkuldangi3@naver.com
- GitHub: [github.com/Martinel2](https://github.com/Martinel2)
- Velog: [velog.io/@kkuldangi3](https://velog.io/@kkuldangi3/posts)

## About

저는 시스템을 안정화하고 이를 기록하려 노력하는 개발자입니다!

- 1GB 규모의 약품 데이터를 전처리하고 문장 블록화, 정규표현식, GPT Batch API를 적용해 LLM 변환 비용을 약 `$200`에서 `$11.18`로 줄였습니다.
- Elasticsearch와 Redis를 함께 사용해 약품 검색 응답 시간을 로컬 기준 최대 `5~7초`에서 `0.8ms` 수준으로 개선했습니다.
- AI가 할 일과 코드가 보장할 일을 분리해, LLM/RAG 기능을 검증 가능한 백엔드 구조 안에 배치하는 데 관심이 있습니다.


## ⚙ Tech Stack 

### Backend

`Spring Boot` `Spring Security` `JUnit5` `Spring AI`

### Database / Search / Cache

`MySQL` `Elasticsearch` `Redis` `Milvus` `Weaviate`

### DevOps / Infra

`AWS EC2` `Azure` `Docker` `Docker Compose` `GitHub Actions` `Nginx`

### AI / Automation

`OpenAI API` `GPT Batch API` `RAG` `Vector DB` `Firebase Cloud Messaging`


## Projects
### [Pilltip: 개인맞춤 AI 의약관리 애플리케이션](https://github.com/PillTipKR/Pilltip)

- Period / Role: 2025.03 ~ 2025.12 / Backend/AI Developer
- Stack: Spring Boot, MySQL, Weaviate, Elasticsearch, Redis, Docker Compose, Spring AI, GPT Batch API, FCM

**Search Performance Optimization**

- Problem: `LIKE %keyword%` 검색과 사용자 맞춤 DUR 판단을 위한 다중 JOIN으로 로컬 Postman 기준 5~7초 이상의 응답 지연이 발생했습니다.
- Solution:
  - RDBMS 데이터를 Elasticsearch로 이관하는 `DataSync` 파이프라인을 구축했습니다.
  - Provider 패턴과 Initializer를 사용해 N-gram, Edge N-gram 기반 인덱스 매핑과 생명주기를 애플리케이션에서 제어했습니다.
  - DUR 태깅 결과를 Redis에 `{type}:DUR:{DUR_type}:{drugId}` 형태로 캐싱해 검색 결과 반환 시 O(1)에 가깝게 태깅되도록 설계했습니다.
- Result: DB 커넥션 병목을 줄이고 검색 응답 시간을 최대 7초 수준에서 0.8ms 수준으로 단축했습니다.

**LLM Cost Optimization**

- Problem: 1GB 규모의 약품 데이터 변환에 약 `$200`의 LLM 비용이 예상되었습니다.
- Solution:
  - 정규표현식 기반 데이터 클리닝을 수행했습니다.
  - 문장을 block 단위로 보고 fuzzy matching과 사전 기반 어미 처리를 적용했습니다.
  - 샘플 분석으로 약 70% 중복률을 확인하고, 팀을 설득해 1주일의 전처리 시간을 확보했습니다.
  - GPT Batch API를 적용해 비실시간 대량 변환 비용을 추가 절감했습니다.
- Result: 변환 대상 데이터를 `1GB -> 326MB`로 줄이고, 비용을 `$200 -> $11.18`로 낮췄습니다.

**RAG Architecture**

- Weaviate에 약품 효능 정보를 임베딩하고 사용자 증상과 유사도 기반으로 매핑하는 구조를 설계했습니다.
- 임신 여부, 복용 중인 약, 기저질환 등 민감 정보는 외부 LLM에 넘기지 않는 방향으로 AI 호출 범위를 제한했습니다.


## Open Source Contribution

### [Rhwp](https://github.com/edwardkim/rhwp)
- Period: 2025.04 ~ 

Rust 기반 HWP/HWPX 라이브러리에서 이슈 분석, 수정 계획, PR 작성, 테스트와 CI 대응을 수행했습니다.

- Issues: [#1188](https://github.com/edwardkim/rhwp/issues/1188), [#1244](https://github.com/edwardkim/rhwp/issues/1244), [#1267](https://github.com/edwardkim/rhwp/issues/1267), [#1289](https://github.com/edwardkim/rhwp/issues/1289), [#1298](https://github.com/edwardkim/rhwp/issues/1298), [#1321](https://github.com/edwardkim/rhwp/issues/1321), [#1350](https://github.com/edwardkim/rhwp/issues/1350)
- Pull Requests: [#1213](https://github.com/edwardkim/rhwp/pull/1213), [#1265](https://github.com/edwardkim/rhwp/pull/1265), [#1272](https://github.com/edwardkim/rhwp/pull/1272), [#1290](https://github.com/edwardkim/rhwp/pull/1290), [#1299](https://github.com/edwardkim/rhwp/pull/1299), [#1324](https://github.com/edwardkim/rhwp/pull/1324), [#1351](https://github.com/edwardkim/rhwp/pull/1351)

## Activities

- 부산대학교 APPTIVE Backend 멘토 / 2025.03 ~ 2026.01
  - REST API, DB 등 백엔드 기초 지식 공유
  - 코드 리뷰 수행
  - 동아리 내 공로상 수상
- SK Summit 2025 부산대학교 대표 전시 부스 운영 / 2025.11
- K-ICT Week in Busan 부산대학교 대표 전시 부스 운영 / 2025.07
- 정보처리기사 취득 / 2025.09

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


