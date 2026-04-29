# Food Image Segmentation — FoodSeg103

Semantic segmentation of food images on the FoodSeg103 dataset, comparing U-Net, DeepLabV3+, and SegFormer-B3. Best result: **33.57% mIoU** with SegFormer-B3 and multi-scale inference.

## Overview

FoodSeg103 is a challenging benchmark containing 7,118 food images annotated with 103 fine-grained ingredient categories (e.g. rice, tomato, egg). This project benchmarks three segmentation architectures and applies inference-time techniques to maximise mIoU.

## Models Compared

| Model | Backbone | Approach | mIoU |
|-------|----------|----------|------|
| U-Net | ResNet-50 | Encoder-decoder with skip connections | ~25% |
| DeepLabV3+ | ResNet-101 | Atrous convolutions + ASPP | ~29% |
| **SegFormer-B3** | Mix Transformer (MiT-B3) | Hierarchical transformer encoder | **33.57%** |

## Key Techniques

- **Transfer learning** from ImageNet pre-trained backbones
- **Data augmentation:** random crop, horizontal flip, colour jitter
- **Multi-scale inference** — averaging predictions across multiple input resolutions to improve boundary detection
- **Class-weighted cross-entropy loss** to address severe label imbalance across 103 categories

## Results

SegFormer-B3 with multi-scale inference achieves the best performance at **33.57% mIoU**, outperforming both convolutional baselines. The transformer's global attention mechanism better captures long-range dependencies between food regions.

## Files

| File | Description |
|------|-------------|
| `food_image_segmentation.ipynb` | Full training, evaluation, and inference pipeline |

## Tech Stack

- Python 3
- PyTorch
- HuggingFace Transformers (SegFormer)
- MMSegmentation (DeepLabV3+, U-Net)
- Google Colab (GPU)
- FoodSeg103 dataset
