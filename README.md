## 안녕하세요! 👋 백엔드 개발자 박지수입니다

> 🎯 **AWS 인프라 운영 경험을 바탕으로 확장 가능한 백엔드 시스템 설계·개발을 목표합니다**

### 🙋‍♂️ 저는 이런 사람입니다
- 🔭 메가존클라우드에서 **AWS 인프라 운영 및 EKS 클러스터 관리**를 담당하고 있습니다  
- 👯 **대규모 트래픽을 고려한 안정적이고 확장 가능한 백엔드 시스템 개발**에 집중하고 있습니다  
- 🔧 인프라 운영 경험을 활용해 **모니터링·장애 대응·성능 최적화**까지 고려하는 백엔드 엔지니어를 지향합니다

---

## 🧑‍💻 경력

### MegazoneCloud (2023.10 ~ 현재)
**AWS 인프라 엔지니어 | EKS 운영 및 모니터링 구축**

- **EKS 클러스터 In-Place 업그레이드 (무중단 운영)**
  - 프로덕션 환경 EKS 클러스터 1.27 → 1.28 → 1.29 업그레이드 수행
  - 사전 검증(DEV/STG) → 운영 반영(Pod Disruption Budget 기반 롤링 업데이트) → 롤백 시나리오 문서화
  - **다운타임 0분 달성**, 내부 표준 업그레이드 프로세스 수립 및 가이드 문서화

- **EKS 모니터링 체계 구축**
  - CloudWatch Container Insights + Prometheus + Grafana 기반 통합 모니터링 구축
  - 노드/파드 리소스 사용률, 애플리케이션 메트릭 대시보드 구성
  - 이상 징후 탐지 알람 설정으로 **장애 탐지 시간 평균 15분 → 3분 이내 단축**

- **운영 장애 대응 및 재발 방지**
  - 로그·지표 기반 원인 분석 및 포스트모템 작성
  - 재발 방지 관점의 자동화 스크립트 및 모니터링 개선

### FutureSense (2021.11 ~ 2023.01)
**백엔드 개발자 | 블록체인/NFT 서비스 개발**

- **기술 스택**: Node.js, Express, MongoDB, Ethereum Web3.js
- **도메인 모델링 및 REST API 설계·구현**
  - NFT 거래/이력 관리 도메인 모델링 및 ERD 설계
  - 복잡한 거래 흐름을 **트랜잭션 단위로 분리**하여 API 설계 개선 (엔드포인트 12개 → 7개로 통합)
  - RESTful API 구현 및 Swagger 문서화

- **블록체인 연동 및 데이터 정합성 관리**
  - Ethereum 스마트 컨트랙트 이벤트 리스닝 및 DB 동기화 로직 구현
  - 블록체인 트랜잭션 실패 시 재시도 및 롤백 처리 로직 설계

---

## 🎓 교육 

### 항해플러스 Backend (2024.10 ~ 2024.12)
<a href="https://hhpluscertificateofcompletion.oopy.io/">
  <img src="https://static.spartaclub.kr/hanghae99/plus/completion/badge_blue.svg" />
</a>

- **Java/Spring 기반 백엔드 심화 커리큘럼 수료**
- 트랜잭션/동시성 제어/클린 아키텍처/성능 테스트/장애 대응 실습
- 결과물은 아래 공개 레포로 정리 (과제/문서/테스트/부하테스트 포함)

### Solutions Architect 교육 (2023.02 ~ 2023.08)
- 메가존클라우드 연계 과정
- AWS Solutions Architect 트랙 중심 (VPC/IAM/EKS/RDS/모니터링)
- 클라우드 아키텍처 설계 기초 및 운영 관점(가용성/비용) 설계 훈련

---

## 🧪 항해플러스 프로젝트 (Public)

### 🔹 [hhplus-ecommerce](https://github.com/hkjs96/hhplus-ecommerce)
> **핵심 요약**: Redis 기반 랭킹/쿠폰 + DB 락 전략 적용 → k6 부하테스트 → p95/p99 기반 장애 대응 문서화

**항해플러스 이커머스 백엔드 (Week 2~10: 핵심 도메인 구현 → 동시성/Redis 적용 → 성능 테스트 & 장애 대응)**

- **아키텍처**: Layered Architecture (Presentation → Application → Domain → Infrastructure) + Redis / MySQL
  
- **핵심 기능**
  - 상품 조회/재고 관리 (Stock 분리, 이력 추적)
  - 장바구니 CRUD, 주문 생성/결제(포인트)
  - **인기 상품 랭킹**: Redis Sorted Set 기반 Top N / 특정 상품 순위 조회
  - **선착순 쿠폰 발급**: Redis(Set/String) + Lua 스크립트로 원자적 처리

- **동시성/정합성 전략**
  - 포인트 차감: **Pessimistic Lock (SELECT … FOR UPDATE)**
  - 재고 차감: **Optimistic Lock (@Version)**
  - 랭킹/쿠폰: **Redis 원자 연산 (ZINCRBY/DECR/SADD) + TTL**

- **가용성/장애 내성**
  - 주문 완료 후 **외부 데이터 플랫폼 전송을 @Async로 분리**
  - Timeout(3s) + Retry(최대 3회) + **Outbox Fallback (재시도 큐)**

- **테스트 전략 (Jacoco 94% 커버리지)**
  - Testcontainers 기반 통합 테스트 (MySQL 8.0, Redis 7.x)
  - ExecutorService + CountDownLatch로 동시성 검증
  - 단위 테스트(도메인 로직) 70% + 통합 테스트(API/DB) 30% 비율 유지

- **성능/장애 대응 산출물 (레포에 포함)**
  - `docs/week10/step19-load-test-plan.md`: 부하 테스트 시나리오/목표치/계획
  - `docs/week10/step20-incident-report.md`: p95/p99, error rate, 리소스 지표 기반 분석 + 장애 대응 문서
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
  <img src="https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white"/>
  <img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white"/>
</div>

### Infra & DevOps
<div>
  <img src="https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white"/>
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white"/>
  <img src="https://img.shields.io/badge/EKS-FF9900?style=flat-square&logo=amazoneks&logoColor=white"/>
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
> Private VPC + 멀티 AWS 계정 환경에서 통합 모니터링 구축

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

---

## 💡 주요 관심사

- 대규모 트래픽을 고려한 **확장성 있는 백엔드 아키텍처**
- **클라우드 네이티브 환경에서의 모니터링/로그/트레이싱 기반 장애 대응**
- **Kubernetes 기반 애플리케이션 배포 및 운영 자동화**

---

## 📫 연락처

[![Gmail Badge](https://img.shields.io/badge/-Gmail-d14836?style=flat-square&logo=Gmail&logoColor=white&link=mailto:jsmini3814@gmail.com)](mailto:jsmini3814@gmail.com)
[![Blog Badge](https://img.shields.io/badge/-Tech%20Blog-20c997?style=flat-square&logo=Velog&logoColor=white&link=velog.io/@hkjs96)](velog.io/@hkjs96)

---

🙌 방문해주셔서 감사합니다.  
👨‍💻 깃허브 이슈나 메일로 언제든지 피드백 제안해주세요!
