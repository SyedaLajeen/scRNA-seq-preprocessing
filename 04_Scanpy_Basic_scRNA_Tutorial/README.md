# 🔬 Section 04 — Basic scRNA-seq Tutorial with Scanpy (PBMC 3K)

> **Source Notebook:** [basic-scrna-tutorial.ipynb — scverse/scanpy-tutorials](https://github.com/scverse/scanpy-tutorials/blob/main/basic-scrna-tutorial.ipynb)
> **Run Environment:** Google Colab
> **Dataset:** 3,000 Peripheral Blood Mononuclear Cells (PBMCs) — freely available from 10X Genomics
> **License:** BSD 3-Clause (Scanpy) · Dataset: 10X Genomics Public

---

## 📌 Overview

This section represents the **downstream analysis** stage of the scRNA-seq pipeline — the step that comes directly after pre-processing (Section 01). Using **Scanpy** (Single-Cell Analysis in Python), we take the count matrix produced by STARsolo/Galaxy and perform the full standard workflow: quality control, normalization, dimensionality reduction, clustering, and cell type annotation.

The dataset used is the canonical **PBMC 3K** benchmark — 2,700 peripheral blood mononuclear cells from a healthy donor, sequenced on an Illumina NextSeq 500 using the 10X Chromium platform. This is the most widely used reference dataset in single-cell bioinformatics and mirrors the famous Seurat PBMC tutorial, reproduced here entirely in Python.

---

## 🧬 What Are PBMCs?

**Peripheral Blood Mononuclear Cells (PBMCs)** are blood cells with a round nucleus — including T cells, B cells, NK cells, and monocytes. They are isolated from whole blood and are a standard model system for immune profiling studies. Each of the 2,700 cells in this dataset represents one individual cell whose full transcriptome has been sequenced.

---

## 🔄 Full Analysis Pipeline

```
Count Matrix (matrix.mtx + barcodes.tsv + features.tsv)
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 1: Data Loading               │  sc.read_10x_mtx()
│  Load 10X matrix into AnnData       │
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 2: Quality Control (QC)       │  sc.pp.calculate_qc_metrics()
│  • Filter low-quality cells         │  sc.pp.filter_cells()
│  • Filter low-count genes           │  sc.pp.filter_genes()
│  • Flag mitochondrial genes         │  adata.var['mt']
│  • Remove dying/broken cells        │  pct_counts_mt threshold
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 3: Normalization              │  sc.pp.normalize_total()
│  • Normalize to 10,000 counts/cell  │  sc.pp.log1p()
│  • Log-transform                    │
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 4: Feature Selection          │  sc.pp.highly_variable_genes()
│  • Identify highly variable genes   │  top 2,000 HVGs selected
│  • Reduces noise, keeps biology     │
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 5: Scaling & Regression       │  sc.pp.regress_out()
│  • Regress out confounders          │  sc.pp.scale()
│  • Scale to unit variance           │
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 6: PCA                        │  sc.pp.pca()
│  • Reduce to 50 principal           │
│    components                       │  sc.pl.pca_variance_ratio()
│  • Elbow plot to choose n_pcs       │
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 7: Neighborhood Graph         │  sc.pp.neighbors()
│  • Build KNN graph in PC space      │  n_neighbors=10, n_pcs=40
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 8: UMAP Embedding             │  sc.tl.umap()
│  • 2D visualization of cell         │  sc.pl.umap()
│    relationships                    │
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 9: Clustering                 │  sc.tl.leiden()
│  • Leiden community detection       │  resolution=0.9
│  • Groups cells by expression       │
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 10: Marker Gene Detection     │  sc.tl.rank_genes_groups()
│  • Wilcoxon rank-sum test           │
│  • Find top genes per cluster       │  sc.pl.rank_genes_groups()
└─────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────┐
│  STEP 11: Cell Type Annotation      │  Manual + marker genes
│  • Map clusters to known cell types │
│  • CD3D → T cells                   │
│  • MS4A1 → B cells                  │
│  • CST3 → Monocytes                 │
└─────────────────────────────────────┘
            │
            ▼
      Annotated UMAP with labeled cell populations
      Saved as: pbmc3k.h5ad
```

---

## 📊 Notebook Contents

| Section | Key Function(s) | What It Does |
|---------|----------------|--------------|
| Setup | `sc.settings`, `sc.logging.print_header()` | Configure Scanpy settings and logging |
| Load Data | `sc.read_10x_mtx()` | Read 10X MTX matrix into AnnData |
| QC Metrics | `sc.pp.calculate_qc_metrics()` | Compute per-cell stats: n_genes, total_counts, pct_mt |
| Cell Filtering | `sc.pp.filter_cells()`, `sc.pp.filter_genes()` | Remove low-quality cells and rarely expressed genes |
| Normalization | `sc.pp.normalize_total()`, `sc.pp.log1p()` | Library-size normalization + log transformation |
| HVG Selection | `sc.pp.highly_variable_genes()` | Keep top 2,000 most variable genes |
| Scaling | `sc.pp.regress_out()`, `sc.pp.scale()` | Regress confounders, scale to zero mean |
| PCA | `sc.pp.pca()`, `sc.pl.pca_variance_ratio()` | Principal component analysis, elbow plot |
| KNN Graph | `sc.pp.neighbors()` | Build nearest-neighbor graph for clustering |
| UMAP | `sc.tl.umap()`, `sc.pl.umap()` | 2D embedding for visualization |
| Clustering | `sc.tl.leiden()` | Leiden graph clustering |
| Marker Genes | `sc.tl.rank_genes_groups()` | Statistical test to find cluster-specific genes |
| Annotation | Manual via `adata.rename_categories()` | Assign cell type labels to clusters |
| Save | `adata.write()` | Export final AnnData as `.h5ad` file |

---

## 🧠 Key Concepts Explained

| Concept | Explanation |
|---------|------------|
| **QC Filtering** | Removes cells with too few genes (likely empty droplets), too many genes (likely doublets), or high mitochondrial content (likely dying cells) |
| **Library Size Normalization** | Each cell is scaled so total counts = 10,000, making cells comparable despite sequencing depth differences |
| **Log Transformation** | `log1p(x)` compresses the wide dynamic range of gene expression and stabilizes variance |
| **Highly Variable Genes (HVGs)** | Genes that differ most across cells — they carry the biological signal. Focusing on HVGs reduces noise |
| **PCA** | Compresses 2,000 HVGs into ~40 principal components, each capturing a major axis of variation |
| **KNN Graph** | Connects each cell to its nearest neighbors in PC space — the basis for both UMAP and clustering |
| **UMAP** | A non-linear dimensionality reduction that preserves local neighborhood structure for 2D visualization |
| **Leiden Clustering** | A community detection algorithm on the KNN graph — finds groups of cells with similar expression |
| **Wilcoxon Test** | Statistical test used to rank genes by how specifically they are expressed in each cluster |
| **Marker Genes** | Canonical genes used to identify cell types: CD3D (T cells), MS4A1 (B cells), CST3 (Monocytes), NKG7 (NK cells) |

---

## 📂 File in This Folder

| File | Description |
|------|-------------|
| `basic-scrna-tutorial-executed.ipynb` | Fully executed Scanpy PBMC 3K tutorial notebook run on Google Colab, with all outputs, plots, and UMAP visualizations visible |

---

## ▶️ How to Re-run This Notebook

**Option 1 — Google Colab (Recommended, no setup needed):**
1. Go to [colab.research.google.com](https://colab.research.google.com)
2. File → Upload notebook → select the `.ipynb` file from this folder
3. Runtime → Run all

**Option 2 — Local Jupyter:**
```bash
pip install scanpy[leiden] matplotlib seaborn
jupyter notebook basic-scrna-tutorial-executed.ipynb
```

---

## 🔗 How This Connects to the Rest of the Pipeline

```
Section 01 (Galaxy)          →  Produces:  matrix.mtx, barcodes.tsv, features.tsv
                                               ↓
Section 02 (AnnData Basics)  →  Teaches:   How AnnData stores this matrix
                                               ↓
Section 03 (Scverse AnnData) →  Teaches:   AnnData in the scverse ecosystem
                                               ↓
Section 04 (THIS SECTION)    →  Applies:   Full Scanpy analysis on real PBMC data
                                           Output: Annotated cell clusters + UMAP
```

---

## 🔗 References

- Scanpy GitHub: https://github.com/scverse/scanpy-tutorials
- Scanpy Documentation: https://scanpy.readthedocs.io
- Original PBMC 3K Dataset: https://www.10xgenomics.com/datasets/3-k-pb-mc-s-from-a-healthy-donor-1-standard-1-1-0
- Wolf et al. 2018 (Scanpy paper): https://doi.org/10.1186/s13059-017-1382-0
- Seurat PBMC Tutorial (original inspiration): https://satijalab.org/seurat/articles/pbmc3k_tutorial
