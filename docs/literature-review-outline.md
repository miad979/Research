# Literature Review Outline (Chapter 2)

## 2.1 Medical imaging motivation + data silos
- Why medical data is siloed; practical barriers to centralization
- Why CXR classification is clinically important; pleural effusion relevance

## 2.2 Federated learning fundamentals
- FL setup: server + clients, rounds, communication
- FedAvg: core baseline
- Objective function and evaluation conventions

## 2.3 Non-IID data in FL (core)
- Definitions: label skew, quantity skew, feature/domain skew
- Why hospital data is Non-IID
- Methods:
  - FedProx (baseline for heterogeneity)
  - SCAFFOLD / FedNova (mention even if not implemented)
  - Personalization: local fine-tuning, FedBN, pFedMe, etc.

## 2.4 Robust FL beyond Non-IID
- Noisy labels in FL
- Byzantine/adversarial clients (overview)
- Robust aggregation (median/trimmed mean/Krum—overview)

## 2.5 Privacy in FL (clarify claims)
- FL reduces data centralization but does not guarantee privacy
- Leakage threats: gradient/model inversion, membership inference
- Defenses: secure aggregation, DP-FL (brief)
- Thesis scope statement: focus on decentralization + robustness under Non-IID

## 2.6 Centralized deep learning for chest X-ray classification
- Common CNN baselines and evaluation (AUC, sensitivity/specificity)
- NIH ChestX-ray14 dataset characteristics
- Class imbalance and label noise

## 2.7 Vision Transformers for medical imaging
- Why transformers
- ViT/DeiT/Swin summary
- Transformers for radiology imaging

## 2.8 Lightweight models + efficient FL
- Why lightweight (compute + communication cost)
- Efficient ViTs (DeiT-Tiny / TinyViT / MobileViT—positioning)
- FL efficiency methods (compression, distillation, adapters) — at least mention

## 2.9 Explainable AI for CXR + transformer interpretability
- Grad-CAM family (CNN explainability)
- ViT explanation (attention rollout / attribution)
- XAI in federated settings: stability, fairness, client-wise consistency

## 2.10 Closest related work
- FL + XAI in medical diagnosis
- FL + Transformers (if available)
- Summarize limitations in prior work

## 2.11 Gap + contributions
- Systematic Non-IID severity study + robust baselines + lightweight ViT + XAI stability

