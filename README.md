# Robustness and Explainability of Lightweight Vision Transformers for Federated Chest X‑ray Classification under Non‑IID Client Distributions — Thesis + Publication Plan

This repository contains the **thesis plan**, **paper plan**, and **execution checklists** for the project:

> **Robustness and Explainability of Lightweight Vision Transformers for Federated Chest X‑ray Classification under Non‑IID Client Distributions**

## Confirmed experimental focus (as of 2026-05-23)
- Modality/Dataset: **NIH ChestX-ray14**
- Task: **Binary classification** — **Pleural Effusion vs No Effusion**
- FL simulation: **10 hospital clients**, **Non‑IID Dirichlet** splits (α = 0.1 / 0.3 / 1.0)
- Baselines: Centralized, Local-only, **FedAvg**, **FedProx**
- Models: **DeiT-Tiny** (lightweight ViT) + **ResNet-18** baseline
- Robustness add-on: **noisy labels on 1–2 clients**
- Explainability: Grad-CAM (CNN) + ViT attribution + **stability/consistency** metric

## Repository map
- `docs/thesis-plan.md`
- `docs/literature-review-outline.md`
- `docs/related-work-matrix-template.csv`
- `docs/experiment-protocol.md`
- `docs/paper-outline.md`
- `docs/timeline-to-jan-2027.md`

## Style conventions (to keep everything consistent)
- Use **“Chest X‑ray”** (with the hyphen) consistently in the thesis/paper.
- Use **“Non‑IID”** (capitalization and hyphen) consistently.
- Use **“DeiT‑Tiny”** (with hyphen) consistently.

