# Enhancing Multi-View Consistency in Real-Time 3D Style Transfer

**Zihan Wang** *Golisano College of Computing and Information Sciences, Rochester Institute of Technology*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Framework: PyTorch](https://img.shields.io/badge/Framework-PyTorch-orange.svg)](https://pytorch.org/)
[![Based on: 3DGS](https://img.shields.io/badge/Based%20on-3D%20Gaussian%20Splatting-blue)](https://github.com/graphdeco-inria/gaussian-splatting)

> **Abstract:** A real-time 3D style transfer pipeline based on 3D Gaussian Splatting (3DGS). This project addresses the "flickering" and "visual noise" artifacts common in existing methods (like StyleSplat) by introducing a hybrid loss function that combines **Perceptual Loss (LPIPS)** for structural coherence and **Reprojection Consistency Loss** for temporal stability.

---

## 🎨 Visual Results

### Qualitative Comparison
**1. Smooth Geometry (Hotdog Scene)** Our method eliminates high-frequency noise and creates coherent brushstrokes.

| <img src="assets/comparison_hotdog.png" width="1000" alt="GT Hotdog"> 


**2. Complex Geometry (Chair Scene)** Our method maintains style consistency even on thin structures and complex occlusions.

| <img src="assets/comparison_chair.png" width="1000" alt="Baseline Chair"> |

---

## 📊 Quantitative Evaluation

### Temporal Stability (Warping Error)
We achieve a **~4% reduction** in temporal warping error compared to the baseline, significantly reducing the "flickering" effect in videos.

| Scene | Baseline Error | **Ours (Phase 2) Error** | Improvement |
| :--- | :---: | :---: | :---: |
| **Ficus** | 0.0493 | **0.0436** | ✅ Significant |
| **Hotdog** | 0.1462 | **0.1300** | ✅ Significant |
| **Ship** | 0.0749 | **0.0735** | ✅ Stable |
| **Mic** | 0.0559 | **0.0556** | ✅ Stable |
| **Average**| **0.1011** | **0.0973** | **~3.8%** |

### Visual Quality (LPIPS)
We achieve an average LPIPS score of **0.72**, indicating robust perceptual similarity to the target style across diverse geometries.

---

## 🚀 Key Features
* **Hybrid Loss Function:** * $L_{total} = \lambda_{nnfm} L_{nnfm} + \lambda_{lpips} L_{lpips} + \lambda_{reproj} L_{reproj}$
* **Perceptual Loss:** Uses VGG-16 features to enforce global structure (removing splotchy artifacts).
* **Reprojection Consistency:** Uses depth-based warping to enforce temporal stability (removing flickering).
* **Robust Segmentation:** Integration with **DEVA** for precise temporal object masking.
* **Colab Optimization:** Custom patches for NumPy 1.x/2.x compatibility and CUDA compilation.

---

## 🛠️ Installation

This project relies on custom CUDA kernels. Please follow the installation steps strictly, especially regarding package versions.

**Prerequisites:**
* Linux (Ubuntu 20.04 recommended or Google Colab)
* NVIDIA GPU (Tesla T4, A100, etc.)
* CUDA Toolkit 11.3
* Python 3.10

### 1. Clone the Repository
```bash
git clone [https://github.com/YOUR_USERNAME/StyleSplat-Consistency.git](https://github.com/YOUR_USERNAME/StyleSplat-Consistency.git)
cd StyleSplat-Consistency
# Important: Clone submodules recursively
git submodule update --init --recursive
