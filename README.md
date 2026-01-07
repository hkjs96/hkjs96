## 안녕하세요! 👋 소프트웨어 엔지니어 박지수 입니다

### 🙋‍♂️ 저는 이런 사람입니다
- 🔭 메가존클라우드에서 **AWS 인프라 운영 및 관리**를 담당하고 있습니다  
- 👯 **안정적이고 효율적인 서비스를 제공하는 백엔드 개발**에 관심이 있습니다  
- 🔧 개인적으로는 다양한 실전형 프로젝트를 통해 **백엔드 역량 강화**를 지속하고 있습니다

---

### 한눈에 보기
- 🏢 **MegazoneCloud**: AWS 기반 인프라 운영/개선, **EKS 운영·업그레이드·모니터링 구축** 경험
- 🎓 **항해플러스(Backend)** 수료: Java/Spring 기반 백엔드 기본기(트랜잭션/테스트/동시성/클린아키텍처/모니터링) 강화
  - 항해플러스 이커머스 시스템: Redis(랭킹 Sorted Set / 선착순 쿠폰 INCR ) + DB 락 전략(비관/낙관) 적용, k6 부하테스트 및 (가상) 장애 대응 문서화(지표 p95/p99, error rate 기반 분석)

- 🧩 관심사: **EKS 운영 표준화**, 모니터링/로그/트레이싱 기반 장애 대응, 확장 가능한 백엔드 설계

---

### 💡 주요 관심사

- 대규모 트래픽을 고려한 **확장성 있는 백엔드 아키텍처**
- **클라우드 기반 자동화 및 운영 효율화 (IaC, 모니터링 등)**
- 백엔드 개발

---

## 🧑‍💻 경력 (Updated)
### MegazoneCloud (2023.10 ~ 현재)
- AWS 인프라 운영 및 개선(고객사/프로덕션 중심)
- **EKS 모니터링 구축/개선**: CloudWatch/Prometheus/Grafana 기반 지표 가시화 및 이상 징후 탐지 체계 정리
- **EKS 클러스터 업그레이드 지원**: 사전 검증(DEV/STG) → 운영 반영(롤백/이슈 수집/문서화) 흐름 정리 → 내부 베이스 프로세스 수립
- 운영 장애/이슈 대응: 로그·지표 기반 원인 파악 및 재발 방지 관점의 조치/기록

### FutureSense (2021.11 ~ 2023.01)
- 블록체인/NFT 기반 서비스 개발 프로젝트에 참여하며 **도메인 모델링/ERD 설계/REST API 구현** 경험을 쌓았습니다.
- 거래/이력 관리 흐름의 복잡도를 낮추기 위해 **데이터 모델과 API 설계를 정리**하고, 기능 단위 개발을 수행했습니다.

---

## 🎓 교육 

### 항해플러스 (2025.10 ~ 2025.12)
<a href="https://hhpluscertificateofcompletion.oopy.io/">
  <img src="https://static.spartaclub.kr/hanghae99/plus/completion/badge_blue.svg" />
</a>

- Java/Spring 기반 백엔드 커리큘럼 수행
- 결과물은 아래 공개 레포로 정리했습니다(과제/문서/테스트/부하테스트)

### Solutions Architect 교육 (2023.02 ~ 2023.08)
- 메가존클라우드 연계 과정
- AWS Solutions Architect 트랙 중심으로 네트워크/VPC/IAM/모니터링 등 **클라우드 아키텍처 설계 기초**를 학습했습니다.
- 실습 기반으로 서비스 구성 요소를 조합하고, **운영 관점(가용성/비용)**에서 설계 판단을 훈련했습니다.

---

## 🧪 항해플러스 과제/프로젝트 (Public)


### 🔹 [hhplus-ecommerce](https://github.com/hkjs96/hhplus-ecommerce)
> 항해플러스 이커머스 백엔드 (Week 2~10: 핵심 도메인 구현 → 동시성/Redis 적용 → 성능 테스트 & (가상) 장애 대응)

- **아키텍처**: Layered Architecture(Presentation → Application → Domain → Infrastructure) + Redis / MySQL
- **핵심 기능**
  - 상품 조회/재고 관리(Stock 분리, 이력 추적)
  - 장바구니 CRUD, 주문 생성/결제(포인트)
  - **인기 상품 랭킹**: Redis Sorted Set 기반 Top N / 특정 상품 순위 조회
  - **선착순 쿠폰 발급**: Redis(Set/String) + (권장) Lua 스크립트로 원자적 처리
- **동시성/정합성 전략**
  - 포인트 차감: **Pessimistic Lock(SELECT … FOR UPDATE)**
  - 재고 차감: **Optimistic Lock(@Version)**
  - 랭킹/쿠폰: **Redis 원자 연산(ZINCRBY/DECR/SADD) + TTL**
- **가용성/장애 내성**
  - 주문 완료 후 **외부 데이터 플랫폼 전송을 @Async로 분리**
  - Timeout(3s) + Retry(최대 3회) + **Outbox Fallback(재시도 큐)**
