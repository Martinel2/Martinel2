Jae Hyeong Kim, Backend Developer
---
## ⚙ Tech Stack 

### Backend Engineering
<img src = "https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"/> <img src = "https://img.shields.io/badge/junit5-25A162?style=for-the-badge&logo=junit5&logoColor=white"/>

### DB
<img src = "https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/> 

<img src ="https://img.shields.io/badge/Milvus-00A1EA?style=for-the-badge&logo=Milvus&logoColor=white"/> <img src ="https://img.shields.io/badge/Weaviate-6DB33F?style=for-the-badge&logo=Weaviate&logoColor=white"/> 

<img src="https://img.shields.io/badge/elasticsearch-005571?style=for-the-badge&logo=elasticsearch&logoColor=white"/> <img src="https://img.shields.io/badge/redis-FF4438?style=for-the-badge&logo=redis&logoColor=white"/> 

### DevOps / Infra
<img src="https://img.shields.io/badge/Amazon_EC2-FF9900?style=for-the-badge&logo=Amazon-EC2&logoColor=white"/> <img src="https://img.shields.io/badge/azure-6492FE?style=for-the-badge&logoColor=white"/> 
<img src="https://img.shields.io/badge/nginx-009639?style=for-the-badge&logo=nginx&logoColor=white"/>

<img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white"/> <img src="https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/> 

<img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=Grafana&logoColor=white"/> <img src="https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=Prometheus&logoColor=white"/> 


<img src = "https://img.shields.io/badge/firebase_cloud_messaging-DD2C00?style=for-the-badge&logo=firebase&logoColor=white"/>

### AI
<img src = "https://img.shields.io/badge/spring AI-6DB33F?style=for-the-badge&logoColor=white"/> <img src="https://img.shields.io/badge/openai API-412991?style=for-the-badge&logo=openai&logoColor=white"/>

---

## 📖 Education
### 부산대학교 학사 (2022.03 ~ 2026.02)
- 정보컴퓨터공학
- GPA : 4.12 / 4.5 (최우등 졸업)

### 대구대학교 중퇴 (2019.03 ~ 2022.02)
- 컴퓨터공학부
- GPA : 4.2 / 4.5 

---

## 💡 PS

