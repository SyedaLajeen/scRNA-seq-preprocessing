# 03 — AnnData Getting Started (Scverse Tutorial)

## Overview
This section follows the official Scverse ecosystem tutorial on AnnData, 
building on the basics from section 02 with more applied examples relevant 
to real single-cell datasets and the broader scverse toolchain (Scanpy, Muon, etc.).

## Source
Scverse Tutorials — "AnnData Getting Started"  
https://scverse-tutorials.readthedocs.io/en/latest/notebooks/anndata_getting_started.html

## Prerequisites
```bash
pip install anndata scanpy scverse-tutorials jupyter
```

## Notebook Contents

| Section | Description |
|---------|-------------|
| AnnData Basics | Recap of AnnData structure in the scverse context |
| Real Dataset Loading | Loading actual scRNA-seq data into AnnData |
| Metadata Handling | Working with cell annotations and gene info |
| Integration with Scanpy | How AnnData feeds into the Scanpy analysis pipeline |
| Visualization | Plotting with AnnData-compatible tools |

## File in This Folder

| File | Description |
|------|-------------|
| `anndata_getting_started.ipynb` | Fully executed Scverse AnnData tutorial notebook |

## Connection to the Pipeline
This notebook represents the entry point into the **scverse ecosystem**:
- AnnData (this section) → stores data
- Scanpy → QC, clustering, differential expression
- Squidpy → spatial transcriptomics
- Muon → multi-modal data
