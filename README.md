# Implementasi Case-Based Reasoning (CBR) pada Dokumen Putusan Hukum Menggunakan TF-IDF dan Cosine Similarity

## Overview

This project implements a Case-Based Reasoning (CBR) approach for legal decision documents obtained from the Indonesian Supreme Court Decision Directory (Direktori Putusan Mahkamah Agung Republik Indonesia). The system constructs a legal case base, represents legal cases through structured attributes, retrieves similar cases using TF-IDF and Cosine Similarity, and predicts legal outcomes based on previously solved cases.

The implementation focuses on fraud-related criminal cases (Pidana Penipuan) and uses a dataset consisting of 50 court decisions.

---

## Dataset

- **Source:** Direktori Putusan Mahkamah Agung Republik Indonesia
- **Domain:** Fraud Cases (Pidana Penipuan)
- **Number of Documents:** 50 Court Decisions
- **Format:** PDF Documents

Dataset can be accessed through the following Google Drive link:

> ** https://drive.google.com/drive/folders/132kOSc27UIzqPLpk2glc8FXZ7P3F3c4j?usp=drive_link **

---

## Repository Structure

```text
cbr-putusan-hukum-tfidf-cosine/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_Membangun_Case_Base.ipynb
│   ├── 02_Case_Representation.ipynb
│   ├── 03_Retrieval.ipynb
│   └── 04_Predict.ipynb
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Installation

### 1. Clone Repository

```bash
git clone https://github.com/USERNAME/cbr-putusan-hukum-tfidf-cosine.git
cd cbr-putusan-hukum-tfidf-cosine
```

### 2. Create Virtual Environment

```bash
python -m venv venv
```

**Windows**

```bash
venv\Scripts\activate
```

**Linux / macOS**

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Running the Project

This project is executed sequentially through four Jupyter notebooks.

### Step 1 – Build Case Base

Run:

```text
notebooks/01_Membangun_Case_Base.ipynb
```

**Input**
- PDF court decision documents

**Process**
- Extract text from PDF documents
- Remove headers, footers, watermarks, and unnecessary metadata
- Clean extracted text

**Output**

```text
data/raw/case_001.txt
data/raw/case_002.txt
...
```

---

### Step 2 – Case Representation

Run:

```text
notebooks/02_Case_Representation.ipynb
```

**Input**

```text
data/raw/*.txt
```

**Process**
- Extract case attributes
- Create structured case representation
- Generate case database

**Output**

```text
data/processed/cases.csv
data/processed/cases.json
```

Example extracted attributes:

- Case ID
- Case Number
- Decision Date
- Summary of Facts
- Legal Articles
- Parties
- Judicial Decision (Amar Putusan)

---

### Step 3 – Case Retrieval

Run:

```text
notebooks/03_Retrieval.ipynb
```

**Process**
- TF-IDF Vectorization
- Cosine Similarity Calculation
- Similar Case Retrieval
- Top-K Ranking

**Output**

```text
Top-K most similar legal cases
```

---

### Step 4 – Predict Legal Outcome

Run:

```text
notebooks/04_Predict.ipynb
```

**Process**
- Retrieve most similar cases
- Reuse solution from retrieved cases
- Generate predicted judicial outcome

**Output**

```text
Predicted legal decision
Actual legal decision
Comparison results
```

Example result:

| Query | Predicted Solution | Actual Solution |
|---------|---------|---------|
| Penipuan jual beli sepeda motor | Retrieved from most similar case | Ground truth decision |
| Penggelapan uang perusahaan oleh karyawan | Retrieved from most similar case | Ground truth decision |

---

## Methodology

### Case-Based Reasoning (CBR)

The system follows the Case-Based Reasoning cycle:

1. Retrieve
2. Reuse
3. Revise
4. Retain

### Text Representation

TF-IDF (Term Frequency–Inverse Document Frequency) is used to transform textual case descriptions into numerical vectors.

### Similarity Measurement

Cosine Similarity is used to measure the similarity between legal cases and retrieve the most relevant previous cases.

---

## Workflow

```text
PDF Court Decisions
        │
        ▼
Case Base Construction
        │
        ▼
Case Representation
        │
        ▼
TF-IDF Vectorization
        │
        ▼
Cosine Similarity
        │
        ▼
Retrieve Similar Cases
        │
        ▼
Predict Legal Outcome
```

---

## Requirements

Main libraries used in this project:

```text
pandas
numpy
scikit-learn
pymupdf
tqdm
```

Install all dependencies using:

```bash
pip install -r requirements.txt
```

---

## Example Query

```text
penipuan jual beli sepeda motor
```

Example output:

```text
Most Similar Case : Case #1

Predicted Solution :
Menyatakan terdakwa terbukti secara sah dan meyakinkan bersalah melakukan tindak pidana penipuan.

Actual Solution :
Menyatakan terdakwa terbukti secara sah dan meyakinkan bersalah melakukan tindak pidana penipuan.
```

---

## Notes

- The dataset is not included in this repository due to file size limitations.
- All court decisions were obtained from the Indonesian Supreme Court Decision Directory.
- The dataset can be downloaded through the provided Google Drive link.
- This project is intended for academic and research purposes.

---
