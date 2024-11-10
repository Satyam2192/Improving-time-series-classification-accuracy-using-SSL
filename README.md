## Improving time series classification accuracy using self-supervised learning

Improving time series classification accuracy using self-supervised learning, An unsupervised autoencoder model for gesture recognition using PyTorch. This project builds an autoencoder to learn representations of different gestures and evaluates model performance with various visualization and reconstruction error analyses.

### Project Overview

The purpose of this project is to develop and evaluate an autoencoder model to identify unique features of gesture patterns. We use techniques like latent space visualization and reconstruction error analysis to gain insight into how well the model can distinguish between different gestures.

#### Key Features

- Unsupervised representation learning with an autoencoder
- Visualization of latent space to analyze clustering of gestures
- Reconstruction error analysis to identify challenging patterns
- Gesture-wise performance evaluation (if labels are available)

### Model Architecture

The autoencoder consists of two parts:
1. **Encoder**: Encodes input data into a compressed latent representation.
2. **Decoder**: Reconstructs the input data from the latent representation.

The model is built using fully connected layers with ReLU activation functions and Mean Squared Error (MSE) as the reconstruction loss.

### Getting Started

#### Prerequisites

- Python 3.x
- PyTorch
- Matplotlib
- Scikit-learn (for PCA and t-SNE)

Install the required packages:
```bash
python3 -m venv .env
```

Activate the Virtual Environment

- On Windows:
```bash
.\.env\Scripts\activate
```
- On macOS/Linux:
```bash
source .env/bin/activate
```
- Install The Packages
```bash
pip install -r requirements.txt
```

### Evaluation and Results:
Test Loss: 0.7409
Mean Absolute Error (MAE): 0.6684
Mean Squared Error (MSE): 0.7409

