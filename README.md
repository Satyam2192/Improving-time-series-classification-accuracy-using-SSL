**Time Series Classification with Ensemble Model**
======================================================

**Table of Contents**
-----------------

1. [Overview](#overview)
2. [Dataset Details](#dataset-details)
3. [Model Architecture](#model-architecture)
4. [Training and Evaluation Results](#training-and-evaluation-results)
5. [Fine-Tuning on Gesture Dataset](#fine-tuning-on-Gesture-Dataset)
6. [Pre-Fine-Tuning vs. Fine-Tuning Comparison](#pre-fine-tuning-vs-fine-tuning-comparison)
7. [Usage](#usage)
8. [Dependencies](#dependencies)

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
| 1-5  | 1.0875 -> 0.2931 | 64.12% -> 90.65% | 0.6559 -> 0.1894 | 82.73% -> 93.27% |
|...  |... |... |... |... |
| 83   | 0.0780 | 96.31% | 0.0613 | 96.67% (**Early Stopping**) |

![image](https://github.com/user-attachments/assets/57fcc8b7-9d64-45cd-a4ff-7d38b25ee920)
![image](https://github.com/user-attachments/assets/02aac6a0-e9f4-4176-853f-425d7a44a93d)

**Fine-Tuning on Gesture Dataset (3 Runs)**
-------------------------------------------

#### **1st Fine-Tuning**

| Epochs | Train Loss | Train Accuracy | Validation Loss | Validation Accuracy |
| --- | --- | --- | --- | --- |
| 1-5  | 4.6224 -> 2.7823 | 12.81% -> 20.31% | 3.0883 -> 1.9086 | 20.00% -> 25.00% |
|...  |... |... |... |... |
| 144  | 1.0686 | 62.81% | 1.0311 | 66.67% (**Early Stopping**) |

* **Evaluation Results**:
    + HAR: Loss: 0.5284, Accuracy: 90.36%
    + Gesture: Loss: 1.0311, Accuracy: 66.67%
  
![image](https://github.com/user-attachments/assets/5d3524d6-0535-4861-aa6b-82612e5b4f78)

![image](https://github.com/user-attachments/assets/dce01cc8-96d9-479f-81cd-cf82a28bf4da)

#### **2nd Fine-Tuning**

| Epochs | Train Loss | Train Accuracy | Validation Loss | Validation Accuracy |
| --- | --- | --- | --- | --- |
| 1-5  | 4.2188 -> 2.6808 | 14.38% -> 19.38% | 2.9988 -> 1.8819 | 22.50% -> 31.67% |
|...  |... |... |... |... |
| 137  | 1.2449 | 61.25% | 1.2568 | 64.17% (**Early Stopping**) |

* **Evaluation Results**:
    + HAR: Loss: 0.5284, Accuracy: 90.36%
    + Gesture: Loss: 1.2568, Accuracy: 64.17%

![image](https://github.com/user-attachments/assets/e3c0445e-943e-459e-aa23-d6034e465456)

![image](https://github.com/user-attachments/assets/3f8e86d0-ac13-4af4-9b65-a2219de74675)

#### **3rd Fine-Tuning**

| Epochs | Train Loss | Train Accuracy | Validation Loss | Validation Accuracy |
| --- | --- | --- | --- | --- |
| 1-5  | 4.5211 -> 2.6780 | 12.81% -> 21.25% | 2.4928 -> 1.6959 | 13.33% -> 50.83% |
|...  |... |... |... |... |
| 148  | 1.0729 | 64.69% | 1.0981 | 60.00% (**Early Stopping**) |

* **Evaluation Results**:
    + HAR: Loss: 0.5284, Accuracy: 90.36%
    + Gesture: Loss: 1.0981, Accuracy: 60.00%
      
![image](https://github.com/user-attachments/assets/56824ac9-92b9-458f-acab-ffff13efd15d)

![image](https://github.com/user-attachments/assets/02aa5134-9f53-4300-a4f3-47f7909dbf29)

**Pre-Fine-Tuning vs. Fine-Tuning Comparison**
---------------------------------------------

| Dataset | Pre-Fine-Tune Loss | Pre-Fine-Tune Accuracy | Fine-Tune Loss (Best) | Fine-Tune Accuracy (Best) |
| --- | --- | --- | --- | --- |
| HAR   | 0.5284 | 90.36% | **N/A** | **N/A** |
| Gesture | 8.2883 | 15.83% | 1.0311 | 66.67% |

**Usage**
---------

1. **Navigate to the repository**: `cd time-series-ensemble`
2. **Activate your virtual environment**: `myenv\Scripts\activate` (Windows) or `source myenv/bin/activate` (macOS/Linux)
3. **Install Dependency**: `pip install -r requirements.txt`
4. **Pre-train on HAR dataset (if desired)**: `python train.py --dataset har --pretrain`
5. **Fine-tune on Gesture dataset**: `python train.py --dataset gesture --finetune`

**Dependencies**
----------------

* Listed in [requirements.txt](requirements.txt)
