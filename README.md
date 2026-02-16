# Genre-aware Metal Album Cover Generation (Diffusion + LoRA)

## Overview
This project explores genre-aware generation of metal album covers.  
A pretrained text-to-image diffusion model (Stable Diffusion v1.5) is adapted to metal aesthetics via LoRA and evaluated with lightweight multimodal metrics (CLIP-based).

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
- Train a **LoRA adapter** on real metal cover art to inject domain aesthetics.
- Compare **baseline vs LoRA** generations using matched seeds.
- Evaluate with: **CLIP text–image similarity**, **zero-shot genre probe**, **kNN distance in CLIP space**, and **distribution coverage**.
- Quick **NST** post-processing experiment (visually minor effect; not pursued further).

## Datasets (Kaggle)
- Large Metal Lyrics Archive (228K songs): https://www.kaggle.com/datasets/markkorvin/large-metal-lyrics-archive-228k-songs
- Metal Albums Artwork: https://www.kaggle.com/datasets/benjamnmachn/metal-albums-artwork

## Method (high level)
1. **Data merge & filtering** (band/album normalization; keep albums with cover + genre + lyrics).
2. **EDA** (balance checks, simple visual features, CLIP embeddings for projections/clustering).
3. **Lyrics preprocessing + TF–IDF** (clean + extract motifs for L/GL modes).
4. **Captioning** with *Florence-2-base* (with anti-cheat crop + re-caption).
5. **Prompt builder** for G/L/GL/C/GC/GLC/P.
6. **Baseline generation** (Stable Diffusion v1.5).
7. **LoRA training** on real metal covers and sanity checks.
8. **Paired generation** (baseline vs LoRA) across modes with matched seeds.
9. **Evaluation** (CLIP alignment, zero-shot genre, kNN realism, coverage plots).
10. **NST experiment** (optional baseline; negligible visual change).

## Results
- Example generations and comparisons are in `results/`.
- Full write-up and slides are in `reports/`.

## Repository
- `metal-album-cover-generation.ipynb` — full pipeline (data → prompts → generation → evaluation)
- `results/` — curated samples (baseline, modes, LoRA vs baseline)
- `reports/` — documentation PDF + presentation
- `lora/` — LoRA weights + training metadata

### `results/` structure
Curated outputs and evaluation artifacts:

- `results/gen_baseline/` — baseline SD generations with simple hand-written prompts (sanity-check samples)
- `results/gen_baseline_6modes/` — baseline generations across the 6 prompt modes (**G/L/GL/C/GC/GLC**)
- `results/gen_lora/` — LoRA-adapted SD generations (same pipeline, LoRA enabled)
- `results/eval_base_vs_lora/` — plots/tables/aggregates comparing baseline vs LoRA (CLIP metrics, kNN distance, coverage)
- `results/exp_sd_styletransfer/` — NST experiment outputs (baseline SD as content + random same-genre real covers as style)
- `results/florence_captions.json` — cached Florence-2-base captions used in **C/GC/GLC**
- `results/exp_sd_styletransfer-20260216T115808Z-1-001.zip` — archived NST outputs bundle

### `lora/` structure
LoRA training artifacts:

- `lora/pytorch_lora_weights.safetensors` — trained LoRA adapter weights
- `lora/metadata.jsonl` — training metadata (image paths + captions/prompts) for reproducibility

### `reports/` structure
Project documents:

- `reports/documentation.doc` — full write-up
- `reports/presentation.pptx` — final slides
- `reports/project_idea.pdf` — initial proposal


## Reproducibility
Install dependencies and run the notebook end-to-end. Data download/paths are described inside the notebook (Kaggle sources above).
