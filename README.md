# Regularized Autoencoder (RAE) Using MNIST

This repository provides an implementation of a Regularized Autoencoder (RAE) based on the methodology described in the paper:

**"THE NEURAL CODING FRAMEWORK FOR LEARNING GENERATIVE MODELS"**  
*(Alexander Ororbia, Daniel Kifer)*

The RAE is trained on the MNIST dataset and evaluated using several metrics including:
- Binary Cross-Entropy (BCE) per sample
- Masked Mean Squared Error (M-MSE) for pattern completion
- Log-Likelihood (using a Gaussian Mixture Model in the latent space)
- Classification Error (via a simple Logistic Regression on the latent representations)

---

## Table of Contents

- [Project Overview](#project-overview)
- [Model Architecture](#model-architecture)
  - [Encoder](#encoder)
  - [Decoder](#decoder)
- [Installation and Requirements](#installation-and-requirements)
- [Usage](#usage)
  - [Training the RAE](#training-the-rae)
  - [Evaluating the Model](#evaluating-the-model)
- [Project Structure](#project-structure)
- [Future Work](#future-work)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## Project Overview

This project implements a Regularized Autoencoder (RAE) that follows the specifications from the paper _"THE NEURAL CODING FRAMEWORK FOR LEARNING GENERATIVE MODELS"_. The autoencoder is designed as follows:

- **Dataset:** MNIST, with images preprocessed to be binary ([0, 1]) and flattened to 784-dimensional vectors.
- **Architecture:**
  - **Encoder:** Two hidden layers with 360 neurons each using ReLU activations, Batch Normalization, and Dropout (0.2). The latent space is 20-dimensional with a sigmoid activation on the final layer.
  - **Decoder:** A symmetric network to the encoder that reconstructs the input from the 20-dimensional latent code. The final layer uses a sigmoid activation to produce outputs in the [0,1] range, and an L2 regularization is applied.
- **Optimizer:** Stochastic Gradient Descent (SGD) with momentum, using an exponentially decaying learning rate and gradient clipping.
- **Evaluation:** In addition to reconstruction loss (BCE), the latent representations are used to:
  - Fit a Gaussian Mixture Model (GMM) for estimating log-likelihood.
  - Train a Logistic Regression classifier to calculate the classification error.
  - Compute a (planned) masked MSE metric for pattern completion tasks.

---

## Model Architecture

### Encoder

- **Input:** 784-dimensional vector (flattened MNIST image)
- **Hidden Layers:** Two Dense layers with 360 neurons each:
  - Activation: ReLU
  - Additional Processing: Batch Normalization and Dropout (0.2)
- **Latent Layer:** Dense layer with 20 neurons and sigmoid activation

### Decoder

- **Input:** 20-dimensional latent vector
- **Hidden Layers:** Two Dense layers with 360 neurons each (mirroring the encoder):
  - Activation: ReLU
  - Regularization: L2 regularization (applied on at least one layer)
  - Additional Processing: Batch Normalization and Dropout (0.2)
- **Output Layer:** Dense layer with 784 neurons, sigmoid activation, then reshaped to (784,)

---

## Installation and Requirements

**Requirements:**

- Python 3.x
- TensorFlow 2.x
- NumPy
- scikit-learn
- Matplotlib
- (Optional) `tensorflow_datasets`

Install dependencies using pip:

```bash
pip install tensorflow numpy scikit-learn matplotlib tensorflow-datasets
