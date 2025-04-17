# 🚇 INU-IDLE Subway Congestion System (deployments)

본 레포지토리는 **INU-IDLE 지하철 혼잡도 기반 경로 탐색 서비스**의 통합 배포 환경을 관리하는 리포지토리입니다.  
혼잡도 예측 머신러닝 모델, FastAPI 서버, Spring Boot 기반의 경로 탐색 서버, 클라이언트 Flutter 앱 등  
각기 다른 서브 시스템들을 Docker 및 CI/CD 환경에서 통합 운영하기 위한 설정과 구성을 포함합니다.

---

## 📁 레포지토리 구조

```
deployments/
├── backend-server/        # FastAPI 기반 API 서버 (서브모듈)
├── congestion-server/     # 혼잡도 예측 머신러닝 서버 (서브모듈)
├── docker-compose.yaml    # 전체 시스템 통합 실행 환경 정의
├── .gitmodules            # 서브모듈 정의
└── README.md              # 현재 문서
```

backend-server와 congestion-server는 각각 별도의 GitHub 레포지토리를 서브모듈로 추가하여 관리합니다.

⸻

🚀 빠른 시작

1. 레포 클론

서브모듈을 포함하여 전체 프로젝트를 클론합니다.

```
git clone --recurse-submodules https://github.com/INU-IDLE/deployments.git
cd deployments
```

2. Docker 환경 실행 (예정)

아래 명령어로 전체 서비스 환경을 Docker Compose로 실행할 수 있습니다.

```
docker-compose up --build
```

⸻

🧠 기술 스택

| 구성 요소     | 기술                                                                   |
| ------------- | ---------------------------------------------------------------------- |
| API 서버      | FastAPI (Python)                                                       |
| ML 예측 서버  | Python + LightGBM + Pandas (Google Colab에서 개발, Docker로 전환 예정) |
| 클라이언트 앱 | Flutter (Android)                                                      |
| 데이터베이스  | PostgreSQL                                                             |
| 배포 환경     | AWS EC2, S3, Route 53 등 활용 예정                                     |
| 통합 관리     | Docker, Docker Compose, GitHub Actions (CI/CD 예정)                    |

⸻

📦 서브모듈 관리 방법

본 레포지토리는 backend-server와 congestion-server를 서브모듈로 관리하고 있습니다.
서브모듈의 내용을 초기화하거나 최신 상태로 유지하려면 다음 명령어를 사용합니다:

# 서브모듈 초기화 및 클론

```
git submodule update --init --recursive
```

# 서브모듈 갱신

```
git submodule update --remote --merge
```

각 서브모듈에서 변경이 발생하면 상위 레포인 deployments에서 해당 서브모듈의 커밋 포인터를 갱신한 후 커밋 및 푸시를 통해 반영해야 합니다. 예:

```
cd backend-server
git pull origin main  # 최신 변경사항 반영
cd ..
git add backend-server
git commit -m "Update backend-server submodule"
git push origin main
```

이 과정을 통해 여러 개발자가 동시에 독립적인 레포지토리에서 작업하면서도, deployments 레포에서 일관된 상태로 서비스 전체를 통합하고 관리할 수 있습니다.

⸻

🛠 개발 중 기능

- 서버/클라이언트/ML 각 레포 분리 및 서브모듈 통합
- 기본 Docker Compose 환경 설계
- CI/CD 파이프라인 구축 (GitHub Actions 예정)
- AWS 상용 서버 배포
- 클라이언트 빌드 자동화 및 앱 배포 연결

⸻
