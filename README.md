Jae Hyeong Kim, Backend Developer
---

## 📞 Contacts
Email : kkuldangi3@naver.com

## Introduce
저는 에러를 두려워하지 않는 백엔드 개발자입니다!
* 84번의 가설 수립과 검증을 반복하며 컨테이너 구동 타이밍에 따른 문제 해결 및 에러의 근본 원인을 끝까지 추적하여 CI/CD 파이프라인 구축
* 1GB 규모의 약품 데이터를 전처리하고 정규표현식 및 Batch API를 도입하여 API 호출 비용 94% 절감
* 외래키 참조 무결성 오류 해결을 위한 ERD 재설계로 데이터 정합성 확보

## ⚙ Tech Stack 

### Backend Engineering
🌱 Spring Boot ✅ JUnit5

### DB
🐬 MySQL 🔍 Elasticsearch ⚡ Redis

🌐 Milvus & Weaviate

### DevOps / Infra
☁️ AWS EC2 & Azure 🐳 Docker & Docker Compose

🏗️ GitHub Actions 🌐 Nginx

🔔 Firebase Cloud Messaging (FCM)


### AI
🧠 OpenAI API 🤖 Spring AI

## Projects
### [Pilltip : 개인맞춤 AI 의약관리 애플리케이션](https://github.com/PillTipKR/Pilltip)

- **기간 / 역할:** 2025.03 ~ 2025.12 / Backend Developer (기여도 100%)
- **기술 스택:** Spring Boot, MySQL, Weaviate, Elasticsearch, Redis, Docker Compose, Spring AI, GPT Batch API, Firebase Cloud Messaging (FCM)

- **Elasticsearch + Redis 검색 응답 속도 5s $\rightarrow$ 0.8ms 단축**
    - **문제**
        - RDBMS `LIKE %keyword%` 사용으로 인한 인덱스 무력화와 다중 JOIN으로 지연(5~7s) 발생
        - 디자이너의 ‘검색 지연 1초 이내’ 요구
    - **해결**
        - **RDBMS의 한계 인지** 및 **Elasticsearch(EdgeNgram, Ngram)** 도입으로 자동완성 로직 구현
        - 실시간 검색 결과에 약품 상충작용 태깅을 위한 **Redis** 사용
        - 약품 데이터의 빈번한 업데이트에 대비해 로컬 캐시가 아닌 Redis 사용
    - **결과 -** 검색 응답 속도를 **0.8ms(Postman 기준)로 단축**하여 UX를 획기적으로 개선

- **논리회로의 모듈화 개념을 응용한 전처리 파이프라인으로 LLM 비용 94% 절감**
    - **문제**
        - 1GB 약품 데이터 변환 시 팀 자본 대비 과도한 LLM 토큰 과금(약 $200)이 예상
        - 팀 내에서는 어쩔 수 없는 지출이니 감내하고 단순 API를 호출하자는 의견이 존재
    - **해결**
        - 정규표현식을 통한 데이터 클리닝
        - 하드웨어 모듈화 관점을 적용한 문장 패턴 블록화 및 해시 테이블 인덱싱 매핑
        - 100개 샘플을 분석 후 처리해 70%의 중복률 탐지
            - 팀원을 주도적으로 설득 →  1주일의 전처리 시간 확보
        - GPT Batch API를 사용해 추가 50% 절감
    - **결과**
        - 처리 비용 $11.18로, 총 94% 절감
        - '더 나은 방향을 위해 동료를 설득하고 일이 되게 만드는' 주도적 엔지니어링 달성

- **신뢰성 확보를 위한 2-Tier Agentic AI (RAG) 구축**
    - 약품 정보 탐색 시 LLM의 할루시네이션 방지 및 민감 정보 유출을 막기 위해, 내부 Vector DB(Weaviate)와 Spring AI를 연동한 RAG 기반 아키텍처 설계 및 구현


### [Todo 웹 애플리케이션 및 CI/CD 인프라 구축](https://github.com/Martinel2/Project_Todo)

