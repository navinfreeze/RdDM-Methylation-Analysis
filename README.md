# RdDM-Methylation-Analysis
Reproducible methylpy-based workflow for analyzing CG, CHG, and CHH methylation across Arabidopsis 45S rDNA from whole-genome bisulfite sequencing data.


# rDNA methylation analysis using methylpy

Reproducible methylpy-based workflow for analyzing CG, CHG, and CHH methylation across Arabidopsis 45S rDNA from whole-genome bisulfite sequencing data.

## Overview

This repository contains a Jupyter notebook for analyzing rDNA cytosine methylation using whole-genome bisulfite sequencing data from Stroud et al. (2013), GSE39901. The workflow maps bisulfite sequencing reads to a 45S rDNA reference sequence, calls methylated cytosines using methylpy, summarizes methylation in CG, CHG, and CHH contexts, and generates publication-ready heatmaps.

## Repository contents

```text
The notebook is designed as an independent, start-to-end workflow with checkpointed steps. If intermediate files already exist, the corresponding steps are skipped and reported.

Main outputs

The workflow generates:

50 bp binned methylation heatmaps across the 45S rDNA unit
region-wise methylation heatmaps across annotated rDNA features
CSV tables containing the plotted methylation values
publication-ready PNG and SVG figures
Analysis summary

The notebook performs the following steps:

Downloads and prepares WGBS sequencing data.
Performs read preprocessing and quality checks.
Prepares the 45S rDNA reference.
Maps reads to the converted 45S rDNA reference.
Calls methylation using methylpy.
Aggregates methylation levels in CG, CHG, and CHH contexts.
Generates 50 bp bin heatmaps.
Generates region-wise methylation frequency heatmaps.
Exports figure values as CSV tables.
Data source

Whole-genome bisulfite sequencing data were obtained from GSE39901, originally published by Stroud et al. (2013).

Requirements

The workflow uses Python/Jupyter and external command-line tools including:

methylpy
Bismark
Bowtie2
FastQC
Trim Galore
samtools

Python packages used include:

pandas
numpy
matplotlib
Usage

Open the notebook and run all cells in order:

methylation_analysis_methylpy_independent_12052026.ipynb

The notebook will create the required working folders and output folders automatically.

Outputs

Generated results are saved into the notebook-defined project directory, including:

out/figures/
out/summary/
work/
ref/
Citation

If using this workflow, please cite the original data source and tools:

Stroud et al. (2013)
Schultz et al. (2015), methylpy
