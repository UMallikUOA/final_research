# FAERS Adverse Reaction Analysis and Retrieval-Augmented Generation (RAG) System

This project investigates adverse event patterns associated with second-generation antihistamines using the FDA Adverse Event Reporting System (FAERS) dataset from 2019 to 2024. It combines exploratory data analysis, embedding-based clustering, and a Retrieval-Augmented Generation (RAG) model to support semantic querying of drug safety profiles.

## Repository Structure and Coding History

The codebase has undergone iterative updates since the project's inception in Trimester 1. Development followed a modular and experimental workflow, with older versions preserved in **branch-wise folders organized weekly** (e.g., `week_4`, `week_22`, etc.). 

> **Main Branch**  
The `main` branch consolidates all final versions of the code, incorporating improvements made across both trimesters. The files were uploaded recently for cleanup and documentation.

## Key Files and Their Roles

### Initial Exploration and Data Standardization

- **`initial_exploration.ipynb`**  
  Early exploration of the 2024 Q4 dataset, used to validate cleaning logic, age and sex imputation, and de-duplication handling strategies.

- **`standardization.ipynb`**  
  Unified preprocessing pipeline for multi-year FAERS data, including cleaning, imputation, drug normalization, and PostgreSQL ingestion.

> Note: In older branches, you may find early versions of these under different names:
> - `research_project.ipynb`: Initial EDA and plotting
> - `functions.ipynb`: Raw ingestion logic
> - `further_analysis.ipynb`: Early sentence embeddings and clustering experiments

---

### Embedding and Clustering

- **`embedding_clustering_tri1.ipynb`**  
  Hybrid MiniLM + BioBERT approach used in Trimester 1, including UMAP and HDBSCAN clustering, followed by reaction grouping.

- **`updated_mapping.ipynb`**  
  Refined approach from Trimester 2 using only BioBERT embeddings for semantic consistency, and final categorization logic based on MedDRA and keyword extraction.

---
### Trend Analysis
- **`data_plots.ipynb`**
  Contains the plots used in the result section of the final report
---
### RAG Model Development and Evaluation

- **`RAG_Experiments/` folder**  
  Contains early LLM-based prompting strategies, filtering logic variations, and retrieval pipelines. The key prototype:

  - `modular_rag_experiments.ipynb`: Basis for the final RAG pipeline.

- **`final_rag_code.ipynb`**  
  Final implementation of the RAG model with:
  - Filtered FAISS retrieval
  - LLaMA-based generation
  - Reaction extraction pipeline
  - Evaluation block with performance metrics
  - Gradio UI for accessibility

- **`dataset_RAG/`**  
  Structured case documents used as input to the RAG system (FAISS + metadata filtering).

- **`RAG_Experiments_Results/`**  
  Results and evaluation metrics from three controlled experiments:

  | **Experiment** | **Fuzzy Threshold** | **Max Documents** | **Estimated Avg. Tokens** |
  |----------------|---------------------|-------------------|----------------------------|
  | 1              | 80                  | 20                | 200                        |
  | 2              | 75                  | 30                | 150                        |
  | 3              | 70                  | 40                | 100                        |

  > The files have been appropriately labeled experiment_1_results, experiment_2_results, and experiment_3_results. These experiments supported optimal parameter tuning for recall, precision, and semantic fidelity.

---




