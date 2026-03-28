# Skin Cancer Classification - HAM10000

Multi-class skin lesion classifier trained on the HAM10000 dataset. Over 10,000 dermoscopic images across 7 diagnostic categories, with a focus on reducing life-critical False Negatives in melanoma detection.

## Results

| Metric | Value |
|---|---|
| Test Accuracy | 71% |
| Macro AUC-ROC | 0.929 |
| Melanoma Recall | 0.64 |
| BCC Recall | 0.75 |

## Methodology

Three-phase progressive training pipeline:

1. **Custom CNN Baseline** - 3-layer CNN trained from scratch at 128x128. Established ~54% accuracy and validated class weighting strategy for handling severe dataset imbalance.
2. **Transfer Learning** - MobileNetV2 with frozen ImageNet weights and trainable classification head. Introduced pre-trained feature extraction for dermoscopic patterns.
3. **Resolution Upgrade & Fine-Tuning** - Upgraded to native 224x224 inputs, selectively unfroze top 50 MobileNetV2 layers, and applied conservative learning rate (1e-5) to specialize for pathological features without catastrophic forgetting.

## Dataset

[HAM10000](https://www.kaggle.com/datasets/kmader/skin-lesion-analysis-toward-melanoma-detection) - Human Against Machine with 10,000 training images.

| Class | Description |
|---|---|
| akiec | Actinic Keratoses & Intraepithelial Carcinoma |
| bcc | Basal Cell Carcinoma |
| bkl | Benign Keratosis-like Lesions |
| df | Dermatofibroma |
| mel | Melanoma |
| nv | Melanocytic Nevi |
| vasc | Vascular Lesions |

## Stack

- Python 3.12
- TensorFlow / Keras
- MobileNetV2 (ImageNet pretrained)
- scikit-learn
- pandas, numpy, matplotlib, seaborn

## Disclaimer

This project is developed for educational purposes only and is not intended for clinical use or medical diagnosis.
