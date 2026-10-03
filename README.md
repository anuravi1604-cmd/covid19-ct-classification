# COVID-19 CT Scan Classification Using EfficientNet-B3

## Overview

This project uses a pretrained EfficientNet-B3 deep learning model to classify CT scan images into COVID and non-COVID categories.

The project covers the workflow from dataset preparation and image preprocessing to model training, validation, model saving, and image-level inference.

## Dataset

The project uses the SARS-CoV-2 CT Scan Dataset downloaded through KaggleHub.

The dataset contains:

- 1,252 COVID images
- 1,229 non-COVID images
- 2,481 images in total

The dataset was divided into training and validation sets using an 80/20 stratified split.

## Preprocessing

Training images were processed using:

- Random resized cropping to 224 × 224
- Random horizontal flipping
- Random rotation
- Tensor conversion
- ImageNet normalization

Validation images were:

- Resized to 224 × 224
- Converted to tensors
- Normalized using ImageNet mean and standard deviation

## Model

The project uses a pretrained EfficientNet-B3 model from the `timm` library.

The final classification layer was configured for two classes:

- non-COVID
- COVID

Training was performed using:

- Loss function: CrossEntropyLoss
- Optimizer: AdamW
- Learning rate: 0.001
- Epochs: 50

## Validation Results

The model was evaluated on the held-out validation split.

| Metric | Result |
|---|---:|
| Accuracy | 97.18% |
| Precision | 96.11% |
| Recall | 98.41% |
| F1-score | 97.24% |
| ROC-AUC | 99.67% |

### Confusion Matrix

| | Predicted non-COVID | Predicted COVID |
|---|---:|---:|
| Actual non-COVID | 236 | 10 |
| Actual COVID | 4 | 247 |

## Model

The trained EfficientNet-B3 weights are saved locally at:

`models/efficientnet_b3_sarscov2_model.pth`

The notebook also demonstrates loading the saved weights and performing image-level inference on validation images.

## Project Structure

```text
covid19-ct-classification/
├── models/
│   └── efficientnet_b3_sarscov2_model.pth
├── dl_proj.ipynb
├── README.md
├── requirements.txt
└── .gitignore