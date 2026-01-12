# Genre-aware Metal Album Cover Generation (Diffusion + LoRA)

## Overview
This project explores a genre-aware system for generating metal album covers.  
We adapt a pretrained text-to-image diffusion model to metal aesthetics and evaluate outputs with multimodal metrics.

## Goals
- Build a “master” dataset linking **album cover + band + album + subgenre + lyrics**
- Generate covers in three prompt modes:
  - **G**: genre + band + album
  - **L**: lyrics summary only
  - **GL**: combined metadata + lyrics summary
- Evaluate results:
  - **CLIP text-image similarity**
  - **FID** (real vs generated)
  - Style coverage via **CLIP-embedding clustering**

## Datasets (Kaggle)
- [Large Metal Lyrics Archive (228K songs)](https://www.kaggle.com/datasets/markkorvin/large-metal-lyrics-archive-228k-songs)
- [Every Metal Archives Band (November 2024)](https://www.kaggle.com/datasets/guimacrlh/every-metal-archives-band-october-2024)
- [Metal Album Art by Subgenre](https://www.kaggle.com/datasets/fraserwtt/metal-album-art-by-subgenre)
- [Metal Albums Artwork](https://www.kaggle.com/datasets/benjamnmachn/metal-albums-artwork)

## Method
### 1) Data unification
- Merge CSVs by band/album names
- Remove duplicates/conflicts
- Map subgenres → broader style clusters (e.g., traditional / extreme)
- Keep only albums with reliable: cover + genre + lyrics

### 2) Prompt builder (G / L / GL)
- G: template prompt with subgenre, band, album
- L: lyrics cleaning + TF-IDF keyword extraction + short templated summary
- GL: combine metadata prompt + lyrics summary

### 3) Visual style clustering
- Extract CLIP embeddings for real covers
- k-means clustering
- Visualize with PCA/t-SNE and compare clusters vs subgenres

### 4) Diffusion generation + adaptation
- Baseline generation with pretrained model
- LoRA fine-tuning on metal cover domain (optionally separate adapters for traditional vs extreme)

### 5) Baseline for comparison
- Neural Style Transfer (content neutral images + style metal covers)

### 6) Evaluation
- CLIP cosine similarity(prompt, image)
- FID(real covers, generated covers)
- Cluster assignment distribution (real vs generated)
- LoRA training
- Evaluation: CLIP + FID + cluster coverage
