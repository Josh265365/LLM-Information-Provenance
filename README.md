Provenance Tracking in Large Language Models Using Information Retrieval Systems
**📘 Overview**

This project investigates how provenance the ability to trace generated text back to its source can be achieved in Large Language Models (LLMs) using an Information Retrieval (IR) based pipeline.
While existing work on membership inference and data extraction focuses on adversarial attacks to expose memorised data, this project explores a constructive approach that enhances transparency and accountability in LLM outputs.

The system compares sparse, and dense retrieval models, using FAISS for vector indexing and a cross-encoder model for re-ranking retrieved documents. Evaluation is based on LLM-generated queries that simulate realistic provenance challenges.

**🧩 Key Features**

* Sparse and Dense Retrieval Comparison:
 *Evaluates BM25, SPLADE, and all-mpnet-base-v2 models.

* FAISS-Based Indexing:
* Efficient vector search across chunk- or chapter-level representations.

* Cross-Encoder Re-Ranking:
* Refines ranking quality and improves retrieval precision.

* LLM-Generated Queries:
* Uses prompt-driven text to test provenance in realistic conditions.

* Quantitative Evaluation:
* Precision, Recall, F1, MAP, MRR, and nDCG metrics.

* Provenance Focus:
* Balances fine-grained retrieval accuracy with contextual coherence.

**  🧠 System Architecture**

LLM Prompt → Generated Text (Query)
      ↓
Document Chunking (Paragraphs / Chapters)
      ↓
Sparse & Dense Encoding (BM25, SPLADE, all-mpnet-base-v2)
      ↓
FAISS Indexing → Similarity Scoring
      ↓
Cross-Encoder Re-ranking
      ↓
Top-k Results + Provenance Attribution

**📊 Results Summary**

| Model             | Level     | Precision@10 | Recall@10 | MAP      | MRR      | nDCG@10  |
| ----------------- | --------- | ------------ | --------- | -------- | -------- | -------- |
| BM25              | Paragraph | 0.10         | 0.10      | 0.03     | 0.14     | 0.15     |
| SPLADE            | Paragraph | 0.20         | 0.20      | 0.04     | 0.18     | 0.16     |
| all-mpnet-base-v2 | Chapter   | **0.90**     | **0.90**  | **0.97** | **1.00** | **0.93** |

Cross-encoder re-ranking improved MAP and MRR to 0.99, maintaining near-perfect precision across recall values (AUC = 0.80, AP = 0.90).

**🧩 Evaluation Scenarios**

Paragraph-Level Retrieval:
Fine-grained precision; risk of fragmented provenance.

Chapter-Level Retrieval:
Preserves context and provenance; slightly lower recall.

Dense vs Sparse Comparison:
Dense retrieval offers semantic robustness, outperforming keyword-based methods.
