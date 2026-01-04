# App Relevance Classification (NLP Case Study)

## Overview
This repository contains an NLP-based case study developed as part of a job interview assignment.  
The goal is to classify enterprise applications with respect to their relevance for Life Sciences, MedTech, and GxP-regulated environments using a low-resource, text-based approach.

The focus of this project is on methodology, interpretability, and practical modeling decisions rather than on building a production-ready system.

---

## Problem Statement
In large enterprise landscapes, identifying applications that are potentially relevant for regulated domains (e.g. GxP, Life Sciences, MedTech, Pharma) is a challenging and largely manual task.  
The objective of this case study is to explore whether textual application metadata can be used to automatically flag potentially relevant applications, even when only very limited labeled data is available.

---

## Approach
The analysis follows a low-resource and weakly supervised setup:

- Application metadata from multiple text fields is combined into a single text representation.
- A small gold-standard dataset is created via manual annotation of a sampled subset of applications.
- Ambiguous cases are explicitly flagged and excluded from training and evaluation.
- Two complementary classification approaches are evaluated:
  - **Method 1:** TF-IDF vectorization + Logistic Regression (interpretable baseline)
  - **Method 2:** TF-IDF + dimensionality reduction (SVD) + k-Nearest Neighbors (similarity-based)
- Model performance is evaluated using precision, recall, F1-score, and confusion matrices.
- Feature importance and embedding visualizations (UMAP) are used to support interpretability.

---

## Results (Summary)
Both approaches demonstrate that useful relevance signals can be extracted from textual metadata, even with a small labeled dataset.  
The TF-IDF + Logistic Regression model provides a strong and interpretable baseline, while the embedding-based approach offers complementary insights into semantic similarity.  
Overlapping classes in embedding space highlight the inherent ambiguity of regulatory relevance, which often depends on usage context rather than distinct vocabulary alone.

---

## Limitations
- The labeled dataset is small and manually created, which limits statistical confidence.
- Labels are based solely on textual descriptions and do not capture real usage context.
- Regulatory relevance is treated as a binary classification, although real-world scenarios may require finer-grained distinctions.

---

## Data Availability
Due to data sensitivity and the interview context, the original dataset and the manually annotated application labels are **not included** in this repository.  
The notebook is intended to demonstrate the modeling approach, reasoning, and evaluation strategy rather than to provide reusable data assets.

---

## Repository Contents
- `app_relevance_classification_case_study.ipynb` – main Jupyter Notebook containing the full analysis
- `requirements.txt` – minimal dependencies required to run the notebook
- `README.md` – project description

---

## Notes
This project is designed as a methodological case study and should be interpreted accordingly.  
All results are illustrative and intended to support discussion around modeling choices, trade-offs, and interpretability in low-resource NLP settings.
