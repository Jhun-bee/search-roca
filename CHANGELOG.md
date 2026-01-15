# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
