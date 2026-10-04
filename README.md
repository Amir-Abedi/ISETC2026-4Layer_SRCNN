# 4-Layer SRCNN

Code for the paper **"Adaptive Image Restoration via Enhanced Multi-Layer SRCNN Architectures"** (ISETC 2026).

This repository studies the effect of adding one convolutional layer to the baseline SRCNN and of reducing the number of filters to lower the parameter count and FLOPs. The goal is not to propose the best-performing architecture, but to quantify the trade-off between reconstruction quality and computational cost.

## Models

All models work on the Y channel of a bicubic-upscaled image (x3).

| Model | Kernels | Parameters | FLOPs* |
|---|---|---|---|
| Baseline | 9-1-5 | 8,129 | 157.4 M |
| Smooth | 11-1-7 | 11,457 | 222.7 M |
| Sharp | 7-3-3 | 21,953 | 428.4 M |
| **Four-layer** | **9-3-1-5** | **7,921** | **154.0 M** |

\*FLOPs = 2 x MACs, for a 33x33 LR patch (a 99x99 input after bicubic upscaling).

## Repository structure

```text
.
├── srcnn-additional-layer.ipynb
├── classical-interpolation.ipynb
├── weights/
└── README.md
```

## Notebooks

| Notebook | Description | Run on Kaggle |
|---|---|---|
| `srcnn-additional-layer.ipynb` | Baseline, smooth, sharp and four-layer SRCNN: PSNR/SSIM benchmark on Set14 and zoomed patch comparison | [![Open in Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://www.kaggle.com/code/amiraliabedi97/srcnn-additional-layer) |
| `classical-interpolation.ipynb` | Nearest, bilinear, bicubic, Hamming, Lanczos and Mitchell-Netravali interpolation, evaluated with the same protocol | [![Open in Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://www.kaggle.com/code/amiraliabedi97/classical-interpolation) |

## Evaluation protocol

- Scale factor: x3
- Test set: Set14
- Metrics: PSNR and SSIM on the Y channel, with a 3-pixel border shaved
- Training sets of the provided weights: T91, Urban100, Manga109, BSDS500, General100

## How to run

The notebooks are written for Kaggle: the datasets and model checkpoints are loaded from Kaggle paths (`/kaggle/input/...`). The easiest way to reproduce the results is to open the notebooks through the Kaggle links above and click **Run All**.

The trained weights are also provided in the `weights/` folder of this repository.

## Citation

If you use this code, please cite:

```bibtex
@inproceedings{
  title     = {Adaptive Image Restoration via Enhanced Multi-Layer SRCNN Architectures},
  author    = {Amirali ABEDI, Mugura{\c{s}} MOCOFAN,
  booktitle = {ISETC 2026},
  year      = {2026}
}
```
