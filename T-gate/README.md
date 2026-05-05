# TGATE Experiment

Folder containing the code and requirements to re-create the metrics for TGATE applied to Stable Diffusion (SD).

Achieves 1.40x speedup on SD1.5 and 1.42x on SD2.1 with minimal impact on CLIP score and slight FID degradation on SD2.1

Hardware: Tested on Google Colab L4 GPUs.

Dataset: COCO val2017 (1000 images) Metrics: FID, CLIP Score, mean inference time, speedup ratio Steps: 25 DDIM steps Batch size: 8


## Results

| Model | Speedup | ΔFID | ΔCLIP |
| ----- | ------- | ---- | ----- |
| SD1.5 | 1.40×   | -3.236 | 0.0018 |
| SD2.1 | 1.42×   | +4.576 | 0.0047 |

| Model Name, TGATE Setting | Total Time | Mean Time | STD Time | FID Score | CLIP Score | Throughput | Peak VRAM |
|---|---|---|---|---|---|---|---|
| SD1.5, TGATE=False | 0 hrs 42 mins 37 secs | 0.404 secs | 0.756 secs | 25.990 | 0.1415 | 2.46 img/s | 22.59 GB |
| SD1.5, TGATE=True  | 0 hrs 32 mins 58 secs | 0.288 secs | 0.561 secs | 22.753 | 0.1433 | 3.46 img/s | 21.46 GB |
| SD2.1, TGATE=False | 0 hrs 37 mins 55 secs | 0.342 secs | 0.692 secs | 29.495 | 0.1484 | 2.91 img/s | 22.96 GB |
| SD2.1, TGATE=True  | 0 hrs 29 mins 36 secs | 0.242 secs | 0.511 secs | 34.071 | 0.1531 | 4.12 img/s | 21.29 GB |

Reference: Liu, H., Zeng, W., Chen, R., & Hou, X. (2024). TGATE: Cross-Attention Makes Inference Caching Viable in Diffusion Transformers. arXiv:2404.02747.
