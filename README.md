# Enhancing Multi-View Consistency in Real-Time 3D Style Transfer

**Zihan Wang** *Golisano College of Computing and Information Sciences, RIT*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Framework: PyTorch](https://img.shields.io/badge/Framework-PyTorch-orange.svg)](https://pytorch.org/)
[![Based on: StyleSplat](https://img.shields.io/badge/Based%20on-StyleSplat-blue)](https://github.com/StyleSplat/StyleSplat)

> **Abstract:** A real-time 3D style transfer pipeline based on 3D Gaussian Splatting (3DGS). This project addresses the "flickering" and "visual noise" artifacts common in existing methods by introducing a hybrid loss function that combines **Perceptual Loss (LPIPS)** for structural coherence and **Reprojection Consistency Loss** for temporal stability.

---

## 🎨 Visual Results

### Qualitative Comparison (Hotdog Scene)
| Ground Truth | Baseline (StyleSplat) | **Ours (Phase 2)** |
|:---:|:---:|:---:|
| <img src="assets/gt_hotdog.jpg" width="200"> | <img src="assets/baseline_hotdog.jpg" width="200"> | <img src="assets/ours_hotdog.jpg" width="200"> |
| *Original Geometry* | *High-frequency noise & artifacts* | *Smooth, coherent brushstrokes* |

### Temporal Stability
Our method reduces temporal warping error (flickering) by approximately **4%** compared to the baseline.

| Scene | Baseline Error | **Ours (Phase 2) Error** | Improvement |
| :--- | :---: | :---: | :---: |
| **Ficus** | 0.0493 | **0.0436** | ✅ Significant |
| **Hotdog** | 0.1462 | **0.1300** | ✅ Significant |
| **Ship** | 0.0749 | **0.0735** | ✅ Stable |

---

## 🚀 Features
* **Hybrid Loss Function:** Combines NNFM (Texture), LPIPS (Structure), and Reprojection (Stability).
* **Real-Time Rendering:** Maintains the >30 FPS performance of 3D Gaussian Splatting.
* **Robust Segmentation:** Integrated **DEVA** (Tracking Anything) for precise temporal object masking.
* **Colab Compatible:** Includes custom patches for NumPy 1.x/2.x compatibility and CUDA compilation on Google Colab.

---

## 🛠️ Installation

This project requires a specific environment due to custom CUDA rasterization kernels.

**Prerequisites:**
* Linux (Tested on Ubuntu 20.04 / Google Colab)
* NVIDIA GPU (Tesla T4 or better recommended)
* CUDA Toolkit 11.3
* Python 3.10

### 1. Clone the Repository
```bash
git clone [https://github.com/YOUR_USERNAME/StyleSplat-Consistency.git](https://github.com/YOUR_USERNAME/StyleSplat-Consistency.git)
cd StyleSplat-Consistency
# Clone submodules (Rasterizer & KNN)
git submodule update --init --recursive
