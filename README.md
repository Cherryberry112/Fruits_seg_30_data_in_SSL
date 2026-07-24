# FruitSeg30 Semantic Segmentation Benchmark 

A comprehensive benchmark of three state-of-the-art semantic segmentation architectures on the **FruitSeg30** dataset. This project covers the complete pipeline—from dataset preprocessing and color remapping to model training, evaluation, and comparative analysis.

---

## Overview

The original FruitSeg30 dataset provides segmentation masks where each fruit class is stored as a grayscale label. To make the dataset easier to visualize, debug, and use across multiple segmentation frameworks, the dataset was reprocessed by:

- Assigning every class a unique RGB color palette
- Standardizing mask formats
- Reorganizing the directory structure
- Creating train/validation/test splits
- Training and evaluating multiple segmentation architectures under identical experimental settings

The final repository serves as a reproducible benchmark for semantic segmentation on FruitSeg30.

---

# Datasets

## Original Dataset

**FruitSeg30 – Segmentation Dataset & Mask Annotations**

https://data.mendeley.com/datasets/vkht8pfsp3/3

- 30 fruit classes
- 1,969 RGB images
- Resolution: 512×512
- Original masks provided as grayscale label images

The original dataset is described in the accompanying Data in Brief publication. :contentReference[oaicite:0]{index=0}

---

## Processed RGB Dataset

After preprocessing, every semantic class was assigned a unique RGB color to improve visualization and compatibility across segmentation frameworks.

**Kaggle Dataset**

https://www.kaggle.com/datasets/mohuaakter/fruitseg30-dataset

Changes include:

- RGB color-coded segmentation masks
- Standardized directory structure
- Consistent image/mask naming
- Model-ready dataset organization

---

## Train / Validation / Test Split

The processed dataset was further split into fixed subsets used by all experiments.

**Kaggle Dataset**

https://www.kaggle.com/datasets/mohuaakter/fruitseg30-splitted-data

Dataset distribution:

| Split | Images |
|-------:|-------:|
| Train | 1369 |
| Validation | 291 |
| Test | 309 |
| **Total** | **1969** |

---

# Models Evaluated

| Model | Backbone | Framework |
|--------|----------|-----------|
| DeepLabV3 | ResNet-101 | PyTorch |
| SegFormer | MiT-B0 | Hugging Face Transformers |
| YOLOv26 Semantic Segmentation | YOLOv26 | Ultralytics |

---

# Training Environment

All experiments were conducted on Kaggle using an NVIDIA Tesla T4 GPU.

| Component | Specification |
|-----------|---------------|
| Platform | Kaggle Notebooks |
| GPU | NVIDIA Tesla T4 (≈16 GB VRAM) |
| Python | 3.12 |
| CUDA | 12.1 |
| PyTorch | 2.3.1 |

---

# Experimental Results

| Model | Backbone | Epochs | Training Time (min) | mIoU ↑ | Mean Dice ↑ | Pixel Accuracy ↑ | Mean Pixel Accuracy ↑ |
|------|-----------|-------:|--------------------:|--------:|------------:|-----------------:|----------------------:|
| **YOLOv26 Semantic** | YOLOv26 | 80 | **274.3** | **0.9442** | **0.9690** | 0.8585 | 0.9676 |
| **SegFormer** | MiT-B0 | 65 | 586.4 | 0.9189 | 0.9553 | **0.9626** | **0.9872** |
| **DeepLabV3** | ResNet-101 | 50 | 497.6 | 0.6081 | 0.7123 | 0.8719 | 0.7704 |

---

# Model Comparison

| Metric | Winner |
|---------|--------|
| Mean IoU | 🥇 YOLOv26 Semantic |
| Mean Dice | 🥇 YOLOv26 Semantic |
| Pixel Accuracy | 🥇 SegFormer |
| Mean Pixel Accuracy | 🥇 SegFormer |
| Fastest Training | 🥇 YOLOv26 Semantic |

---

# Best Overall Model

## 🏆 YOLOv26 Semantic Segmentation

YOLOv26 Semantic Segmentation achieved the strongest overall performance in this benchmark.

### Performance

- **Highest Mean IoU:** 0.9442
- **Highest Dice Score:** 0.9690
- **Fastest training time**
- Excellent qualitative segmentation across fruit classes

Although SegFormer achieved the highest Pixel Accuracy and Mean Pixel Accuracy, YOLOv26 delivered substantially better region overlap metrics (mIoU and Dice), which are generally more representative of semantic segmentation quality. Combined with the shortest training time, YOLOv26 was selected as the best overall model.

---

# Repository Structure

```
.
├── fruitseg30-preprocess.ipynb
├── eda-and-data-prep.ipynb
├── seg-deeplabv3.ipynb
├── seg-segformer-b0.ipynb
├── seg-yolov26-semantic.ipynb
├── seg-nb4-comparison.ipynb
└── README.md
```

---

# Acknowledgements

- FruitSeg30 Dataset Authors
- Mendeley Data
- Kaggle
- PyTorch
- Hugging Face Transformers
- Ultralytics YOLO
