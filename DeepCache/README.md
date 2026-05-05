Folder containing the code and requirements to re-create the metrics in the DeepCache Paper

Achieves 2.3x speedup on Stable
Diffusion v1.5 with only 0.05 CLIP Score decrease, and 4.1x speedup on LDM-4 (ImageNet) with 0.22
FID increase -- all without any training or fine-tuning.

Hardware: Tested on Google Colab A100 GPUs.

Dataset: COCO val2017 (1000 images)
Metrics: FID, CLIP Score, mean inference time, speedup ratio
Steps: 25 DDIM steps
Batch size: 8

Results:
| Model | Speedup | FID ↑ | CLIP Δ |
| ----- | ------- | ----- | ------ |
| SD1.5 | 2.63×    | -0.841   | 0.0033  |
| SD2.1 | 2.86×    | 12.167  | 0.0075  |

| Model Name, Cache Setting | Total Time | Mean Time | Variance Time | STD Time |FID Score| CLIP Score | Throughput | UNet MACs
|---|---|---|---|---|---|---|---|---|
| SD1.5, Cache=False | 2 hrs 21 mins 51 secs |0.4216 secs | 0.000003 secs | 0.001776 secs | 25.330 | 0.1419 | 1.90 img/s | 169.51 GMACs
| SD1.5, Cache=True | 59 mins 32 secs |0.1774 secs | 0.000041 secs | 0.006391 secs | 24.489 | 0.1452 | 3.51 imgs/s | 169.51 GMACs
| SD2.1, Cache=False | 2 hrs 9 min 42 secs|0.3568 secs | 0.000002 secs | 0.001226 secs |  29.861 | 0.1479 | 2.14 img/s | 169.75 GMACs
| SD2.1, Cache=True | 51 mins 30 secs |0.1326 secs | 0.000008 secs | 0.002817 secs |  42.028 | 0.1554 | 4.09 img/s | 169.75 GMACs
