Jae Hyeong Kim, Backend Developer
---

## 📞 Contacts
Email : kkuldangi3@naver.com

## Introduce
저는 에러를 두려워하지 않는 백엔드 개발자입니다!
* 81번의 가설 수립과 검증을 반복하며 컨테이너 구동 타이밍에 따른 문제 해결 및 에러의 근본 원인을 끝까지 추적하여 CI/CD 파이프라인 구축
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

- **정규표현식 및 Batch API 도입으로 LLM 처리 비용 94% 절감**
    - **문제 -** 1GB 약품 데이터의 구어체 변환 시, 단순 LLM API 호출로 인한 과도한 토큰 과금(약 $200) 예상
    - **해결**
        - 100개 샘플 패턴 분석 및 **정규표현식**을 통한 중복 문장 전처리
            - 약 70%의 중복률을 근거로 팀원들을 설득 → 일주일의 시간 확보
        - 총 데이터 67% 압축 (1GB $\rightarrow$ 326MB)
        - 비동기 처리가 가능한 점을 활용하여 일반 API 대신 **GPT Batch API**로 파이프라인 전환
    - **결과 -** 데이터 처리 비용을 **$11.18로 약 94% 절감** 및 98% 변환 성공으로 비즈니스 자본 방어

- **신뢰성 확보를 위한 2-Tier Agentic AI (RAG) 구축**
    - 약품 정보 탐색 시 LLM의 할루시네이션 방지 및 민감 정보 유출을 막기 위해, 내부 Vector DB(Weaviate)와 Spring AI를 연동한 RAG 기반 아키텍처 설계 및 구현


### [Todo 웹 애플리케이션 및 CI/CD 인프라 구축](https://github.com/Martinel2/Project_Todo)

- **기간 / 역할:** 2025.02 ~ 2025.03 / 개인 프로젝트
- **기술 스택:** Spring Boot, MySQL, Docker Compose, Nginx, GitHub Actions, AWS EC2

- **84번의 가설 검증과 컨테이너 의존성(Race Condition) 해결**
    - **문제 -** GitHub Actions 기반 CI/CD 구축 중, CI 단계의 테스트 DB 종속성 문제와 CD 배포 단계의 컨테이너 연결 실패 등 복합적인 장애 발생
        
    - **해결** - 84번의 에러 로그 분석
        - **CI 환경 격리 -** 테스트 전용 프로파일 설정 및 **H2 인메모리 DB**를 도입하여 테스트 독립성 확보
        - **CD 의존성 제어** - WAS와 DB 컨테이너 간의 **구동 타이밍 불일치**임을 파악하고 Docker Compose의 `depends_on` 옵션으로 실행 순서를 강제 제어
    - **결과 -** 의존성을 명확히 확립하여 배포 파이프라인의 **안정성 확보**


### [쇼핑몰 웹사이트](https://github.com/Martinel2/SpringProject_Shoppingmall)

- **기간 / 역할:** 2024.03 ~ 2024.09 / 개인 프로젝트
- **기술 스택:** Spring Boot, Spring Security, MySQL

- **유실 없는 데이터 정합성 확보 및 도메인 정책 기반 ERD 재설계**
    - **문제 -** 상품-주문-장바구니 간 외래키(FK) 꼬임으로 인해 판매자가 상품 삭제 시 타 사용자의 장바구니 제약 조건 위배 에러 발생 및 다중 결제 데이터 적재 방식에 대한 아키텍처 한계 직면
    - **해결**
        - **도메인 정책 수립**
            - 쇼핑몰 정책상 상품 관리 주체는 판매자여야 함을 정의
            - 상품 삭제 시 참조되는 장바구니 데이터를 선제적으로 일괄 삭제하도록 비즈니스 로직 재구축
        - **확장성을 고려한 데이터 분할**
            - 다중 결제 시 배열이 아닌 상품 수(N개)만큼 Row를 나누어 적재
            - 장바구니 비우기 역시 Bulk Delete 대신 단건 반복 삭제로 구현
                - 미래의 '일부 상품 선택 결제' 및 '개별 배송/취소' 요구사항에 유연하게 대응
    - **결과**
        - 플랫폼 도메인 정책 관점에서 에러를 근본적으로 해결
        - 향후 기능 확장에 대비한 유연한 결제 데이터 구조 확립

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


