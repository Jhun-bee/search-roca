# Search ROCA PoC Walkthrough

## PoC v2: AG Reranker Pipeline

This Proof of Concept validates the **Query Processor -> Hybrid Search -> AG Reranker** pipeline.

### 1. Setup
Ensure dependencies are installed and `.env` contains `GOOGLE_API_KEY`.
```bash
conda activate search-roca
pip install -r requirements.txt
```

### 2. Data Generation (Step 0)
Generate enriched mock data and golden test cases.
```bash
python poc/poc_v2_generate_mock_data.py
python poc/poc_v2_generate_golden_dataset.py
```

### 3. Run Experiments
**Step 1: Query Processor**
Validates Intent Classification & Keyword Extraction.
```bash
python poc/poc_v2_step1_query_processor.py
```

**Step 2: Hybrid Retrieval**
Compares BM25, Vector, and Hybrid search Recall@K.
```bash
python poc/poc_v2_step2_hybrid_retrieval.py
```

**Step 3: AG Reranker (Target)**
Validates Top-1 Precision and Location Guidance logic.
```bash
python poc/poc_v2_step3_ag_reranker.py
```

### 4. Check Results
See the following reports for detailed analysis:

| Report | Description |
|:---|:---|
| `poc/document/poc_v2_AG_Module_Validation_Report.md` | AG 모듈 검증 리포트 (핵심) |
| `poc/document/poc_v2_Comprehensive_Review_Report.md` | PoC 검증 체계 종합 검토 |
| `poc/document/poc_v2_Golden_Test_Cases_Analysis.md` | 테스트 케이스 상세 분석 |
| `poc/document/poc_v2_Mock_Product_DB_Analysis.md` | Mock DB 품질 분석 |
| `poc/POC_v2_FINAL_REPORT.md` | PoC 전체 요약 |
