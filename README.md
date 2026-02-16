# Genre-aware Metal Album Cover Generation (Diffusion + LoRA)

## Overview
This project explores genre-aware generation of metal album covers.  
A pretrained text-to-image diffusion model (Stable Diffusion v1.5) is adapted to metal aesthetics via LoRA and evaluated with lightweight multimodal metrics (CLIP-based).

# Visual Results

---

## 1. Simple Handwritten Prompts (Baseline and LoRA)

### Death Metal – Simple Handwritten Prompt

<img src="results/gen_baseline/death_01.png" width="350">
<img src="results/gen_lora/lora_001.png" width="350">

### Thrash Metal – Simple Handwritten Prompt

<img src="results/gen_baseline/thrash_01.png" width="350">
<img src="results/gen_lora/lora_005.png" width="350">

---

## 2. Prompt Mode Examples (Mixed Baseline and LoRA Samples)

Below are representative examples from different prompt modes (seed = 0).

### G Mode (Genre + Metadata)

<img src="results/eval_base_vs_lora/images/base/G/a0099_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/base/G/a0091_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/lora/G/a0057_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/lora/G/a0035_s0.png" width="350">

---

### GL Mode (Genre + Lyrics)

<img src="results/eval_base_vs_lora/images/base/GL/a0007_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/base/GL/a0002_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/lora/GL/a0095_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/lora/GL/a0062_s0.png" width="350">

---

### C Mode (Caption-based)

<img src="results/eval_base_vs_lora/images/base/C/a0080_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/base/C/a0070_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/lora/C/a0095_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/lora/C/a0007_s0.png" width="350">

---

### GLC Mode (Genre + Lyrics + Caption)

<img src="results/eval_base_vs_lora/images/base/GLC/a0035_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/base/GLC/a0022_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/lora/GLC/a0017_s0.png" width="350">
<img src="results/eval_base_vs_lora/images/lora/GLC/a0023_s0.png" width="350">

---

## 3. Direct Baseline vs LoRA Comparison (Per Mode)

### G Mode

| Baseline | LoRA |
|----------|------|
| <img src="results/eval_base_vs_lora/images/base/G/a0005_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/G/a0005_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/G/a0045_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/G/a0045_s0.png" width="350"> |

---

### L Mode

| Baseline | LoRA |
|----------|------|
| <img src="results/eval_base_vs_lora/images/base/L/a0026_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/L/a0026_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/L/a0035_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/L/a0035_s0.png" width="350"> |

---

### GL Mode

| Baseline | LoRA |
|----------|------|
| <img src="results/eval_base_vs_lora/images/base/GL/a0005_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GL/a0005_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GL/a0075_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GL/a0075_s0.png" width="350"> |

---

### C Mode

| Baseline | LoRA |
|----------|------|
| <img src="results/eval_base_vs_lora/images/base/C/a0051_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/C/a0051_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/C/a0011_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/C/a0011_s0.png" width="350"> |

---

### GC Mode

| Baseline | LoRA |
|----------|------|
| <img src="results/eval_base_vs_lora/images/base/GC/a0011_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GC/a0011_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GC/a0095_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GC/a0095_s0.png" width="350"> |

---

### GLC Mode

| Baseline | LoRA |
|----------|------|
| <img src="results/eval_base_vs_lora/images/base/GLC/a0001_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GLC/a0001_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GLC/a0096_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GLC/a0096_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GLC/a0007_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GLC/a0007_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GLC/a0008_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GLC/a0008_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GLC/a0042_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GLC/a0042_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GLC/a0020_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GLC/a0020_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GLC/a0036_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GLC/a0036_s0.png" width="350"> |
| <img src="results/eval_base_vs_lora/images/base/GLC/a0073_s0.png" width="350"> | <img src="results/eval_base_vs_lora/images/lora/GLC/a0073_s0.png" width="350"> |

## Goals
- Build a “master” dataset linking **cover + band + album + subgenre + lyrics**.
- Generate covers under multiple prompt modes:
  - **G**: genre + band + album (metadata-only)
  - **L**: lyrics-summary-only
  - **GL**: metadata + lyrics summary
  - **C**: Florence caption
  - **GC**: metadata + caption
  - **GLC**: metadata + lyrics summary + caption
  - **P**: additional prompt variants
- Train a **LoRA adapter** on real metal cover art to inject domain-specific aesthetics.
- Compare **baseline vs LoRA** generations using matched seeds.
- Evaluate with: **CLIP text–image similarity**, **zero-shot genre probe**, **kNN distance in CLIP space**, and **distribution coverage**.
- Quick **NST** post-processing experiment (visually minor effect; not pursued further).