![Solved.ac Profile](http://mazassumnida.wtf/api/v2/generate_badge?boj=kkuldangi3)

---

## 🏆 Awards
* 2025 SW 중심대학 디지털 경진대회 / 후원기업상(딥노이드) / 2025.08.12 / SW중심대학협의회
* 부산 DATA WEEK - 데이터 활용 경진대회 / 최우수상 / 2025.09.23 / 부산테크노파크
* AI커리어스쿨 창업톤(L:AUNCH) / 장려상 / 2025.09.28 / Root Impact

---

## Projects

### [Pilltip : 개인맞춤 AI 의약관리 애플리케이션](https://github.com/PillTipKR/Pilltip) / Backend Developer / 2025.03 ~ 2025.12
* 의약 데이터베이스 설계 및 구현
    * MySQL을 이용하여 약품 정보, DUR(의약품안전사용서비스) 정보, 영양제 정보 ERD 설계
    * 약품과 성분을 분리 저장하여 DUR 탐색시 유용하도록 설계
    * Join Fetch 연산을 사용하여 N+1 문제 해결

* 비용 최적화
    * 약품 설명 구어체 변환 과정에서 대규모 API 호출 비용 문제 인식
    * 문장들의 연관성을 파악하여 중복 문장 전처리 (44,032개의 약품 설명 -> 27,526개의 문장)
    * GPT Batch API를 이용하여 비용 50% 추가 절감
    * 결과적으로 $200(추정) -> $15 로 약 92%의 비용 절감, 전체 데이터의 98% 변환 성공

* 자동 검색 기능 구현
    *  사용자가 입력 시, 연관된 약품명 리스트 제공
    *  검색 수행 시, 주의가 필요한 약을 자동으로 표시 
    *  Redis와의 상호작용을 고려하여 Generic 타입의 Index 제작
    *  검색 응답 속도를 위해 Elasticsearch 사용
    *  커스텀까지는 필요없다고 판단하여 제공되는 Ngram, EdgeNGram을 사용
    *  최대 2s -> 0.8ms(Postman 측정 시)로 응답 시간 개선
     
* RAG,Spring AI를 이용한 Multi-turn 방식의 Agentic AI 구현(베타 버전)
    *  DUR(의약품안전사용서비스), 영양제 추천, 하루 권장량 안내
    *  RAG를 이용해 할루시네이션 및 개인정보 유출 방지
    *  Spring AI를 이용해 Agentic AI 구현

### [트래픽 스트레스 테스트](https://github.com/Martinel2/traffic-control) / 우테코 프리코스 오픈 미션 / 2025.11 ~ 2025.11
* 안정적인 서버 운영 및 병목 지점 파악을 위해 Grafana-Prometheus를 이용한 시스템 모니터링 환경 구축 및 k6를 이용해 트래픽 부하 상황 가정
    * JVM 튜닝(GC옵션, 힙 크기 조정)을 통한 성능 개선으로 최대 수용 가능 동시 접속자 수 1명 ➔ 12명으로 12배 향상 
    * p(95) 지연 시간 1.22s -> 226.31ms로 약 81% 대폭 단축
    * 최대 지연 시간 6.29s -> 2.79s로 개선

### [TODO 웹사이트](https://github.com/Martinel2/Todo_backend) / 개인 프로젝트 / 2024.12 ~ 2025.02
* CI/CD 파이프라인 구축
    * AWS EC2 이해도 상승 및 수동 배포의 비효율성 개선을 위해 Github Action을 이용한 CI/CD 파이프라인 구축
    * 약 161번의 시행착오를 거쳐 EC2의 SSH 연결 및 Docker hub, Docker-compose를 이용해 배포 성공
    * Nginx 리버스 프록시 설정을 통해 서버의 보안 강화

### [쇼핑몰 웹사이트](https://github.com/Martinel2/SpringProject_Shoppingmall) / 개인 프로젝트 / 2024.03 ~ 2024.08
* Spring Boot Framework와 MySQL의 기본 아키텍처 및 동작 원리 학습을 위해 수행
* ERD 설계
    * [2015년 G-Market ERD](https://www.slideshare.net/slideshow/db-project-gmarket/54873434#47)를 참고하여 ERD 설계
 
* 로그인 기능 구현
    * 초기에는 세션을 통한 구현으로 로그인 과정 학습
    * 추후에 Spring Security 6을 시행착오를 거쳐 적용 성공 [(링크)](https://velog.io/@kkuldangi3/%EC%87%BC%ED%95%91%EB%AA%B0-%EC%9B%B9%EC%82%AC%EC%9D%B4%ED%8A%B8-%EB%A7%8C%EB%93%A4%EC%96%B4%EB%B3%B4%EA%B8%B0-%EC%A4%91%EA%B0%84%EC%A0%90%EA%B2%801)
 
* 결제 기능 구현
    * Toss 결제 API 사용 [(링크)](https://velog.io/@kkuldangi3/%EC%87%BC%ED%95%91%EB%AA%B0-%EC%9B%B9%EC%82%AC%EC%9D%B4%ED%8A%B8-%EB%A7%8C%EB%93%A4%EC%96%B4%EB%B3%B4%EA%B8%B0-13)

---

## Other Activities

### 부산대학교 APPTIVE 동아리 활동 / 2025.03 ~ 2026.01
* Backend 멘토 역할 수행
    * Backend 기초 지식(Rest API, DB 등) 공유 및 코드 리뷰 수행 
    * 성과를 인정 받아 동아리 내 공로상 수상

---

## 📞 Contacts
Tel : 010-5329-4516 <br/>
Email : kkuldangi3@naver.com
