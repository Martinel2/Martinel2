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

### [Pilltip : 개인맞춤 AI 의약관리 애플리케이션](https://github.com/PillTipKR/Pilltip) / Backend Developer / 2025.03 ~ 2025.12
* 의약 데이터베이스 설계 및 구현
    * MySQL을 이용하여 약품 정보, DUR(의약품안전사용서비스) 정보, 영양제 정보 ERD 설계
    * 약품과 성분을 분리 저장하여 DUR 탐색시 유용하도록 설계

* 비용 최적화
    * 약품 설명 구어체 변환 과정에서 대규모 API 호출 비용 문제 인식
    * 문장들의 연관성을 파악하여 정규표현식 기반 중복 문장 전처리 (1GB의 약품 데이터 -> 326MB의 약품 데이터)
    * GPT Batch API를 이용하여 비용 50% 추가 절감
    * 결과적으로 $200(추정) -> $11.18 로 약 94%의 비용 절감, 전체 데이터의 98% 변환 성공

* 자동 검색 기능 구현
    *  사용자가 입력 시, 연관된 약품명 리스트 제공
    *  검색 수행 시, 주의가 필요한 약을 자동으로 표시 
    *  확장성을 위한 Generic 타입의 Index 제작
    *  검색 응답 속도 및 RDBMS의 한계 돌파를 위해 Elasticsearch 사용
    *  커스텀까지는 필요없다고 판단하여 제공되는 Ngram, EdgeNGram을 사용
    *  빈번한 약품 데이터 업데이트에 대비해 Redis 사용
    *  최대 5~7s -> 0.8ms(Postman 측정 시)로 응답 시간 개선
     
* RAG,Spring AI를 이용한 Multi-turn 방식의 Agentic AI 구현(베타 버전)
    *  DUR(의약품안전사용서비스), 영양제 추천, 하루 권장량 안내
    *  RAG를 이용해 할루시네이션 및 개인정보 유출 방지
    *  Spring AI를 이용해 Agentic AI 구현

### [트래픽 스트레스 테스트](https://github.com/Martinel2/traffic-control) / 우테코 프리코스 오픈 미션 / 2025.11 ~ 2025.11
* 안정적인 서버 운영 및 병목 지점 파악을 위해 Grafana-Prometheus를 이용한 시스템 모니터링 환경 구축 및 k6를 이용해 트래픽 부하 상황 가정
    * p(95) 지연 시간 1.22s -> 226.31ms로 약 81% 대폭 단축
    * 최대 지연 시간 6.29s -> 2.79s로 개선

### [Todo 웹 애플리케이션 및 CI/CD 인프라 구축](https://github.com/Martinel2/Project_Todo) / 개인프로젝트 / 2025.02 ~ 2025.03
* 컨테이너 오케스트레이션 및 리버스 프록시 구축
   * Docker Compose를 활용하여 Spring Boot WAS, MySQL, Nginx 웹 서버를 동일한 가상 네트워크로 구성
   * Nginx 리버스 프록시(Reverse Proxy) 설정으로 클라이언트의 요청을 WAS로 안전하게 라우팅하는 배포 환경 구축

* CI/CD 배포 자동화 및 배포 환경 트러블슈팅
   * GitHub Actions와 AWS EC2를 연동하여 CI/CD 파이프라인 구축 중 Docker 컨테이너 구동 시 Spring 애플리케이션과 DB 연결 에러 발생
   * 배포 스크립트와 에러 로그 분석 및 84번에 걸친 시행착오
   * 단순한 네트워크 오류가 아닌 DB 컨테이너의 접속 준비 이전에 WAS 컨테이너가 먼저 실행되어 연결을 시도하는 구동 타이밍 문제임을 파악
   * Docker Compose의 depends_on 옵션 적용으로 컨테이너 간의 실행 순서와 의존성 제어

### [쇼핑몰 웹사이트](https://github.com/Martinel2/SpringProject_Shoppingmall) / 개인프로젝트 / 2024.03 ~ 2024.09
* ERD 재설계를 통한 외래키 연관관계 지옥 탈출
   * 상품-주문-회원 간의 외래키가 복잡하게 꼬여 참조 무결성 제약 조건 위배 에러 발생
   * 1:N, N:M 관계 재분석 및 ERD 재설계로 데이터 무결성 확보
   
* 결제 및 장바구니 로직 데이터 정합성 확보
   * 장바구니에서 총 결제 금액이 동기화되지 않거나 1개 기준으로만 할인이 적용되는 버그 발생
   * 트랜잭션 내에서 정확히 재계산하도록 로직 수정

* 로그인 보안 취약점 인지 및 개선
   * 초기 세션 및 JS 기반의 인증 정보 처리 시 브라우저 쿠키를 통한 보안 취약점 확인
   * 기존 블로그 레퍼런스들과 최신 Spring Security 버전 간 설정 방식 차이로 인한 호환성 에러 발생
   * 각 레거시 코드 라인의 역할 인지 및 공식 문서와의 교차 검증을 통한 최신 버전 설정으로 재구성

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


