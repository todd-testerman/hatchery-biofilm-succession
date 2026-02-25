# Succession and Shifting Identities in Freshwater, Built Environment Biofilm Communities

Code and data for Testerman et al. (2025).

## Overview

This study examines the temporal dynamics of microbial biofilm communities on surfaces within an indoor rainbow trout (*Oncorhynchus mykiss*) hatchery facility. Wall swabs from epoxy-coated concrete raceways were collected across biofilms ranging from 9 to 80 days old. Community composition was profiled using 16S rRNA gene (V4 region) amplicon sequencing.

## Repository Contents

### Analysis Code (R Markdown)
- `Updated_2021_markdown_for_pub.Rmd` - **Primary analysis script** for the publication. Analyzes wall swab communities grouped by maturity days (9, 23, 38, 53, 65, 80 days), concrete surfaces only. Generates all main and supplemental figures.
- `Updated_2021_markdown.Rmd` - Extended working version with additional exploratory analyses (network analysis, mortality regression, raceway comparisons).
- `2021_markdown.Rmd` - Original analysis (2022) using 3-level maturity grouping (Early/Middle/Late).
- `Material Comparison.Rmd` - Comparison of concrete vs. stainless steel surface communities at day 23.

### Metadata
- `mapping_file_all_runs.txt` - Sample metadata including sample type, raceway, maturity days, material, disease status, treatments, and QC metrics.

### Statistical Results (CSV)
- `*_perm_results.csv` - PERMANOVA results for beta diversity (Bray-Curtis, Jaccard, weighted/unweighted UniFrac)
- `pairwise_*_perm_results.csv` - Pairwise PERMANOVA comparisons between maturity groups
- `faith_ttest_ws.csv`, `faith_wilcox_ws.csv` - Faith's PD pairwise tests
- `shannon_wilcox_ws.csv` - Shannon diversity pairwise tests
- `observed_ASV_wilcox_ws.csv` - Observed ASV richness pairwise tests
- `*_material.csv` - Corresponding tests for material comparison

### Figures (PNG)
Located in `Figures_all_maturity_days/`:
- Figure 1: Taxonomic barplots (Class and Genus level)
- Figure 2: Beta diversity NMDS ordinations (4 metrics)
- Figure 3: Alpha diversity (Observed ASVs, Shannon, Faith's PD)
- Figure 4: UpSet plot of shared/unique ASVs across timepoints
- Figure 5: ANCOM-BC differential abundance (Early vs Late)
- Figure 6: Boxplots of important indicator taxa
- Supplemental figures: Tailscreen/baffle barplots, PCA biplot, class-level UpSet, Random Forest importance

## Methods Summary

- **Sequencing**: 16S rRNA V4 region, Illumina MiSeq paired-end
- **Bioinformatics**: QIIME 2, DADA2 for ASV calling, Silva 138 taxonomy
- **Quality control**: Samples retained with >=8,000 sequencing reads AND >=8,000 16S copies (qPCR); 261/528 samples retained
- **Analysis**: R with phyloseq, microViz, vegan, ANCOM-BC, randomForest
- **Rarefaction depth**: 8,000 reads
- **Statistical testing**: PERMANOVA, beta-dispersion, Wilcoxon/t-tests (Holm-corrected), ANCOM-BC, Random Forest classification

## Requirements

R packages (installed via `pacman`):
phyloseq, qiime2R, tidyverse, microViz, ANCOMBC, vegan, rstatix, pairwiseAdonis, randomForest, rsample, ComplexUpset, MicrobiotaProcess, patchwork, ggpubr, and others (see Rmd files for full list).

QIIME 2 artifacts (`.qza`/`.qzv` files) are required to run the analysis but are not included in this repository due to size. Contact the corresponding author for access.

## Authors

- Todd Testerman - University of Connecticut
- Stacy King - Riverence Provisions (posthumous)
- Timothy J. Welch - USDA-ARS NCCCWA
- Gregory D. Wiens - USDA-ARS NCCCWA
- Joerg Graf - University of Connecticut
