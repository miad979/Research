# Thesis Plan (Literature Review → Experiments → Publication)

**Project title (final)**: **Robustness, Explainability, and Attribution Stability of Lightweight Vision Transformers for Federated Chest X‑ray Classification under Non‑IID Client Distributions**

Date: 2026-05-23

## 0) Confirmed scope (frozen unless revised)
- **Dataset**: NIH ChestX-ray14
- **Task**: Binary classification — *Pleural Effusion vs No Effusion*
- **Clients (hospitals)**: 10
- **Non-IID**: Dirichlet label skew with α ∈ {0.1, 0.3, 1.0}
- **Baselines**: centralized, local-only, FedAvg, FedProx
- **Models**: DeiT-Tiny (lightweight ViT) + ResNet-18 baseline
- **Robustness stress test**: noisy labels on 1–2 clients
- **Explainability**: Grad-CAM (CNN) + transformer attribution + stability/consistency metric + attribution stability

## 1) Research questions (adapt as needed)
- **RQ1 (Non-IID)**: How does Non-IID severity affect FL performance for effusion classification?
- **RQ2 (Robustness)**: Does FedProx (vs FedAvg) improve robustness under Non-IID and noisy labels?
- **RQ3 (Explainability)**: Are explanations stable across clients and across rounds? How does Non-IID affect interpretability?
- **RQ4 (Attribution stability)**: How stable are attribution maps across FL rounds and across clients for DeiT-Tiny vs ResNet-18?
- **RQ5 (Lightweight ViTs)**: Can lightweight ViTs match/beat CNN baselines in FL with comparable compute/communication?

## 2) Chapter structure
### Chapter 1 — Introduction
- Motivation: medical data silos, cross-hospital heterogeneity (Non-IID)
- Why CXR + pleural effusion
- Contributions (3–5 bullets)

### Chapter 2 — Literature Review
Use `docs/literature-review-outline.md`.

### Chapter 3 — Methodology
- Data preprocessing & label definition
- FL simulation protocol (clients, rounds)
- Non-IID partition method
- Models and training (ResNet-18, DeiT-Tiny)
- FL algorithms (FedAvg, FedProx)
- Robustness test design (noisy labels)
- Explainability pipeline + attribution stability metric

### Chapter 4 — Experiments & Results
- Main metrics + confidence intervals
- Non-IID sweep (α values)
- FedAvg vs FedProx comparison
- Robustness (noisy labels)
- Explainability quantitative analysis + visual examples
- Attribution stability analysis (across rounds / across clients)

### Chapter 5 — Discussion
- tradeoffs, limitations, ethics/privacy clarity

### Chapter 6 — Conclusion & Future Work
- Future: secure aggregation/DP, real multi-site data, personalization, multi-label

## 3) Deliverables
- Thesis PDF
- Submission-ready paper PDF (`docs/paper-outline.md`)
- Reproducible code + split scripts
- Figures/tables for Non-IID, robustness, XAI stability
