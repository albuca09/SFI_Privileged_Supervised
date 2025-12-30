# SFI_IEEE — Spectrogram Analysis Pipeline for the SFI Smart Ocean Dataset

This repository provides a **Jupyter Notebook–based experimental pipeline** for loading, processing, and visualizing underwater acoustic signals from the **SFI Smart Ocean Dataset (SODAC)**. The focus is on **time–frequency analysis using spectrograms**, with figure layouts and parameter choices aligned with **IEEE-style scientific publications**. The notebook is designed for execution in **Google Colab**, assuming the dataset is stored in **Google Drive**.

## Objective

The main goals of this notebook are to (i) load underwater acoustic **TX/RX recordings** from SODAC, (ii) select the **frequency band** (LF, MF, HF) and **receiver** (R1 or R2), (iii) compute **STFT-based spectrograms** with physically motivated parameters, (iv) generate **publication-ready figures** consistent with IEEE formatting, and (v) optionally save figures and intermediate results. The pipeline is suitable for underwater acoustic propagation analysis, studies of multipath, reverberation, and Doppler effects, and preparation of figures for IEEE journals and conferences.

## Expected Dataset Structure

The notebook assumes that the dataset has been **extracted** in Google Drive with the following directory structure:

    SFI SMART OCEAN DATASET/
    ├── DESCOMPAC/
    │   ├── RX_LF/
    │   ├── RX_MF/
    │   ├── RX_HF/
    │   ├── TX_WAVEFORMS/
    │   │   └── TX/
    │   │       ├── wav/
    │   │       │   ├── LF/
    │   │       │   ├── MF/
    │   │       │   └── HF/
    │   │       └── csv/
    │   │           ├── LF/
    │   │           ├── MF/
    │   │           └── HF/
    │   └── ENVIRONMENT/
    │       └── Environmental/
    │           └── CTD.csv

**Note:** The environmental file `CTD.csv` is not required for spectrogram generation and is not directly used in the current pipeline.

## Dependencies

The notebook relies exclusively on standard scientific Python libraries, all available by default in Google Colab:

- `numpy`
- `scipy`
- `matplotlib`
- `soundfile`
- `torch`
- `pathlib`

## How to Run

1. Open `SFI_IEEE.ipynb` in Google Colab.  
2. Mount Google Drive:
   - `from google.colab import drive`
   - `drive.mount('/content/drive')`
3. Configure the frequency band and receiver in the configuration cell:
   - `BAND = "LF"` (options: `"LF"`, `"MF"`, `"HF"`)
   - `RX   = "R1"` (options: `"R1"`, `"R2"`)
4. Run all notebook cells sequentially from top to bottom.

## Main Features

- Robust loading of WAV files  
- Consistent handling of sampling rates  
- STFT-based spectrogram computation  
- Band-specific frequency limits (LF/MF/HF)  
- IEEE-compatible figure layout and color scaling  
- Explicit configuration for reproducibility  

## Physical Motivation

Spectrogram-based representations are physically motivated in underwater acoustics, as they explicitly encode key channel phenomena: multipath propagation (time-delayed replicas), reverberation (long energy tails in time), Doppler effects (frequency shifts and spectral tilting), frequency-selective fading, and impulsive noise. These effects are fundamental in underwater acoustic communications and motivate the use of time–frequency analysis both for signal interpretation and as input to machine learning models.

## Notes and Extensions

The notebook does **not** perform model training; it focuses on **signal analysis and visualization**. It can be extended to feature extraction, CNN-based learning pipelines, knowledge distillation experiments, and in-distribution/out-of-distribution (ID/OOD) evaluations. Figure layouts are intended for direct inclusion in IEEE-style papers.

## Dataset Citation

If this code or derived results are used in academic work, please cite the dataset as follows:

**Paul van Walree**, **Roald Otnes**, **Beatrice Tomasi**, **Bård Henriksen**, **Jean-Baptiste Danre**, and **Øivind Bergh**,  
*SFI Smart Ocean Dataset for Underwater Acoustic Communications*,  
IEEE DataPort, 2025.  
DOI: **10.21227/3aa6-4k33**  
Research article: https://doi.org/10.1109/IEEEDATA.2025.3577998  
Dataset page: https://ieee-dataport.org/open-access/sfi-smart-ocean-dataset-underwater-acoustic-communications

**Data formats:** WAV, CSV, JPG, ZIP.

## Intended Use

This notebook is intended for **academic and research use** in underwater acoustic communications, signal processing, machine learning for acoustics, and reproducible experimental analysis.
