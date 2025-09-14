# 🍳 다모아요리학원 (Damoa Cook Academy)

<p align="center">
  <img src="./assets/damoacook.png" alt="Damoa Cook Academy Cover" width="720">
</p>

<p align="center">
  <a href="https://damoacook.com"><img alt="Website" src="https://img.shields.io/badge/Website-live-2ea44f?style=flat"></a>
  <img alt="React" src="https://img.shields.io/badge/React-18-61DAFB?style=flat">
  <img alt="Vite" src="https://img.shields.io/badge/Vite-4-646CFF?style=flat">
  <img alt="TailwindCSS" src="https://img.shields.io/badge/TailwindCSS-3-06B6D4?style=flat">
  <img alt="Django" src="https://img.shields.io/badge/Django-5-092E20?style=flat">
  <img alt="DRF" src="https://img.shields.io/badge/DRF-REST_API-red?style=flat">
  <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-14%2B-4169E1?style=flat">
  <img alt="Render" src="https://img.shields.io/badge/Render-backend-46E3B7?style=flat">
  <img alt="Vercel" src="https://img.shields.io/badge/Vercel-frontend-000000?style=flat">
  <img alt="Naver Object Storage" src="https://img.shields.io/badge/Naver_Object_Storage-S3-03C75A?style=flat">
</p>



- 학원 소개/강의 안내/공지·갤러리/수강문의 기능을 제공하는 **다모아요리학원 공식 웹사이트**입니다.  
- HRD-Net(공공데이터) 연동, 네이버 지도/스토리지, 문의 이메일 전송 등 **실서비스 운영 기능**을 갖췄습니다.

---

## 🔗 배포 & 접근
- **웹사이트**: https://damoacook.com  
- **관리자/테스트 계정**: 내부 운영용으로 비공개 (일반 사용자는 로그인 불필요)
- **백엔드레포**: https://github.com/damoacook/damoacook-back/tree/main

---

