# 다모아요리학원 (Damoa Cook Academy) — Organization Profile

<p align="center">
  <img src="./profile/assets/logo.png" alt="Damoa Cook Academy Logo" width="300" />
</p>

<p align="center">
  <a href="https://damoacook.com"><img alt="Website" src="https://img.shields.io/badge/website-live-2ea44f"></a>
  <img alt="Python" src="https://img.shields.io/badge/Python-3.12%2B-3776AB?logo=python&logoColor=white">
  <img alt="Django" src="https://img.shields.io/badge/Django-5.x-092E20?logo=django&logoColor=white">
  <img alt="DRF" src="https://img.shields.io/badge/DRF-REST_API-red">
  <img alt="React" src="https://img.shields.io/badge/React-18-blue?logo=react&logoColor=white">
  <img alt="Tailwind" src="https://img.shields.io/badge/Tailwind-CSS-06B6D4?logo=tailwindcss&logoColor=white">
  <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-14%2B-4169E1?logo=postgresql&logoColor=white">
  <img alt="Vercel" src="https://img.shields.io/badge/Frontend-Vercel-000000?logo=vercel&logoColor=white">
  <img alt="Render" src="https://img.shields.io/badge/Backend-Render-46E3B7?logo=render&logoColor=white">
  <img alt="License" src="https://img.shields.io/badge/license-UNLICENSED-lightgrey">
</p>

<p align="center">
  <!-- 방문자 카운터: url 파라미터를 조직 프로필 또는 웹사이트로 맞추세요 -->
  <a href="https://hits.seeyoufarm.com">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdamoacook.com&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=visits&edge_flat=false" alt="hits"/>
  </a>
</p>

> 다모아요리학원은 학원 소개, 강의/자격증 정보, 수강문의 접수를 제공하는 공식 웹사이트입니다.

- [프로젝트 개요](#프로젝트-개요)
- [빠른 링크](#빠른-링크)
- [스크린샷](#스크린샷)
- [주요 기능](#주요-기능)
- [기술 스택](#기술-스택)
- [아키텍처](#아키텍처)
- [문의](#문의)

---

## 프로젝트 개요
- **기간**: 2025.06 ~ 2025.08  
- **특징**: HRD-Net 공공데이터 연동, Naver Object Storage(S3 호환), Naver Maps / SMTP, 무로그인 문의 접수

## 빠른 링크
- 🏠 **웹사이트**: https://damoacook.com  
- 📦 **Frontend Repo**: <!-- 예: https://github.com/ORG_NAME/damoa-front -->  
- 🔧 **Backend Repo**: <!-- 예: https://github.com/ORG_NAME/damoa-back -->  
- 📄 **API Base**: https://damoacook.com/api/

## 스크린샷
> 이미지는 이 저장소의 `profile/assets/` 폴더에 두고, 아래 경로를 맞춰주세요.

<p align="center">
  <img src="./profile/assets/screen-home.png" alt="Home" width="800"><br/>
  <em>홈 — 모집중 강의/공지/갤러리</em>
</p>

<p align="center">
  <img src="./profile/assets/screen-lectures.png" alt="Lectures" width="800"><br/>
  <em>강의 목록/상세</em>
</p>

<p align="center">
  <img src="./profile/assets/screen-inquiry.png" alt="Inquiry" width="800"><br/>
  <em>수강문의 폼</em>
</p>

<p align="center">
  <img src="./profile/assets/screen-map.png" alt="Map" width="800"><br/>
  <em>오시는 길 — Naver Maps</em>
</p>

## 주요 기능
- 강의/자격증 정보 제공, HRD-Net 강의 연동
- 수강문의 접수 → 이메일 알림
- 공지/갤러리 콘텐츠
- 네이버 지도(오시는 길), OG/Kakao 미리보기

## 기술 스택
- **Frontend**: React(Vite), Tailwind, React Query, React Router  
- **Backend**: Django + DRF, SimpleJWT, Gunicorn, WhiteNoise  
- **Infra**: Vercel(프론트), Render(백엔드), PostgreSQL, Naver Object Storage(S3)  
- **Integrations**: HRD-Net, Naver SMTP, Naver Maps

## 아키텍처
```mermaid
flowchart LR
  User -->|HTTPS| Vercel[Frontend]
  Vercel -->|/api rewrite| Render[Backend: Gunicorn]
  Render -->|ORM| PostgreSQL[(DB)]
  Render -->|SMTP| NaverMail[(SMTP)]
  Render -->|Media| NaverObjectStorage[(S3)]
  Render -->|OpenAPI| HRDNet[HRD-Net]
