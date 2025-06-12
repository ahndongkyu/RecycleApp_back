# 불쑥 (Bulssuk) - Backend 🛠

불쑥(Bulssuk)은 분리수거를 보다 쉽고 재미있게 실천할 수 있도록 돕는 AI 기반 환경 보호 앱입니다.  
이 저장소는 Flutter 프론트엔드 앱과 연동되는 백엔드 API 서버입니다.  
사용자 인증, 배출일 캘린더, 나무 키우기 gamification, 관리자 기능 등을 제공합니다.

---

## 🚀 주요 기능

- ✅ 사용자 회원가입, 로그인 (JWT 인증)
- ✅ 나무 키우기(gamification) 기반 포인트 시스템
- ✅ 분리수거 배출일 등록 및 조회 (캘린더 기능)
- ✅ 관리자용 통계/FAQ/제품/회사 관리
- ✅ 사용자/판매자/관리자 역할 분리
- ✅ PostgreSQL 연동 및 Docker 지원

---

## 📁 폴더 구조
```
recycle_back_dk/
├── controllers/               # 기능별 비즈니스 로직
│   ├── admin/                 # 관리자 기능
│   │   ├── calendarController.js
│   │   ├── productController.js
│   │   ├── dashboardController.js
│   │   ├── companyController.js
│   │   └── faqController.js
│   ├── user/                  # 일반 사용자 기능
│   └── recycleController.js   # 분리수거 관련 기능
│
├── routes/                    # 각 기능별 라우터
│   ├── adminRoutes.js
│   ├── userRoutes.js
│   └── recycleRoutes.js
│
├── database/
│   └── database.js            # PostgreSQL 연결
│
├── middleware/
│   ├── authenticateToken.js  # JWT 인증 처리
│   └── middleware.js         # 공통 미들웨어
│
├── scheduler.js               # 예약 작업 처리 (예: 나무 성장)
├── index.js                   # 서버 실행 진입점
├── Dockerfile                 # Docker 설정
├── .env                       # 환경변수
├── package.json               # 의존성 목록
└── .gitignore
```

---

## 🔐 인증 구조

- 로그인 시 JWT 발급
- `authenticateToken.js`에서 토큰 검증 후 인증 처리
- 모든 민감 API에 인증 미들웨어 적용 (`/mypage`, `/tree`, `/calendar` 등)

---

## 🔗 주요 API 예시

| 메서드 | 경로 | 설명 |
|--------|------|------|
| `POST` | `/login` | 사용자 로그인 및 JWT 발급 |
| `GET`  | `/calendar` | 분리수거 일정 조회 |
| `POST` | `/tree/water` | 나무 물주기 이벤트 |
| `GET`  | `/dashboard/stats` | 관리자용 통계 데이터 |
| `GET`  | `/faq` | FAQ 목록 조회 |

---

## ⚙️ 실행 방법

### 1. 의존성 설치
```bash
npm install
```

### 2. 환경변수 설정
`.env` 예시:
```env
PORT=8080
DB_HOST=localhost
DB_PORT=5432
DB_USER=bulssuk_user
DB_PASSWORD=your_password
DB_NAME=bulssuk_db
JWT_SECRET=your_jwt_secret
```

### 3. 서버 실행
```bash
node index.js
```

---

## 🐳 Docker 실행

```bash
docker build -t bulssuk-backend .
docker run -p 8080:8080 bulssuk-backend
```

---

## 👥 기여자 및 역할 분담

| 이름     | 담당 영역                          |
|----------|-------------------------------------|
| **정현지** | 인프라 구축, 전체 프로젝트 총괄, DB 설계 |
| **안동규** | Node.js 백엔드 개발, Flutter 프론트엔드, DB |
| **이혜연** | Node.js 백엔드 개발, DB |
| **최민경** | Node.js 백엔드 개발, Flutter 프론트엔드, DB |
| **심건우** | Python 기반 AI (LLM), MLflow 모델 관리 |

---

## 📄 라이선스

MIT License
