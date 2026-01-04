# App Relevance Classification (Case Study)

## Overview
This repository contains an NLP-based case study developed as part of a job interview assignment.  
The goal is to classify enterprise applications with respect to their relevance for Life Sciences, MedTech, and GxP-regulated environments using a low-resource, text-based approach.

---

## Goal
In large enterprise landscapes, identifying applications that are potentially relevant for regulated domains (e.g. GxP, Life Sciences, MedTech, Pharma) is a challenging and largely manual task.  
The objective of this case study is to use textual application metadata to automatically flag potentially relevant applications when only very limited labeled data is available.

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
- The labeled dataset is small and manually created.
- Labels are based solely on textual descriptions and do not capture real usage context.
- Regulatory relevance is treated as a binary classification, although real-world scenarios may require finer-grained distinctions.

---

## Data 
Due to data sensitivity and the interview context, the following files are **not included** in this repository:

- The original raw application metadata dataset
- The manually annotated application label file

To illustrate the structure of the annotated labels, the table below shows an anonymized example of how the labeling file is formatted:

```text
AppID,FullText,is_relevant,uncertain
A001,"batch validation and quality inspection workflow",1,0
A002,"invoice processing and financial reconciliation",0,0
A003,"clinical trial data entry and audit logging",1,0```

---

## Requirements
The analysis was conducted using standard Python data science libraries, including:
 ```
- numpy
- pandas
- scikit-learn
- matplotlib
- umap-learn

