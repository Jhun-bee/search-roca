# Search-Roca 전체 워크플로우

## 시스템 구성도

```mermaid
graph TB
    subgraph "🖥️ PC/태블릿 (Kiosk)"
        A[Home Page<br/>로봇 얼굴] -->|터치| B[Search Page<br/>검색 화면]
        B -->|음성/텍스트 입력| C{Backend API<br/>검색 요청}
        C -->|결과 반환| D[상품 정보 + QR 생성]
    end
    
    subgraph "⚙️ Backend Server"
        C --> E[search_engine.py<br/>의미 검색]
        E --> F[inventory.py<br/>상품 DB + 좌표]
    end
    
    subgraph "📱 고객 스마트폰"
        D -->|QR 스캔| G[AR Page 열림]
        G -->|권한 요청| H{카메라 + 나침반}
        H --> I[AR 네비게이션<br/>화살표가 상품 방향 가리킴]
        I --> J[지도 보기 가능]
    end
```

---

## 핵심 검색 아키텍처 (RAG Pipeline) v0.6.0

```mermaid
graph LR
    subgraph "1. Meaning Extraction (Input)"
        U[User Query<br/>'안 미끄러지는 욕실 매트'] -->|Agent| K[Keyword: '욕실 매트'<br/>Feature: '미끄럼방지']
    end

    subgraph "2. Vector Search (Retrieval)"
        K -->|Embedding| V[Vector Search]
        V -->|Top-K=30| C1[후보군 30개]
    end

    subgraph "3. Reranking (Refinement)"
        C1 -->|Intent Rule| R[Gemini 2.0<br/>Traffic Control]
        R -->|Re-scoring| C2[최종 순위]
    end

    C2 -->|Top-1| RES[최적 상품 반환]
```

---

## 사용자 여정

```mermaid
sequenceDiagram
    actor 고객
    participant K as 키오스크 (PC)
    participant B as Backend
    participant M as 고객 스마트폰
    
    고객->>K: 1. 화면 터치
    K->>K: 2. 검색 화면으로 이동
    고객->>K: 3. "여행용 샴푸" 검색
    K->>B: 4. POST /api/search
    B->>B: 5. 의미 검색 (Sentence Transformer)
    B->>K: 6. 상품 정보 + 좌표 반환
    K->>K: 7. QR 코드 생성 (좌표 포함)
    고객->>M: 8. QR 스캔
    M->>M: 9. AR 페이지 열림
    고객->>M: 10. "Start Camera" 버튼 탭
    M->>M: 11. 카메라/나침반 활성화
    M->>M: 12. 화살표가 상품 방향 가리킴
    고객->>고객: 13. 화살표 따라 이동 → 상품 발견!
```

---

## 좌표 시스템

```mermaid
graph LR
    subgraph "매장 지도 (20x20 Grid)"
        direction TB
        K["🔵 키오스크<br/>(10, 2)"]
        P1["🔴 욕실용품<br/>(2, 14)"]
        P2["🔴 여행용품<br/>(6, 8)"]
        P3["🔴 전자용품<br/>(8, 14)"]
        P4["🔴 식품<br/>(16, 14)"]
    end
    
    K -.->|"~12m"| P1
    K -.->|"~8m"| P2
    K -.->|"~12m"| P3
    K -.->|"~13m"| P4
```

---

## 서버 구성 (4개 터미널)

| # | 용도 | 명령어 | 포트 |
|---|------|--------|------|
| 1 | Backend 서버 | `python main.py` | 8000 |
| 2 | Backend 터널 | `npx.cmd localtunnel --port 8000 ...` | - |
| 3 | Frontend 서버 | `npm start` | 3000 |
| 4 | Frontend 터널 | `npx.cmd localtunnel --port 3000 ...` | - |

---

## 핵심 알고리즘: 화살표 방향 계산

```
목표 방위각 = atan2(상품X - 사용자X, 상품Y - 사용자Y)
화살표 회전 = 목표 방위각 - 폰 나침반 각도
```

이렇게 하면 **폰을 돌려도 화살표는 항상 상품을 가리킴** (포켓몬고 스타일)
