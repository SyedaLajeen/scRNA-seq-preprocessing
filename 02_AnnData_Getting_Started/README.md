# 02 — Getting Started with AnnData

## Overview
This section introduces the `AnnData` object — the core data structure used 
throughout the scverse ecosystem for single-cell analysis in Python. 
The notebook covers creation, annotation, subsetting, and I/O of AnnData objects.

## Source
Official AnnData Tutorial — "Getting Started with anndata"  
https://anndata.readthedocs.io/en/latest/tutorials/notebooks/getting-started.html  
Authors: Adam Gayoso, Alex Wolf

## Prerequisites
```bash
pip install anndata numpy pandas scipy
```

## Notebook Contents

| Section | Description |
|---------|-------------|
| Initializing AnnData | Creating an AnnData object from a sparse count matrix |
| Subsetting AnnData | Slicing by cell or gene names, boolean masks |
| Observation/Variable Metadata | Adding cell-level and gene-level metadata via `.obs` and `.var` |
| obsm / varm | Storing multi-dimensional metadata (e.g., UMAP embeddings) |
| Unstructured Metadata `.uns` | Storing arbitrary metadata dictionaries |
| Layers | Storing multiple forms of data (raw, normalized, log-transformed) |
| DataFrame Conversion | Converting AnnData layers to Pandas DataFrames |
| Writing to Disk | Saving as `.h5ad` (HDF5-backed AnnData format) |
| Views vs Copies | Understanding memory-efficient views and `.copy()` |
| Backed Mode | Partially reading large `.h5ad` files from disk |

## Key AnnData Structure
