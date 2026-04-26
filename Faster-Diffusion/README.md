Folder containing the code and requirements for the Faster-Diffusion Model

Hardware: Tested on RunPod A100 40GB GPU. Minimum 40GB container disk recommended.

Faster-Diffusion Benchmark — SD v1.5 and SD v2.1
Benchmarks Faster-Diffusion (NeurIPS 2024) as an inference acceleration method for Stable Diffusion, evaluated against a baseline on SD v1.5 and SD v2.1.

Method:
Faster-Diffusion accelerates inference by reusing U-Net encoder features across adjacent timesteps, avoiding redundant computation without any retraining. Integrated via register_parallel_pipeline and register_faster_forward with mod='50ls'.


Dataset: COCO val2017 (1000 images)
Metrics: FID, CLIP Score, mean inference time, speedup ratio, time per image, peak VRAM
Steps: 25 steps
Batch size: 25

Results:

| Model                               | Mean Time/batch | Time/image | Var/image | Peak VRAM | FID    | CLIP   |
| ----------------------------------- | --------------- | ---------- | --------- | --------- | ------ | ------ |
| SD1.5 + Faster-Diffusion (mod=50ls) | 12.768s         | 0.399s     | 0.052s    | 20.84 GB  | 53.359 | 0.1464 |
| SD2.1 + Faster-Diffusion (mod=50ls) | 10.742s         | 0.336s     | 0.043s    | 20.67 GB  | 58.772 | 0.1525 |



Usage:
Open FasterDiffusion_SD15_SD21.ipynb in Jupyter and run all cells. The notebook handles COCO download, model loading, inference, and metric computation automatically.


Reference:
Li et al., "Faster Diffusion: Rethinking the Role of UNet Encoder in Diffusion Models", NeurIPS 2024