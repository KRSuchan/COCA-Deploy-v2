# 📆COCA Deploy v2

COCA 프로젝트의 배포를 위한 리포지토리입니다. 이 리포지토리는 CI/CD, Docker, EC2, Nginx 등을 통해 [백엔드(Spring Boot 기반)](https://github.com//KRSuchan/COCA-Backend-v2/)와 [프론트엔드(React 기반)](https://github.com//KRSuchan/COCA-Frontend-v2/)를 통합 배포하고 있습니다.

#### COCA 프로젝트 페이지 : [https://coca-project.site](https://coca-project.site)

version : 202505261422

---

## 📦 시스템 개요

### 백엔드 (COCA Backend v2)

-   **주요 기술 스택**: Spring Boot, Spring Security, JWT (with Redis), MySQL
-   **CI**: GitHub Actions 기반 자동 빌드
-   **Docker 이미지**: CI 단계에서 자동으로 생성되어 DockerHub에 업로드
-   **기능**:
    -   Spring Security 기반 인증/인가
    -   Redis를 이용한 JWT 토큰 관리
    -   RDS(MySQL) 연동
-   GitHub : [`COCA-Backend-v2`](https://github.com/KRSuchan/COCA-Backend-v2)

### 프론트엔드 (COCA Frontend v2)

-   **주요 기술 스택**: React, Nginx
-   **CI**: GitHub Actions 기반 자동 빌드
-   **Docker 이미지**: CI 단계에서 자동으로 생성되어 DockerHub에 업로드
-   GitHub : [`COCA-Frontend-v2`](https://github.com//KRSuchan/COCA-Frontend-v2)

---

## 🚀 배포 구조 (CD)

-   **도메인 관리**: AWS Route 53
-   **HTTPS 구성**: AWS Application Load Balancer + ACM을 통해 TLS 인증서 적용
-   **도메인**: [`https://coca-project.site`](https://coca-project.site)
-   **CD 리포지토리**: `coca-deploy-v2` (본 리포지토리)
-   **배포 환경**: AWS EC2 (Ubuntu 기반)
-   **Docker Compose** 기반 전체 시스템 통합 운영

---

## 📁 리포지토리 구성

```
coca-deploy-v2/
├── docker-compose.yml     # 전체 서비스 구성
├── .github/workflows/
│   └── deploy.yml
│   .gitignore
└── README.md               # 현재 문서
```

---

## 🔐 인증 및 보안

-   HTTPS 적용: **AWS Route 53 + Application Load Balancer (ALB)**를 이용한 TLS 인증서 구성 (ACM 활용)
-   사용자 도메인 `https://coca-project.site`은 Route 53을 통해 ALB로 연결
-   JWT 기반 인증 토큰 관리: Redis 연동

---

## 🔄 CI/CD 흐름 요약

1. **백엔드/프론트엔드 레포지토리**에서 GitHub Actions로 CI 수행
2. 빌드된 결과물은 Docker 이미지로 만들어 **DockerHub에 업로드**
3. 이 `coca-deploy-v2` 리포지토리의 GitHub Actions(`deploy.yml`)에서 CD 수행
4. EC2 서버에서 `docker-compose`로 전체 시스템 자동 배포

---

## 🌐 서비스 주소

-   **Domain**: [https://coca-project.site](https://coca-project.site)

---

## 🛠 주요 사용 기술

-   Spring Boot / Spring Security / JWT / Redis / MySQL
-   React / Nginx
-   Docker / Docker Compose
-   GitHub Actions (CI/CD)
-   AWS EC2 / RDS
-   HTTPS
