# Changelog

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
