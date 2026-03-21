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
* 부산대학교 정보컴퓨터공학부 졸업과제 SW/AI 분과 / 금상 / 2025.10.01 / 부산대학교 정보컴퓨터공학부
* AI커리어스쿨 창업톤(L:AUNCH) / 장려상 / 2025.09.28 / Root Impact
* 부산 DATA WEEK - 데이터 활용 우수사례 공모전 / 최우수상 / 2025.09.23 / 부산테크노파크
* 2025 SW 중심대학 디지털 경진대회 SW부문/ 후원기업상(딥노이드) / 2025.08.12 / SW중심대학협의회
---

## Projects

### [Pilltip : 개인맞춤 AI 의약관리 애플리케이션](https://github.com/PillTipKR/Pilltip) / Backend Developer / 2025.03 ~ 2025.12
* 의약 데이터베이스 설계 및 구현
    * MySQL을 이용하여 약품 정보, DUR(의약품안전사용서비스) 정보, 영양제 정보 ERD 설계
    * 약품과 성분을 분리 저장하여 DUR 탐색시 유용하도록 설계

* 비용 최적화
    * 약품 설명 구어체 변환 과정에서 대규모 API 호출 비용 문제 인식
    * 문장들의 연관성을 파악하여 중복 문장 전처리 (44,032개의 약품 데이터 -> 27,526개의 문장)
    * GPT Batch API를 이용하여 비용 50% 추가 절감
    * 결과적으로 $200(추정) -> $11.18 로 약 98%의 비용 절감, 전체 데이터의 98% 변환 성공

* 자동 검색 기능 구현
    *  사용자가 입력 시, 연관된 약품명 리스트 제공
    *  검색 수행 시, 주의가 필요한 약을 자동으로 표시 
    *  Redis와의 상호작용을 고려하여 Generic 타입의 Index 제작
    *  검색 응답 속도를 위해 Elasticsearch 사용
    *  커스텀까지는 필요없다고 판단하여 제공되는 Ngram, EdgeNGram을 사용
    *  최대 7~8s -> 0.8ms(Postman 측정 시)로 응답 시간 개선
     
* RAG,Spring AI를 이용한 Multi-turn 방식의 Agentic AI 구현(베타 버전)
    *  DUR(의약품안전사용서비스), 영양제 추천, 하루 권장량 안내
    *  RAG를 이용해 할루시네이션 및 개인정보 유출 방지
    *  Spring AI를 이용해 Agentic AI 구현

### [트래픽 스트레스 테스트](https://github.com/Martinel2/traffic-control) / 우테코 프리코스 오픈 미션 / 2025.11 ~ 2025.11
* 안정적인 서버 운영 및 병목 지점 파악을 위해 Grafana-Prometheus를 이용한 시스템 모니터링 환경 구축 및 k6를 이용해 트래픽 부하 상황 가정
    * p(95) 지연 시간 1.22s -> 226.31ms로 약 81% 대폭 단축
    * 최대 지연 시간 6.29s -> 2.79s로 개선

---

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
    * ~최근에는 많이 적지 못함...~
---

## 📞 Contacts
Tel : 010-5329-4516 <br/>
Email : kkuldangi3@naver.com
