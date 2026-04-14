# Pre-processing of 10X Single-Cell RNA Datasets

A structured repository covering the full pipeline for scRNA-seq data 
pre-processing, from raw Galaxy-based alignment through Python-based 
AnnData object manipulation.

## Repository Structure

| Folder | Description |
|--------|-------------|
| [`01_Galaxy_Tutorial/`](./01_Galaxy_Tutorial/) | Raw FASTQ pre-processing using the Galaxy platform |
| [`02_AnnData_Getting_Started/`](./02_AnnData_Getting_Started/) | Introduction to AnnData objects (official anndata tutorial) |
| [`03_AnnData_Scverse_Tutorial/`](./03_AnnData_Scverse_Tutorial/) | AnnData in the Scverse ecosystem (scverse tutorial) |

## Overview

Single-cell RNA sequencing (scRNA-seq) requires careful pre-processing 
before any biological interpretation. This repo is organized as three 
progressive sections:

1. **Galaxy** handles the bioinformatics pipeline (alignment, demultiplexing, 
   count matrix generation) without writing code.
2. **AnnData basics** teaches you to load and manipulate that count matrix 
   in Python using the AnnData format.
3. **Scverse tutorial** shows how AnnData integrates with tools like Scanpy 
   for downstream analysis.

## Requirements

- Python ≥ 3.9
- anndata
- scanpy
- numpy, pandas, scipy
- Jupyter Notebook or JupyterLab

Install with:
```bash
pip install anndata scanpy numpy pandas scipy jupyter
```

## References
- [AnnData Documentation](https://anndata.readthedocs.io)
- [Scverse Tutorials](https://scverse-tutorials.readthedocs.io)
- [Galaxy Training Network — Single Cell](https://training.galaxyproject.org/training-material/topics/single-cell/)
