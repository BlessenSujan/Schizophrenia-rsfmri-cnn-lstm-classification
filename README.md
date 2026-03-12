# Deep Learning Framework for Schizophrenia Classification Using rs-fMRI Functional Connectivity

## Overview
This project presents a deep learning framework for classifying schizophrenia using resting-state functional MRI (rs-fMRI) data. Functional connectivity matrices were generated from brain-region time series using Pearson correlation and used as input to a hybrid CNN-LSTM model.

The project aims to distinguish schizophrenia patients from healthy controls by learning subtle disruptions in functional brain connectivity. In addition to classification, the project also incorporates saliency-map-based interpretability to identify the brain regions that contribute most strongly to the model’s predictions.

## Motivation
Schizophrenia diagnosis often relies heavily on behavioural assessment and clinical judgement, which can be subjective. Neuroimaging-based biomarkers offer the possibility of more objective support for diagnosis, but fMRI data is highly complex and high-dimensional.

This project addresses that challenge by combining:
- **CNNs** for spatial feature extraction from connectivity matrices
- **LSTMs** for capturing long-range dependencies across brain connectivity patterns
- **Saliency maps** for model interpretability

## Objectives
- Develop a CNN-LSTM architecture for schizophrenia classification using functional connectivity matrices derived from rs-fMRI
- Classify schizophrenia patients and healthy controls based on connectivity differences
- Evaluate performance using standard classification metrics
- Improve interpretability through saliency map analysis

## Dataset and Input Representation
- Resting-state fMRI data was used to derive functional connectivity information
- Pearson correlation was applied to ROI time series to compute connectivity matrices
- Each subject was represented by a **116 × 116** symmetric connectivity matrix
- The matrices were reshaped to **(116, 116, 1)** for CNN input

## Methodology

### 1. Functional Connectivity Extraction
Functional connectivity matrices were computed using **Pearson correlation** between ROI time series. These matrices capture the strength of relationships between brain regions and serve as the primary feature representation.

### 2. CNN-LSTM Architecture
The classification model combines convolutional and recurrent layers:

- **CNN layers** to extract spatial patterns from connectivity matrices
- **MaxPooling** and **BatchNormalization** to stabilise and optimise learning
- **Dropout** layers to reduce overfitting
- **LSTM layer** to capture long-range dependencies across extracted features
- **Fully connected layers** for binary classification
- **Sigmoid output layer** for schizophrenia vs healthy control prediction

### 3. Training Strategy
The model was trained using:
- **Adam optimizer**
- **Binary cross-entropy loss**
- **Early stopping**
- **ReduceLROnPlateau**

These strategies were used to improve convergence and reduce overfitting.

### 4. Interpretability
Saliency maps were used to highlight the brain regions and connectivity patterns that contributed most strongly to classification decisions, improving the interpretability of the model.

## Results
- Achieved a classification accuracy of **87.5%**
- Demonstrated that rs-fMRI-derived functional connectivity matrices can effectively support schizophrenia classification
- Showed the value of combining deep learning performance with interpretability

## Tools and Libraries
- Python
- TensorFlow / Keras
- NumPy
- SciPy
- Nilearn
- Matplotlib
- Jupyter Notebook

## Repository Structure
```text
README.md
schizophrenia_classification_cnn_lstm.ipynb
requirements.txt
figures/
results/
docs/