- **기간 / 역할:** 2025.02 ~ 2025.03 / 개인 프로젝트
- **기술 스택:** Spring Boot, MySQL, Docker Compose, Nginx, GitHub Actions, AWS EC2

- **84번의 가설 검증과 컨테이너 의존성(Race Condition) 해결**
    - **문제 -** GitHub Actions 기반 CI/CD 구축 중, CI 단계의 테스트 DB 종속성 문제와 CD 배포 단계의 컨테이너 연결 실패 등 복합적인 장애 발생
        
    - **해결** - 84번의 에러 로그 분석
        - **CI 환경 격리 -** 테스트 전용 프로파일 설정 및 **H2 인메모리 DB**를 도입하여 테스트 독립성 확보
        - **CD 의존성 제어**
            - WAS와 DB 컨테이너 간의 **구동 타이밍 불일치**임을 파악하고 Docker Compose의 `depends_on` 옵션으로 실행 순서를 강제 제어
            - restart: on-failure 장애 복구 패턴을 적용하여 DB 초기화 지연으로 인한 WAS 커넥션 실패를 자동 재시작으로 완벽 제어
    - **결과 -** 의존성을 명확히 확립하여 배포 파이프라인의 **안정성 확보**


### [쇼핑몰 웹사이트](https://github.com/Martinel2/SpringProject_Shoppingmall)

- **기간 / 역할:** 2024.03 ~ 2024.09 / 개인 프로젝트
- **기술 스택:** Spring Boot, Spring Security, MySQL

- **결제 데이터 제1 정규화 및 스냅샷 아키텍처를 통한 무결성 확보**
    - **문제:** 비정규화 구조의 한계 및 결제 시점 가격 변동으로 인한 데이터 정합성 리스크 인지
    - **해결**
        - 결제 시점의 가격/할인가를 스냅샷을 통해 보존
        - 미래의 '부분 취소/배송 조회'를 위해 결제 데이터를 N개의 단건으로 분할하는     정규화 수행
    - **결과**
        - 도메인 정책 관점에서 SQL 에러를 해결
        - 결제 도메인에서 가장 중요한 데이터 정합성 확보 및 확장성에 유연한 데이터베이스 구조 확립

- **로그인 보안 취약점 인지 및 개선**
    - **문제**
        - 초기 세션 및 JS 기반의 인증 정보 처리 시 브라우저 쿠키를 통한 보안 취약점 확인
        - 기존 블로그 레퍼런스들과 최신 Spring Security 버전 간 설정 방식 차이로 인한 호환성 에러 발생
    - **해결** - 각 레거시 코드 라인의 역할 인지 및 공식 문서와의 교차 검증을 통한 최신 버전 설정으로 재구성
    - **결과** - JS기반 취약한 쿠키 인증 로직 삭제 및 서버 중심 인증 로직 확보


## Other Activities

* [전시] SK Summit 2025 / 2025.11
    * 부산대학교 대표 전시 부스 운영

* [자격증] 정보처리기사 취득 / 2025.09

* [전시] K-ICT Week in Busan / 2025.07
    * 부산대학교 대표 전시 부스 운영

* [동아리] 부산대학교 APPTIVE 활동 / 2025.03 ~ 2026.01
    * Backend 멘토 역할 수행
        * Backend 기초 지식(Rest API, DB 등) 공유 및 코드 리뷰 수행 
        * 성과를 인정 받아 동아리 내 공로상 수상

* [Velog](https://velog.io/@kkuldangi3/posts) 글 작성 / 2023.07 ~
    * 새로 배운 것 혹은 프로젝트 일대기 작성

## 🏆 Awards
* 부산대학교 정보컴퓨터공학부 졸업과제 SW/AI 분과 / 금상 / 2025.10.01 / 부산대학교 정보컴퓨터공학부
* AI커리어스쿨 창업톤(L:AUNCH) / 장려상 / 2025.09.28 / Root Impact
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


