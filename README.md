# Search-Roca 🔍🤖

**다이소 매장 상품 검색 + AR 네비게이션 키오스크 시스템**

고객이 키오스크에서 상품을 검색하면, QR 코드를 통해 스마트폰으로 AR 화살표 네비게이션을 제공합니다.

---

## 🎯 주요 기능

| 기능 | 설명 |
|------|------|
| 🔍 의미 검색 | Sentence Transformers 기반 자연어 상품 검색 |
| 🎤 음성 입력 | Web Speech API를 통한 한국어 음성 인식 |
| 📱 QR 연동 | 검색 결과를 QR로 스마트폰에 전달 |
| 🧭 AR 네비게이션 | 포켓몬고 스타일 화살표가 상품 위치 안내 |
| 🗺️ 매장 지도 | 지도 오버레이로 현재 위치 및 목표 표시 |

---

## 🏗️ 시스템 구조

```
search-roca/
├── backend/           # Python FastAPI 서버
│   ├── main.py        # API 엔드포인트
│   ├── search_engine.py  # 의미 검색 엔진
│   └── inventory.py   # 상품 DB + 좌표
├── frontend/          # Next.js 웹 앱
│   └── app/
│       ├── page.tsx      # 홈 (로봇 얼굴)
│       ├── search/       # 검색 페이지
│       └── ar/           # AR 네비게이션
└── WORKFLOW.md        # 시스템 플로우 다이어그램
```

---

## 🚀 실행 방법

### 1. 환경 설정

```bash
# Conda 환경 생성 (Python 3.10)
conda create -n search-roca python=3.10
conda activate search-roca

# Backend 의존성 설치
cd backend
pip install -r requirements.txt

# Frontend 의존성 설치
cd ../frontend
npm install
```

### 2. 서버 실행 (4개 터미널)

| 터미널 | 폴더 | 명령어 |
|--------|------|--------|
| 1 | backend | `python main.py` |
| 2 | - | `npx localtunnel --port 8000` |
| 3 | frontend | `npm start` |
| 4 | - | `npx localtunnel --port 3000` |

### 3. 테스트

1. **PC**: 터널 URL로 접속 → 상품 검색 → QR 생성
2. **스마트폰**: QR 스캔 → AR 화살표 따라 이동!

---

## 📋 기술 스택

- **Backend**: Python 3.10, FastAPI, Sentence-Transformers
- **Frontend**: Next.js 16, React, TailwindCSS
- **AR**: Device Orientation API, getUserMedia (Camera)
- **Tunneling**: localtunnel (개발/테스트용)

---

## 📄 라이선스

MIT License
