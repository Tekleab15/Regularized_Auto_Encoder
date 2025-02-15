# RAE-Project
Implementation of a Regularized Autoencoder based on Backpropagation

## Project Description
This project implements a Regularized Autoencoder (RAE) using backpropagation, inspired by the methodologies described in "The Neural Coding Framework for Learning Generative Models".

# Regularized Autoencoder Implementation

## Overview
This repository contains the implementation of a Regularized Autoencoder (RAE) based on the methodology outlined in the research paper. The project includes training and evaluation of the RAE on multiple datasets, including MNIST, KMNIST, FMNIST, and CalTech101. The model's performance is evaluated using various metrics: Binary Cross-Entropy (BCE), Masked Mean Squared Error (M-MSE), log-likelihood, and classification error.

## Datasets
- **MNIST**: Handwritten digits.
- **KMNIST**: Japanese Kanji characters.
- **FMNIST**: Fashion items.
- **CalTech101**: 101 object categories plus background.

## Preprocessing
- **Normalization**: Pixel values are normalized to [0, 1].
- **Thresholding**: Images are converted to binary using a threshold of 0.5.
- **Resizing**: CalTech101 images are resized to 16x16 pixels.

## Model Architecture
The Regularized Autoencoder consists of an encoder and a decoder with the following structure:
- **Encoder**:
  - Flatten layer
  - Dense layer with 256 units, ReLU activation, L2 regularization
  - Dense layer with 128 units, ReLU activation, L2 regularization
  - Dense layer with 20 units (latent space), ReLU activation, L2 regularization
- **Decoder**:
  - Dense layer with 128 units, ReLU activation, L2 regularization
  - Dense layer with 256 units, ReLU activation, L2 regularization
  - Dense output layer, Sigmoid activation, L2 regularization, reshape to original dimensions

## Training
- **Optimizer**: Adam
- **Loss Function**: Binary Cross-Entropy
- **Epochs**: 50
- **Batch Size**: 200

## Results
### MNIST
- **Binary Cross-Entropy (BCE)**: 0.0659
- **Masked Mean Squared Error (M-MSE)**: 0.0093
- **Classification Error**: 0.0999
- **Log-Likelihood**: (To be calculated)

### KMNIST
- **Binary Cross-Entropy (BCE)**: (To be updated)
- **Masked Mean Squared Error (M-MSE)**: (To be updated)
- **Classification Error**: (To be updated)
- **Log-Likelihood**: (To be calculated)

### FMNIST
- **Binary Cross-Entropy (BCE)**: (To be updated)
- **Masked Mean Squared Error (M-MSE)**: (To be updated)
- **Classification Error**: (To be updated)
- **Log-Likelihood**: (To be calculated)

### CalTech101
- **Binary Cross-Entropy (BCE)**: 0.366
- **Masked Mean Squared Error (M-MSE)**: 0.057
- **Classification Error**: 76.00%
- **Log-Likelihood**: (To be calculated)

## How to Use
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Tekleab15/Regularized_Auto_Encoder.git
   cd Regularized_Auto_Encoder

