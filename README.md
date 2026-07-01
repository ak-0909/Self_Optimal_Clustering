# Self-Optimal Clustering (SOC) Algorithm 

## Overview
Self-Optimal Clustering (SOC) is an advanced unsupervised learning algorithm that improves upon Improved Mountain Clustering (IMC) by replacing heuristic threshold selection with a mathematically grounded optimization procedure. By embedding an optimized threshold function driven by Lagrange interpolation and silhouette-based validation, SOC dynamically adapts the neighbourhood radius for potential estimation.

Developed as part of the EE656 course project, this repository contains the complete 15-step pipeline of the SOC algorithm implemented entirely from scratch.

## Key Features
* **Mathematical Optimization:** Replaces manual tuning with a 1000-point grid search and Lagrange interpolation over 10 iterations to find the optimal cluster threshold.
* **Robust Cluster Quality:** Evaluates partitions dynamically using the Global Silhouette Index (GSI), Partition Index (PI), Separation Index (SI), and Dunn Index (DI).
* **Comprehensive Benchmarking:** Includes automated comparisons against standard algorithms including K-Means, Fuzzy C-Means (FCM), Expectation-Maximization (EM), IMC-1, and IMC-2.

## Experimental Results
The algorithm was rigorously evaluated on RGB image segmentation tasks using 6 test images resized to 80x80 pixels (yielding a 6400x3 feature matrix per image). 

* **High Separation & Compactness:** Achieved GSI values ranging from 0.6614 to 0.9689 across the benchmark images.
* **Superior Performance:** Outperformed the EM algorithm (which failed heavily on complex images) and IMC-2 (which degraded due to heuristic misfiring). For example, on complex multimodal images, SOC attained an optimal PI of 0.0987 and SI of 0.1474.
* **Rapid Convergence:** Unlike theoretical oscillatory behaviour, this implementation demonstrated highly stable and rapid threshold convergence within just 1 to 3 iterations.

## Tech Stack
* **Language:** Python 
* **Libraries:** NumPy, Scikit-learn (silhouette scoring), scikit-fuzzy (FCM), OpenCV (image I/O), and Matplotlib.

## Repository Structure
```text
├── data/                   # Contains the 6 benchmark RGB images (2color, house, lenna, etc.)
├── notebooks/              # Google Colab notebook containing the full implementation
├── src/                    # (Optional) Extracted Python scripts for modular execution
│   ├── normalize.py        # Data normalization modules
│   ├── metrics.py          # Cluster quality indices computation
│   └── soc_pipeline.py     # Core 15-step SOC algorithm class
├── results/                # Generated segmentation masks and convergence plots