## Datasets (Kaggle)
- Large Metal Lyrics Archive (228K songs): https://www.kaggle.com/datasets/markkorvin/large-metal-lyrics-archive-228k-songs
- Metal Albums Artwork: https://www.kaggle.com/datasets/benjamnmachn/metal-albums-artwork

## Method (high level)
1. **Data merge and filtering** (band/album normalization; keep albums with cover + genre + lyrics).
2. **EDA** (balance checks, simple visual features, CLIP embeddings for projections and clustering).
3. **Lyrics preprocessing + TF–IDF** (clean and extract motifs for L/GL modes).
4. **Captioning** with *Florence-2-base* (with anti-cheat crop + re-caption).
5. **Prompt builder** for G/L/GL/C/GC/GLC/P.
6. **Baseline generation** (Stable Diffusion v1.5).
7. **LoRA training** on real metal covers and sanity checks.
8. **Paired generation** (baseline vs LoRA) across modes with matched seeds.
9. **Base SD vs LoRA evaluation**
    - **Text–image alignment (CLIP):** compute cosine similarity between each prompt and its generated image embedding, then aggregate per mode (G/L/GL/C/GC/GLC/…) and per genre.
    - **Zero-shot genre probe (CLIP):** classify each generated image as death vs thrash by comparing its CLIP embedding to two genre text prompts and report accuracy/bias patterns per mode and per model.
    - **Realism via nearest real cover (kNN in CLIP space):** for every generated image, find the closest real album cover embedding and record the minimum cosine distance (lower is better). Report averages per mode for baseline vs LoRA.
    - **Style coverage (distribution plots):** project CLIP embeddings (e.g., PCA) and visually compare real, baseline, and LoRA distributions to assess domain coverage.
10. **Neural Style Transfer (NST) experiment**
    - Apply Gatys-style NST to baseline SD generations (content) using a random real cover from the same genre as the style reference.
    - Save both baseline and stylized outputs; visual changes were minor, so NST is treated as exploratory rather than a competitive baseline.

## Results
- Example generations and comparisons are in `results/`.
- Full write-up and slides are in `reports/`.

## Repository
- `metal-album-cover-generation.ipynb` — full pipeline (data → prompts → generation → evaluation)
- `results/` — curated samples (baseline, modes, LoRA vs baseline)
- `reports/` — documentation and presentation
- `lora/` — LoRA weights and training metadata

### `results/` structure
Curated outputs and evaluation artifacts:

- `results/gen_baseline/` — baseline Stable Diffusion generations with simple hand-written prompts (sanity check)
- `results/gen_lora/` — LoRA-adapted Stable Diffusion generations with simple hand-written prompts (same pipeline as above, LoRA enabled)
- `results/gen_baseline_6modes/` — baseline Stable Diffusion generations across the 6 prompt modes (**G/L/GL/C/GC/GLC**)
- `results/eval_base_vs_lora/` — paired generation for **baseline vs LoRA** (same albums, modes and seeds)
  - `images/` — generated images organized by model and mode:
    - `images/base/<MODE>/` — baseline SD outputs per mode (G/L/GL/C/GC/GLC/…)
    - `images/lora/<MODE>/` — LoRA-adapted outputs per mode (G/L/GL/C/GC/GLC/…)
  - `sanity/` — sanity-check set (2 albums × 2 models × all modes), used to validate the pipeline
  - `eval_records.jsonl` — raw per-sample records (album metadata + mode + seed + prompt + paths to base/lora images)
  - `eval_records_clean.jsonl` — cleaned records (black/censored generations removed by safety filtering)
  - `dropped_black_records.csv` — list of removed “black” (censored) samples
  - `run_config.json` — evaluation run configuration (steps, guidance, resolution, seeds, model id, LoRA dir, etc.)
- `results/exp_sd_styletransfer/` — Neural Style Transfer (NST) experiment outputs
  - `generated_base/` — baseline Stable Diffusion generations used as **content** images for NST
  - `generated_stylized/` — NST results (stylized outputs) produced using **same-genre real covers** as style references
- `results/florence_captions.json` — cached Florence-2-base captions used in **C/GC/GLC**

### `lora/` structure
LoRA training artifacts:

- `lora/pytorch_lora_weights.safetensors` — trained LoRA adapter weights
- `lora/metadata.jsonl` — training metadata (image paths and prompts) for reproducibility

### `reports/` structure
Project documents:

- `reports/documentation.doc` — full write-up
- `reports/presentation.pptx` — presentation slides
- `reports/project_idea.pdf` — initial project idea

## Reproducibility
Install dependencies and run the notebook end-to-end. Data download/paths are described inside the notebook (Kaggle sources above).


