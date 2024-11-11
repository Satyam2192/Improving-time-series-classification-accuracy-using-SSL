**Time Series Classification with Ensemble Model**
======================================================

**Table of Contents**
-----------------

1. [Overview](#overview)
2. [Dataset Details](#dataset-details)
3. [Model Architecture](#model-architecture)
4. [Training and Evaluation Results](#training-and-evaluation-results)
5. [Pre-Fine-Tuning vs. Fine-Tuning Comparison](#pre-fine-tuning-vs-fine-tuning-comparison)
6. [Usage](#usage)
7. [Dependencies](#dependencies)

**Overview**
------------

This repository presents a deep learning approach for time series classification using an ensemble model, combining the strengths of CNN, LSTM, Residual, and Transformer blocks. The model is pre-trained on the Human Activity Recognition (HAR) dataset and fine-tuned on the Gesture dataset, demonstrating its adaptability and effectiveness.

**Dataset Details**
-------------------

* **Human Activity Recognition (HAR) Dataset**:
    + Classes: 6
    + Pre-training results: [View](#training-and-evaluation-results)
* **Gesture Dataset**:
    + Classes: 8
    + Fine-tuning results: [View](#training-and-evaluation-results)

**Model Architecture**
----------------------

* **Ensemble Model**:
    + CNN Block (x2) + Residual Block + LSTM Block + Transformer Block
    + Fusion layer with dropout for classification

**Training and Evaluation Results**
-----------------------------------

### Pre-Training on HAR Dataset

| Epochs | Train Loss | Train Accuracy | Validation Loss | Validation Accuracy |
| --- | --- | --- | --- | --- |
| 1-5  | 1.1048 -> 0.2594 | 62.73% -> 91.50% | 0.6754 -> 0.1696 | 82.60% -> 94.90% |
|...  |... |... |... |... |
| 91   | 0.0799 | 96.29% | 0.0639 | 96.40% (**Early Stopping**) |

### Fine-Tuning on Gesture Dataset

| Epochs | Train Loss | Train Accuracy | Validation Loss | Validation Accuracy |
| --- | --- | --- | --- | --- |
| 1-5  | 4.7589 -> 2.6436 | 10.94% -> 21.25% | 2.8836 -> 1.8742 | 15.00% -> 29.17% |
|...  |... |... |... |... |
| 150  | 1.2392 | 61.88% | 1.1296 | 65.00% |

### Evaluation on Test Sets

| Dataset | Loss | Accuracy |
| --- | --- | --- |
| **HAR (Pre-Fine-Tune)** | 0.5394 | 89.96% |
| **HAR (Final)** | 0.5394 | 89.96% |
| **Gesture (Pre-Fine-Tune)** | 11.7970 | 12.50% |
| **Gesture (Final)** | 1.1296 | 65.00% |

**Pre-Fine-Tuning vs. Fine-Tuning Comparison**
---------------------------------------------

| Dataset | Pre-Fine-Tune Loss | Pre-Fine-Tune Accuracy | Fine-Tune Loss | Fine-Tune Accuracy |
| --- | --- | --- | --- | --- |
| HAR   | 0.5394 | 89.96% | **N/A** | **N/A** |
| Gesture | 11.7970 | 12.50% | 1.1296 | 65.00% |

**Usage**
---------

1. **Activate your virtual environment**: `myenv\Scripts\activate` (Windows) or `source myenv/bin/activate` (macOS/Linux)
2. **Navigate to the repository**: `cd time-series-ensemble`
3. **Prepare your dataset** (HAR and/or Gesture)
4. **Pre-train on HAR dataset (if desired)**: `python train.py --dataset har --pretrain`
5. **Fine-tune on Gesture dataset**: `python train.py --dataset gesture --finetune`

**Dependencies**
----------------

* Listed in [requirements.txt](requirements.txt) (installed via `pip install -r requirements.txt`)