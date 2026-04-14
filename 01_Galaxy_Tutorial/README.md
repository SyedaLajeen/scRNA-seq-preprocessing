# 01 — Galaxy scRNA-seq Pre-processing Tutorial

## Overview
This section covers the pre-processing of 10X Chromium single-cell RNA-seq data 
using the Galaxy platform. The steps include quality control, alignment, 
and generation of count matrices from raw FASTQ files.

## Source
Galaxy Training Network — Single-cell RNA-seq tutorial  
https://training.galaxyproject.org/training-material/topics/single-cell/

## Workflow Summary
1. **Input:** Raw 10X FASTQ files (R1 = barcodes/UMI, R2 = cDNA reads)
2. **QC:** FastQC / MultiQC for read quality assessment
3. **Alignment:** STARsolo or Cell Ranger to align reads to reference genome
4. **Demultiplexing:** Cell barcode identification and UMI counting
5. **Output:** Sparse count matrix (matrix.mtx + barcodes.tsv + features.tsv)

## Files in This Folder

| File | Description |
|------|-------------|
| `matrix.mtx` | Sparse gene expression count matrix |
| `barcodes.tsv` | List of valid cell barcodes |
| `features.tsv` | List of detected genes/features |
| `workflow.ga` | Exported Galaxy workflow (importable) |
| `qc_report.html` | MultiQC quality control report |

## Key Concepts
- **UMI (Unique Molecular Identifier):** Removes PCR duplicates
- **Cell Barcode:** 16bp sequence identifying each cell
- **10X Chromium Format:** Produces 3-file sparse matrix output
- **STARsolo:** Alignment tool that directly outputs 10X-compatible matrices

## How to Re-run
1. Import `workflow.ga` into your Galaxy instance
2. Upload your FASTQ files
3. Run the workflow end-to-end

## Expected Output
A filtered feature-barcode matrix ready for downstream Python-based 
analysis with Scanpy or AnnData (see sections 02 and 03).
