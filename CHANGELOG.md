# Changelog

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
