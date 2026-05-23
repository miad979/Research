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

## 8) Explainability quantitative metric (choose 1 primary)
- Explanation stability across rounds (e.g., similarity of attribution maps)
- Explanation consistency across clients
- Deletion/insertion score (if implemented)

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
- XAI qualitative examples + quantitative stability table