## 📜 목차
- [프로젝트 소개](#-프로젝트-소개)
- [개발 환경](#-개발-환경)
- [채택 기술](#-채택-기술)
- [프로젝트 구조](#-프로젝트-구조)
- [역할(개인 프로젝트)](#-역할개인-프로젝트)
- [개발 기간](#-개발-기간)
- [신경 쓴 부분](#-신경-쓴-부분)
- [페이지별 기능](#-페이지별-기능)
- [트러블 슈팅](#-트러블-슈팅)
- [개선 목표](#-개선-목표)
- [설치 & 실행](#-설치--실행)
- [API 요약](#-api-요약)
- [운영/보안 체크리스트](#운영보안-체크리스트)
- [라이선스](#라이선스)

---

## 📘 프로젝트 소개
- **서비스명**: 다모아요리학원 홈페이지  
- **목표**
  - 학원 브랜드/커리큘럼 명확 전달, 수강 문의 흐름 최적화
  - HRD-Net 등 **외부 데이터 연동**으로 최신 정보 제공
- **핵심 가치**
  - 콘텐츠 관리 효율(Django Admin)
  - 가벼운 프론트(React+Vite) / 빠른 배포(Vercel)
  - 확장 가능한 미디어 관리(Naver Object Storage)

---

## 🛠 개발 환경
- **Frontend**: React 18, Vite, Tailwind CSS, React Router, React Query  
- **Backend**: Django 5, Django REST Framework, SimpleJWT(관리자 인증)  
- **Infra**: Vercel(프론트), Render(백엔드), PostgreSQL, **Naver Object Storage(S3)**  
- **지도/메일**: Naver Maps JS v3, Naver SMTP  
- **이슈/보드**: GitHub Issues/Projects

---

## ⚙ 채택 기술
### React + Vite + Tailwind
- **Vite**: dev 서버 기동/핫리로드 체감 속도 ↑, 빌드 구성 단순.
- **Tailwind**: 유틸리티 클래스 기반으로 디자인 토큰 공유가 쉬움 → **일관성** 확보, CSS 전역 충돌 리스크 ↓.
- **React Query**: HRD-Net/뉴스/갤러리 등 **읽기 중심 API**에 캐싱/리트라이/에러 경계 제공 → 사용자 체감 속도 ↑.

### Django + DRF
- **Admin**이 강력: 강의/공지/갤러리/팝업을 비개발자도 즉시 운영 가능.
- **DRF**의 시리얼라이저/권한/페이지네이션이 규격화돼 있어 유지보수 비용 ↓.
- **SimpleJWT**: 공개 API와 관리자용 API를 분리해 **최소 권한 원칙** 적용.

### Vercel + Render + Naver Object Storage
- **FE/BE 분리 배포**: 장애 범위 분리, 롤백/프리뷰 편리.
- **Object Storage(S3)**: Render는 로컬 디스크 휘발성 → **이미지 영속성/서빙 성능**을 위해 외부 스토리지 채택.
---

## 🧱 프로젝트 구조
# Front
```
┣ 📂api (axios 래퍼/각 도메인 fetch)
┣ 📂assets
┣ 📂components (공용 UI 컴포넌트)
┣ 📂contexts
┣ 📂data (정적 데이터: 자격증/파트너)
┣ 📂lib (네이버맵 loader 등)
┣ 📂pages (Home, Lectures, Community, Inquiry, Login ...)
┣ 📂routes (권한 경로)
┣ 📂sections (홈/CTA 섹션)
┣ 📜App.jsx / main.jsx / index.css ...
```
# Back
```
📦apps
┣ about / accounts / certificates / gallery / inquiries / lectures / news / popup
📦config
┣ settings.py / urls.py / wsgi.py
```

## 👤 역할(개인 프로젝트)
- **기획·디자인·프론트·백엔드·배포·모니터링** 전 과정 단독 수행
- 도메인 모델링, Admin 구성, 문의 메일 연동, 배포 자동화, CORS/보안 헤더 설정

---

## 🗓 개발 기간
- **2025-07 ~ 2025-09**

---

## ✨ 신경 쓴 부분
- **문의 전송 신뢰성**
  - 흐름을 **DB 저장 → SMTP 발송**의 2단계로 분리하여, 메일 실패가 접수 데이터 유실로 이어지지 않도록 설계.
  - (현재) 동기 처리이며 **예외 로깅은 미도입**. 로컬 개발에서는 `console EmailBackend`로 플로우만 검증.
  - (운영 예정) `fail_silently=False` + **구조적 로깅/알림**(예: Sentry, 관리자 메일) 적용, 재발송 트리거 분리(Celery 도입 검토).

- **공공데이터 연동**
  - **HRD-Net** 강의 데이터 연동 후 프론트에서는 **React Query**로 캐시·재시도·에러 경계 제공.
  - 외부 API 장애 시 사용자에게 스켈레톤/오류 메시지 노출, 내부 강의 데이터로 **폴백**.
  - (확장) **Q-NET** 시험 일정/원서접수 정보 연계 준비(환경변수/키 구조 반영 완료).

- **데이터 신선도 & 프론트 성능**
  - React Query의 **stale-while-revalidate** 전략으로 체감 속도 개선.
  - 이미지 **Lazy Loading** + 명시적 `width/height`로 **CLS 억제**.

- **운영 편의**
  - 팝업 배너(오늘 하루 보지 않기), 관리자 전용 에디터(공지/갤러리), 브레드크럼, 반응형 레이아웃.

- **안전한 통신**
  - CORS 화이트리스트, **Vercel 프리뷰 정규식 허용**, CSRF Trusted Origins.
  - HTTPS 프록시 헤더 인지(`SECURE_PROXY_SSL_HEADER`), 해시 기반 정적 서빙(WhiteNoise).

---


## 📱 페이지별 기능

### 홈 (Home)
- 모집중 강의 슬라이드, 공지/갤러리 하이라이트
- ![home](./assets/메인화면.gif)

### 학원소개 (abouut)
- 학원 인사말, 연혁, 비전, 시설소개, 협력업체, 오시는길 안내
- ![Lectures](./assets/학원소개.gif)

### 강의 (Lectures)
- 내부 강의 목록/상세, **HRD-Net 연동 강의** 정보 제공
- ![Lectures](./assets/모집과정.gif)

### 공지/갤러리 (News/Gallery)
- 목록/상세, 이미지 S3 저장/서빙
- ![news](./assets/공지사항.gif)

### 수강문의 (Inquiry)
- 무로그인 폼 제출 → **이메일 알림**
- ![Inquiry](./assets/수강문의.gif)

### 오시는 길 (Map)
- **Naver Maps JS v3**로 위치 안내
- ![map](./assets/학원위치안내.gif)

### 팝업배너 (Popup)
- **팝업배너**로 이벤트 및 소식 안내
- ![Popup](./assets/팝업배너.gif)

---

## 🧩 트러블 슈팅
### 1) 201인데 수강문의 메일이 오지 않음

- **증상**  
  `POST /api/inquiries/`가 201(저장 성공)을 반환하지만, 실제 수신 메일이 없음.

- **원인 분석**  
  - Naver SMTP 정책상 **From 주소 ≠ 로그인 계정(EMAIL_HOST_USER)** 인 경우 차단 가능.  
  - `DEFAULT_FROM_EMAIL`에 큰따옴표 등 **헤더 포맷 오류**.  
  - TLS/포트 설정 불일치 + 애플리케이션에서 예외를 묵살(기본 `fail_silently=True` 관성).

- **조치**  
  - 운영 환경변수 교정: `EMAIL_USE_TLS=True`, `EMAIL_PORT=587`, **From = EMAIL_HOST_USER 동일화**.  
  - `DEFAULT_FROM_EMAIL`을 `다모아요리학원 <id@naver.com>` 형태로 규격화(큰따옴표 제거).  
  - 수신자 다중화: `INQUIRY_TO_EMAILS`로 운영/관리자 복수 수신 구성.  
  - 개발·검증 단계는 **콘솔 메일 백엔드**로 교체하여 헤더/본문 즉시 확인.  

- **결과**  
  동일 테스트 데이터로 201 응답 ↔ 실제 수신 이벤트 **일치** 확인.  
  (SMTP 측 Bounce/Drop 재발 없음)

---

### 2) HRD-Net(Work24) 목록 호출 콜드 스타트 지연

- **증상**  
  외부 API 최초 호출 시 네트워크/파싱 지연으로 **2초대 스파이크** 발생.

- **백엔드 조치**  
  메모리 캐시 + 스냅샷 폴백: 목록 TTL 10분, 상세 TTL 30분
  계측 헤더 추가: X-Elapsed-ms(서버 처리 ms) / X-Cache = MISS | REFRESH | HIT-FALLBACK

- **프론트 조치**
  React Query 캐시/리트라이/에러 경계 + 스켈레톤 UI로 사용자 체감 개선

- **측정 결과(로컬 30회 연속 호출)**

  | 구간         | Avg(ms) | P50(ms) | Max(ms)  |
  |--------------|---------|---------|----------|
  | 최적화 전    | 132.4   | 56.4    | 2184.3   |
  | 최적화 후    | 64.7    | 55.7    | 142.9    |

  - **평균 응답**: 132.4 → 64.7ms (**약 51% 단축**)  
  - **최악 응답(콜드 스타트)**: 2184.3 → 142.9ms (**약 93% 단축**)  
  - 동일 머신/로컬 네트워크 기준. 외부망/시간대에 따라 수치는 변동 가능.

---

### 3) Vercel 프리뷰에서 CORS/CSRF 프리플라이트 실패

- **증상**  
  프리뷰 도메인에서만 `OPTIONS`(preflight) 403, 후속 `GET/POST`도 차단.

- **원인 분석**  
  - 프리뷰 오리진이 **CORS 허용 목록/정규식**에 포함되지 않음.  
  - `CSRF_TRUSTED_ORIGINS`에 프리뷰 도메인 누락.  
  - 프록시 HTTPS 인지 미설정 시 CSRF 판단이 오작동할 여지.

- **조치**  
  - `CORS_ALLOWED_ORIGIN_REGEXES`에 `^https://.*\.vercel\.app$` 추가.  
  - `CSRF_TRUSTED_ORIGINS`에 운영 도메인 + 프리뷰 와일드카드 반영.  
  - `SECURE_PROXY_SSL_HEADER=("HTTP_X_FORWARDED_PROTO","https")` 설정 확인.

- **결과**  
  프리뷰/프로덕션 모두 정상 동작

---

### 4) 수강문의 API 남용(스팸/폭주) 예방

> 프러덕션 안정성을 위해 **서버 사이드**에서 1차 방어를 적용했고, 추가 방어는 단계적으로 확대 중입니다.

- **위험 시나리오**  
  자동화된 봇/스크립트가 `POST /api/inquiries/`를 대량 호출 → SMTP 큐 폭주/알림 테러 위험.

- **적용(1차)**  
  - **서버 검증 강제**: `name(max_length=100)`, `phone(max_length=20)`, `message(Text)` 길이 제한 및 필수값 체크.  
  - **Payload 중복 차단**: 동일 `(name, phone, message)` 조합 **60초 내 재요청 차단**(디듀프).  
  - **IP 기반 레이트 리미트**: **5회/10분** 초과 시 **429** 응답(캐시 기반).  
  - **SMTP 경로 분리**: DB 저장과 메일 발송 경로를 분리하여, 발송 실패가 API 응답시간을 지연시키지 않도록 처리.

- **추가 계획(2차)**  
  - **reCAPTCHA/Turnstile** 도입(봇 트래픽 차단)  
  - **전화번호 패턴/통신사 블랙리스트** 기반 정교화  
  - **관리자 재발송 큐**(지연·실패 재시도, 폭주 시 유예 정책)
 
---


### 5) 정적 자원 캐시 불일치(배너 교체 후 구버전 노출)**
- **증상**: 배너 이미지를 교체했지만 일부 사용자에게 구버전 노출.  
- **해결**  
  - 백엔드: `CompressedManifestStaticFilesStorage`로 **해시 기반 파일명** 서빙  
  - 프론트: 빌드 산출물 파일명 해시 + Vercel 캐시 무효화  
- **결과**: 배포 직후 일관된 최신 파일 제공.

### 6) 프론트 성능/UX(체감 품질)**
- 에러/로딩 UX: 스켈레톤, 에러 경계 도입 → 외부 API 지연에도 부드러운 전환
- 품질 지표: Lighthouse Best Practices/SEO 85~100 목표 운영

---

## 🚀 개선 목표
- **백엔드 로직 성능 최적화(우선 과제)**
  - 쿼리 **N+1 제거**(`select_related`, `prefetch_related`) 및 DRF 시리얼라이저 비용 절감.
  - **인덱스/정렬 최적화**(공지·갤러리 최신순 페이지네이션), 연결 풀/`conn_max_age` 튜닝.
  - **읽기 캐시**(Redis)와 조건부 캐싱(ETag/Last-Modified) 적용 검토.
  - 요청/응답 **프로파일링**(쿼리 로그, Django toolbar in dev)로 병목 지점 식별.

- **비동기 처리**
  - **Celery + Redis**로 문의 메일 발송/HRD 동기화를 백그라운드화.
  - 재시도(지수 백오프)·서킷브레이커로 외부 API 불안정성 완충.

- **공공데이터(시험) 연계 강화**
  - **Q-NET** 시험 일정/원서접수 정보 주기 수집(야간 배치) + **백업 루트**(PDF 파싱/크롤 백업).
  - 학원 강의와 시험 일정을 **매칭**해 응시 타이밍 가이드 제공.

- **시험 커뮤니티 게시판**
  - 카테고리(후기/팁/자료) + **태그/검색**, 마크다운 에디터, 이미지 업로드(S3).
  - 좋아요/댓글/신고 및 **모더레이션**(관리자 승인/블락).

- **공지/갤러리 리치 텍스트 CMS(블로그 형식)**
  - **목표**: 공지/갤러리를 블로그처럼 운영—**하이퍼링크(하이퍼 텍스트)**로 외부/내부 문서 이동, **글자 크기/색상/글꼴** 제어, 이미지 자유 삽입.
  - **에디터 후보**: tiptap / Quill / Editor.js (모바일 터치 최적화, 툴바 커스텀).
  - **지원 포맷**:  
    - 저장: **HTML(+서버 Sanitize)** 또는 **Markdown(+remark/rehype 파이프라인)**  
    - 보안: **bleach/owasp rules**로 허용 태그/속성 화이트리스트, `rel="noopener"`·`target="_blank"`.
  - **이미지/첨부**: 드래그&드롭 업로드 → **S3 저장**, 썸네일/리사이즈·WebP 생성, 캡션/정렬 지원.
  - **퍼블리싱/SEO**: 슬러그 자동화, **예약 발행/초안**, OG 메타/트위터 카드, 사이트맵 반영.
  - **권한/이력**: 작성/검수/발행 롤, **버저닝/롤백**(history), 미리보기 URL.
  - **마이그레이션**: 기존 `content` → 리치 텍스트로 점진 전환(스크립트 변환/혼용 기간 운영).

- **프론트/정적 자원 최적화**
  - Lighthouse Best Practices/SEO **90~100 유지**, **LCP/CLS** 개선 지속.
  - 이미지 **WebP/AVIF** 파이프라인, 썸네일 변환, 프리커넥트/프리로드, 에지 캐시 정책 정교화.

- **가시성(Observability)**
  - 에러 트래킹(Sentry), 접근/응답 시간 로그, 알림 채널 정비(Slack/메일).

---

## 🧪 설치 & 실행

### 사전 요구사항
- Node.js **>= 20**
- Python **>= 3.12**
- PostgreSQL **>= 14**

---

### 1) 프론트엔드
```bash
cd frontend
npm i

# 로컬 API 사용 시 .env.local 생성
#   frontend/.env.local
#   VITE_API_BASE="http://localhost:8000/api"

npm run dev   # http://localhost:5173
# 프로덕션 빌드: npm run build
```

### 2) 백엔드 (PostgreSQL)
```bash
cd backend

# 가상환경 & 의존성
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows PowerShell
# .\.venv\Scripts\Activate.ps1

pip install -r requirements.txt

# ── 환경변수 설정 ──
# macOS/Linux
export DATABASE_URL="postgresql://USER:PASS@HOST:5432/DBNAME"
# 개발 중 실제 메일 발송이 부담되면 콘솔 메일 백엔드 사용
export EMAIL_BACKEND="django.core.mail.backends.console.EmailBackend"

# Windows PowerShell
# $env:DATABASE_URL="postgresql://USER:PASS@HOST:5432/DBNAME"
# $env:EMAIL_BACKEND="django.core.mail.backends.console.EmailBackend"

# DB 마이그레이션 & 서버 실행
python manage.py migrate
python manage.py runserver 0.0.0.0:8000
# 로컬 API: http://localhost:8000/api
# Swagger:   http://localhost:8000/api/docs/
```

## 🔎 API 요약
> 공개 API는 인증 없이 접근, **관리자용 엔드포인트는 JWT 필요**  
> 로컬: http://localhost:8000/api/docs/

---

### 1) 수강문의 (무로그인)
`POST /api/inquiries/`  
요청(모델 기준):
```json
{
  "name": "홍길동",        // 최대 100자
  "phone": "010-1234-5678", // 최대 20자
  "message": "한식 기능사 과정 문의합니다."
}

성공(201):

{
  "id": 5301,
  "name": "홍길동",
  "phone": "010-1234-5678",
  "message": "한식 기능사 과정 문의합니다.",
  "created_at": "2025-09-01T10:11:12+09:00"
}


유효성 오류(예):

{
  "phone": ["이 필드는 최대 20자 이하이어야 합니다."]
}
```

2) 강의 (내부 DB)

GET /api/lectures/?page=1&page_size=12
응답(요약):
```json
{
  "count": 42,
  "next": "https://damoacook.com/api/lectures/?page=2&page_size=12",
  "previous": null,
  "results": [
    {
      "id": 101,
      "type": "academy",           // "academy" | "hrd"
      "title": "한식 기능사 실기",
      "description": "과정 설명...",
      "image": "https://.../media/lectures/xxx.jpg",  // ImageField URL
      "tags": "한식,실기",
      "day_of_week": "월/수/금",
      "time": "14:00~16:00",
      "start_date": "2025-09-15",
      "end_date": "2025-10-30",
      "capacity": 20,
      "applied": 7,
      "created_at": "2025-08-20T12:00:00+09:00"
    }
  ]
}
```

GET /api/lectures/{id}/
응답(예):
```json
{
  "id": 101,
  "type": "academy",
  "title": "한식 기능사 실기",
  "description": "과정 설명...",
  "image": "https://.../media/lectures/xxx.jpg",
  "tags": "한식,실기",
  "day_of_week": "월/수/금",
  "time": "14:00~16:00",
  "start_date": "2025-09-15",
  "end_date": "2025-10-30",
  "capacity": 20,
  "applied": 7,
  "created_at": "2025-08-20T12:00:00+09:00"
}
```


3) HRD-Net 강의(연동)

GET /api/hrd-lectures/?q=한식&region=서울&page=1

HRD-Net 외부 데이터 연동 결과를 페이지네이션하여 제공

응답 필드는 연동 스키마에 맞춰 다를 수 있습니다(예: 과정명, 기관명, 지역, 접수/개강일, 상세링크 등).
```json
{
  "count": 120,
  "next": "...",
  "previous": null,
  "results": [
    {
      "id": "HRD-24-0001",
      "title": "한식 조리기능사 취득과정",
      "provider": "○○직업학교",
      "region": "서울",
      "start_date": "2025-09-10",
      "link": "https://www.hrd.go.kr/..."
    }
  ]
}
```
4) 공지/갤러리

GET /api/news/ / GET /api/news/{id}/

GET /api/gallery/ / GET /api/gallery/{id}/

목록 응답(요약):
```json
{
  "count": 10,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": 301,
      "title": "9월 모집 안내",
      "thumbnail": "https://.../thumb.jpg",
      "created_at": "2025-08-31T20:00:00+09:00"
    }
  ]
}
```

상세 응답(예):
```json
{
  "id": 301,
  "title": "9월 모집 안내",
  "content": "<p>상세 공지 본문...</p>",
  "images": ["https://.../1.jpg", "https://.../2.jpg"],
  "created_at": "2025-08-31T20:00:00+09:00"
}
```
🔐 인증(관리자용)

JWT Bearer 토큰 사용 (SimpleJWT)
Swagger UI 우상단 Authorize → Bearer <JWT> 입력 후 보호 엔드포인트 시도 가능

## 운영/보안 체크리스트

- 비밀값(DB/SMTP/S3/API 키 등)은 환경변수로만 주입(레포 내 노출 금지)
- 업로드 파일은 S3 저장, 정적은 WhiteNoise 해시 서빙
- 관리자 API는 JWT로 보호, 토큰 만료/권한 점검

## 라이선스
- 본 저장소는 UNLICENSED 상태이며, 학원 서비스 운영을 위한 목적으로만 사용합니다.
