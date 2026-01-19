# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.6.0] - 2026-01-19

### 🚀 Major Feature: RAG Optimization & Robustness
*   **Verified Architecture**: Meaning Extraction -> Vector Search (K=30) -> Intent Rules -> LLM Reranking.
*   **Performance Achievement**:
    *   **Retrieval Recall**: 92.0% (vs Baseline 57.8%)
    *   **Intent Accuracy**: 96.0% (with Rule-based Prompt)
    *   **Validated**: 200 Products / 25 Keyword Test Cases.

### Added
- **Reports** (in `/docs`)
  - `RAG_ROBUSTNESS.md`: Full verification report of the optimization.
  - `RAG_BASELINE.md`: Failure analysis of raw sentence input.
- **PoC Scripts** (in `poc/`)
  - `RAG_System_experiment_keyword.py`: The winning optimization script (K=30).
  - `RAG_System_experiment_baseline.py`: The failing baseline script (for reference).
  - `prompts/intent_rules_prompt.txt`: The finalized Intent Classifer prompt.

### Changed
- **Search Logic Update**:
  - Increased `Top-K` from 10 to **30**.
  - Enforced "Keyword-Only" input strategy (upstream dependency).
  - Added Rule-based "Traffic Control" for ambiguous keywords (e.g., Latex Gloves).

---

## [0.0.0] - 2026-01-15

### Added
- **Backend (FastAPI)**
  - `/api/search` endpoint with semantic search using Sentence Transformers
  - Product inventory with map coordinates (20x20 grid system)
  - Kiosk position configuration at `(10, 2)`

- **Frontend (Next.js)**
  - Home page with animated robot face kiosk standby screen
  - Search page with text/voice input and QR code generation
  - AR navigation page with:
    - Real camera background (getUserMedia)
    - Pokemon Go-style compass navigation
    - Airplane-shaped directional arrow
    - Distance display (meters)
    - Store map overlay

- **Documentation**
  - `README.md` with setup instructions
  - `WORKFLOW.md` with Mermaid diagrams
  - `CHANGELOG.md` for version tracking

### Technical Details
- Coordinate system: 20x20 grid (1 unit ≈ 1 meter)
- Arrow logic: `rotation = targetBearing - deviceHeading`
- Supports both iOS (webkitCompassHeading) and Android (alpha)
