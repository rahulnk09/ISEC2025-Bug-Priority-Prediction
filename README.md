# ISEC2025-Bug-Priority-Prediction
A repository containing the code and documentation for predicting bug priority levels (0–4) in the ISEC2025 challenge. The project explores two main strategies: an all-in-text BERT model and a two-stage multi-modal RoBERTa approach integrating textual, categorical, and numerical features.

## Overview

In this project, we explore two main strategies for bug priority prediction:
- **Strategy A: All-in-Text BERT**  
  All features (textual, categorical, and numerical) are concatenated into a single text sequence and fine-tuned using a BERT-base model.
- **Strategy B: Two-Stage Multi-Modal RoBERTa**  
  This approach uses a multi-modal architecture where:
  - Textual features (bug title and description) are processed via a pre-trained RoBERTa-large model.
  - Categorical features are passed through dedicated embedding layers.
  - Numerical features are processed through a small MLP.
  
  A two-stage training process is employed:
  1. **Stage 1:** Fine-tune RoBERTa while freezing categorical and numerical modules.
  2. **Stage 2:** Freeze RoBERTa and unfreeze categorical and numerical modules to refine their representations.
  
  Additionally, we use Focal Loss to mitigate the impact of class imbalance.

  
