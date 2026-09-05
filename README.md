# Comparative Analysis of Type III Effector Repertoires in Environmental *Pseudomonas*

This repository contains the bioinformatics pipeline and supporting data used in:

> Nedeljković M, Milanović Đ, Anđelković M, Nikolić I, Stanković S, Lozo J, Atanasković I. **Comparative analysis of predicted Type III effector repertoires in environmental *Pseudomonas* identifies new candidate effectors.**

## Overview

The Type III secretion system (T3SS) is used by Gram-negative bacteria to translocate effector proteins (T3SEs) into host cells. While T3SE repertoires are well studied in pathogens such as *Pseudomonas syringae* (Psy), their diversity in environmental, plant- and soil-associated *Pseudomonas* strains remains largely unexplored.

This project implements a customized bioinformatics pipeline to:

1. Predict candidate T3SEs in a curated collection of 51 T3SS-positive *Pseudomonas* genomes using [Effectidor](https://effectors.tau.ac.il/) (prediction score ≥ 0.6).
2. Compare the predicted effectors (**Database 1**) against a reference set of known Psy effectors (**Database 2**) via BLASTp (e-value ≤ 1e-5) to filter out effectors homologous to characterized Psy effectors.
3. Summarize the resulting non-Psy-like effector repertoire (596 sequences / 93 unique annotations) and identify the most frequent candidate annotations, including ankyrin repeat-containing proteins (ARP) and MaoC dehydratase, for downstream experimental follow-up.

## Repository Structure

```
.
├── data/
│   ├── database_2.xlsx        # Reference database of known P. syringae (Psy) T3SE sequences
│   └── effectidor_output/     # Raw Effectidor prediction output for the 51-genome collection (Database 1)
├── pipeline.ipynb             # Jupyter notebook implementing the full analysis pipeline
├── requirements.txt           # Python dependencies
└── README.md
```

## Pipeline Summary

The notebook (`pipeline.ipynb`) walks through:

- Loading and parsing Effectidor prediction results across the genome collection.
- Filtering predicted effectors by prediction score (≥ 0.6).
- Running/parsing BLASTp comparisons between Database 1 (environmental effectors) and Database 2 (Psy effectors).
- Removing environmental effectors with significant homology (e-value ≤ 1e-5) to known Psy effectors.
- Tallying and ranking functional annotations to identify the most frequent candidate effectors.
- Generating summary tables and figures

## Requirements

Python dependencies are listed in `requirements.txt`. Install them with:

```bash
pip install -r requirements.txt
```

In addition to the Python packages, **BLAST+ version 2.16.0** must be installed and available on your system `PATH`, since the pipeline calls BLASTp directly to compare Database 1 and Database 2. You can download it from the [NCBI BLAST+ releases](https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.16.0/) and verify the installation with:

```bash
blastp -version
```

## Citation

If you use this pipeline, please cite:

Nedeljković M, et al. Comparative analysis of predicted Type III effector repertoires in environmental *Pseudomonas* identifies new candidate effectors.

## Contact

Corresponding author: prof Jelena Lozo — jlozo@bio.bg.ac.rs
