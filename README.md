# 김재형 | Backend & AI Application Developer

실패의 원인을 깊이 파고들어 해결하는 것을 좋아하는 개발자

가설을 실험으로 확인하고, 결과가 달라진 원인을 찾아 다음 개선으로 연결합니다. AI의 정확도와 비용, 처리 시간을 함께 살피며 서비스에 맞는 구현을 선택합니다.

[소개](https://martinel2.github.io/) · [포트폴리오](https://martinel2.github.io/portfolio.html) · [블로그](https://velog.io/@kkuldangi3/posts) · [LinkedIn](https://www.linkedin.com/in/%EC%9E%AC%ED%98%95-%EA%B9%80-b75920345/)

**Email**: kkuldangi2@gmail.com

## 주요 경험

- **[PDF 변환 통과율 45.17% → 89.89% 개선](https://martinel2.github.io/portfolio.html#fruition-document)** — PDF 30쪽의 내부 평가 결과. 본문과 표·수식의 처리 경로를 나누고, 필요한 부분만 AI로 복원했습니다.
- **[RAG 근거 충족률 66.25% → 91.25% 개선](https://martinel2.github.io/portfolio.html#fruition-jev-evidence)** — 답이 있는 80문항에서 필요한 근거를 충족한 질문 53 → 73건. Jev 도입 후 후보 수와 병렬 처리를 조정해 시간 중앙값 9.090초 → 2.251초로 단축했습니다.
- **[약품 설명 변환: 예상 $200 대비 실제 $11.18](https://martinel2.github.io/portfolio.html#pilltip-data)** — 완전 일치·의미 중복 제거, 누락된 성분별 주의사항 보완, GPT Batch API 변환을 연결했습니다. 비용은 전체 원문 변환 예상치와 실제 API 지출의 비교입니다.

## 기술

- **Backend:** Java · Spring Boot · Spring AI · Python
- **AI / Search:** LangChain · LangGraph · RAG · LLM Evaluation · Elasticsearch · Weaviate
- **Data / Infra:** MySQL · PostgreSQL · Redis · Kafka / Docker · Docker Compose · GitHub Actions

## 프로젝트

### Fruition | 문서를 지식으로 쌓고 활용하는 AI 워크스페이스

[Github](https://github.com/FruitionKR/local-pilot) · [Github AI 분리 저장소](https://github.com/FruitionKR/Fruition-ai) · [상세 경험](https://martinel2.github.io/portfolio.html#fruition-document)

2026.04 — 현재 · AI SW 마에스트로 17기 · 팀 프로젝트 (3명 + 디자이너) · **AI 파트 리드**

- **시작 계기:** 팀원이 제기한 문서 관리의 불편함을 디자인 싱킹으로 구체화했습니다. 문서를 저장만 해 두고 정작 필요할 때 찾지 못하는 문제를 풀고자 했습니다.
- **팀 구성:** 본인(AI 기능 전체), 백엔드 1명(Spring 백엔드 전체), 프론트엔드·DevOps 1명(프론트엔드, MSA 기반 AWS 배포), 외주 디자이너 · 멘토 3명(Gen AI 품질·평가 / 백엔드 / 마일스톤·MSA 설계·문서화)
- MSA의 초기 설계를 제안하고 팀원·멘토와 논의해 최종 구조를 함께 완성했습니다.

<img src="https://martinel2.github.io/assets/projects/fruition-system-architecture.jpg" alt="Fruition 시스템 아키텍처" width="720">

**주요 개발**


- **문서 변환과 분석:** 본문을 추출·복원하고 표·수식·그림을 보존하는 PDF 변환 파이프라인 구현. 문서별 병렬 처리로 문서 4개 분석 시간 282.11초 → 73.89초, 약 74% 단축.
- **답변 근거 검색:** 검색으로 후보를 모으고 선택형 판단 모델 Jev로 근거를 고르는 구조를 적용. 동일 후보·반환 조건으로 비교한 뒤 정확도와 처리 시간을 함께 개선.
- **사용자 정의 작업:** 자연어로 반복 작업 지침(Skill)을 작성·검토·게시하고, 문서 변경을 미리 확인한 뒤 승인하는 흐름 구현.
- **문서 편집 품질:** 편집 목적 전달과 재시도 입력, 의미 평가 후 재작성을 개선해 동일 초안 114개의 내부 평가 통과 94 → 104건.


### Pilltip | 개인 맞춤 AI 복약 관리 서비스

[GitHub](https://github.com/PillTipKR/Pilltip) · [데이터 정제 경험](https://martinel2.github.io/portfolio.html#pilltip-data) · [복약 챗봇 설계](https://martinel2.github.io/portfolio.html#pilltip-personalization)

2025.03 — 2025.12 · 부산대학교 졸업과제 · 팀 프로젝트 (3명 + 디자이너) · **핵심 백엔드 · 데이터 정제**

- **시작 계기:** 약품 정보가 흩어져 있어, 지금 건강 상태에서 특정 약을 먹어도 되는지 확인하기 어렵다는 문제에서 출발했습니다.
- **팀 구성:** 본인(백엔드·AI), Android 1명(Kotlin 앱 전반), 백엔드·보안 1명(사용자 DB, 로그인, 문진표, AES-GCM), 디자이너

**주요 개발**

- Java·Spring Boot 기반 의약품·건강기능식품 DB 설계, 검색·자동완성과 복약 위험정보(DUR)·주의 정보 표출 구현.
- FCM을 활용한 복약 알림·복약 로그, 딥링크 기반 친구 초대, 가족 프로필 전환 기능 구현.
- **의약품 데이터 정제·변환:** 약 4만 4천 건의 원문을 쉬운 설명으로 변환. 문장 중복 제거와 성분별 누락 보완, Batch API를 적용해 변환 대상을 1GB → 326MB로 축소.
- **개인화 복약 챗봇:** 증상과 약품 효능을 의미 검색으로 연결하고, 약품 탐색·복약 위험·섭취량별 처리 경로 구현. 임신 여부·복용약·기저질환은 외부 LLM 입력에서 제외하고 내부 코드로 판단.

### 개인 프로젝트

- [쇼핑몰](https://github.com/Martinel2/SpringProject_Shoppingmall): Java·Spring 기반 쇼핑몰과 로그인 기능 구현
- [Todo 웹](https://github.com/Martinel2/Project_Todo): OAuth 연동과 CI/CD 구축 경험

## 오픈소스 기여

**[Rhwp](https://github.com/edwardkim/rhwp)** — Rust 기반 HWP/HWPX 프로젝트의 오류 분석, 수정안 제출과 CI 대응. 그림·표·도형의 textFlow 속성이 저장 후 초기화되는 오류를 수정했습니다.

[PR #1213 · 병합](https://github.com/edwardkim/rhwp/pull/1213) · [PR #1351](https://github.com/edwardkim/rhwp/pull/1351) · [전체 기여](https://github.com/edwardkim/rhwp/pulls?q=is%3Apr+author%3AMartinel2)

## 활동

- **부산대학교 APPTIVE** (2025.03 — 2026.01): Backend 멘티 및 멘토. 멘티 12명 대상 6회 멘토링과 코드 리뷰. HTTP·Servlet·REST API·DB 기초를 보강하는 커리큘럼 개편에 참여했습니다. [멘토 공로상](https://martinel2.github.io/assets/evidence/apptive-merit.jpeg)
- **SK AI SUMMIT · K-ICT WEEK in Busan** (2025.11 / 2025.07): 부산대학교 대표 전시팀으로 Pilltip 부스를 운영하고 서비스 시연과 기술 질의응답을 진행했습니다. [현장 사진](https://martinel2.github.io/#activity-gallery)
- **AWS 교육** (2026.06 — 2026.07): Cloud Practitioner Essentials, Machine Learning Engineering on AWS, Developing Generative AI Applications on AWS 이수
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
