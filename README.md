# ONE-DC scRNA-seq Analysis

Analysis code accompanying the manuscript "A clinical grade type 1 dendritic cell manufacturing leveraging BATF3 expression and notch signalling"
To characterise the transcriptional identity of our culture-derived DC populations and assess their similarity to their blood counterparts, we performed scRNAseq on a combined dataset comprising FACS-sorted peripheral blood DC1 and DC2, and live-sorted ONE-DC-derived populations.

This repository contains the R script used to cluster, annotate, and compare blood- and culture-derived dendritic cell populations from single-cell RNA-seq data, and to generate the corresponding figure panels.

## Contents

| File | Description |
|---|---|
| `ONE_DC_Script(1).Rmd` | Main analysis script: clustering (Seurat), UMAP, marker gene identification, and inter-cluster correlation analysis |

## What this script does

1. Loads a pre-processed `Seurat` object and performs graph-based clustering (`FindNeighbors`/`FindClusters`) and UMAP embedding
2. **Panel A** — UMAP of clusters; **Supplementary Panel A** — heatmap of top marker genes per cluster
3. **Panel B** — feature plots of curated DC/lineage marker genes across the UMAP
4. **Supplementary Panel C** / **Panel C** — pseudobulk Pearson correlation of blood DC1, culture-derived DC1, and blood DC2 clusters using highly variable genes

## Requirements

- R ≥ 4.3
- R packages: `Seurat`, `ggplot2`, `dplyr`, `ggrepel`, `patchwork`, `pheatmap`, `RColorBrewer`

Exact package versions used to generate the published figures are recorded in the `sessionInfo()` output at the end of `ONE_DC_Script.Rmd` (rendered output also available on request).

Install dependencies:
```r
install.packages(c("ggplot2", "dplyr", "ggrepel", "patchwork", "pheatmap", "RColorBrewer"))
if (!require("BiocManager", quietly = TRUE)) install.packages("BiocManager")
BiocManager::install("Seurat")
```

## Data

The processed `Seurat` object (`Seurat_Join_Filt_fresh_unstim.rds`) required to run this script is not hosted in this repository due to size. 
Processed object is available at **10.5281/zenodo.21093824**.
To run the script, place the `.rds` file at `data/Seurat_Join_Filt_fresh_unstim.rds` relative to the script, or edit the path in the `load-data` chunk.

## Usage
Open `ONE_DC_Script.Rmd` in RStudio and knit, or run interactively chunk-by-chunk. Output figures (PDF) are written to the working directory by default (configurable via the `OUTDIR` parameter near the top of the script).

## Contact
For questions about this code, contact audiger.c@wehi.edu.au
