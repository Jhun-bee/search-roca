# Changelog

## [v0.8.1] - 2026-02-05
### Added
- **Performance Verification**:
  - **Latency Benchmark**: Added `poc/benchmark_latency.py` to measure end-to-end system latency (Gemini 2.0 Flash + QR Gen).
  - **Reports**: Added `poc/document/poc_v6_latency_benchmark_report.md` confirming average 1.13s system latency.
- **Utils**: Added `poc/fix_encoding.py` for file encoding corrections.

### Changed
- **Data**: Updated `data/poc_v6_mock_product_db.json`.

## [v0.8.0] - 2026-01-29
### Added
- **PoC v6 Map & AR Upgrade**:
  - **Map Debugger**: Created `poc_v6_map_debug.html` to visualize all shelf locations and entrances for B1/B2 floors.
  - **Multi-Entrance Support**: Added logic to handle multiple entrances (Main/Sub) on B1 floor. Kiosk now supports selecting the starting location, which is passed to the mobile AR view.
  - **Product Addition**: Added 'Stainless Sieve (Chae-ban)' to Mock Product DB and search logic (`KI01` - Kitchen).
  - **AR Navigation Fixes**: 
    - Implemented dynamic Ngrok URL configuration in Kiosk.
    - Improved AR arrow direction logic to calculate relative bearing from the selected entrance (Start Location).

### Improved
- **Map Accuracy**: Refined `poc_v6_map_data.js` coordinates for approximately 20 shelf locations based on visual feedback (annotated images).
- **Mobile Access**: Added cache-busting to map data scripts to ensure mobile devices load the latest coordinates immediately.

## [v0.7.0] - 2026-01-27
### Added
- **PoC v5**: Advanced reasoning experiments with Chain-of-Thought (CoT).
- **New Scripts**:
  - `poc/poc_v5_experiment_phase_1.py`: Phase 1 experiment script (Reasoning).
  - `poc/poc_v5_experiment_phase_1_eval.py`: Evaluation script for Phase 1.
- **Documentation**:
  - `poc/document/poc_v5_experiment_results_phase_1-2.md`: Detailed results of Phase 1 & 2.
  - `poc/document/poc_v5_goal_phase_1.md`: Goals for Phase 1.
  - `poc/document/poc_v4_goal_phase_2.md`: Goals for Phase 2 (v4 referenced).

## [v0.6.5] - 2026-01-23
### Added
- **Report Upgrade**: `poc/document/poc_v3_AG_Module_Validation_Report.md` 추가 (구조 개선: 목적/목표/계획/결과/결론)
- **Data Restoration**: `poc_v2` 데이터셋(Golden Test Case 30건, Mock DB)을 v0.4.0 원본으로 복구하여 보존

### Changed
- `poc/document/poc_v2_AG_Module_Validation_Report.md`를 원본 상태로 복구 (v3와 분리)

## [v0.6.4] - 2026-01-23
### Added
- **Latency Monitoring**: LLM 호출 시간(Latency) 측정 로그 기능 추가 (Average 1.7s)
- **Data Refinement**: Mock DB 내 '기타/미분류' 상품 200건 전량 재분류 (LLM Automated + Manual Fix)

### Improved
- **Test Coverage**: Golden Test Cases 42건으로 확장 (Hard/False Positive 케이스 집중 보강)
- **Documentation**: Test Case 분석 리포트 전면 리팩토링 및 검증 보고서 근거 보강

### Fixed
- Mock DB Category 필드 누락 문제 해결

## [v0.6.2] - 2026-01-23
### Added
- **PoC 검증 체계 종합 검토**: 5가지 관점에서 전체 PoC 분석
  - `poc/document/poc_v2_Comprehensive_Review_Report.md`: 검증 방법 논리성, 데이터 품질, 보고서 구조, 수정 사항, 확장 계획 분석
  - `poc/document/poc_v2_Golden_Test_Cases_Analysis.md`: 30건 테스트 케이스 상세 분석
  - `poc/document/poc_v2_Mock_Product_DB_Analysis.md`: 601건 Mock DB 통계 및 품질 분석
- **AG 모듈 추가 검토 섹션**: Re-ranking 필요성/성능 검증, 한국어 모델 비교, Generation 충분성 분석

### Changed
- `poc/document/poc_v2_AG_Module_Validation_Report.md`: 섹션 5 "추가 검토 사항" 추가

---

## [v0.4.0] - 2026-01-22
### Added
- **PoC v2 Integrated**: AG Reranker Module validation complete.
- **New Scripts**:
  - `poc/poc_v2_generate_mock_data.py`: Mock DB enrichment with LLM.
  - `poc/poc_v2_generate_golden_dataset.py`: 30 Hard Test Cases.
  - `poc/poc_v2_step1_query_processor.py`: Intent Extraction.
  - `poc/poc_v2_step2_hybrid_retrieval.py`: Hybrid Search (BM25+Vector).
  - `poc/poc_v2_step3_ag_reranker.py`: LLM Reranking & Location Guide.
- **Documentation**:
  - `poc/document/poc_v2_AG_Module_Validation_Report.md`: Deep dive validation report.
  - `poc/POC_v2_FINAL_REPORT.md`: Overall PoC summary.
  - `poc/GITHUB_ISSUE_DRAFT.md`: Ready-to-use issue template.
- **Prompts**: All prompts renamed with `poc_v2_` prefix for consistency.

### Changed
- Reorganized PoC documentation into `poc/document/` folder.
- Migrated v1 reports with `poc_v1_` prefix.
