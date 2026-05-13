# RdDM-Methylation-Analysis

<div align="center">

**Reproducible methylpy-based workflow for analyzing cytosine methylation across Arabidopsis 45S rDNA**

Whole-genome bisulfite sequencing analysis with context-specific methylation quantification (CG, CHG, CHH)

</div>

---

## Overview

This repository contains a comprehensive Jupyter notebook workflow for analyzing rDNA cytosine methylation patterns from whole-genome bisulfite sequencing (WGBS) data. Using publicly available data from [GSE39901 (Stroud et al., 2013)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE39901), the workflow:

✓ Maps bisulfite sequencing reads to the 45S rDNA reference  
✓ Calls methylated cytosines using `methylpy`  
✓ Quantifies methylation in CG, CHG, and CHH contexts  
✓ Generates 50 bp binned methylation heatmaps  
✓ Produces publication-ready figures (PNG & SVG)  

---

## Quick Start

1. **Open the main analysis notebook:**
   ```
   methylation_analysis_methylpy_independent_12052026.ipynb
   ```

2. **Run all cells in order** - The notebook will automatically:
   - Create required working directories
   - Download and preprocess WGBS data
   - Generate output folders

3. **Explore extended analyses:**
   ```
   extended_analysis.ipynb
   ```

---

## Project Structure

```
RdDM-Methylation-Analysis/
├── README.md                                          # This file
├── samples_manifest.csv                               # Sample metadata
│
├── ref/                                               # Reference sequences
│   ├── rDNA_45S.fa                                   # 45S rDNA sequence
│   ├── rDNA_45S_sanitized.fa                         # Cleaned 45S rDNA (chrRDN45S)
│   ├── 45S_annotation.csv                            # rDNA feature annotations
│   ├── NOR2-flanking 150 kb.gb                       # NOR2 genomic context
│   └── NOR4-flanking 150 kb.gb                       # NOR4 genomic context
│
├── methylation_analysis_methylpy_independent_12052026.ipynb    # Main workflow
└── extended_analysis.ipynb                            # Additional analyses
```

---

## Workflow Pipeline

| Step | Description |
|------|-------------|
| **1. Data Prep** | Downloads and prepares WGBS sequencing data from GSE39901 |
| **2. QC** | Performs read preprocessing and quality checks (FastQC, Trim Galore) |
| **3. Indexing** | Prepares 45S rDNA reference and creates bisulfite-converted versions |
| **4. Mapping** | Maps reads to converted 45S rDNA with Bowtie2 via Bismark |
| **5. Methylation Calling** | Calls methylated cytosines using methylpy |
| **6. Aggregation** | Calculates methylation levels in CG, CHG, and CHH contexts |
| **7. Visualization** | Generates 50 bp bin heatmaps and region-wise methylation plots |
| **8. Export** | Exports figure values as CSV tables |

---

## Main Outputs

The workflow generates:

- **Heatmaps:** 50 bp binned methylation across the 45S rDNA unit
- **Region Maps:** Methylation levels across annotated rDNA features  
- **Data Files:** CSV tables containing plotted methylation values
- **Figures:** Publication-ready PNG and SVG images

**Output Directories:**
```
out/figures/          # PNG and SVG output figures
out/summary/          # Summary statistics
work/                 # Intermediate analysis files
```

---

## Requirements

### External Tools
- `methylpy` - Methylation analysis
- `Bismark` - Bisulfite read mapper
- `Bowtie2` - Sequence alignment
- `FastQC` - Quality control
- `Trim Galore` - Read trimming
- `samtools` - BAM/SAM manipulation

### Python Packages
```
pandas
numpy
matplotlib
```

---

## Data Source

Whole-genome bisulfite sequencing data: **GSE39901**

**Citation:** Stroud et al. (2013) – RdDM pathway-dependent methylation patterns

---

## Citations

If using this workflow, please cite:

- **Stroud, H., et al.** (2013). RNA-directed DNA methylation and Pol IV-dependent transcription initiation at heterochromatic repeats. *Nature Structural & Molecular Biology*, 20(3), 318-324. [[PubMed]](https://pubmed.ncbi.nlm.nih.gov/23463315/)

- **Schultz, M.D., et al.** (2015). methylpy: A comprehensive Python library for analyzing whole genome bisulfite sequencing data. *PLoS ONE*, 10(11), e0143309. [[DOI]](https://doi.org/10.1371/journal.pone.0143309)

---

## Notes

- The notebook is designed as an independent, start-to-end workflow with **checkpointed steps**
- If intermediate files already exist, corresponding steps are skipped and reported
- All paths and dependencies are configured within the notebook

---

<div align="center">

Last updated: May 2026

</div>
