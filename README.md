# PDAC-Spatial-Deconvolution-Benchmark

This repository provides an end-to-end pipeline for benchmarking spatial deconvolution in pancreatic cancer by integrating:

- Non-immune scRNA-seq (GSE194247, n=5)
- Immune scRNA-seq (GSE235449, n=1)
- Spatial transcriptomics (GSE235315, n=7)

Inspired by the benchmarking paper: [Nature Methods 2022](https://www.nature.com/articles/s41592-022-01480-9), this project evaluates how well different methods can reconstruct cellular architecture in PDAC tissues using matched multimodal data.

---

## Goals

1. Preprocess all modalities consistently (QC, batch correction, annotation)
2. Train a reference on combined scRNA (immune + non-immune)
3. Apply four major deconvolution tools:
   - Cell2location
   - Tangram
   - SPOTlight
   - RCTD
4. Compare predictions using standard spatial metrics:
   - Correlation vs reference
   - Spatial coherence
   - Entropy and specificity
   - Abundance agreement across methods

---

## Datasets

| Dataset     | Modality           | Samples | Description         |
|-------------|--------------------|---------|----------------------|
| GSE194247   | scRNA-seq (non-immune) | 5     | Tumor + stroma cells |
| GSE235449   | scRNA-seq (immune) | 1       | T cells, B cells, NK |
| GSE235315   | Spatial Visium     | 7       | Matched ST from PDAC |

---

## Generalization

This pipeline is modular and reusable:
- Any `.h5ad` or Seurat scRNA-seq reference
- Any 10x Visium-compatible spatial dataset
- Tools can be added (e.g., BayesPrism, DestVI)

---

## Benchmarking Metrics (from SpatialBenchmarking) - In Process

- **Spearman correlation** (predicted vs true abundance)
- **Co-localization index**
- **Reconstruction score**
- **Abundance entropy**
- **Cross-method consistency**

---

## Setup

```bash
git clone https://github.com/sohini0512/PDAC-Spatial-Deconvolution-Benchmark.git
cd PDAC-SpatialDeconvBench
Run all the scripts sequentially.
