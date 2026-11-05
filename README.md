# 4-Layer SRCNN

Code for the paper **"Adaptive Image Restoration via Enhanced Multi-Layer SRCNN Architectures"** (ISETC 2026).

This repository studies the effect of adding one convolutional layer to the baseline SRCNN and of reducing the number of filters to lower the parameter count and FLOPs. The goal is not to propose the best-performing architecture, but to show the impact of adding one layer to non-linear mapping layer so the impact in visuality could be significant for some images since RF is 15 in this variant instead of the others which has 13.

## Models

All models work on the Y channel of a bicubic-upscaled image (x3).

| Model | Kernels | Filters | Parameters | FLOPs* |
|---|---|---|---|---|
| Baseline | 9-1-5 | 64-32 | 8,129 | 14.80 G |
| Smooth | 7-1-7 | 64-48 | 8,673 | 15.78 G |
| Sharp | 9-3-3 | 32-20 | 8,585 | 15.73 G |
| **Four-layer** | **9-3-1-5** | **32-16-16** | **7,921** | **14.48 G** |

\*FLOPs = 2 × MACs, for a 1280×720 single-channel (Y) input with same padding; biases and ReLU not counted.


## Repository structure

```text
.
├── srcnn-additional-layer.ipynb
├── classical-interpolation.ipynb
└── 4layer-vs-3layer-proof.ipynb
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
@inproceedings{abedi2026adaptive,
  title     = {Adaptive Image Restoration via Enhanced Multi-Layer SRCNN Architectures},
  author    = {Abedi, Amirali and Mocofan, Muguraş},
  booktitle = {ISETC 2026},
  year      = {2026}
}
```
