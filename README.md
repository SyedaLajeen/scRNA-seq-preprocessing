# 🧬 Pre-processing of 10X Single-Cell RNA Datasets

A complete and structured repository demonstrating the **end-to-end preprocessing and analysis workflow of single-cell RNA sequencing (scRNA-seq) data** generated using **10X Genomics Chromium technology**.

This repository covers the full computational pipeline — from **raw sequencing FASTQ files** to **quality-controlled, clustered, and biologically annotated cell populations** — using both **Galaxy web-based tools** and the **Python scverse ecosystem**.

It is intended as a beginner-friendly educational resource for understanding modern **single-cell transcriptomics workflows**, while also serving as a reproducible bioinformatics project repository.

---

##  Repository Structure

| Folder | Tool / Platform | Description |
|--------|----------------|-------------|
| [`01_Galaxy_Tutorial/`](./01_Galaxy_Tutorial/) | Galaxy + STARsolo | Preprocess raw FASTQ sequencing files into a gene expression count matrix using the Galaxy web platform |
| [`02_AnnData_Getting_Started/`](./02_AnnData_Getting_Started/) | AnnData (Python) | Learn the internal structure of AnnData objects used to store single-cell data |
| [`03_AnnData_Scverse_Tutorial/`](./03_AnnData_Scverse_Tutorial/) | AnnData + Scverse | Understand how AnnData integrates within the broader scverse ecosystem |
| [`04_Scanpy_Basic_scRNA_Tutorial/`](./04_Scanpy_Basic_scRNA_Tutorial/) | Scanpy + Google Colab | Perform downstream scRNA-seq analysis including QC, clustering, visualization, and annotation |

---

## 🎯 Learning Objectives

This repository demonstrates the following core concepts in single-cell RNA sequencing analysis:

- Understanding the **10X Genomics scRNA-seq experimental workflow**
- Converting raw FASTQ sequencing reads into **gene-cell count matrices**
- Learning the importance of **cell barcodes**, **UMIs**, and **feature quantification**
- Understanding the **AnnData object structure** for storing single-cell datasets
- Performing downstream analysis using **Scanpy**
- Visualizing and interpreting **cell clusters** and **marker genes**
- Annotating clusters into biologically meaningful **cell types**

---

## 🔄 Workflow Overview

The repository follows the real-world scRNA-seq computational pipeline:

```text
RAW DATA (FASTQ files from 10X Chromium sequencer)
         │
         ▼
 ┌───────────────────────────────────┐
 │  01 — Galaxy Tutorial             │
 │  Tool: STARsolo on Galaxy         │
 │                                   │
 │  Raw FASTQ → Count Matrix         │
 │                                   │
 │  Output Files:                    │
 │  • matrix.mtx                     │
 │  • barcodes.tsv                   │
 │  • features.tsv                   │
 └───────────────┬───────────────────┘
                 │
                 ▼
 ┌───────────────────────────────────┐
 │  02 — AnnData Getting Started     │
 │                                   │
 │  Learn AnnData structure for      │
 │  storing expression matrices      │
 │                                   │
 │  Topics Covered:                  │
 │  • .X                             │
 │  • .obs                           │
 │  • .var                           │
 │  • .obsm                          │
 │  • layers / uns                   │
 └───────────────┬───────────────────┘
                 │
                 ▼
 ┌───────────────────────────────────┐
 │  03 — AnnData Scverse Tutorial    │
 │                                   │
 │  Explore AnnData in the larger    │
 │  scverse ecosystem                │
 └───────────────┬───────────────────┘
                 │
                 ▼
 ┌───────────────────────────────────┐
 │  04 — Scanpy Basic Tutorial       │
 │                                   │
 │  Full Downstream Analysis:        │
 │                                   │
 │  QC → Normalize → PCA → UMAP      │
 │  → Leiden Clustering              │
 │  → Marker Genes → Annotation      │
 │                                   │
 │  Output: Annotated .h5ad File     │
 └───────────────────────────────────┘
```

---

## 🧪 Dataset Used

This repository uses the **PBMC 3K dataset**, one of the most widely used benchmark datasets in single-cell RNA-seq tutorials.

### Dataset Information

- **Source:** 10X Genomics
- **Organism:** Human
- **Cell Count:** ~2,700 cells
- **Sample Type:** Peripheral Blood Mononuclear Cells (PBMCs)

PBMCs contain diverse immune cell populations including:

- T Cells
- B Cells
- Natural Killer (NK) Cells
- Monocytes
- Dendritic Cells

This dataset is ideal for learning due to its well-separated clusters and known marker genes.

---

## 🛠️ Tools and Technologies Used

| Tool | Purpose |
|------|--------|
| **Galaxy** | Web-based bioinformatics workflow platform |
| **STARsolo** | Alignment and quantification of scRNA-seq reads |
| **AnnData** | Annotated data matrix storage format |
| **Scanpy** | Downstream single-cell analysis toolkit |
| **Google Colab** | Cloud notebook execution environment |
| **Python** | Data analysis and scripting language |

---

## ⚙️ Installation / Requirements

All notebooks can be run directly on **Google Colab** with no installation required.

For local execution, install dependencies using:

```bash
pip install anndata scanpy[leiden] numpy pandas scipy matplotlib seaborn jupyter
```

For Galaxy preprocessing, use the free public Galaxy server:

**https://usegalaxy.org**

---

## 📂 Expected Outputs

By completing all sections, the following outputs are generated:

- Processed **count matrices** from raw FASTQ data
- Structured **AnnData objects** for single-cell storage
- Dimensionality reduction plots (**PCA / UMAP**)
- Cluster assignments using **Leiden clustering**
- Marker gene identification results
- Final annotated **.h5ad single-cell dataset**

---

## 📚 Sources and References

| Section | Source |
|---------|--------|
| Galaxy Tutorial | https://training.galaxyproject.org/training-material/topics/single-cell/tutorials/scrna-preprocessing-tenx/tutorial.html |
| AnnData Getting Started | https://anndata.readthedocs.io/en/latest/tutorials/notebooks/getting-started.html |
| Scverse AnnData Tutorial | https://scverse-tutorials.readthedocs.io/en/latest/notebooks/anndata_getting_started.html |
| Scanpy Basic Tutorial | https://github.com/scverse/scanpy-tutorials/blob/main/basic-scrna-tutorial.ipynb |

---

##  Assignment Context

**Topic:** Pre-processing of 10X Single-Cell RNA Datasets  
**Area:** Single-Cell Transcriptomics / Bioinformatics  
**Tools Covered:** Galaxy, STARsolo, AnnData, Scanpy, Google Colab  

This repository was developed to document and demonstrate the standard preprocessing and downstream analysis workflow for modern single-cell RNA sequencing data.

---

##  Repository Goal

The goal of this repository is to provide:

- A **step-by-step educational walkthrough** of scRNA-seq preprocessing  
- A **well-documented reproducible workflow** for learning purposes  
- A structured **bioinformatics portfolio project** showcasing practical computational biology skills  

---
