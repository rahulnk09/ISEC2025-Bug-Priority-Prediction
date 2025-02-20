# ISEC2025-Bug-Priority-Prediction
A repository containing the code and documentation for predicting bug priority levels (0–4) in the ISEC2025 challenge- [link](https://www.kaggle.com/competitions/isec-sdc-2025/leaderboard). The project explores two main strategies: an all-in-text BERT model and a two-stage multi-modal RoBERTa approach integrating textual, categorical, and numerical features.

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

 ## Visualizations

This section contains key visualizations that provide insights into the dataset and model architecture.

### 1️⃣ Class Distribution of Bug Priorities
The dataset exhibits a strong class imbalance, with Priority 2 being the most frequent. The following plot visualizes the distribution of bug priority levels in the training dataset.

![Class Distribution](Screenshot%202025-02-19%20235524.png)

### 2️⃣ Word Cloud for Bug Titles
The word cloud highlights the most frequently occurring words in bug titles. Common words such as *"error"*, *"crash"*, *"fail"*, and *"load"* indicate the prevalent types of issues reported.

![Word Cloud](Screenshot%202025-02-20%20012940.png)

### 3️⃣ Normalized Priority Distribution Across Top 34 Components
The heatmap below illustrates how different software components are associated with bug priority levels. Some components exhibit a higher concentration of urgent (Priority 0) or low-priority (Priority 4) bugs.

![Normalized Priority Distribution](Screenshot%202025-02-19%20235813.png)

### 4️⃣ High-Level Multi-Modal RoBERTa Architecture
The following diagram illustrates our **two-stage multi-modal RoBERTa** approach. The model integrates:
- **RoBERTa** for textual feature extraction.
- **Learnable embeddings** for categorical variables.
- **A lightweight MLP** for numeric features.
- A **final classification layer** that predicts the bug priority level.

![Multi-Modal RoBERTa Architecture](_-%20visual%20selection.png)
