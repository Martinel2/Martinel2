# 김재형 | Backend & AI Application Developer

실패의 원인을 깊이 파고들어 해결하는 것을 좋아하는 개발자

RAG 근거 충족률을 66.25%에서 91.25%로, AI 문서 편집 품질을 82.5%에서 91.2%로 높이며, AI가 틀린 근거로 답하거나 사용자 문서를 함부로 바꾸지 않도록 평가, 승인, 복구 구조를 설계해 온 AI 애플리케이션 개발자입니다. 새 방법을 찾기 전에 지금 무엇이 문제인지부터 파고들고, 정확도·비용·응답 시간을 평가로 확인한 뒤 서비스에 맞는 구현을 고릅니다.

[소개](https://martinel2.github.io/?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=header-intro) · [포트폴리오](https://martinel2.github.io/portfolio.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=header-portfolio) · [블로그](https://velog.io/@kkuldangi3/posts) · [LinkedIn](https://www.linkedin.com/in/%EC%9E%AC%ED%98%95-%EA%B9%80-b75920345/)

**Email**: kkuldangi2@gmail.com

## 주요 경험

- **[RAG 근거 선택: 근거 충족률 66.25% → 91.25%](https://martinel2.github.io/portfolio.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=exp-jev#fruition-jev-evidence)** — 근거가 틀리면 답변 전체를 믿을 수 없는 서비스라, 근거를 고르는 단계를 판단 전용 모델 Jev로 교체했습니다. GPT로 고르면 비용·시간이 크고 검색 가중치 조정은 개선 폭이 작았기 때문입니다. 동일 후보·블라인드 교차 채점으로 비교했고, 후보 수와 병렬 수(4·6·8·10 비교)를 조정해 선택 시간 중앙값을 9.090초 → 1.137초로 줄였습니다.
- **[에이전트 실행 환경: 편집 품질 82.5% → 91.2%(114건 평가)](https://martinel2.github.io/portfolio.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=exp-agent#fruition-agent)** — AI가 문서를 함부로 바꾸면 서비스를 믿고 맡길 수 없어, 권한·프롬프트 주입 검사는 코드가, 지침과 수정안은 AI가, 게시와 반영은 사용자가 맡도록 나눴습니다. 코드 검사만으로는 요청 누락을 못 잡아 의미 평가 후 한 번만 다시 쓰게 했고, 사용자가 승인하기 전에는 문서를 바꾸지 않습니다.
- **[데이터 파이프라인: PDF 변환 통과율 45.17% → 89.89%, 약품 변환 비용 예상 $200 대비 $11.18](https://martinel2.github.io/portfolio.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=exp-pdf#fruition-document)** — 논문의 표·수식이 깨지면 답변 근거가 되는 수치를 쓸 수 없어, 본문은 빠른 AnyDoc으로 추출하고 표·수식은 원본 영역을 따로 판독했습니다. 약품 데이터는 같은 문장을 한 번만 변환하고, 실시간 응답이 필요 없는 작업이라 Batch API로 약 4만 4천 건을 예산 안에서 처리했습니다.

수치는 모두 내부 평가 기준입니다.

## 기술

- **Backend:** Java · Spring Boot · Python
- **AI:** LangChain · LangGraph · Spring AI · RAG · LangSmith · LLM Evaluation · LLM Guardrail
- **Data / Infra:** MySQL · PostgreSQL · Redis · Elasticsearch · Weaviate · Kafka / Docker · Docker Compose · GitHub Actions

## 프로젝트

### Fruition | 문서를 지식으로 쌓고 활용하는 AI 워크스페이스

[GitHub · AI 저장소](https://github.com/FruitionKR/Fruition-ai) · [상세 경험](https://martinel2.github.io/portfolio.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=fruition-detail#fruition-document)

2026.04 — 현재 · AI SW 마에스트로 17기 · 팀 프로젝트 (3명 + 디자이너) · **AI 파트 리드**

- **시작 계기:** 팀원이 제기한 문서 관리의 불편함을 디자인 싱킹으로 구체화했습니다. 문서를 저장만 해 두고 정작 필요할 때 찾지 못하는 문제를 풀고자 했습니다.
- **팀 구성:** 본인(AI 기능 전체), 백엔드 1명(Spring 백엔드 전체), 프론트엔드·DevOps 1명(프론트엔드, MSA 기반 AWS 배포), 외주 디자이너 · 멘토 3명(Gen AI 품질·평가 / 백엔드 / 마일스톤·MSA 설계·문서화)
- MSA의 초기 설계를 제안하고 팀원·멘토와 논의해 최종 구조를 함께 완성했습니다.

<img src="https://martinel2.github.io/assets/projects/fruition-system-architecture.jpg" alt="Fruition 시스템 아키텍처" width="720">

**주요 개발**

- **답변 근거 선택**
  - 문제: 문서 근거로 답하는 서비스에서 기존 검색이 근거를 놓치거나 답 없는 질문에도 근거를 붙여 답변 신뢰도가 흔들림.
  - 판단: GPT 선택은 비용(약 2.5배)·시간 부담, 가중치·RRF 조정은 여러 값을 실험해도 점수가 비슷해, 요청 분류에서 먼저 검증한 Jev(정답 77 → 81/98건) 채택.
  - 해결: 벤치마크상 한국어 의미 검색이 가장 좋은 BGE-M3와 정확한 용어를 잡는 BM25로 후보를 모으고 Jev가 최종 근거를 고르는 2단계 구조. 후보를 300개로 줄이고 병렬 4·6·8·10을 비교해 정확도 차이 없이 8병렬로 조정.
  - 성과: 답이 있는 80문항의 근거 충족률 66.25% → 91.25%. 선택 시간 중앙값 9.090초 → 1.137초(기존 0.431초보다 느림). 문서 기반 답변을 근거째 믿고 쓸 수 있게 함.
- **사용자 정의 작업 지침(Skill)과 승인 기반 실행**
  - 문제: 사용자마다 반복 작업이 달라 모두 기능으로 만들 수 없고, AI 편집안이 요청을 빠뜨린 채 전달돼 같은 결과를 원하는 작업을 운에 맡기게 됨.
  - 판단: 지침은 AI, 권한·실행 범위 검사는 코드, 게시와 실제 반영은 사용자가 맡도록 책임 분리. 코드의 형식 검사만으로는 요청 누락을 못 잡아 LLM 의미 평가를 추가.
  - 해결: 자연어 지침 작성·검토·게시와 권한·승인 우회 검사, 미리보기 후 별도 승인. 생성·평가·재작성은 LangGraph 노드로 나눠 단계별로 추적하고, 게시한 Skill은 PostgreSQL에 불변 버전으로 저장.
  - 성과: 편집 품질 94 → 104/114건(82.5% → 91.2%). 승인 전에는 문서가 바뀌지 않음을 확인. 반복 작업을 매번 설명하지 않고 안심하고 맡길 수 있게 함.
- **PDF → Markdown 변환**
  - 문제: 논문 PDF의 표·수식이 깨지면 Wiki와 답변의 근거가 되는 수치를 쓸 수 없음.
  - 판단: 깨진 곳만 고치는 방식은 탐지가 오류를 놓쳤고, 전체 AI 변환은 표·수식 정확도와 비용이 부족해 내용 유형별 처리로 전환. 본문은 추출이 빠른 AnyDoc, 복원은 GPU 운영비가 드는 sLLM 대신 상용 LLM API.
  - 해결: 본문은 AnyDoc으로 추출해 깨진 부분만 AI로 보완, 표·수식은 원본 영역을 따로 판독, 그림은 원본 보존.
  - 성과: 같은 30쪽·445단위 블라인드 평가에서 통과율 45.17% → 89.89%. 논문 속 표·수식 수치를 Wiki와 답변 근거로 쓸 수 있게 함.
- **MSA:** 기능별로만 나누면 DB 부하는 그대로이고 서비스 간 호출만 늘어난다고 보고 데이터 소유권 기준 분리를 제안, 팀원·멘토와 경계·통신 방식을 공동 설계.

### Pilltip | 개인 맞춤 AI 복약 관리 서비스

[GitHub](https://github.com/PillTipKR/Pilltip) · [데이터 정제 경험](https://martinel2.github.io/portfolio.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=pilltip-data#pilltip-data) · [복약 챗봇 설계](https://martinel2.github.io/portfolio.html?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=pilltip-chatbot#pilltip-personalization)

2025.03 — 2025.12 · 부산대학교 졸업과제 · 팀 프로젝트 (3명 + 디자이너) · **핵심 백엔드 · 데이터 정제**

- **시작 계기:** 약품 정보가 흩어져 있어, 지금 건강 상태에서 특정 약을 먹어도 되는지 확인하기 어렵다는 문제에서 출발했습니다.
- **팀 구성:** 본인(백엔드·AI), Android 1명(Kotlin 앱 전반), 백엔드·보안 1명(사용자 DB, 로그인, 문진표, AES-GCM), 디자이너

**주요 개발**

- **의약품 데이터 정제 파이프라인**
  - 문제: 약 4만 4천 건을 그대로 쉬운 설명으로 바꾸면 API 비용이 약 $200으로, 예산 안에서 모든 약의 설명을 제공할 수 없었음.
  - 판단: 약 수를 줄이는 대신 같은 문장은 한 번만 변환. 실시간 응답이 필요 없는 작업이라 Batch API로 대기 시간을 받아들이고 비용을 낮춤.
  - 해결: 문장 블록으로 나눠 완전 일치 문장을 통합하고 GPT Batch API로 변환한 뒤 약품별로 재연결. 2026년 코어 병렬 처리와 확장이 가능한 PySpark로 재현해 단계별 효과 측정.
  - 성과: 전체 원문 변환 예상 비용 약 $200 대비 실제 API 지출 $11.18(전처리 인건비 제외). 재현 실험에서 완전 일치 중복 제거로 텍스트 744MB → 44.1MB(−94.1%).
- **개인 건강 정보 기반 AI 복약 챗봇**
  - 문제: 약을 먹어도 되는지 확인하려는 사용자의 증상 표현과 약 효능 용어가 달라 검색이 어렵고, 개인화에 필요한 건강 정보는 외부 AI로 보낼 수 없었음.
  - 판단: 동의어 사전은 증상이 많고 서로 겹쳐 의미 검색으로, 프로필 필터링은 걸러야 할 경우가 너무 많아 내부 판단으로 전환. 벡터 DB는 Milvus보다 가벼운 Weaviate, 오케스트레이션은 백엔드가 Spring이라 별도 Python 컨테이너 부하를 피해 Spring AI 사용.
  - 해결: Weaviate 의미 검색과 AI 오케스트레이션으로 약품 탐색·복약 위험·섭취량별 처리 경로 구성. 임신 여부·복용약·기저질환은 내부 코드로 판단.
  - 성과: 자연어 증상으로 약품 정보를 탐색하고, 해당 건강 프로필을 외부 LLM 입력에서 제외한 개인화 흐름 구현.
- **백엔드:** Java·Spring Boot 기반 의약품·건강기능식품 DB, 검색·자동완성(Elasticsearch)과 복약 위험정보(DUR) 표출(Redis 캐시)로 검색 응답 5~7초 → 평균 0.8초. FCM 복약 알림·로그, 딥링크 친구 초대, 가족 프로필 전환 구현.

## 오픈소스 기여

**[Rhwp](https://github.com/edwardkim/rhwp)** — Rust 기반 HWP/HWPX 프로젝트의 오류 분석, 수정안 제출과 CI 대응. 그림·표·도형의 textFlow 속성이 저장 후 초기화되는 오류를 수정했습니다.

[PR #1213 · 병합](https://github.com/edwardkim/rhwp/pull/1213) · [PR #1351](https://github.com/edwardkim/rhwp/pull/1351) · [전체 기여](https://github.com/edwardkim/rhwp/pulls?q=is%3Apr+author%3AMartinel2)

## 활동

- **AWS 교육** (2026.06 — 2026.07): Cloud Practitioner Essentials, Machine Learning Engineering on AWS, Developing Generative AI Applications on AWS 이수
- **부산대학교 APPTIVE** (2025.03 — 2026.01): Backend 멘티 및 멘토. 멘티 12명 대상 6회 멘토링과 코드 리뷰. HTTP·Servlet·REST API·DB 기초를 보강하는 커리큘럼 개편에 참여했습니다. [멘토 공로상](https://martinel2.github.io/assets/evidence/apptive-merit.jpeg)
- **SK AI SUMMIT · K-ICT WEEK in Busan** (2025.11 / 2025.07): 부산대학교 대표 전시팀으로 Pilltip 부스를 운영하고 서비스 시연과 기술 질의응답을 진행했습니다. [현장 사진](https://martinel2.github.io/?utm_source=github&utm_medium=referral&utm_campaign=profile&utm_content=activity-gallery#activity-gallery)
- **백준 945일 연속 문제 해결** (2022.02 — 2025.07): 하루 한 문제를 목표로 solved.ac 기준 최장 945일 연속 문제를 해결했습니다. 누적 1,659문제, Platinum IV. [풀이 저장소](https://github.com/Martinel2/BaekJoon) · [solved.ac](https://solved.ac/profile/kkuldangi3)

## 수상

- **캡스톤디자인 금상** · 2025.10 · 소프트웨어·인공지능 분과 / 부산대학교 정보의생명공학대학
- **부산 DATA WEEK 최우수상** · 2025.09 · 데이터 활용 우수사례 공모전 / 부산테크노파크
- **AI LAUNCH 커리어스쿨 창업톤 장려상** · 2025.09 · KRYPTON X x Root Impact x Google.org
- **SW중심대학 디지털 경진대회 후원기업상** · 2025.08 · SW중심대학협의회

## 학력·자격

- **부산대학교** · 2022.02 — 2026.02 (편입) · 평균 학점 4.12 / 4.5
- **대구대학교** · 2019.03 — 2022.02 (중퇴) · 평균 학점 4.2 / 4.5
- **정보처리기사** · 2025.09 · 한국산업인력공단

## 글

- [MSA 전환과 피드백](https://velog.io/@kkuldangi3/MSA-전환과-피드백)
- [디자인 싱킹 회고](https://velog.io/@kkuldangi3/디자인-싱킹-회고)

## 알고리즘

[![Solved.ac Profile](https://mazassumnida.wtf/api/v2/generate_badge?boj=kkuldangi3)](https://solved.ac/profile/kkuldangi3)

<img src="https://martinel2.github.io/assets/evidence/baekjoon-streak.png" alt="solved.ac 2022–2025 연도별 스트릭" width="720">