- **테스트/검증**
  - Testcontainers 기반 통합 테스트(MySQL 8.0, Redis 7.x)
  - ExecutorService + CountDownLatch로 동시성 검증
  - Jacoco 라인 커버리지 관리(레포 기준 94% 표기)
- **성능/장애 대응 산출물(레포에 포함)**
  - `docs/week10/step19-load-test-plan.md`: 부하 테스트 시나리오/목표치/계획
  - `docs/week10/step20-incident-report.md`: p95/p99, error rate, 리소스 지표 기반 분석 + (가상) 장애 대응 문서
- **산출물/구조**
  - `docs/`: 요구사항, API 명세(엔드포인트), ERD/시퀀스 다이어그램, Week별 학습/피드백 기록
  - `loadtest/k6/`: k6 스크립트 및 실행 산출물
  - `observability/monitoring/`: 모니터링 관련 구성/산출물 정리


### 🔹 [hhplus-week-1-tdd](https://github.com/hkjs96/hhplus-week-1-tdd)
> 포인트 시스템 TDD & 동시성 제어 실습 레포

- 포인트 충전/사용 도메인을 **TDD로 구현**하고 테스트로 요구사항을 고정
- 동시 요청에서 발생하는 Race Condition을 재현하고, **사용자 단위로 충돌을 막는 방식**으로 해결

---


## 🛠 기술 스택

### Back-End
<div>
  <img src="https://img.shields.io/badge/Java-17-orange.svg"/>
  <img src="https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen.svg"/>
  <img src="https://img.shields.io/badge/Spring%20Security-6B7280?style=flat-square"/>
  <!--
  <img src="https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white"/>
  <img src="https://img.shields.io/badge/Kafka-000000?style=flat-square&logo=apachekafka&logoColor=white"/>
  -->
</div>

### Infra & DevOps
<div>
  <img src="https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white"/>
  <img src="https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white"/>
  <img src="https://img.shields.io/badge/CloudWatch-FF9900?style=flat-square&logo=amazonaws&logoColor=white"/>
</div>

### Front-End (기본 활용)
<div>
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white"/>
</div>

---

## 🧪 Public Repos (GitHub)

### 🔹 [Private Multi-Account Grafana AMP Monitoring](https://github.com/hkjs96/private-multiaccount-monitoring)
> 사설 VPC + 멀티 AWS 계정 환경에서 통합 모니터링 구축

- **기술 스택**: AWS CloudWatch, Amazon Managed Prometheus, Grafana, IAM, VPC Peering
- **성과**:
  - 계정 간 Prometheus Metric 통합 수집 및 대시보드 구성
  - Grafana Agent 기반 로그/메트릭 이중 전송 구조 설계
  - 운영 리소스 현황 파악 및 이상 탐지 시스템 구축

---

## 🧪 개인 프로젝트 (Backend)
### 🔹 [SimpleShop – 세션 기반 쇼핑몰 API](https://github.com/hkjs96/simpleshop)
- Spring Session 기반 로그인 + 인증 필터 수동 구현
- AWS S3 연동 이미지 업로드 + 순서 보장 + 삭제 기능
- Swagger 문서화에 Cookie 기반 인증 연동

### 🔹 [JWT 인증 & Google OAuth2 예제](https://github.com/hkjs96/jwt)
- JWT + RefreshToken 저장 구조 구성
- Google OAuth2 인가코드 흐름 통합
- React + Vite 프론트와 연동하여 인증 플로우 구현

### 🔹 [NewsTracker – 키워드 기반 뉴스 수집 시스템](https://github.com/hkjs96/newstracker)
- OAuth2 → JWT 발급 후 인증 처리 구현
- `@Scheduled` 기반 뉴스 수집 + 중복 저장 방지 + 실패 방어
- Naver 뉴스 API 연동, Swagger + 테스트 적용

<!--
### 🔹 [Mini E-Commerce Order System](https://github.com/hkjs96/ordersystem)
> DDD + Hexagonal + Kafka 기반 주문 시스템

- 주문/결제/배송 상태 전이 완전 구현
- Kafka 기반 이벤트 설계 + Redis 재고 TTL 시스템 구현
- 멱등성 보장, 분산 락, 스케줄러 기반 배송 전환 처리
-->
---

## 📫 연락처

[![Gmail Badge](https://img.shields.io/badge/-Gmail-d14836?style=flat-square&logo=Gmail&logoColor=white&link=mailto:jsmini3814@gmail.com)](mailto:jsmini3814@gmail.com)
[![Blog Badge](https://img.shields.io/badge/-Tech%20Blog-20c997?style=flat-square&logo=Velog&logoColor=white&link=블로그주소)](블로그주소)
---

🙌 방문해주셔서 감사합니다.  
👨‍💻 깃허브 이슈나 메일로 언제든지 피드백 제안해주세요!
