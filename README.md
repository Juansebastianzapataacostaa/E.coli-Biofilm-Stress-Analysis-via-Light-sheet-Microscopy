# E.-coli-Biofilm-Stress-Analysis-via-Light-sheet-Microscopy
Quantitative image analysis pipeline for tracking gene expression dynamics in E. coli biofilms under metabolic stress, from Light Sheet Fluorescence Microscopy (LSFM) time-lapse data. Processes GFP fluorescence intensity (pRpoH heat-stress reporter) across microfluidic chip experiments, reconstructing community-level expression curves over time.
Background

Biofilms are closely linked to bacterial virulence and antibiotic resistance strategies. Understanding how stress-response genes drive biofilm formation is key to tackling these mechanisms. This project uses Light Sheet Fluorescence Microscopy (LSFM) to capture the real-time dynamics of biofilm formation in Escherichia coli K12 under ethanol-induced metabolic stress (90% EtOH), tracking expression of the heat-stress reporter pRpoH via GFP fluorescence in a custom PDMS microfluidic chip.

This repository contains the image processing and data reconstruction pipeline built to extract quantitative insights from those experiments.

LSFM time-lapse images (microfluidic chip)
            │
            ▼
    image_processing.py
    ┌─────────────────────────────────┐
    │  Per-image processing           │
    │  · Top-Hat morphological filter │
    │  · Segmentation                 │
    │  · Mean GFP intensity extraction│
    └─────────────────────────────────┘
            │
            ▼
    main.py
    ┌─────────────────────────────────┐
    │  Pipeline configuration         │
    │  · Parameter setup (Top-Hat     │
    │    size, paths, thresholds)     │
    │  · Batch execution              │
    └─────────────────────────────────┘
            │
            ▼
      .txt files (mean intensity per image)
            │
            ▼
    reconstruct_intensity.py
    ┌─────────────────────────────────┐
    │  Data reconstruction            │
    │  · Reads per-image .txt outputs │
    │  · Reconstructs community-level │
    │    intensity curve over time    │
    └─────────────────────────────────┘
            │
            ▼
    Gene expression dynamics plot
