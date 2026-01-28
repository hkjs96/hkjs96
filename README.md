# 안녕하세요! 👋 문제를 해결하는 백엔드 엔지니어, 박지수입니다.

> 🎯 **"견고한 인프라 위에 유연한 서비스를 쌓아 올립니다."**
>
> **비효율적인 프로세스**와 **구조적 한계**를 기술로 극복하며, <br>
> 가장 합리적이고 단단한 소프트웨어를 만듭니다.

<br>

## 🙋‍♂️ About Me

- 🔭 **Efficiency:** 메가존클라우드 매니저로서 **운영 자동화(92% 시간 단축)**와 **비용 최적화(연 $24k 절감)**를 주도했습니다.
- 👯 **Stability:** 대규모 트래픽 환경의 **동시성 제어(Redis)**와 **데이터 정합성 100%**를 보장하는 설계를 지향합니다.
- 🔧 **Visibility:** **Prometheus/Grafana/Athena** 기반의 관제 시스템을 직접 구축하여 장애를 조기에 감지하고 대응합니다.

<br>

---

## 🧑‍💻 Work Experience

### **MegazoneCloud** (2023.10 ~ 현재)
**AWS Infrastructure Manager | Cloud Operations & FinOps**

> *엔터프라이즈 고객사(삼성물산, 현대오토에버 등)의 인프라 운영 및 기술 지원 총괄*

- **[자동화] Python 기반 모니터링 알람 생성 스크립트 개발 (설정 시간 6h → 30m, 92% 단축)**
  - 반복적인 CloudWatch 설정을 코드화(IaC)하여 운영 리소스를 절감하고 휴먼 에러 제로화

- **[트러블슈팅] AWS Network Firewall 비대칭 라우팅 이슈 해결 (통신 성공률 100% 확보)**
  - 멀티 AZ 환경의 패킷 드롭(Drop) 현상을 트래픽 분석으로 규명하고, 라우팅 경로 최적화 수행

- **[비용최적화] 상용 APM(SaaS) → OSS 관제 시스템 전환 (연간 $24,000 절감)**
  - Prometheus/Grafana/Loki 스택을 직접 구축하여 라이선스 비용 제거 및 커스텀 대시보드 가시성 확보

- **[유지보수] 비용 효율적인 EKS In-Place 업그레이드 및 PM 수행**
  - 고비용 Blue/Green 대신 Rolling Update 전략과 PDB 설정을 통해 무중단 배포 및 비용 효율성 동시 달성

<br>

### **FutureSense** (2021.11 ~ 2023.01)
**Backend Developer | Blockchain & NFT Platform**

- **🚀 AWS SQS 비동기 아키텍처 도입 (API 응답 4.5s → 1.0s, 78% 개선)**
  - 블록체인 합의 지연으로 인한 Blocking 현상을 Event-Driven 구조로 해결하여 사용자 경험 개선

- **🌍 CloudFront CDN 글로벌 캐싱 적용 (로딩 속도 22s → 4s, 82% 향상)**
  - 유럽 지역 사용자의 접속 지연 문제를 해결하기 위해 엣지 로케이션 캐싱 전략 도입

- **🛡️ Jest 테스트 자동화 파이프라인 구축**
  - 복잡한 NFT 경매/거래 로직의 신뢰성 확보를 위해 단위/통합 테스트 도입 (수동 검증 시간 90% 단축)

<br>

---

## 🧪 Featured Projects

### 🔹 [이커머스 서버 아키텍처 고도화 (항해플러스)](https://github.com/hkjs96/hhplus-ecommerce)
> **대규모 트래픽(1,000 TPS) 환경에서의 동시성 제어 및 아키텍처 진화 프로젝트**
> <br> *Stack: Java 17, Spring Boot 3.x, Redis, MySQL, Docker, Testcontainers*

**1. 동시성 제어 및 데이터 정합성 100% 보장**
- **(Challenge)** 선착순 쿠폰 발급 시 Race Condition으로 인한 재고 초과 발행(Overselling) 문제
- **(Solution)** **Redis Distributed Lock (Redisson)** 도입 및 대기열 로직 구현으로 1,000 TPS 부하 상황에서도 정합성 확보
- **(Detail)** 상황별 락 전략 최적화: 포인트(비관적 락), 재고(낙관적 락), 선착순(분산락)

**2. 아키텍처 리팩토링 (Layered → Event-Driven)**
- **(Challenge)** 서비스 계층 비대화 및 강한 결합도(Coupling)로 인한 유지보수 저하
- **(Solution)** **UseCase 패턴**으로 애플리케이션 책임을 분리하고, **TransactionalEventListener**를 통해 트랜잭션과 후속 로직(알림 등)을 비동기 분리

**3. Testcontainers 기반의 신뢰성 있는 테스트 환경**
- **(Challenge)** H2(인메모리)와 운영 DB(MySQL) 간의 동작 차이로 인한 거짓 양성(False Positive) 문제
- **(Solution)** Docker 기반의 격리된 통합 테스트 환경을 구축하여 락(Lock) 동작 및 동시성 시나리오 완벽 검증

<br>

### 🔹 [Private Multi-Account 모니터링 시스템](https://github.com/hkjs96/private-multiaccount-monitoring)
> **폐쇄망(Private) 및 멀티 계정 환경을 위한 통합 관제 아키텍처 구축**

- **VPC Peering & Grafana Agent**를 활용한 계정 간 메트릭/로그 중앙 집중화 설계
- 보안 컴플라이언스를 준수하며 다수 계정의 리소스 현황을 단일 대시보드에서 시각화

<br>

---

## 🛠 Tech Stack

| Category | Skills |
| :--- | :--- |
| **Backend** | ![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![JPA](https://img.shields.io/badge/JPA-59666C?style=flat-square&logo=hibernate&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white) |
| **Infrastructure** | ![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white) ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white) |
| **Database & Cache** | ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white) |
| **Observability** | ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white) ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white) ![Athena](https://img.shields.io/badge/AWS%20Athena-232F3E?style=flat-square&logo=amazonaws&logoColor=white) |

<br>

---

## 📫 Contact

- **Email:** [jsmini3814@gmail.com](mailto:jsmini3814@gmail.com)
- **Blog:** [velog.io/@hkjs96](https://velog.io/@hkjs96)
- **GitHub:** [github.com/hkjs96](https://github.com/hkjs96)
