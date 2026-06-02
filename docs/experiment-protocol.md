# Experiment Protocol (paper-ready)

## 1) Task
- Binary classification: **Pleural Effusion vs No Effusion**
- Dataset: **NIH ChestX-ray14**

## 2) Data preprocessing
- Image resize: 224×224 (baseline)
- Normalization: ImageNet mean/std (for pretrained DeiT/ResNet) or dataset-specific if needed
- Train/val/test split: patient-level split strongly preferred

## 3) FL simulation
- Number of clients (hospitals): **10**
- Round-based training: select all clients per round (start), later optionally sample fraction C
- Local epochs: 1–5 (tune)
- Communication rounds: 50 for dev; 100–200 for final

## 4) Non-IID generation
- Dirichlet label skew with α ∈ {0.1, 0.3, 1.0}
- Verify and report per-client label distributions (plots)

## 5) Methods
### Baselines
- Centralized training (upper bound)
- Local-only training per client (lower bound)
- FedAvg
- FedProx

### Models
- CNN baseline: ResNet-18
- Lightweight ViT: DeiT-Tiny

## 6) Robustness stress test (optional but recommended)
- Noisy labels on 1–2 clients:
  - Noise rate: 20–40%
  - Noise type: random flip or targeted label-flipping

## 7) Explainability
- ResNet: Grad-CAM
- DeiT: attention rollout / transformer attribution

## 8) Attribution stability (primary quantitative XAI metric)
Define and report *attribution stability* in a way that is comparable across rounds and clients.

### 8.1) Attribution map generation (fixed across all experiments)
- Compute attribution maps on a fixed evaluation subset (e.g., 200 images sampled once and held fixed).
- Use the same preprocessing, target class, and normalization for all rounds.
- Normalize attribution maps to [0, 1] per image.

### 8.2) Stability across rounds (temporal stability)
For each image and each client/model, compute similarity between attribution maps at two rounds (e.g., r and r+Δ).
- Choose Δ (recommended): 5 or 10 rounds.
- Similarity metric (pick 1 primary):
  - **SSIM** on normalized maps, or
  - **Spearman rank correlation** on flattened maps.
Report mean ± std over images, and plot stability vs round.

### 8.3) Consistency across clients (cross-site consistency)
For a fixed global round r*, compare attribution maps across clients for the same fixed evaluation subset.
- Report average pairwise similarity (same similarity metric as 8.2).
- Also report dispersion (std / IQR) to show heterogeneity.

### 8.4) Thresholded-region overlap (optional secondary)
- Threshold attribution maps at top-k% mass (e.g., k = 10%).
- Compute IoU overlap across rounds/clients.

## 9) Metrics
- Primary: AUC (preferred in medical classification)
- Secondary: accuracy, F1, sensitivity/specificity
- Report mean ± std over ≥3 seeds
- Report per-client performance variance (fairness)

## 10) Required figures/tables
- Non-IID label distribution plots per α
- Global performance vs rounds (FedAvg vs FedProx)
- Performance vs α severity
- Robustness (noise) table
- XAI qualitative examples + **attribution stability** table/plots:
  - Stability vs rounds (Δ fixed)
  - Consistency across clients at round r*

