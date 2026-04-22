Folder containing the code and requirements for the Faster-Diffusion Model

Hardware: Tested on RunPod A40 40GB GPU. Minimum 80GB container disk recommended.

Faster-Diffusion Benchmark — SD v1.5 and SD v2.1
Benchmarks Faster-Diffusion (NeurIPS 2024) as an inference acceleration method for Stable Diffusion, evaluated against a baseline on SD v1.5 and SD v2.1.

Method:
Faster-Diffusion accelerates inference by reusing U-Net encoder features across adjacent timesteps, avoiding redundant computation without any retraining. Integrated via register_parallel_pipeline and register_faster_forward with mod='50ls'.


Dataset: COCO val2017 (1000 images)
Metrics: FID, CLIP Score, mean inference time, speedup ratio
Steps: 25 DDIM steps
Batch size: 8

Results:
| Model | Speedup | FID ↑ | CLIP Δ |
| ----- | ------- | ----- | ------ |
| SD1.5 | 0.99×   | 1.588 | -0.0006 |
| SD2.1 | 0.98×   | 0.473 | +0.0019 |

| Faster-Diffusion Model Name     | Mean Time  | Var. Time  | FID Score | CLIP Score |
| ------------------------------- | ---------- | ---------- | --------- | ---------- |
| SD1.5, Faster=False             | 6.925 secs | 0.071 secs | 53.599    | 0.1459     |
| SD1.5, Faster=True  (mod=50ls)  | 7.021 secs | 0.068 secs | 55.187    | 0.1453     |
| SD2.1, Faster=False             | 5.823 secs | 0.028 secs | 58.546    | 0.1513     |
| SD2.1, Faster=True  (mod=50ls)  | 5.915 secs | 0.024 secs | 59.019    | 0.1532     |


Evaluation:
Faster-Diffusion demonstrated 1.7x speedup on RTX 3090 in the original paper's single-image benchmark. However on A40 with batch size 8 no meaningful speedup was observed, suggesting the method's benefits are hardware-dependent and most pronounced on memory-bandwidth-constrained consumer GPUs rather than high-throughput datacenter hardware.


Usage:
Open FasterDiffusion_SD15_SD21.ipynb in Jupyter and run all cells. The notebook handles COCO download, model loading, inference, and metric computation automatically.


Reference:
Li et al., "Faster Diffusion: Rethinking the Role of UNet Encoder in Diffusion Models", NeurIPS 2024